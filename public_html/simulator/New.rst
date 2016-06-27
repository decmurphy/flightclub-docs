New Simulation
##############

HTTP Method
===========

``POST https://www.flightclub.io:8443/FlightClub/api/v1/simulator/new/``

This method must include the following headers:

``Content-Type: application/json``

Request
=======

Request structure is identical to ``missions/{id}/`` response!

Response
========

.. code-block:: json

  {
    "Mission": {
      "errors": [],
      "warnings": [
        "Burn occurring before Release for stage 0"
      ],
      "success": true,
      "output": "https://www.flightclub.io:8443/FlightClub/api/v1/simulator/results?id=774520b1-3c1b-4c08-8953-fb11f79af50d&code=JSN3"
    }
  }

Response Overview
=================

+---------+-----------+----------------------------------------------+
| Element | Attribute | Explanation                                  |
+---------+-----------+----------------------------------------------+
| Mission | errors    | Any errors which made the sim impossible to  |
|         |           | run.                                         |
|         +-----------+----------------------------------------------+
|         | warnings  | A sim can still be run with warnings, but    |
|         |           | results might not be complete                |
|         +-----------+----------------------------------------------+
|         | success   | Success flag (boolean)                       |
|         +-----------+----------------------------------------------+
|         | output    | API ``GET`` method for output images/files   |
+---------+-----------+----------------------------------------------+
