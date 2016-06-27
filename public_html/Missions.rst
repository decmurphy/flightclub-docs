Missions
########

The parent endpoint returns a brief list of all missions in the database in
chronological order (not necessarily in order of ascending id). For a
launch profile and more verbose description of each, you'll need to drill down
into the children.

HTTP Method
===========

``GET https://www.flightclub.io:8443/FlightClub/api/v1/missions/``

``GET https://www.flightclub.io:8443/FlightClub/api/v1/missions/?display=1``

``GET https://www.flightclub.io:8443/FlightClub/api/v1/missions/?company=SPX``

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
        "company": "SPX",
        "payload": "SATL",
        "links": {
          "self": "https://www.flightclub.io:8443/FlightClub/api/v1/missions/1/"
        },
        "code": "FSAT"
      },
      {
        "id": 2,
        "launchsite": "OMLK",
        "description": "DemoSat",
        "launchvehicle": "F1A",
        "company": "SPX",
        "payload": "SATL",
        "links": {
          "self": "https://www.flightclub.io:8443/FlightClub/api/v1/missions/2/"
        },
        "code": "DEMO"
      }
    ],
    "links": {
      "self": "https://www.flightclub.io:8443/FlightClub/api/v1/missions/"
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
      "company": "SPX",
      "display": true,
      "livelaunch": "c47f2778-2f9f-4284-95c4-1d91431d3e9b",
      "Payload": {
        "code": "DRG1",
        "mass": 6678
      },
      "Stages": [
        {
          "id": 0,
          "name": "Booster",
          "legs": true
        },
        {
          "id": 1,
          "name": "UpperStage",
          "legs": false
        }
      ],
      "Events": [
        {
          "type": "IGNITION",
          "stage": 0,
          "name": "Main Engine Ignition",
          "engines": 9,
          "time": -1,
          "end": null,
          "dynamic": false,
          "Attitude": {
            "pitch": null,
            "yaw": null,
            "gt": null,
            "throttle": null
          }
        },
        {
          "type": "SEPARATION",
          "stage": 0,
          "name": "Launch",
          "engines": null,
          "time": 0,
          "end": null,
          "dynamic": null,
          "Attitude": {
            "pitch": null,
            "yaw": null,
            "gt": null,
            "throttle": null
          }
        },
        {
          "type": "GUIDANCE",
          "stage": 0,
          "name": "Pitch Kick",
          "engines": null,
          "time": 7,
          "end": null,
          "dynamic": null,
          "Attitude": {
            "pitch": 86.900001525879,
            "yaw": 47,
            "gt": null,
            "throttle": null
          }
        },
        {
          "type": "GUIDANCE",
          "stage": 0,
          "name": "Gravity Turn",
          "engines": null,
          "time": 55,
          "end": null,
          "dynamic": null,
          "Attitude": {
            "pitch": null,
            "yaw": null,
            "gt": "FORWARD",
            "throttle": null
          }
        },
        {
          "type": "CUTOFF",
          "stage": 0,
          "name": "MECO-1",
          "engines": 9,
          "time": 139,
          "end": null,
          "dynamic": false,
          "Attitude": {
            "pitch": null,
            "yaw": null,
            "gt": null,
            "throttle": null
          }
        },
        {
          "type": "SEPARATION",
          "stage": 1,
          "name": "First Stage Separation",
          "engines": null,
          "time": 140,
          "end": null,
          "dynamic": null,
          "Attitude": {
            "pitch": null,
            "yaw": null,
            "gt": null,
            "throttle": null
          }
        }
      ]
    }
  }
  
Response Overview
=================
  
All fields required unless marked ``optional``. Some fields only required 
based on choice of ``Events.type``.
  
