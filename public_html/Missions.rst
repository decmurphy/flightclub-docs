Missions
########

The parent endpoint returns a brief list of all missions in the database in
chronological order (not necessarily in order of ascending id). For a
launch profile and more verbose description of each, you'll need to drill down
into the children.

HTTP Method
===========

``GET https://www.flightclub.io:8443/FlightClub/api/v1/missions/``

Response
========

.. code-block:: json

  {
    "data": [
      {
        "id": 1,
        "launchsite": "OMLK",
        "description": "FalconSAT-2",
        "launchvehicle": "F1A",
        "payload": "SATL",
        "links": {
          "self": "http://localhost:8080/FlightClub/api/v1/missions/1/"
        },
        "code": "FSAT"
      },
      {
        "id": 2,
        "launchsite": "OMLK",
        "description": "DemoSat",
        "launchvehicle": "F1A",
        "payload": "SATL",
        "links": {
          "self": "http://localhost:8080/FlightClub/api/v1/missions/2/"
        },
        "code": "DEMO"
      },
      {
        "id": 30,
        "launchsite": "LC40",
        "description": "Orbcomm OG2 Mission 2",
        "launchvehicle": "F92",
        "payload": "SATL",
        "links": {
          "self": "http://localhost:8080/FlightClub/api/v1/missions/30/"
        },
        "code": "OG22"
      },
      {
        "id": 26,
        "launchsite": "LC4E",
        "description": "Jason-3",
        "launchvehicle": "F91",
        "payload": "SATL",
        "links": {
          "self": "http://localhost:8080/FlightClub/api/v1/missions/26/"
        },
        "code": "JSN3"
      }
    ],
    "links": {
      "self": "http://localhost:8080/FlightClub/api/v1/missions/"
    }
  }

Since the child response is pretty huge, we'll dissect it here. Let's take CRS-7
(RIP) as an example.

HTTP Method
===========

``GET https://www.flightclub.io:8443/FlightClub/api/v1/missions/27/``

OR

``GET https://www.flightclub.io:8443/FlightClub/api/v1/missions/CRS7/``

Response
========
  
.. code-block:: json

  {
    "Mission": {
      "code": "CRS7",
      "description": "CRS-7",
      "date": "2015-06-28",
      "time": "14:21:11",
      "launchsite": "LC40",
      "launchvehicle": "F91",
      "Profile": {
        "Payload": {
          "code": "DRG1",
          "mass": "6678"
        },
        "Stages": [
          {
            "Core": {
              "id": "0",
              "legs": "true"
            },
            "release": "0",
            "PitchKick": {
              "start": "7",
              "pitch": "2.35",
              "yaw": "47"
            },
            "Burns": [
              {
                "tag": "init",
                "engines": "9",
                "start": "-2",
                "end": "160"
              },
              {
                "tag": "boost",
                "engines": "3",
                "start": "220",
                "end": "230"
              },
              {
                "tag": "entry",
                "engines": "1",
                "start": "380",
                "end": "440"
              },
              {
                "tag": "landing",
                "engines": "1",
                "start": "460"
              }
            ],
            "Course": [
              {
                "tag": "gravturn",
                "start": "55",
                "Attitude": {
                  "gt": "fgt"
                }
              },
              {
                "tag": "boost",
                "Attitude": {
                  "pitch": "-28.5"
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
              "id": "1",
              "legs": "false"
            },
            "release": "162",
            "Burns": [
              {
                "tag": "init",
                "engines": "1",
                "start": "165"
              }
            ],
            "Course": [
              {
                "tag": "guidance-1",
                "start": "340",
                "Attitude": {
                  "pitch": "0"
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
|           | description   || Plain text mission name                           |
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