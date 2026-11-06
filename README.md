**Microservices Resilience POC**

**Overview**
This project is a Proof of Concept (POC) created to explore resilience and fault-tolerance patterns in a microservices architecture.

In a distributed system, one service often depends on other services to complete a request. If a downstream service becomes unavailable, responds slowly, or starts failing, that failure can propagate to the calling service and impact the overall user experience.

This POC demonstrates how resilience patterns can be applied to Spring Boot microservices using Resilience4j.

The primary focus is on understanding:

1. Service-to-service communication
2. Failure propagation in distributed systems
3. Circuit Breaker
4. Fallback handling
5. Timeout / slow downstream scenarios
6. Graceful degradation
7. Recovery after a downstream service becomes healthy again

**Architecture**
The POC consists primarily of two microservices:

1. Order Service: https://github.com/Anusha853/order-service
The Order Service acts as the upstream/calling service.
When an order-related request is received, it communicates with the Inventory Service to check whether the requested product is available.

2. Inventory Service: https://github.com/Anusha853/inventory-service
The Inventory Service acts as the downstream service.

- It receives product/inventory requests
- Queries the database for the requested product
- Returns inventory information when the product exists

**Request Flow**
Client
   |
   v
Order Service
   |
   | HTTP request
   v
Inventory Service
   |
   v
Database

Eureka server: https://github.com/Anusha853/eureka-server
