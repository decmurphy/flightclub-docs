FlightClub API documentation
############################

Contents:

.. toctree::
   :maxdepth: 1
   
   Companies
   Engines
   LaunchSites
   Missions
   Simulator
   Stages

All requests to the FlightClub API must be sent to the endpoint root

    ``https://www.flightclub.io:8443/FlightClub/api/{VERSION}/``
    
and all requests to the FlightSchool test server must be sent to
    
    ``https://www.flightclub.io:8443/FlightSchool/api/{VERSION}/``
    
Currently, the only active API version is 'v1'. 
The dedicated pages for each method provide example requests, responses 
and any other nuances you need to know.

Querying the root endpoint returns an API 'Table of Contents', which you can
traverse without the need for this documentation:
  
.. code-block :: json
  
    {
      "links": {
        "self": "https://www.flightclub.io:8443/FlightClub/api/v1/"
      },
      "data": {
        "type": "version",
        "id": "1",
        "links": {
          "companies": "https://www.flightclub.io:8443/FlightClub/api/v1/companies/",
          "engines": "https://www.flightclub.io:8443/FlightClub/api/v1/engines/",
          "launchsites": "https://www.flightclub.io:8443/FlightClub/api/v1/launchsites/",
          "missions": "https://www.flightclub.io:8443/FlightClub/api/v1/missions/",
          "stages": "https://www.flightclub.io:8443/FlightClub/api/v1/stages/"
        }
      }
    }

Good luck!
