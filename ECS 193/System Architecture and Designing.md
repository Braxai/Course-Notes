## C4 Model 
* Architecture framework to help define, design, and document a software system
* Stands for
  * System Context Diagram
  * Container Diagram
  * Component Diagram
  * Class / Code Diagram

c4model.com

System Context Diagram
* Overview of requirement provided by client

Container Diagram 
* Represent all containers and how they interact
  * components that need to be developed 
* Mention tech stack being used

Component Diagram 
* Define features within a container

Code Diagram (optional)
* developer only task diagram

## Design Considerations 

Architectures : consider the best type of architecture according to use case 
* Serverless
* Client - Server
* Peer to Peer (P2P)
* Microservices

Software Design Patterns 
* Model View Controller (MVC) vs Model View Presenter (MVP)

Databases
* Type : SQL vs NoSQL
* How to allow faster reads? more reads than writes 
  * Database replication
* How to scale DB from 100 to 1 million users
  * horizontal vs vertical DB scaling
    * vertical : max out ram, storage, cpu resources...
    * horizontal : split database into multiple shards (worth looking into)

Middleware : connect frontend to backend service
* Helps protect and not expose API keys in network packets
* Helps protect routes and allows configuration of different calls without changing the route on the front end
* system design and utility considerations
  * rate limiting
  * load balancing
  * caching
  * health checks
  * logging, etc.
 
Notifications 
* Fanout notifications/emails
* event driven web hooks
  * SNS, Kafka, RabbitMQ, etc.
* other pub sub architectures

## Next Steps 
* define and create backlog of tasks
* Identfiy API Calls, database scripts, etc to be implemented based on your designs
* Start working on the MVP and high priority tasks by moving them to your task/kanban boards
