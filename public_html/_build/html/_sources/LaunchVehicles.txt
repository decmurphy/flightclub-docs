LaunchVehicles
##############

HTTP Method
===========

``GET http://www.decmurphy.com:8080/FlightClub/api/v1/launchvehicles/``

Response
========
  
.. code-block:: json

  {
    "data": [
      {
        "id": 1,
        "code": "F1A",
        "description": "Falcon 1 (Merlin 1A)",
        "links": {
          "self": "http://www.decmurphy.com:8080/FlightSchool/api/v1/launchvehicles/1/"
        }
      },
      {
        "id": 2,
        "code": "F1C",
        "description": "Falcon 1 (Merlin 1C)",
        "links": {
          "self": "http://www.decmurphy.com:8080/FlightSchool/api/v1/launchvehicles/2/"
        }
      },
      {
        "id": 3,
        "code": "FN9",
        "description": "Falcon 9v1.0",
        "links": {
          "self": "http://www.decmurphy.com:8080/FlightSchool/api/v1/launchvehicles/3/"
        }
      },
      {
        "id": 4,
        "code": "F91",
        "description": "Falcon 9v1.1",
        "links": {
          "self": "http://www.decmurphy.com:8080/FlightSchool/api/v1/launchvehicles/4/"
        }
      },
      {
        "id": 5,
        "code": "F92",
        "description": "Falcon 9v1.2",
        "links": {
          "self": "http://www.decmurphy.com:8080/FlightSchool/api/v1/launchvehicles/5/"
        }
      },
      {
        "id": 6,
        "code": "FNH",
        "description": "Falcon Heavy",
        "links": {
          "self": "http://www.decmurphy.com:8080/FlightSchool/api/v1/launchvehicles/6/"
        }
      }
    ],
    "links": {
      "self": "http://www.decmurphy.com:8080/FlightSchool/api/v1/launchvehicles/"
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