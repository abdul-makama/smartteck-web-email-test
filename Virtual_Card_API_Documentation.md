
# Virtual Card API Documentation

## Overview

The **Virtual Card API** provides endpoints to manage virtual card services for customers. Using these APIs, you can create, retrieve, fund, freeze/unfreeze, and delete virtual cards securely.

All requests must be authenticated using a valid API token. Responses are returned in JSON format.

---

## Base URL

```
https://yourdomain.com/api/
```

---

## Authentication

All endpoints require Bearer token authentication.

### Request Header

```
Authorization: Bearer YOUR_ACCESS_TOKEN
```

If the token is missing or invalid, a `401 Unauthorized` error will be returned.

---

## Endpoints

### 1. Create Virtual Card

- **Endpoint**: `POST /virtual-cards/create`
- **Description**: Create a new virtual card for a user.
- **Request Body**:

```json
{
  "user_id": "1"
}
```

- **Response**:

```json
{
  "status": "success",
  "message": "Virtual card created successfully.",
  "data": {
    "card_id": "2a065a099f25490a86f06f38b320735d",
    "card_number": "5320376307072027",
    "expiry_month": "04",
    "expiry_year": "2029",
    "cvv": "624",
    "card_currency": "NGN"
  }
}
```

---

### 2. Get All Virtual Cards

- **Endpoint**: `GET /virtual-cards`
- **Description**: Retrieve all virtual cards associated with the authenticated user.

---

### 3. Get Virtual Card Details

- **Endpoint**: `GET /virtual-cards/{card_id}`
- **Description**: Retrieve details of a specific virtual card.

- **Response**:

```json
{
  "status": "success",
  "data": {
    "card_id": "2a065a099f25490a86f06f38b320735d",
    "card_number": "5320376307072027",
    "expiry_month": "04",
    "expiry_year": "2029",
    "cvv": "624",
    "card_currency": "NGN",
    "balance": "0.00",
    "created_at": "2025-04-24T11:58:29.000000Z",
    "active": true,
    "frozen": false
  }
}
```

---

### 4. Fund Virtual Card

- **Endpoint**: `POST /virtual-cards/fund`
- **Description**: Fund a virtual card.

- **Request Body**:

```json
{
  "card_id": "2a065a099f25490a86f06f38b320735d",
  "amount": "5000"
}
```

- **Response**:

```json
{
  "status": "success",
  "message": "Card funded successfully.",
  "data": {
    "new_balance": "5000.00"
  }
}
```

---

### 5. Unload Virtual Card

- **Endpoint**: `POST /virtual-cards/unload`
- **Description**: Remove funds from a virtual card.

- **Request Body**:

```json
{
  "card_id": "2a065a099f25490a86f06f38b320735d",
  "amount": "2000"
}
```

- **Response**:

```json
{
  "status": "success",
  "message": "Card unloaded successfully.",
  "data": {
    "remaining_balance": "3000.00"
  }
}
```

---

### 6. Freeze/Unfreeze Virtual Card

- **Endpoint**: `POST /virtual-cards/freeze`
- **Description**: Freeze or unfreeze a virtual card.

- **Request Body**:

```json
{
  "card_id": "2a065a099f25490a86f06f38b320735d",
  "action": "freeze" // or "unfreeze"
}
```

- **Response**:

```json
{
  "status": "success",
  "message": "Card frozen successfully."
}
```

---

### 7. Delete Virtual Card

- **Endpoint**: `DELETE /virtual-cards/{card_id}`
- **Description**: Permanently delete a virtual card.

- **Response**:

```json
{
  "status": "success",
  "message": "Virtual card deleted successfully."
}
```

---

## Status Codes

| Code | Meaning                       |
|------|-------------------------------|
| 200  | OK - Request succeeded        |
| 201  | Created - Resource created    |
| 400  | Bad Request                   |
| 401  | Unauthorized - Invalid token  |
| 403  | Forbidden - Access denied     |
| 404  | Not Found                     |
| 422  | Validation error              |
| 429  | Too Many Requests             |
| 500  | Internal Server Error         |

---

## Postman Collection

You can test the API using [Postman](https://www.postman.com/).  
Import the provided Postman collection JSON to get started quickly. The collection includes:

- All endpoints
- Pre-configured Authorization
- Sample requests and responses

---

## Need Help?

If you encounter issues or have questions:

- Visit our documentation site
- Join the developer forum: **https://community.yourdomain.com**
- Contact our support team at **support@yourdomain.com**
