
#EcommerenceBackend - Scalable E-Commerce Platform (CQRS + DDD + .NET 8 Web API)

Welcome to **EcommerenceBackend**, a cleanly architected, production-ready **.NET 8 E-Commerce Backend** built using modern best practices including **Domain-Driven Design (DDD)**, **CQRS**, **Redis caching**, **Stripe payments**, and **Dockerized deployment**.

This is the public showcase version of the ASP.NET Core backend for the Ecommerence full-stack e-commerce platform.

Live API Documentation: [Swagger UI](https://swagger-nshoppe.com/swagger/index.html)

---

## Project Highlights

-   **.NET 8 Web API** with C#
-   **Domain-Driven Design (DDD)** folder structure
-   **CQRS pattern** with `Commands` and `Queries`
-   **Stripe** integration for secure online payments webhook handling
-   **FluentValidation** validation 
-   **MySQL (via RDS)** Database
-   **Redis** caching for performance
-   **Docker** for containerization
-   **GitHub Actions CI/CD** to EC2
-   **Unit Tests** using xUnit

---

##  Clean Architecture & DDD Overview

The project follows **DDD principles**, separating business logic from application concerns:

```
EcommerenceBackend/
├── Application.Dto/                    # Request/Response DTOs
├── Application.Interfaces/             # Interfaces
├── Application.UseCases/               # Commands, Queries, Handlers

├── Application.Domain/                 # Domain Models, Aggregates, Events

├── Infrastructure/                     # Persistence, Redis, Stripe integrations

├── WebApi/                             # Controllers, Middleware, Program.cs

├── EcommerenceBackendUnitTestProj/     # xUnit

├── Dockerfile                          # Dockerfile
├── docker-compose.yml                  # Full stack deployment
├── .github/workflows/deploy.yml # CI/CD pipeline
```

---

## Tech Stack

| Layer            | Technology                      |
|------------------|----------------------------------|
| API              | ASP.NET Core 8 Web API           |
| Architecture     | DDD, CQRS                        |
| Caching          | Redis                            |
| Payments         | Stripe API                       |
| Deployment       | Docker, EC2, GitHub Actions      |
| Testing          | xUnit                            |
| Validateion      | Fluent Validation                |
| Database         | Mysql (via AWS RDS)              |


---

##  Running the Project Locally (with Docker)

```bash
# Clone the repo
git clone https://github.com/yourusername/EcommerenceBackend.git
cd EcommerenceBackend

# Build & run containers
docker-compose up --build
```

Access API: `http://localhost:5000/swagger/index.html`

---

## Stripe Integration

- Create Checkout Session: `POST /api/payment/checkout`
- Webhook Handler: `POST /api/stripe/webhook`
- Secrets: Add your `Stripe:SecretKey` and `Stripe:WebhookSecret` in `appsettings.json`

---

## Redis Caching

- Applied to frequently accessed endpoints (e.g. `Products`, `Categories`)
- Configured via `Redis__ConnectionString` in environment variables

---

### Custom Middleware

This project includes a custom middleware pipeline to handle:

- Centralized exception handling
- Logging and tracing

##  API Sample - Checkout

```json
POST /api/payment/checkout
{
  "customerId": "guid",
  "items": [
    {
      "productId": "guid",
      "price": 1200,
      "quantity": 1
    }
  ],
  "shippingCost": 5.19,
  "status": "Pending",
  "paymentStatus": "Pending"
}
```

---

##  GitHub Actions Deployment (CI/CD)

Automatically deploys to AWS EC2 on `master` branch push:

`.github/workflows/deploy.yml` contains:

- SSH to EC2
- Upload zipped Docker app
- Build and restart containers
- Runs with `docker-compose up --build -d`

---

##  Author

Developed by **Kyaw Zay Ya** – .NET Core Backend Developer (Malaysia)

---

##  Contact

Want to collaborate or hire? Let's connect!  
Email: saimawkhann@gmail.com

---

 This project showcases production-grade architecture using modern .NET 8 techniques. Feel free to fork, learn, and grow!

