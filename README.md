# 💳 Stripe API Postman Testing Suite

This repository contains a comprehensive manual API testing collection built from scratch using **Postman**, targeting the **Stripe Sandbox API** (`v1`). The project demonstrates professional Quality Assurance (QA) practices, including environment variable scoping, dynamic data handling, and both positive/negative test scenarios.

---

## 🚀 Features & Test Scenarios

The collection is structured into logical folders covering core e-commerce and fintech payment flows:

### 1. 🔐 Auth & Setup
* **Check API Connection:** Validates the validity of the Bearer Token and verifies that the environment is up and running.

### 2. 👤 Customers Management
* **Create a Customer (Positive):** Successfully creates a new customer with a dynamically generated email (`$randomInt`) and extracts the `customerId` into environment variables automatically via test scripts.
* **Get Customer by ID (Positive):** Fetches customer details using the dynamically saved `customerId` and asserts accuracy.
* **Create Customer with Invalid Data (Negative):** Verifies that the system properly rejects malformed email formats and returns a `400 Bad Request` status code.

### 3. 📦 Products Management
* **Create a Product (Positive):** Adds a new item to the store catalog and saves the generated `productId` dynamically.
* **Get All Products (Positive):** Retrieves the full product list and verifies that the response structure returns an array (`data`).

### 4. 💳 Payments & Charges
* **Create a Charge with Test Card (Positive):** Simulates a successful payment transaction using Stripe's standard test token (`tok_visa`) and asserts `paid: true` and status `succeeded`.
* **Create Charge with Declined Card (Negative):** Simulates a failed payment using a declined test card token (`tok_chargeDeclined`) and verifies that the system handles card errors correctly by returning a `402 Payment Required` status along with the `card_declined` error code.

---

## 🛠️ Tech Stack & Concepts Applied
* **Tool:** Postman
* **API:** Stripe Sandbox API (`v1`)
* **Authentication:** Bearer Token (`Authorization: Bearer`)
* **Data Format:** `application/x-www-form-urlencoded`
* **Test Automation Scripts (`pm.test`):** Status code verification, JSON payload assertion, and dynamic environment variable extraction (`pm.environment.set`).

---

## ⚙️ How to Run This Collection

1. Clone this repository or download the JSON collection file.
2. Import the collection into **Postman**.
3. Create a Postman Environment (e.g., `Stripe-QA-Environment`) with the following variables:
   * `baseUrl`: `https://api.stripe.com/v1`
   * `accessToken`: `sk_test_...` (Your Stripe Test Secret Key)
4. Run the requests sequentially (`Auth` ➔ `Customers` ➔ `Products` ➔ `Payments`).
