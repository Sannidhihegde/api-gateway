# api-gateway

Single entry point for the microservices system. Routes incoming requests to the
correct backend service by path, resolving actual locations via Eureka.

## Routes
| Path            | Routes to          |
|-----------------|---------------------|
| `/inventory/**` | inventory-service    |
| `/pricing/**`   | pricing-service      |
| `/agent/**`     | agent-service        |

## Run
    mvn spring-boot:run
Runs on port 8080. Requires `eureka-server` running, and ideally the backend
services it routes to.

## Tech
Spring Boot 4.1, Spring Cloud Gateway Server **WebMVC** variant
(`spring-cloud-starter-gateway-server-webmvc`) — the blocking/servlet-based
Gateway implementation, chosen because every service in this system uses
Spring MVC, not WebFlux (the classic reactive Gateway is incompatible with
Spring MVC on the same classpath).

## Related services
Routes to: [inventory-service](https://github.com/Sannidhihegde/inventory-service), [pricing-service](https://github.com/Sannidhihegde/pricing-service), [agent-service](https://github.com/Sannidhihegde/agent-service)
