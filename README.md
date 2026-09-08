# api-gateway

Single entry point for the microservices system. Routes incoming requests
to the correct backend service by path, resolving actual locations via
Eureka.

## Routes
| Path            | Routes to          |
|-----------------|---------------------|
| `/inventory/**` | inventory-service    |
| `/pricing/**`   | pricing-service      |
| `/agent/**`     | agent-service        |

## Run
    mvn spring-boot:run
Runs on port 8080 (from `config-repo/api-gateway.yml`). Requires
`config-server` and `eureka-server` running first.

## Tech
Spring Boot 4.1, Spring Cloud Gateway Server **WebMVC** variant
(`spring-cloud-starter-gateway-server-webmvc`) — chosen because every
service in this system uses Spring MVC, not WebFlux (the classic reactive
Gateway refuses to start alongside Spring MVC on the classpath).

## Related services
Routes to: [inventory-service](https://github.com/Sannidhihegde/inventory-service), [pricing-service](https://github.com/Sannidhihegde/pricing-service), [agent-service](https://github.com/Sannidhihegde/agent-service)
