# QuantityMeasurementSpringBoot

The **Quantity Measurement Application** is a Spring Boot–based RESTful service designed to perform operations on physical quantities such as **Length, Volume, Weight, and Temperature**.

The application supports:

- Arithmetic operations
- Unit conversions
- Quantity comparisons
- Operation history tracking using a relational database

This project demonstrates:

- Clean Architecture
- Layered Design
- Validation
- Exception Handling
- API Documentation using OpenAPI (Swagger)

---

# Features

## Arithmetic Operations on Quantities

The application supports the following operations:

- Addition
- Subtraction
- Division
- Compare two quantities

---

## Unit Conversion

Convert quantities between supported units.

Example:
- Meter → Centimeter
- Liter → Milliliter
- Kilogram → Gram
- Celsius → Fahrenheit

---

## Supported Measurement Types

The application supports:

- Length
- Volume
- Weight
- Temperature

---

## Operation History

Store and retrieve operation history from the database.

### Filter History By

- Operation Type
- Measurement Type
- Error Status

### Additional Support

- Count successful operations

---

## Validation

Uses **Jakarta Validation** for:

- Required field validation
- Measurement type validation
- Unit compatibility checks

Invalid inputs return structured error responses.

---

## Exception Handling

Centralized exception handling using:

- `GlobalExceptionHandler`
- Custom exceptions

Handles:

- Validation errors
- Runtime exceptions
- Business logic exceptions

---

## Swagger Documentation

Interactive API documentation is available using Swagger UI.

Features:

- Interactive API testing
- Request/response schemas
- Example payloads

Swagger URL:

```text
http://localhost:8080/swagger-ui/index.html
```

---

# Technology Stack

| Technology | Purpose |
|---|---|
| Java 17+ | Programming Language |
| Spring Boot | Backend Framework |
| Spring Web | REST APIs |
| Spring Data JPA | Database Access |
| Hibernate | ORM |
| H2 / MySQL | Database |
| Jakarta Validation | Input Validation |
| OpenAPI (springdoc) | API Documentation |
| Maven | Build Tool |

---

# Project Structure

```text
com.app.quantitymeasurement
│
├── config
│   └── OpenAPIConfig.java
│
├── controller
│   └── QuantityMeasurementController.java
│
├── service
│   ├── QuantityMeasurementService.java
│   └── QuantityMeasurementServiceImpl.java
│
├── repository
│   └── QuantityMeasurementRepository.java
│
├── model
│   ├── QuantityDTO.java
│   ├── QuantityInputDTO.java
│   ├── QuantityMeasurementDTO.java
│   └── QuantityMeasurementEntity.java
│
├── unit
│   ├── Unit.java
│   ├── Quantity.java
│   ├── LengthUnit.java
│   ├── VolumeUnit.java
│   ├── WeightUnit.java
│   └── TemperatureUnit.java
│
├── exception
│   ├── GlobalExceptionHandler.java
│   └── QuantityMeasurementException.java
│
test
│
├── controller
│   └── QuantityMeasurementControllerTest.java
│
├── service
│   └── QuantityMeasurementServiceImplTest.java
│
├── repository
│   └── QuantityMeasurementRepositoryTest.java
```

---

# API Endpoints

## Base URL

```text
/api/v1/quantities
```

---

# 1. Compare Quantities

## Endpoint

```http
POST /compare
```

## Request Body

```json
{
  "thisQuantityDTO": {
    "value": 1,
    "unit": "METER",
    "measurementType": "LengthUnit"
  },
  "thatQuantityDTO": {
    "value": 100,
    "unit": "CENTIMETER",
    "measurementType": "LengthUnit"
  }
}
```

---

# 2. Convert Quantity

## Endpoint

```http
POST /convert
```

## Request Body

```json
{
  "thisQuantityDTO": {
    "value": 1,
    "unit": "METER",
    "measurementType": "LengthUnit"
  },
  "targetQuantityDTO": {
    "unit": "CENTIMETER",
    "measurementType": "LengthUnit"
  }
}
```

---

# 3. Add Quantities

## Endpoint

```http
POST /add
```

---

# 4. Add Quantities with Target Unit

## Endpoint

```http
POST /add-with-target-unit
```

---

# 5. Subtract Quantities

## Endpoint

```http
POST /subtract
```

---

# 6. Subtract Quantities with Target Unit

## Endpoint

```http
POST /subtract-with-target-unit
```

---

# 7. Divide Quantities

## Endpoint

```http
POST /divide
```

---

# 8. Get Operation History

## Endpoint

```http
GET /history/operation/{operation}
```

---

# 9. Get History by Measurement Type

## Endpoint

```http
GET /history/type/{type}
```

---

# 10. Get Operation Count

## Endpoint

```http
GET /count/{operation}
```

---

# 11. Get Error History

## Endpoint

```http
GET /history/errored
```

---

# Validation

The application uses **Jakarta Validation** to ensure:

- Required fields are not null
- Measurement types are valid
- Units correspond to measurement types

Invalid requests return proper validation messages with HTTP status codes.

---

# Exception Handling

A centralized exception handler manages:

- Validation exceptions
- Runtime exceptions
- Business exceptions

All errors are returned with:

- Appropriate HTTP status codes
- Structured error messages

---

# How to Run

## 1. Clone the Repository

```bash
git clone <repository-url>
```

---

## 2. Navigate to Project Directory

```bash
cd QuantityMeasurementSpringBoot
```

---

## 3. Build the Project

```bash
mvn clean install
```

---

## 4. Run the Application

```bash
mvn spring-boot:run
```

---

# Future Enhancements

- Add multiplication operation
- Improve unit validation logic
- Add authentication and authorization
- Deploy to cloud platforms (AWS/GCP/Azure)
- Add frontend interface using React/Next.js
- Extend support for additional measurement systems

---

# Author

Developed as a Spring Boot RESTful backend application for quantity measurement operations and unit conversion.
Conclusion
This project demonstrates a robust implementation of a quantity measurement system using Spring Boot. It highlights best practices in REST API design, layered architecture, validation, and persistence, making it suitable for academic, learning, and production-ready extensions.
