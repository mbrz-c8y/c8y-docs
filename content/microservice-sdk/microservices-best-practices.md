---
weight: 30
title: Best practices
layout: bundle

---

The following list is a collection of best practices you should take into consideration before you start developing and deploying microservices on top of Cumulocity IoT.


#### Cumulocity IoT Microservice SDK

Whenever possible, use the Cumulocity IoT Microservice SDK as it builds a lot of functionality. It is fully open source and can be extended as required. See the relevant chapters of this guide for further instructions on the [SDK for Java](/microservice-sdk/java/) and the [SDK for C#](/microservice-sdk/cs/).


#### Disk I/O and local disk

Do not use a local disk, store everything in Cumulocity IoT. You do not have a guaranteed amount of bandwidth for disk I/O and also not guaranteed capacity.


#### Liveness probes

Liveness probes should be exposed to Kubernetes as well, just a health endpoint is not sufficient. Moreover, take special attention to implement liveness probes properly. Kubernetes will restart or undeploy the service if the liveness probe is not reliable. Never check 3rd parties in the liveness probe - this can prevent the service from working. 


#### Network traffic

It is not recommended to build a small microservice that loads most of the functionality on start.


#### Resource consumption

Resource consumption should be defined as necessary in the [microservice manifest](/microservice-sdk/concept/#manifest). Resource consumption has an impact on billing. Also consider carefully how many resources you will need in a production scenario per microservice started. 


#### Scaling

There is currently no way to influence load balancer behaviour for scaled microservices (for details on scaling see [General aspects > Isolation and scaling](/microservice-sdk/concept/#isolation-levels). The behaviour is round-robin. Refer to [Microservice manifest](/microservice-sdk/concept/#manifest) for further information on how to configure scaling in the manifest file *cumulocity.json*.


#### Shared microservices

When building microservices for multiple tenants, try to build them in the multi-tenant isolation level, see [General aspects > Isolation and scaling](/microservice-sdk/concept/#isolation-levels). 


#### Statefulness

Avoid statefulness wherever possible, rather write data via REST requests or DB to a persistent shared storage. You can actually find statelessness as one of the requirements listed under [General concepts > Requirements and interactions](/microservice-sdk/concept/#requirements). 


#### Testing of microservices

* Do not develop or test on a production platform.
* You should develop in a local environment before even deploying something in a development or test cluster. 
* Use existing development platforms to test your microservices before rolling them out to any production system.


