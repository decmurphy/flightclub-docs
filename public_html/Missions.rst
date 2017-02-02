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
    "links": {
      "self": "https://www.flightclub.io:8443/FlightClub/api/v1/missions/"
    },
    "data": [
      {
        "id": 49,
        "code": "AP11",
        "description": "Apollo 11",
        "date": "1969-07-16",
        "time": "13:32:00",
        "launchsite": "K39A",
        "company": "NASA",
        "display": true,
        "links": {
          "self": "https://www.flightclub.io:8443/FlightClub/api/v1/missions/AP11/"
        }
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
      "company": "SPX",
      "display": true,
      "livelaunch": "c47f2778-2f9f-4284-95c4-1d91431d3e9b",
      "Payload": {
        "mass": 6678.0
      },
      "Vehicle": {
        "Stages": [
          {
            "id": 6,
            "name": "Falcon 9v1.1 Stage 1",
            "radius": 1.83,
            "length": 45.7,
            "dryMass": 22100.0,
            "fuelCapacity": 395700.0,
            "maxAccel": 6.0,
            "propMass": 395700.0,
            "minimumFuel": 200.0,
            "stageNumber": 0,
            "stageName": "Falcon 9v1.1 Stage 1",
            "Engines": [
              {
                "engineId": 0,
                "number": 9,
                "Engine": {
                  "id": 6,
                  "name": "Merlin 1D",
                  "mass": 470.0,
                  "ispSL": 282.0,
                  "ispVac": 311.0,
                  "thrustSL": 654000.0,
                  "thrustVac": 716000.0,
                  "throttleCapability": 0.55
                }
              }
            ],
            "Boosters": []
          },
          {
            "id": 7,
            "name": "Falcon 9v1.1 Stage 2",
            "radius": 1.83,
            "length": 15.2,
            "dryMass": 3900.0,
            "fuelCapacity": 92670.0,
            "maxAccel": 6.0,
            "propMass": 92670.0,
            "minimumFuel": 200.0,
            "stageNumber": 1,
            "stageName": "Falcon 9v1.1 Stage 2",
            "Engines": [
              {
                "engineId": 0,
                "number": 1,
                "Engine": {
                  "id": 7,
                  "name": "Merlin 1D Vac",
                  "mass": 470.0,
                  "ispVac": 345.0,
                  "thrustVac": 801000.0,
                  "throttleCapability": 0.45
                }
              }
            ],
            "Boosters": []
          }
        ]
      },
      "Events": [
        {
          "type": "IGNITION",
          "name": "Main Engine Ignition",
          "Engines": [
            {
              "engineId": 0,
              "number": 9
            }
          ],
          "stageNumbers": [
            0
          ],
          "time": -1.0,
          "dynamic": false,
          "Attitude": {}
        },
        {
          "type": "LAUNCH",
          "name": "Launch",
          "Engines": [],
          "stageNumbers": [
            0
          ],
          "time": 0.0,
          "dynamic": false,
          "Attitude": {}
        },
        {
          "type": "GUIDANCE",
          "name": "Pitch Kick",
          "Engines": [],
          "stageNumbers": [
            0
          ],
          "time": 7.0,
          "dynamic": false,
          "Attitude": {
            "pitch": 86.9000015258789,
            "yaw": 47.0
          }
        },
        {
          "type": "GUIDANCE",
          "name": "Gravity Turn",
          "Engines": [],
          "stageNumbers": [
            0
          ],
          "time": 55.0,
          "dynamic": false,
          "Attitude": {
            "gt": "FORWARD"
          }
        },
        {
          "type": "CUTOFF",
          "name": "MECO-1",
          "Engines": [
            {
              "engineId": 0,
              "number": 9
            }
          ],
          "stageNumbers": [
            0
          ],
          "time": 139.0,
          "dynamic": false,
          "Attitude": {}
        },
        {
          "type": "SEPARATION",
          "name": "First Stage Separation",
          "Engines": [],
          "stageNumbers": [
            0
          ],
          "time": 140.0,
          "dynamic": false,
          "Attitude": {}
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
| Payload   | mass          || Mass of payload (kg)                              |
+-----------+---------------+----------------------------------------------------+
| Vehicle   | **Stages**    || This element is identical to the ``stages``       |
|           |               || response, but includes 3 extra elements           |
+-----------+---------------+----------------------------------------------------+
| Stages    | stageNumber   || 0-based index, used for linking stages to events  |
+-----------+---------------+----------------------------------------------------+
|           | stageName     || Descriptive only                                  |
+-----------+---------------+----------------------------------------------------+
|           | **Engines**   || An array of Engine types used on this stage       |
+-----------+---------------+----------------------------------------------------+
|           | **Boosters**  || An array of Stage types used as boosters on this  |
|           |               || Stage. A Booster element is identical to a Stage  |
|           |               || element, but it doesn't have a Booster element of |
|           |               || its own.                                          |
+-----------+---------------+----------------------------------------------------+
| Engines   | engineId      || 0-based index, used for linking engines to events |
+-----------+---------------+----------------------------------------------------+
|           | number        || The amount of engines of this engine type         |
+-----------+---------------+----------------------------------------------------+
|           | **Engine**    || This element is identical to the ``engines``      |
|           |               || response                                          |
+-----------+---------------+----------------------------------------------------+
| Events    | type          || Event type. Can be one of: IGNITION, CUTOFF,      |
|           |               || SEPARATION, GUIDANCE, FAIRING_SEP, PAYLOAD_SEP    |
|           +---------------+----------------------------------------------------+
|           | name          || Plain text description                            |
|           +---------------+----------------------------------------------------+
|           | Engines       || Array - links event to engines via ``Engine.id``  |
|           +---------------+----------------------------------------------------+
|           | stageNumbers  || Array - links event to stages via ``Stage.id``    |
|           +---------------+----------------------------------------------------+
|           | time          || Time (seconds relative to T-0) to begin event     |
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
|           |               || specified by ``Engine.throttleCapability``.       |
+-----------+---------------+----------------------------------------------------+
