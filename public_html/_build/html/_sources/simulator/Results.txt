Simulation Results
##################

HTTP Method
===========

``GET http://www.decmurphy.com:8080/FlightClub/api/v1/simulator/results?id=774520b1-3c1b-4c08-8953-fb11f79af50d&pl=JSN3``

Response
========

.. code-block:: json

  {
    "Output": {
      "Files": [],
      "Images": [
        {
          "desc": "globe",
          "url": "/FlightClub/output/eaca5b7d-5ed7-4707-aac7-cd8095db629e_globe.png"
        },
        {
          "desc": "ground-track",
          "url": "/FlightClub/output/eaca5b7d-5ed7-4707-aac7-cd8095db629e_ground-track.png"
        }
      ]
    }
  }

Response Overview
=================
  
+------------------+------------+-------------------------------------------------+
| Element          | Attribute  | Explanation                                     |
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