Missions
########

The parent endpoint returns a brief list of all missions in the database in
chronological order (not necessarily in order of ascending id). For a
launch profile and more verbose description of each, you'll need to drill down
into the children.

HTTP Method
===========

``GET http://www.decmurphy.com:8080/FlightClub/api/v1/missions/``

Response
========

.. code-block:: json

  {
    "data": [
      {
        "id": 1,
        "description": "FalconSAT-2",
        "links": {
          "self": "http://www.decmurphy.com:8080/FlightSchool/api/v1/missions/1/"
        },
        "code": "FSAT"
      },
      {
        "id": 2,
        "description": "DemoSat",
        "links": {
          "self": "http://www.decmurphy.com:8080/FlightSchool/api/v1/missions/2/"
        },
        "code": "DEMO"
      },
      {
        "id": 26,
        "description": "Jason-3",
        "links": {
          "self": "http://www.decmurphy.com:8080/FlightSchool/api/v1/missions/26/"
        },
        "code": "JSN3"
      },
      {
        "id": 28,
        "description": "SES-9",
        "links": {
          "self": "http://www.decmurphy.com:8080/FlightSchool/api/v1/missions/28/"
        },
        "code": "SES9"
      }
    ],
    "links": {
      "self": "http://www.decmurphy.com:8080/FlightSchool/api/v1/missions/"
    }
  }

Since the child response is pretty huge, we'll dissect it here. Let's take CRS-7
(RIP) as an example.

HTTP Method
===========

``GET http://www.decmurphy.com:8080/FlightClub/api/v1/missions/27/``

OR

``GET http://www.decmurphy.com:8080/FlightClub/api/v1/missions/CRS7/``

Response
========
  
.. code-block:: json

  {
    "Mission": {
      "code": "CRS7",
      "launchvehicle": "F91",
      "launchsite": "LC40",
      "dateTime": "2015-06-28T14:21:11.000-04:00",
      "Profile": {
        "Payload": {
          "mass": 6678,
          "code": "DRG1"
        },
        "Stages": [
          {
            "Core": {
              "id": 0,
              "legs": true
            },
            "release": 0,
            "PitchKick": {
              "start": 7,
              "pitch": 2.35,
              "yaw": 47
            },
            "Burns": [
              {
                "tag": "init",
                "start": -2,
                "end": 160,
                "engines": 9,
                "throttle": 1
              },
              {
                "tag": "boost",
                "start": 220,
                "end": 230,
                "engines": 3,
                "throttle": 1
              },
              {
                "tag": "entry",
                "start": 380,
                "end": 440,
                "engines": 1,
                "throttle": 1
              },
              {
                "tag": "landing",
                "start": 460,
                "engines": 1,
                "throttle": 1
              }
            ],
            "Course": [
              {
                "tag": "gravturn",
                "start": 55,
                "Attitude": {
                  "gt": "fgt"
                }
              },
              {
                "tag": "boost",
                "Attitude": {
                  "pitch": -28.5
                }
              },
              {
                "tag": "entry",
                "Attitude": {
                  "gt": "rgt"
                }
              },
              {
                "tag": "landing",
                "Attitude": {
                  "gt": "rgt"
                }
              }
            ]
          },
          {
            "Core": {
              "id": 1,
              "legs": false
            },
            "release": 162,
            "Burns": [
              {
                "tag": "init",
                "start": 165,
                "engines": 1,
                "throttle": 1
              }
            ],
            "Course": [
              {
                "tag": "guidance-1",
                "start": 340,
                "Attitude": {
                  "pitch": 0
                }
              }
            ]
          }
        ]
      }
    }
  }
  
Response Overview
=================
  
