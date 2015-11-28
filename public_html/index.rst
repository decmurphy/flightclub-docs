FlightClub API documentation
############################

Contents:

.. toctree::
   :maxdepth: 1
   
   LaunchSites
   LaunchVehicles
   Missions
   Payloads
   Simulator

All requests to the FlightClub API must be sent to the endpoint root

    ``http://www.flightclub.io:8080/FlightClub/api/{VERSION}/``
    
and all requests to the FlightSchool test server must be sent to
    
    ``http://www.flightclub.io:8080/FlightSchool/api/{VERSION}/``
    
Currently, the only active API version is 'v1'. 
The dedicated pages for each method provide example requests, responses 
and any other nuances you need to know.

Querying the root endpoint returns an API 'Table of Contents', which you can
traverse without the need for this documentation:
  
.. code-block :: json
  
  {
    "data": [
      {
        "type": "version",
        "id": "1",
        "links": {
          "launchsites": "http://www.flightclub.io:8080/FlightClub/api/v1/launchsites/",
          "launchvehicles": "http://www.flightclub.io:8080/FlightClub/api/v1/launchvehicles/",
          "payloads": "http://www.flightclub.io:8080/FlightClub/api/v1/payloads/",
          "missions": "http://www.flightclub.io:8080/FlightClub/api/v1/missions/"
        }
      }
    ],
    "links": {
      "self": "http://www.flightclub.io:8080/FlightClub/api/v1/"
    }
  }

Good luck!
