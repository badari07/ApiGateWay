## API Gateway

Spring Cloud Gateway project that fronts downstream services for products, users, and payments. The gateway is a reactive Spring Boot 3.5 application registered with a Eureka service discovery server so it can route requests dynamically.

### Features
- Routes `/products/**`, `/users/**`, and `/payments/**` traffic to service instances discovered via Eureka.
- Uses Spring Cloud LoadBalancer for client-side load balancing when multiple service instances are registered.
- Ships with devtools, Lombok, and configuration processor for faster local development.

### Requirements
- Java 17+
- Maven 3.9+
- Running Eureka server reachable at `SERVICE_DISCOVERY_URL` (defaults to `http://localhost:8761/eureka/`)
- Product, User, and Payment services registered in Eureka with IDs `ProductService`, `userService`, and `PaymentSerive`.

### Getting Started
1. Install dependencies and build:
   ```bash
   mvn clean package
   ```
2. Run the application:
   ```bash
   ./mvnw spring-boot:run
   ```
   The gateway starts on port `9200`.

### Configuration
- `server.port`: Override to change the gateway port.
- `SERVICE_DISCOVERY_URL`: Set to point at a non-default Eureka server URL.
- `spring.cloud.gateway.server.webflux.routes[*]`: Update or add Spring Cloud Gateway routes. The default configuration lives in `src/main/resources/application.properties`.

### Testing
```bash
mvn test
```

### Troubleshooting
- Ensure the Eureka server is reachable before starting the gateway.
- Verify downstream services register with the expected service IDs.
- Check the console logs for routing errors or missing service instances.

