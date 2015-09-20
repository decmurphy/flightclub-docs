LaunchSites
###########

HTTP Method
===========

``GET http://www.decmurphy.com:8080/FlightClub/api/v1/launchsites/``

Response
========
  
.. code-block:: json

  {
    "data": [
      {
        "id": 1,
        "code": "OMLK",
        "description": "Omelek Island, Kwajalein Atoll",
        "links": {
          "self": "http://www.decmurphy.com:8080/FlightSchool/api/v1/launchsites/1/"
        }
      },
      {
        "id": 2,
        "code": "LC40",
        "description": "CCAFS SLC-40",
        "links": {
          "self": "http://www.decmurphy.com:8080/FlightSchool/api/v1/launchsites/2/"
        }
      },
      {
        "id": 3,
        "code": "LC4E",
        "description": "Vandenburg SLC-4E",
        "links": {
          "self": "http://www.decmurphy.com:8080/FlightSchool/api/v1/launchsites/3/"
        }
      },
      {
        "id": 4,
        "code": "K39A",
        "description": "KSC 39-A",
        "links": {
          "self": "http://www.decmurphy.com:8080/FlightSchool/api/v1/launchsites/4/"
        }
      },
      {
        "id": 5,
        "code": "BOCA",
        "description": "Boca Chica, Texas",
        "links": {
          "self": "http://www.decmurphy.com:8080/FlightSchool/api/v1/launchsites/5/"
        }
      },
      {
        "id": 6,
        "code": "EQTR",
        "description": "Equatorial Launch Site",
        "links": {
          "self": "http://www.decmurphy.com:8080/FlightSchool/api/v1/launchsites/6/"
        }
      }
    ],
    "links": {
      "self": "http://www.decmurphy.com:8080/FlightSchool/api/v1/launchsites/"
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