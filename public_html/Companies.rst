Companies
#################

HTTP Method
===========

``GET https://www.flightclub.io:8443/FlightClub/api/v1/companies/``

Response
========
  
.. code-block:: json

  {
    "links": {
      "self": "https://www.flightclub.io:8443/FlightClub/api/v1/companies/"
    },
    "data": [
      {
        "id": 3,
        "code": "ULA",
        "description": "United Launch Alliance",
        "links": {
          "self": "https://www.flightclub.io:8443/FlightClub/api/v1/companies/3/"
        }
      }
    ]
  }
  
Response Overview
=================
  
+--------------+-------------+----------------------------------------------+
| Element      | Attribute   | Explanation                                  |
+--------------+-------------+----------------------------------------------+
| data         | id          | Incremental 1-based identifier               |
|              +-------------+----------------------------------------------+
|              | code        | Constant enum identifier                     |
|              +-------------+----------------------------------------------+
|              | description | Plain text description                       |
|              +-------------+----------------------------------------------+
|              | **links**   |                                              |
+--------------+-------------+----------------------------------------------+
| links        | self        | The URL that returns this element            |
+--------------+-------------+----------------------------------------------+