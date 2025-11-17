# Module 7: Basics of API Testing

## 🌱 Why This Module Matters

APIs (Application Programming Interfaces) are the **backbone of modern applications**. Most applications today are built with APIs connecting frontend, backend, and third-party services.

Understanding API testing is essential because:
- APIs are often tested before UI is ready
- API testing is faster and more reliable than UI testing
- Many defects are found at the API level
- APIs are the integration points between systems

---

## 📚 Learning Objectives

By the end of this module, you will understand:

1. **What is an API** - Understanding APIs conceptually
2. **Types of APIs** - Different API architectures
3. **How APIs Work** - Request-response cycle
4. **API Testing with Postman** - Practical testing tool

---

## 🧩 Conceptual Overview

### What is an API?

**API = Application Programming Interface**

**Simple explanation**: An API is a **contract** between two systems. It defines:
- What requests one system can make
- What responses the other system will return
- How to format requests and responses

**Analogy**: Like a restaurant menu—it tells you what you can order (requests) and what you'll get (responses), but you don't see the kitchen (implementation).

**Why APIs matter**:
- Enable systems to communicate
- Allow frontend and backend to be separate
- Enable third-party integrations
- Make applications modular

---

### Types of APIs

#### 1. REST (Representational State Transfer)

**Most common**:
- Uses HTTP methods (GET, POST, PUT, DELETE)
- Stateless (each request is independent)
- JSON format typically
- Resource-based URLs

**Example**:
```
GET /api/users/123
POST /api/users
PUT /api/users/123
DELETE /api/users/123
```

**Testing perspective**: RESTful, predictable, easy to test

---

#### 2. SOAP (Simple Object Access Protocol)

**Older, more formal**:
- XML format
- More structured
- WSDL (Web Service Description Language) defines contract
- More overhead

**Use case**: Enterprise systems, formal contracts

---

#### 3. GraphQL

**Modern, flexible**:
- Single endpoint
- Client specifies what data it needs
- Reduces over-fetching
- More complex queries

**Example**:
```
POST /graphql
{
  user(id: 123) {
    name
    email
  }
}
```

---

### How APIs Work

**Request-Response Cycle**:

1. **Client sends request**:
   - Method (GET, POST, etc.)
   - URL (endpoint)
   - Headers (authentication, content type)
   - Body (data, if POST/PUT)

2. **Server processes request**:
   - Validates request
   - Processes business logic
   - Queries database (if needed)
   - Prepares response

3. **Server sends response**:
   - Status code (200, 404, 500, etc.)
   - Headers
   - Body (data)

**HTTP Status Codes**:
- **2xx**: Success (200 OK, 201 Created)
- **3xx**: Redirection
- **4xx**: Client error (400 Bad Request, 401 Unauthorized, 404 Not Found)
- **5xx**: Server error (500 Internal Server Error)

---

### How to Make an API

**For testing purposes, understanding helps**:

1. **Define endpoints** (URLs)
2. **Define methods** (GET, POST, etc.)
3. **Define request format** (JSON structure)
4. **Define response format** (JSON structure)
5. **Implement logic** (server-side code)
6. **Handle errors** (appropriate status codes)

**Testing perspective**: You don't need to build APIs, but understanding helps you test them effectively.

---

### How to Test an API Using Postman

**Postman** is a tool for API testing. It allows you to:
- Send HTTP requests
- View responses
- Organize requests
- Create test scripts
- Run collections

#### Basic Postman Workflow

1. **Create Request**:
   - Select method (GET, POST, etc.)
   - Enter URL
   - Add headers (if needed)
   - Add body (if POST/PUT)

2. **Send Request**:
   - Click "Send"
   - View response

3. **Verify Response**:
   - Check status code
   - Check response body
   - Check response time

4. **Write Tests** (optional):
   - Assert status code
   - Assert response data
   - Assert response time

#### Example: Testing Login API

**Request**:
```
POST https://api.example.com/login
Headers:
  Content-Type: application/json
Body:
{
  "username": "testuser",
  "password": "testpass"
}
```

**Expected Response**:
```
Status: 200 OK
Body:
{
  "token": "abc123...",
  "user": {
    "id": 1,
    "name": "Test User"
  }
}
```

**What to test**:
- Valid credentials return token
- Invalid credentials return 401
- Missing fields return 400
- Response time < 1 second

---

## 🎯 Key Takeaways

1. **APIs are contracts** - They define how systems communicate
2. **REST is most common** - HTTP-based, JSON format
3. **Request-response cycle** - Understand the flow
4. **Status codes matter** - They indicate success/failure
5. **Postman is essential** - Primary tool for API testing

---

## 📝 Exercises

See `exercises/` folder for hands-on practice.

---

## 🔗 Connections to Other Modules

- **Module 4**: API testing uses test design techniques
- **Module 5**: Web apps use APIs
- **Module 6**: Mobile apps use APIs
- **Module 8**: Postman is a testing tool

---

**Reflection Question**: How does API testing differ from UI testing, and when is each more appropriate?

