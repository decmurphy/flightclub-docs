Simulation Results
##################

HTTP Method
===========

``GET https://www.flightclub.io:8443/FlightClub/api/v1/simulator/results/?id=972a55e9-67a1-40e2-885e-f35968abbcbd&code=CRS9``

Response
========

.. code-block:: json

  {
    "Mission": {
      "desc": "CRS-9",
      "Output": {
        "Files": [
          {
            "desc": "telemetry",
            "url": "/output/972a55e9-67a1-40e2-885e-f35968abbcbd_telemetry"
          },
          {
            "desc": "warnings",
            "url": "/output/972a55e9-67a1-40e2-885e-f35968abbcbd_warnings"
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
+------------------+------------+-------------------------------------------------+
| Files            | desc       | Plain text description of data file             |
|                  +------------+-------------------------------------------------+
|                  | url        | API ``GET`` path to data file                   |
+------------------+------------+-------------------------------------------------+