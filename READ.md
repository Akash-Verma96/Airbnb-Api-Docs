# Airbnb Backend API Documentation

A lightweight, interactive API documentation frontend for the **Airbnb Backend Microservices** project.

The documentation provides a centralized reference for available API endpoints, request payloads, response formats, authentication requirements, service architecture, and an integrated API testing console.

## 🌐 Live Documentation

**Live API Docs:**
https://airbnb-api-docs-dg88.onrender.com/

**Backend Gateway:**
https://airbnb-auth.onrender.com/

---

## ✨ Features

* 📚 Complete API endpoint documentation
* 🔍 Search endpoints from the sidebar
* 🧪 Built-in API testing console
* 📦 Request payload examples
* 📤 Response examples
* 🔐 Authentication requirements
* ⚠️ Error response documentation
* 🏗️ Microservices architecture overview
* 🗄️ Data model references
* 🌙 Dark / light theme
* 📱 Responsive design
* ⚡ No frontend framework required

---

## 🏗️ Backend Services

The documentation covers the following backend services:

| Service              | Description                          |
| -------------------- | ------------------------------------ |
| AuthInGo             | API Gateway and authentication       |
| Hotel Service        | Hotel and room management            |
| Booking Service      | Booking and reservation management   |
| Notification Service | Asynchronous notification processing |
| Redis / BullMQ       | Queue and distributed processing     |

### Architecture

```text
                    ┌──────────────────┐
                    │   API Docs UI    │
                    └────────┬─────────┘
                             │
                             ▼
                    ┌──────────────────┐
                    │   AuthInGo        │
                    │   API Gateway     │
                    └────────┬─────────┘
                             │
                 ┌───────────┴───────────┐
                 ▼                       ▼
        ┌─────────────────┐     ┌─────────────────┐
        │  Hotel Service  │     │ Booking Service │
        └────────┬────────┘     └────────┬────────┘
                 │                       │
              MySQL                  MySQL / Redis
                                         │
                                         ▼
                               ┌──────────────────┐
                               │ Notification /   │
                               │ Background Jobs  │
                               └──────────────────┘
```

---

## 📁 Project Structure

```text
api-docs/
│
├── index.html
└── README.md
```

The project intentionally uses a single HTML file containing the documentation UI, styling, and API console functionality.

---

## 🚀 Running Locally

Clone the repository:

```bash
git clone <your-repository-url>
cd api-docs
```

Since this is a static frontend, no Node.js dependency installation is required.

You can open:

```text
index.html
```

directly in your browser.

For local development, you can also use VS Code Live Server.

---

## 🧪 API Console

The documentation includes an interactive API console that allows you to send requests directly from the browser.

Before sending a request:

1. Select the required endpoint.
2. Verify the request URL.
3. Select/check the HTTP method.
4. Enter the required request payload.
5. Add required headers.
6. Click **Send Request**.

Example:

```http
POST https://airbnb-auth.onrender.com/HotelService/api/v1/hotels
```

Request:

```json
{
  "name": "Grand Palace",
  "address": "Lucknow, India",
  "location": "Lucknow",
  "price": 2500,
  "roomType": "DELUXE"
}
```

> API Console requests are executed from the browser, so the backend must allow the documentation frontend origin through CORS.

---

## 🔐 Authentication

Some backend endpoints require authentication.

For protected endpoints, provide the required authentication information through the API Console.

Example:

```http
Authorization: Bearer <JWT_TOKEN>
```

Authentication requirements are documented individually for each endpoint.

---

## 📦 API Response Format

Successful responses generally follow the project's response structure:

```json
{
  "message": "Operation successful",
  "data": {},
  "success": true
}
```

Error responses follow the backend error-handling structure:

```json
{
  "success": false,
  "error": "Error message"
}
```

Validation errors may contain detailed information about the invalid fields.

---

## ⚠️ CORS

Because the API Console runs inside the browser, the backend must allow the API Docs frontend origin.

Frontend:

```text
https://airbnb-api-docs-dg88.onrender.com
```

Backend Gateway:

```text
https://airbnb-auth.onrender.com
```

If requests fail with a CORS error, verify the backend gateway's CORS configuration.

---

## 🚀 Deployment

This project is a static frontend and can be deployed using platforms such as:

* Render
* Vercel
* Netlify
* GitHub Pages

### Render

Recommended configuration:

```text
Environment: Static Site
Root Directory: .
Build Command: None
Publish Directory: .
```

The main entry point is:

```text
index.html
```

---

## 🛠️ Tech Stack

* HTML5
* CSS3
* JavaScript
* REST APIs
* JSON
* Google Fonts
* Render

No frontend framework or package manager is required.

---

## 🔄 Keeping Documentation Updated

Whenever backend APIs change, update the corresponding documentation for:

* Endpoint URL
* HTTP method
* Path parameters
* Query parameters
* Request body
* Response body
* Authentication requirements
* HTTP status codes
* API Console configuration

The API documentation should always reflect the current backend implementation.

---

## 👨‍💻 Backend Project

This frontend is part of the Airbnb Backend Microservices project.

The backend contains services for:

* Authentication
* Hotel management
* Room management
* Booking management
* Notifications
* Redis/BullMQ processing
* Distributed locking

---

## 📄 License

This project is intended for educational and portfolio purposes.