+-----------+---------------+----------------------------------------------------+
| Element   | Attribute     | Explanation                                        |
+-----------+---------------+----------------------------------------------------+
| Mission   | code          || ``code`` from ``missions/``                       |
|           +---------------+----------------------------------------------------+
|           | launchvehicle || ``code`` from ``launchvehicles/``                 |
|           +---------------+----------------------------------------------------+
|           | launchsite    || ``code`` from ``launchsites/``                    |
|           +---------------+----------------------------------------------------+
|           | dateTime      || Date & time of launch (UTC)                       |
|           +---------------+----------------------------------------------------+
|           | **Profile**   || TODO: Change to ``Vehicle``                       |
+-----------+---------------+----------------------------------------------------+
| Profile   | **Payload**   || Object holding Payload info                       |
+-----------+---------------+----------------------------------------------------+
| Payload   | code          || ``code`` from ``payloads/``                       |
|           +---------------+----------------------------------------------------+
|           | mass          || Mass of payload (kg)                              |
+-----------+---------------+----------------------------------------------------+
| Profile   | **Stages**    || Array of stages and their flight profiles         |
+-----------+---------------+----------------------------------------------------+
| Stages    | **Core**      || Core information about a stage                    |
+-----------+---------------+----------------------------------------------------+
| Core      | id            || Stage id (integer, zero-based)                    |
|           +---------------+----------------------------------------------------+
|           | legs          || Whether or not stage has legs (boolean)           |
+-----------+---------------+----------------------------------------------------+
| Stages    | release       || Time of stage release (T+xxx s). For the first    |
|           |               || stage, this is launch time. For the higher stages,|
|           |               || this is the time of separation from the stage     |
|           |               || below.                                            |
|           +---------------+----------------------------------------------------+
|           | **PitchKick** || All other values for pitch and yaw are absolute.  |
|           |               || Pitch-kick values are delta-values.               |
+-----------+---------------+----------------------------------------------------+
| PitchKick | start         || Start time for pitch-kick (T+xxx s)               |
|           +---------------+----------------------------------------------------+
|           | pitch         || Change in pitch (deg)                             |
|           +---------------+----------------------------------------------------+
|           | yaw           || Change in yaw (deg)                               |
+-----------+---------------+----------------------------------------------------+
| Stages    | **Burns**     || Array of burns executed in flight profile         |
+-----------+---------------+----------------------------------------------------+
| Burns     | tag           || Plain-text identifier                             |
|           +---------------+----------------------------------------------------+
|           | start         || Start time (T+xxx s)                              |
|           +---------------+----------------------------------------------------+
|           | end           || (optional) End time (T+xxx s). If omitted, stage  |
|           |               || burns until crash/no fuel.                        |
|           +---------------+----------------------------------------------------+
|           | engines       || Number of engines used in burn (int)              |
|           +---------------+----------------------------------------------------+
|           | throttle      || Engine throttle during burn (t_min<=t<=1). t_min  |
|           |               || determined by engines on chosen launch vehicle    |
+-----------+---------------+----------------------------------------------------+
| Stages    | **Course**    || Array of course corrections in flight profile     |
+-----------+---------------+----------------------------------------------------+
| Course    | tag           || (optional) Plain-text identifier. If ``start`` is |
|           |               || empty and this matches a Burn ``tag``, the Burn's |
|           |               || start time will be used for this correction.      |
|           +---------------+----------------------------------------------------+
|           | start         || (optional if tag included) Start time (T+xxx s)   |
|           +---------------+----------------------------------------------------+
|           | end           || (optional) End time (T+xxx s)                     |
|           +---------------+----------------------------------------------------+
|           | **Attitude**  || If you specify ``pitch`` or ``yaw`` here, you     |
|           |               || **cannot** specify ``gt``, and vice versa.        |
+-----------+---------------+----------------------------------------------------+
| Attitude  | pitch         || (optional) Pitch param (degrees)                  |
+-----------+---------------+----------------------------------------------------+
|           | yaw           || (optional) Yaw param (degrees)                    |
|           +---------------+----------------------------------------------------+
|           | gt            || (optional) Gravity Turn can be "fgt","rgt"        |
|           |               || TODO: Change to "FORWARD"/"REVERSE"               |
|           +---------------+----------------------------------------------------+
|           | throttle      || (optional) Throttle param t, t_min<=t<=1. t_min   |
|           |               || specified by launch vehicle's engines             |
+-----------+---------------+----------------------------------------------------+