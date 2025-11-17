# Exercise 1: API Testing with Postman

## Purpose

These exercises help you understand APIs conceptually and practice testing them with Postman. The goal is to develop **intuition** for API testing—understanding what to test and why, not just how to use the tool.

---

## Exercise 1.1: Understanding APIs Conceptually

### Task (No Tools Required)

Think about a mobile app you use (e.g., weather app, social media).

1. **Identify the API**:
   - What data does the app display? (This comes from an API)
   - What actions can you take? (These call APIs)
   - Example: Weather app shows temperature → API provides weather data

2. **Map User Actions to API Calls**:
   - User action: "Refresh weather"
   - API call: GET /api/weather?location=city
   - What data is sent? What data is received?

3. **Think About the Contract**:
   - What must the API provide?
   - What format is the data in?
   - What happens if the API is down?

### Reflection

- How does understanding APIs help you test mobile/web apps?
- Why test APIs separately from UI?
- What would break if an API changed?

---

## Exercise 1.2: Setting Up Postman

### Task

1. **Install Postman**:
   - Download from postman.com
   - Create account (free)
   - Familiarize yourself with interface

2. **Explore the Interface**:
   - What is a Collection?
   - What is an Environment?
   - What is a Request?
   - What is a Response?

3. **Create Your First Request**:
   - Create a new request
   - Set method to GET
   - Enter URL: `https://jsonplaceholder.typicode.com/posts/1`
   - Click Send
   - Observe the response

### Reflection

- What information does the response contain?
- What do the different parts mean? (Status, Headers, Body)
- How is this different from visiting a website in a browser?

---

## Exercise 1.3: Understanding HTTP Methods

### Task

