New Simulation
##############

HTTP Method
===========

``POST http://www.decmurphy.com:8080/FlightClub/api/v1/simulator/new/``

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
      "url": "http://www.decmurphy.com:8080/FlightClub/api/v1/simulator/results?id=774520b1-3c1b-4c08-8953-fb11f79af50d&pl=JSN3"
    }
  }

Response Overview
=================

+---------+-----------+----------------------------------------------+
| Element | Attribute | Explanation                                  |
+---------+-----------+----------------------------------------------+
| Mission | success   | Success flag (boolean)                       |
|         +-----------+----------------------------------------------+
|         | url       | API ``GET`` method for output images/files   |
+---------+-----------+----------------------------------------------+
