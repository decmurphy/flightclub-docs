Payloads
#################

HTTP Method
===========

``GET http://www.decmurphy.com:8080/FlightClub/api/v1/payloads/``

Response
========
  
.. code-block:: json

  {
    "data": [
      {
        "id": 1,
        "description": "Dragon 1",
        "links": {
          "self": "http://www.decmurphy.com:8080/FlightSchool/api/v1/payloads/1/"
        },
        "code": "DRG1"
      },
      {
        "id": 2,
        "description": "Dragon 2",
        "links": {
          "self": "http://www.decmurphy.com:8080/FlightSchool/api/v1/payloads/2/"
        },
        "code": "DRG2"
      },
      {
        "id": 3,
        "description": "Satellite",
        "links": {
          "self": "http://www.decmurphy.com:8080/FlightSchool/api/v1/payloads/3/"
        },
        "code": "SATL"
      }
    ],
    "links": {
      "self": "http://www.decmurphy.com:8080/FlightSchool/api/v1/payloads/"
    }
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