Use a public API (e.g., JSONPlaceholder: https://jsonplaceholder.typicode.com)

1. **GET Request**:
   - GET `/posts/1`
   - What does this do? (Retrieve data)
   - What's in the response?

2. **POST Request**:
   - POST `/posts`
   - Add body (JSON):
     ```json
     {
       "title": "Test Post",
       "body": "This is a test",
       "userId": 1
     }
     ```
   - What does this do? (Create data)
   - What's in the response? (Newly created post with ID)

3. **PUT Request**:
   - PUT `/posts/1`
   - Update the body
   - What does this do? (Update existing data)

4. **DELETE Request**:
   - DELETE `/posts/1`
   - What does this do? (Delete data)

### Reflection

- How do HTTP methods map to database operations? (GET=SELECT, POST=INSERT, etc.)
- Why are there different methods instead of one?
- When would you use PUT vs PATCH?

---

## Exercise 1.4: Understanding Status Codes

### Task

Make requests and observe status codes:

1. **Success Codes**:
   - Make a valid GET request
   - What status code? (200 OK)
   - What does it mean?

2. **Client Error Codes**:
   - GET `/posts/99999` (non-existent)
   - What status code? (404 Not Found)
   - What does it mean?
   - Try invalid URL: What status code? (404)

3. **Server Error Codes**:
   - Find an API that might return 500
   - Or simulate: What would cause 500?

### Create a Reference Table

| Status Code | Meaning | When You See It |
|-------------|---------|-----------------|
| 200 | OK | Successful request |
| 201 | Created | Resource created |
| 400 | Bad Request | Invalid request format |
| 401 | Unauthorized | Not authenticated |
| 403 | Forbidden | Authenticated but not authorized |
| 404 | Not Found | Resource doesn't exist |
| 500 | Internal Server Error | Server problem |

### Reflection

- Why are status codes important for testing?
- How do status codes help you understand what went wrong?
- What status codes indicate a bug vs. expected behavior?

---

## Exercise 1.5: Testing API Endpoints

### Scenario

You're testing a blog API with these endpoints:
- GET `/posts` - Get all posts
- GET `/posts/{id}` - Get specific post
- POST `/posts` - Create new post
- PUT `/posts/{id}` - Update post
- DELETE `/posts/{id}` - Delete post

### Task

Create test cases for each endpoint:

1. **GET /posts**:
   - Test: Valid request
   - Expected: List of posts, status 200
   - Test: What if no posts exist?

2. **GET /posts/{id}**:
   - Test: Valid ID (e.g., 1)
   - Test: Invalid ID (e.g., 99999)
   - Test: Non-numeric ID (e.g., "abc")
   - What status codes do you expect?

3. **POST /posts**:
   - Test: Valid data
   - Test: Missing required fields
   - Test: Invalid data types
   - Test: Extra fields (should they be ignored?)

4. **PUT /posts/{id}**:
   - Test: Update existing post
   - Test: Update non-existent post
   - Test: Partial update

5. **DELETE /posts/{id}**:
   - Test: Delete existing post
   - Test: Delete non-existent post
   - Test: Delete already deleted post

### Reflection

- What patterns do you see in testing different HTTP methods?
- How do you decide what to test?
- What edge cases might developers miss?

---

## Exercise 1.6: Request Headers and Authentication

### Task

1. **Explore Headers**:
   - In Postman, look at Headers tab
   - What headers are sent by default?
   - What is `Content-Type`? Why does it matter?

2. **Set Custom Headers**:
   - Add header: `X-Custom-Header: test-value`
   - Send request, check if it's received

3. **Authentication** (if API requires it):
   - Try API that requires API key
   - Add to Headers: `Authorization: Bearer your-token`
   - Or use Postman's Auth tab

### Common Headers to Understand

- `Content-Type`: What format is the body? (application/json, etc.)
- `Authorization`: Authentication token
- `Accept`: What format do you want response in?

### Reflection

- Why are headers important?
- How does authentication work in APIs?
- What happens if you send wrong headers?

---

## Exercise 1.7: Response Validation

### Task

After making API requests, validate responses:

1. **Status Code**:
   - Is it what you expected?
   - Does it match the documentation?

2. **Response Time**:
   - How long did it take?
   - Is it acceptable? (< 1 second typically)

3. **Response Body**:
   - Is the structure correct? (JSON format)
   - Are required fields present?
   - Are data types correct?
   - Are values reasonable?

4. **Response Headers**:
   - What headers are in response?
   - What do they tell you?

### Example Validation Checklist

For GET `/posts/1`:
- [ ] Status code is 200
- [ ] Response time < 1 second
- [ ] Response is valid JSON
- [ ] Contains `id` field (number)
- [ ] Contains `title` field (string)
- [ ] Contains `body` field (string)
- [ ] Contains `userId` field (number)

### Reflection

- What makes a response "correct"?
- How do you know if an API is working properly?
- What would indicate a bug vs. expected behavior?

---

## Exercise 1.8: Creating a Postman Collection

### Task

1. **Create Collection**:
   - Name it "Blog API Tests"
   - Add description

2. **Add Requests**:
   - Organize by endpoint
   - Name requests clearly (e.g., "Get All Posts", "Get Post by ID")
   - Add descriptions

3. **Use Variables**:
   - Create environment variable: `base_url = https://api.example.com`
   - Use in requests: `{{base_url}}/posts`
   - Why is this useful?

4. **Add Tests** (Basic):
   - In Tests tab, add:
     ```javascript
     pm.test("Status code is 200", function () {
         pm.response.to.have.status(200);
     });
     
     pm.test("Response has posts array", function () {
         var jsonData = pm.response.json();
         pm.expect(jsonData).to.be.an('array');
     });
     ```

### Reflection

- How does organizing requests help?
- Why use variables?
- How do automated tests in Postman help?

---

## Exercise 1.9: Error Scenarios

### Task

Test how APIs handle errors:

1. **Invalid Input**:
   - Send string where number expected
   - Send missing required fields
   - Send malformed JSON
   - What errors do you get?

2. **Boundary Conditions**:
   - Very large numbers
   - Very long strings
   - Empty strings
   - Null values

3. **Security**:
   - SQL injection attempts (if applicable)
   - XSS attempts
   - Unauthorized access attempts

### Reflection

- How should APIs handle errors gracefully?
- What error messages are helpful?
- What makes an error response "good"?

---

## Exercise 1.10: API Testing Mindset

### Task (Conceptual)

Answer these questions:

1. **Why Test APIs?**
   - What can API testing find that UI testing can't?
   - When is API testing more efficient?

2. **What to Test?**
   - Functionality: Does it work?
   - Performance: Is it fast enough?
   - Security: Is it secure?
   - Reliability: Does it handle errors?

3. **API vs UI Testing**:
   - What's easier to test at API level?
   - What requires UI testing?
   - How do they complement each other?

### Reflection

- How does API testing fit into overall testing strategy?
- What's the relationship between API testing and integration testing?
- How does understanding APIs make you a better tester?

---

## 🎯 Self-Assessment

After completing these exercises, ask yourself:

1. Can I explain what an API is to someone else?
2. Do I understand HTTP methods and when to use them?
3. Can I interpret status codes?
4. Can I create and organize API tests in Postman?
5. Do I understand what to test in APIs?

---

## 💡 Key Insights to Carry Forward

- **APIs are contracts** - They define how systems communicate
- **HTTP methods have meaning** - GET retrieves, POST creates, etc.
- **Status codes tell stories** - They indicate what happened
- **API testing is efficient** - Test logic before UI
- **Understanding APIs helps everywhere** - Mobile, web, integration testing

---

**Next Steps**: Practice with real APIs. Many public APIs are available for practice. The more you practice, the more intuitive API testing becomes.