+-----------+---------------+----------------------------------------------------+
| Element   | Attribute     | Explanation                                        |
+-----------+---------------+----------------------------------------------------+
| Mission   | code          || ``code`` from ``missions/``                       |
|           +---------------+----------------------------------------------------+
|           | description   || Plain text mission name                           |
|           +---------------+----------------------------------------------------+
|           | date          || Date of launch (UTC)                              |
|           +---------------+----------------------------------------------------+
|           | time          || Time of launch (UTC)                              |
|           +---------------+----------------------------------------------------+
|           | launchsite    || ``code`` from ``launchsites/``                    |
|           +---------------+----------------------------------------------------+
|           | launchvehicle || ``code`` from ``launchvehicles/``                 |
|           +---------------+----------------------------------------------------+
|           | company       || ``code`` from ``companies/``                      |
|           +---------------+----------------------------------------------------+
|           | display       || boolean value for whether or not to show on client|
|           +---------------+----------------------------------------------------+
|           | livelaunch    || ID for simulation to be used for plotting live    |
|           +---------------+----------------------------------------------------+
|           | **Payload**   || Object holding Payload info                       |
|           +---------------+----------------------------------------------------+
|           | **Stages**    || Array of Stages and their details                 |
|           +---------------+----------------------------------------------------+
|           | **Events**    || Array of Events making up the flight profile      |
+-----------+---------------+----------------------------------------------------+
| Payload   | code          || ``code`` from ``payloads/``                       |
|           +---------------+----------------------------------------------------+
|           | mass          || Mass of payload (kg)                              |
+-----------+---------------+----------------------------------------------------+
| Stages    | id            || 0-based incremental index                         |
+-----------+---------------+----------------------------------------------------+
|           | name          || Name of Stage                                     |
+-----------+---------------+----------------------------------------------------+
|           | legs          || boolean value - if Stage has legs attached. Legs  |
|           |               || add extra mass to Stage.                          |
+-----------+---------------+----------------------------------------------------+
| Events    | type          || Event type. Can be one of: IGNITION, CUTOFF,      |
|           |               || SEPARATION, GUIDANCE, FAIRING_SEP, PAYLOAD_SEP    |
|           +---------------+----------------------------------------------------+
|           | name          || Plain text description                            |
|           +---------------+----------------------------------------------------+
|           | stage         || Links event to stage via ``Stage.id``             |
|           +---------------+----------------------------------------------------+
|           | time          || Time (seconds relative to T-0) to begin event     |
|           +---------------+----------------------------------------------------+
|           | engines       || (If IGNITION) Number of engines                   |
|           +---------------+----------------------------------------------------+
|           | end           || (If GUIDANCE, optional) Time maneouvre should end.|
|           |               || ``time`` and ``end`` can be used together to      |
|           |               || manipulate the rate of changing throttle, pitch,  |
|           |               || yaw, etc. If empty, maneouvre happens as fast as  |
|           |               || possible.                                         |
|           +---------------+----------------------------------------------------+
|           | dynamic       || (If IGNITION, optional) A dynamic burn is a       |
|           |               || hoverslam. To be used for landing burns. Vastly   |
|           |               || increases computational time if invoked too early.|
|           +---------------+----------------------------------------------------+
|           | **Attitude**  || (If GUIDANCE) If you specify ``pitch`` or ``yaw`` |
|           |               || here, you **cannot** specify ``gt``, vice versa.  |
+-----------+---------------+----------------------------------------------------+
| Attitude  | pitch         || (optional) Target pitch (degrees)                 |
+-----------+---------------+----------------------------------------------------+
|           | yaw           || (optional) Target yaw (degrees)                   |
|           +---------------+----------------------------------------------------+
|           | gt            || (optional) Set target heading to be a Gravity     |
|           |               || Turn. Can be one of: FORWARD, REVERSE             |
|           +---------------+----------------------------------------------------+
|           | throttle      || (optional) Target throttle t: t_min<=t<=1. t_min  |
|           |               || specified by launch vehicle's engines.            |
+-----------+---------------+----------------------------------------------------+
