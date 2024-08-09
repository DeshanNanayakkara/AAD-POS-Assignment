# POS System Documentation

This documentation provides details on the POS (Point of Sale) system, which is designed for managing customers, items, and orders. The backend is built using Java Servlets and MySQL, offering a RESTful API for seamless operations.

## Overview

- **Technologies:**
    - Java EE (Servlets)
    - MySQL
    - Jakarta JSON-B
    - Logback (Logging)
    - Apache Tomcat

- **Project Purpose:**
  The POS system allows small to medium-sized businesses to manage their sales operations effectively, including customer management, inventory control, and order processing.

## Getting Started

### Prerequisites

Ensure you have the following installed:

- JDK 11 or higher
- Apache Tomcat 9.x or higher
- MySQL Server
- Git (for cloning the repository)

### Installation Steps

1. **Clone the Project Repository:**
   ```bash
   git clone https://github.com/DeshanNanayakkara/AAD-POS-Assignment.git
   cd AAD-POS-Assignment
   ```

2. **Set Up MySQL Database:**
    - Create a new database in MySQL:
      ```sql
      CREATE DATABASE pos_system;
      ```
    - Import the database schema:
      ```bash
      mysql -u [username] -p pos_system < db_schema.sql
      ```

3. **Deploy the Application:**
    - Package the project into a WAR file.
    - Deploy the WAR file to the Tomcat server.

4. **Run the Application:**
    - Start the Tomcat server and access the application at `http://localhost:8080/PosSystem`.

## API Reference

The system provides RESTful APIs for managing customers, items, and orders. Below is an overview of the available endpoints:

### Customer Management

- **Add Customer (POST /customer):**
    - **Request:**
      ```json
      {
        "id": "C001",
        "name": "Deshan Nanayakkara",
        "address": "Galle",
        "salary": 5000
      }
      ```
    - **Response:** `201 Created`

- **Retrieve Customers (GET /customer):**
    - **Parameters:**
        - `type=one&id=C001`: Fetch a single customer by ID.
        - `type=all`: Fetch all customers.
    - **Response:** `200 OK`

- **Update Customer (PUT /customer?id={customerId}):**
    - **Request:**
      ```json
      {
        "name": "Deshan Nanayakkara",
        "address": "Galle",
        "salary": 6000
      }
      ```
    - **Response:** `200 OK`

- **Delete Customer (DELETE /customer?id={customerId}):**
    - **Response:** `204 No Content`

### Item Management

- **Add Item (POST /item):**
    - **Request:**
      ```json
      {
        "code": "I001",
        "itemName": "Laptop",
        "qty": 10,
        "unitPrice": 1500
      }
      ```
    - **Response:** `201 Created`

- **Retrieve Items (GET /item):**
    - **Parameters:**
        - `type=one&itemCode=I001`: Fetch a single item by code.
        - `type=all`: Fetch all items.
    - **Response:** `200 OK`

- **Update Item (PUT /item?itemCode={itemCode}):**
    - **Request:**
      ```json
      {
        "itemName": "Laptop",
        "qty": 5,
        "unitPrice": 2000
      }
      ```
    - **Response:** `200 OK`

- **Delete Item (DELETE /item?itemCode={itemCode}):**
    - **Response:** `204 No Content`

### Order Processing

- **Place Order (POST /placeorder):**
    - **Request:**
      ```json
      {
        "orderId": "ORD001",
        "date": "2024-08-09",
        "customerId": "C001"
      }
      ```
    - **Response:** `201 Created`

- **Save Order Details (POST /orderdetail):**
    - **Request:**
      ```json
      [
        {
          "itemCode": "I001",
          "qty": 2,
          "unitPrice": 1500
        }
      ]
      ```
    - **Response:** `201 Created`

## Additional Information

### Logging and Monitoring

The application uses Logback for logging. Logs are generated in both the console and log files, providing detailed information about API requests, errors, and other significant events.

### Error Handling

The API includes robust error handling mechanisms to return meaningful HTTP status codes and messages, ensuring clients can easily identify and resolve issues.

## Conclusion

This POS system offers a comprehensive solution for managing sales operations, making it ideal for businesses that need an efficient and scalable tool. With its RESTful API, the system can easily integrate with other platforms or services, providing flexibility and ease of use.
