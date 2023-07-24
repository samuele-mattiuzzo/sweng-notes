# System Design Basics

## Large scale distributed system

- Large scale: very intense compute time / large amount of data / large userbase / frequently updated
- Distributed system: code does not reside on one single server


## Design patterns

A software design pattern is a general, reusable solution to a commonly occurring problem 
within a given software design context.


### Live streaming system design EXAMPLE

- Define user requirements from the user's perspective
  - Product requirements doc -> features/abstract concepts -> data definitions -> objects -> database
  - Then define endpoints to manipulate data
- Most important features first
  - Primary issue: video availability, server uptime
  - Secondary issue: video quality, likes, comments

- **FAULT TOLERANCE** in case of outage, no service failures (no single point of failure)
- **EXTENSIBILITY** how easy is it to change a code solution (loose coupling better than tight coupling)
- **TESTING** a design needs to be tested (edge/common cases, test for sensible flows; tools to load test)

- Example requirements for video services:
  - Streaming video
  - Processing video
  - Failproof
  - Advertisement
  - Reactions
  - Disclaimers/News flashes
  - Degradation of video quality
  - Support for multiple devices

- **CORE REQUIREMENT**
  - Stream the appropriate quality video based on the device/bandwidth -> black box for the user, does not need to be exposed to it
  - Good approach:
    - Customers define problems
    - APIs allow to query the data
    - Data is stored in tables on the server
  - System design focusses on the backend aspect of the system (no UI, no frontend caching)
  - Start with a simple api (eg: getVideoFrames(id, device, offset) that returns a list of Frame[]; comment(id, data, author, video_id) as a POST)
  - Design the tables (Video with fk to User, Frame with fk to Video, User, Comment with fk to User and Video)
  - At this point in time, the system is fairly complete
  - How do we make the above happen?
    - Client: different APIs need different behaviours -> HTTP? TCP? UDP? WebRTC?
    - Pick a datastore: S3/HDFS for frames (cost based solutions); SQL solution for the data tables (MySQL/PostgreSQL) for Videos; NoSQL for Comments (scale > relationship)
    - Video manipulation: use map/reduce, parallel processing of pieces of data to convert the video (1080p, 720p etc)
  - CDN solutions to persist static data / allow clients to poll for dynamic data
 
Low level design:

- memory optimizations
- api calling
- user behaviour

- Use UML to define user actions/behaviours (use case diagram)
- Define classes with attributes + methods -> states + behaviours (class diagram)
- Define the sequence of event between actors/services (sequence diagram)

