Simulation Results
##################

HTTP Method
===========

``GET https://www.flightclub.io:8443/FlightClub/api/v1/simulator/results?id=774520b1-3c1b-4c08-8953-fb11f79af50d&code=JSN3``

Response
========

.. code-block:: json

  {
    "Mission": {
      "desc": "Jason-3",
      "Output": {
        "Files": [],
        "Images": [
          {
            "desc": "globe",
            "url": "http://localhost:8080/FlightClub/output/774520b1-3c1b-4c08-8953-fb11f79af50d_globe.png"
          },
          {
            "desc": "ground-track",
            "url": "http://localhost:8080/FlightClub/output/774520b1-3c1b-4c08-8953-fb11f79af50d_ground-track.png"
          }
        ]
      }
    }
  }

Response Overview
=================
  
+------------------+------------+-------------------------------------------------+
| Element          | Attribute  | Explanation                                     |
+------------------+------------+-------------------------------------------------+
| Mission          | desc       | Plain text mission name                         |
|                  +------------+-------------------------------------------------+
|                  | **Output** | Collection of output images                     |
+------------------+------------+-------------------------------------------------+
| Output           | **Files**  | Array of output files and their paths           |
|                  +------------+-------------------------------------------------+
|                  | **Images** | Array of some output graphs and their paths     |
+------------------+------------+-------------------------------------------------+
| Files            | desc       | Plain text description of data file             |
|                  +------------+-------------------------------------------------+
|                  | url        | API ``GET`` path to data file                   |
+------------------+------------+-------------------------------------------------+
| Images           | desc       | Plain text description of image                 |
|                  +------------+-------------------------------------------------+
|                  | url        | API ``GET`` path to image                       |
+------------------+------------+-------------------------------------------------+