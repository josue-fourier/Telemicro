# Telemicro

A project that seeks to showcase Telematics skills through the development 
of a web application that handles telemetry from buses (micros), showcases an 
operations/administration panel, messaging between them, and finally give 
information to users (people) that want to know the ETA for buses for a particular stop.

This project will be slowly growing, but without the help of AI,
not because of hate, but to master the needed skills on my own. 

**Built by hand as a learning project**

Given the small scale by now, the documentation of the project will all be
centralized here.

### Current Status
  - [x] Write the project's outline
  - [x] Write the Context Diagram
  - [x] Write the first User Stories
  - [ ] Add acceptance criteria
  - [x] Use standard form for User Stories
  - [ ] Split US05 into smaller USs.
  - [ ] Add non functional requirements
  - [ ] Create the Domain Model
  - [ ] Create the Architecture Diagram
  - [ ] Start modeling the communications between Backend, Database and MQTT Broker
  - [ ] Start modeling the MQTT Broker's topics
  - [ ] Start Database modeling (Logic-Relational diagram and Physical diagram)
  - [ ] Select a frontend...
  - Other development steps.


## Documentation

### Context Diagram

*Note: IS stands for the Telemicro Information System*

```mermaid
graph LR
Buses -- Traveling status data --> IS
IS -- Messages from administration --> Buses
Administrators -- Messages for buses --> IS
IS -- Useful/crunched bus-stop-route data --> Administrators
Users -- View stop --> IS
IS -- ETA of next 3 buses arriving --> Users
```

The ETA of the next 3 buses arriving shown for each stop to the Users has been decided like that, 
given that otherwise the users would be able to see the location of all the buses; this produces security 
concerns over the other buses, its passengers and drivers. Thinking big (very early) also helps for controlled scalability.

### User Stories

#### US01:
As a User, I want to see any stop and the Estimated Time of Arrival for the next three buses arriving,
so that I can leave on time for the stop.

**Acceptance Criteria**:
- Given that I opened the map within the website, when I select a stop in the map, then I want to see the next three buses arriving
- Given that I opened the map within the website, when I select a stop in the map, then I want to see the number of the buses that take the course 
of which the stop is part of.

#### US02:
As a Bus, I want to send and receive messages to and from the Administration, so that I can report emergencies and
know the directives from the Administration.

#### US03: As an Administrator, I want to view the information of each bus quickly,
so that I get to know its position, status and route. 

#### US04: As an Administrator, I want to communicate with the buses
through messaging, so that I become aware of emergencies and communicate the bus appropriate
directives to follow and or relevant information.

#### US05: As an Administrator, I want to view each stablished route, its stops,
and buses, as well as relevant statistics like average ETA for stop of a route, route's lenght,
amount of buses (per route and total), amount of stops (per route and total), and 
amount of Users (people) watching the stops of a route, so that I obtain
situational awareness of each element for ease of decision taking.


### Known limitations
For ease of development, this version or iteration will hardcode the existing routes,
will use simulated data like Buses and Users, and will not care about authentication by now.

### Tech Stack used
  - PostgreSQL: For Data persistency and crunching, as well as management.
  - Django: For Backend.
  - Eclipse Mosquitto: For low latency communication between Backend, Buses and Administrators.
  - Frontend?
  - Hardware: Raspberry Pi 3 for Bus simulation (through Python), ESP32 + GPS for real data gathering (in the future)
  - Containerization: Docker. For Ease of development and deployment.

