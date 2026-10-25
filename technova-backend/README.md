# TechNova backend

Spring Boot REST API for the TechNova store. It uses Java 21, MyBatis, and
MySQL 8.

## Run with Docker

Copy `.env.example` to `.env`, set a local database password and a long,
random JWT secret, then run from this directory:

```powershell
docker compose up --build
```

This starts MySQL, initializes the database, and starts the API at
`http://localhost:8080`. `DEEPSEEK_API_KEY` is optional and only required for
AI features. Keep `.env` private.

## Run locally

Requirements: JDK 21+, Maven 3.8+, and MySQL 8.

1. Create the `shop` database and initialize it with `init.sql`. **The script
   drops and recreates the application tables; do not run it against data you
   need to keep.**
2. Set the connection and JWT settings in the environment. In PowerShell:

   ```powershell
   $env:DB_HOST = "localhost"
   $env:DB_PORT = "3306"
   $env:DB_USERNAME = "root"
   $env:DB_PASSWORD = "your_mysql_password"
   $env:JWT_SECRET = "your_long_random_secret"
   ```

3. Start the application:

   ```powershell
   mvn spring-boot:run
   ```

The API listens on port 8080. `DEEPSEEK_API_KEY` is optional.

## Tests

```powershell
mvn test
```

## Main API routes

| Method | Path | Purpose |
|---|---|---|
| POST | `/api/auth/register` | Create an account |
| POST | `/api/auth/login` | Sign in |
| GET | `/api/products` | Search and browse products |
| GET | `/api/products/{id}` | Product details |
| GET | `/api/categories` | Category tree |
| GET/POST | `/api/cart` | View or add cart items |
| GET/POST | `/api/orders` | View orders or check out |
| GET/POST/DELETE | `/api/wishlist` | Manage saved products |
| GET/PUT | `/api/users/me` | Read or update the profile |

Most account, cart, order, and profile routes require authentication.
