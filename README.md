# 🌍 Smart Travel Booking Platform

<div align="center">

![Java](https://img.shields.io/badge/Java-ED8B00?style=for-the-badge&logo=openjdk&logoColor=white)
![Spring Boot](https://img.shields.io/badge/Spring_Boot-6DB33F?style=for-the-badge&logo=spring-boot&logoColor=white)
![Microservices](https://img.shields.io/badge/Microservices-FF6B6B?style=for-the-badge&logo=apache&logoColor=white)
![REST API](https://img.shields.io/badge/REST_API-009688?style=for-the-badge&logo=fastapi&logoColor=white)
![License](https://img.shields.io/badge/License-MIT-yellow.svg?style=for-the-badge)

**A comprehensive, enterprise-grade travel booking platform built with microservices architecture**

[Features](#-features) • [Architecture](#-architecture) • [Getting Started](#-getting-started) • [API Documentation](#-api-documentation) • [Contributing](#-contributing)

</div>

---

## 📋 Overview

Smart Travel Booking Platform is a production-ready RESTful API system designed to handle end-to-end travel booking operations. Built with modern microservices architecture, it provides seamless integration between multiple services to deliver a robust and scalable travel booking experience.

> 🚀 **Quick Start:** Uses H2 in-memory database - no complex database setup required! Clone, build, and run!

### 🎯 Key Highlights

- **6 Independent Microservices** - Modular architecture for easy maintenance and scaling
- **RESTful API Design** - Clean, consistent, and well-documented endpoints
- **H2 In-Memory Database** - Zero configuration, instant setup for development
- **Comprehensive Testing** - Complete Postman collection with automated test scripts
- **Production Ready** - Built with enterprise-grade patterns and best practices
- **Easy to Run** - No Docker required, simple Maven commands to get started

---

## ✨ Features

### 🔐 User Management
- User registration and authentication
- Profile management
- Secure session handling
- Role-based access control

### ✈️ Flight Booking
- Real-time flight availability search
- Flight booking and reservation
- Multi-city and round-trip support
- Seat selection and management

### 🏨 Hotel Reservations
- Hotel search with advanced filters
- Room availability checking
- Booking management
- Special requests handling

### 📅 Booking Management
- Unified booking interface
- Booking history and tracking
- Modification and cancellation
- Booking confirmation

### 💳 Payment Processing
- Secure payment gateway integration
- Multiple payment methods support
- Transaction history
- Refund management

### 📧 Notification System
- Email notifications
- SMS alerts
- Booking confirmations
- Payment receipts
- Real-time updates

---

## 🏗️ Architecture

### Microservices Overview

```
┌─────────────────────────────────────────────────────────────┐
│                     API Gateway / Load Balancer             │
└─────────────────────────────────────────────────────────────┘
                              │
        ┌─────────────────────┼─────────────────────┐
        │                     │                     │
┌───────▼────────┐   ┌────────▼────────┐   ┌───────▼────────┐
│  User Service  │   │ Booking Service │   │ Flight Service │
└────────────────┘   └─────────────────┘   └────────────────┘
        │                     │                     │
        └─────────────────────┼─────────────────────┘
                              │
        ┌─────────────────────┼─────────────────────┐
        │                     │                     │
┌───────▼────────┐   ┌────────▼────────┐   ┌───────▼────────┐
│ Hotel Service  │   │ Payment Service │   │ Notification   │
│                │   │                 │   │    Service     │
└────────────────┘   └─────────────────┘   └────────────────┘
```

### Service Responsibilities

| Service | Description | Port |
|---------|-------------|------|
| 🧑‍💼 **User Service** | Handles user authentication, registration, and profile management | 8081 |
| 📅 **Booking Service** | Manages booking operations and coordinates between services | 8082 |
| ✈️ **Flight Service** | Provides flight search, availability, and booking capabilities | 8083 |
| 🏨 **Hotel Service** | Handles hotel search, room availability, and reservations | 8084 |
| 💳 **Payment Service** | Processes payments, refunds, and transaction management | 8085 |
| 📧 **Notification Service** | Sends notifications via email, SMS, and push notifications | 8086 |

---

## 🚀 Getting Started

### Prerequisites

- **Java JDK** 11 or higher
- **Maven** 3.6+
- **Postman** (for API testing)
- **Git**

> 💡 **Note:** This project uses H2 in-memory database for easy setup and development. No external database installation required!

### Installation

1. **Clone the repository**
   ```bash
   git clone https://github.com/gunathilakax/smart-travel-booking-platform.git
   cd smart-travel-booking-platform
   ```

2. **Build all services**
   ```bash
   # Build user service
   cd user-service
   mvn clean install
   
   # Repeat for other services
   cd ../booking-service
   mvn clean install
   
   # ... and so on for all services
   ```

5. **Run the services**
   ```bash
   # Start each service in a separate terminal
   cd user-service && mvn spring-boot:run
   cd booking-service && mvn spring-boot:run
   cd flight-service && mvn spring-boot:run
   cd hotel-service && mvn spring-boot:run
   cd payment-service && mvn spring-boot:run
   cd notification-service && mvn spring-boot:run
   ```

6. **Access H2 Console** (Optional - for database inspection)

   Each service has its own H2 console accessible at:
   ```
   http://localhost:808X/h2-console
   ```
   Where X is the service port number (1-6)

   Default credentials:
    - **JDBC URL:** `jdbc:h2:mem:testdb`
    - **Username:** `sa`
    - **Password:** *(leave blank)*

---

## 📚 API Documentation

### Interactive API Documentation with Swagger

Each service comes with built-in Swagger UI for interactive API documentation and testing.

**Access Swagger UI:**
```
User Service:         http://localhost:8081/swagger-ui.html
Booking Service:      http://localhost:8082/swagger-ui.html
Flight Service:       http://localhost:8083/swagger-ui.html
Hotel Service:        http://localhost:8084/swagger-ui.html
Payment Service:      http://localhost:8085/swagger-ui.html
Notification Service: http://localhost:8086/swagger-ui.html
```

**OpenAPI Specification (JSON):**
```
http://localhost:808X/v3/api-docs
```

### Service Endpoints

#### User Service (Port 8081)
- `POST /api/users/register` - Register new user
- `POST /api/users/login` - User authentication
- `GET /api/users/{id}` - Get user profile
- `PUT /api/users/{id}` - Update user profile

#### Booking Service (Port 8082)
- `POST /api/bookings` - Create new booking
- `GET /api/bookings/{id}` - Get booking details
- `GET /api/bookings/user/{userId}` - Get user bookings
- `PUT /api/bookings/{id}` - Update booking
- `DELETE /api/bookings/{id}` - Cancel booking

#### Flight Service (Port 8083)
- `GET /api/flights/search` - Search available flights
- `GET /api/flights/{id}` - Get flight details
- `POST /api/flights/{id}/book` - Book a flight
- `GET /api/flights/availability` - Check seat availability

#### Hotel Service (Port 8084)
- `GET /api/hotels/search` - Search hotels
- `GET /api/hotels/{id}` - Get hotel details
- `GET /api/hotels/{id}/rooms` - Get available rooms
- `POST /api/hotels/book` - Book a hotel room

#### Payment Service (Port 8085)
- `POST /api/payments/process` - Process payment
- `GET /api/payments/{id}` - Get payment details
- `POST /api/payments/refund` - Process refund
- `GET /api/payments/user/{userId}` - Get user transactions

#### Notification Service (Port 8086)
- `POST /api/notifications/send` - Send notification
- `GET /api/notifications/user/{userId}` - Get user notifications
- `PUT /api/notifications/{id}/read` - Mark as read

### Testing with Postman

A comprehensive Postman collection is included in the [`Postman_Collection`](Postman_Collection/Smart_Travel_Booking_Platform.postman_testing_collection.json) folder with automated tests for all endpoints.

#### Import and Run Tests

1. **Import Collection**
   ```
   Open Postman → Import → Upload Files
   Select: Postman_Collection/Smart_Travel_Booking_Platform.postman_testing_collection.json
   ```

2. **Set Up Environment** (Optional)

   The collection uses environment variables for dynamic testing:
    - `created_user_id` - Auto-set after user creation
    - Variables are automatically managed by test scripts

3. **Run Complete Test Suite**
   ```
   Click on Collection → Run
   Select all requests → Run Smart_Travel_Booking_Platform
   ```

#### Available Test Cases

**User Service Tests:**
- ✅ Create User - Validates user creation with all fields
- ✅ Get All Users - Fetches and validates user list
- ✅ Get User by ID - Retrieves specific user details
- ✅ Update User - Modifies user information
- ✅ Validate User - Checks user validation endpoint
- ✅ Delete User - Removes user and cleans up

**Automated Testing Features:**
- Response status code validation
- Response structure verification
- Data integrity checks
- Environment variable management
- Automatic test data cleanup

#### Manual Testing

You can also test individual endpoints:

**Example: Create User**
```bash
curl -X POST http://localhost:8081/api/users \
  -H "Content-Type: application/json" \
  -d '{
    "name": "John Doe",
    "email": "john.doe@test.com",
    "phone": "9876543210",
    "address": "123 Main St, New York",
    "active": true
  }'
```

**Expected Response:**
```json
{
  "success": true,
  "message": "User created successfully",
  "data": {
    "id": 1,
    "name": "John Doe",
    "email": "john.doe@test.com",
    "phone": "9876543210",
    "address": "123 Main St, New York",
    "active": true
  }
}
```

---

## 🛠️ Technology Stack

### Backend Framework
- **Spring Boot** - Application framework
- **Spring Data JPA** - Database operations
- **Spring Security** - Authentication & authorization
- **Spring Cloud** - Microservices infrastructure

### Database
- **H2 Database** - In-memory database for development
- **JPA/Hibernate** - ORM framework

### Communication
- **REST API** - Service-to-service communication
- **Spring Cloud OpenFeign** - Declarative REST client
- **Apache Kafka/RabbitMQ** - Event-driven messaging (optional)

### Documentation & Testing
- **Swagger/OpenAPI** - Interactive API documentation and testing
- **Postman** - Comprehensive API testing with automated scripts

### Build & Deployment
- **Maven** - Dependency management & build tool
- **Spring Boot DevTools** - Hot reload for development

### Testing
- **Postman** - API testing with automated test scripts
- **Swagger/OpenAPI** - Interactive API documentation

---

## 📸 Screenshots

Check out the [`Screenshots`](Screenshots) folder for visual documentation of the platform's functionality and API responses.

---

## 🤝 Contributing

We welcome contributions! Please follow these steps:

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/AmazingFeature`)
3. Commit your changes (`git commit -m 'Add some AmazingFeature'`)
4. Push to the branch (`git push origin feature/AmazingFeature`)
5. Open a Pull Request

### Coding Standards

- Follow Java coding conventions
- Write meaningful commit messages
- Add unit tests for new features
- Update documentation as needed
- Ensure all tests pass before submitting PR

---

## 📝 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

---

## 👥 Authors

- **Gunathilaka** - *Initial work* - [@gunathilakax](https://github.com/gunathilakax)

---

## 🙏 Acknowledgments

- Spring Boot community for excellent documentation
- All contributors who help improve this project
- Open source community for inspiration and support

---

## 📞 Support

If you encounter any issues or have questions:

- 🐛 **Report bugs** via [GitHub Issues](https://github.com/gunathilakax/smart-travel-booking-platform/issues)
- 💡 **Request features** via [GitHub Issues](https://github.com/gunathilakax/smart-travel-booking-platform/issues)
- 📧 **Contact** the maintainer for urgent matters

---

<div align="center">

**⭐ Star this repository if you find it helpful!**

Made with ❤️ by developers, for developers

</div>