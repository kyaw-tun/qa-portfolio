# API Testing Documentation

## 🌐 REST API Testing Examples

### ✅ Authentication Endpoint

**Endpoint:** `POST /api/v1/auth/login`

**Request Headers:**
Content-Type: application/json
Accept: application/json
**Valid Request Body:**
{
  "email": "user@example.com",
  "password": "SecurePass123!",
  "remember_me": true
}
**Valid Response (200 OK):**
{
  "status": "success",
  "data": {
    "user": {
      "id": 123,
      "name": "John Doe",
      "email": "user@example.com"
    },
    "access_token": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9...",
    "refresh_token": "dGhpcyBpcyBhIHJlZnJlc2ggdG9rZW4",
    "expires_in": 3600
  }
}

**Test Cases Covered:**
| Test ID | Scenario | Expected Status | Expected Response |
|---------|----------|----------------|-------------------|
| API-AUTH-001 | Valid credentials | 200 | Success with tokens |
| API-AUTH-002 | Invalid password | 401 | Error message |
| API-AUTH-003 | Missing email field | 400 | Validation error |
| API-AUTH-004 | Malformed JSON | 400 | Parse error |

### Postman Test Scripts

**Basic Status Check:**
pm.test("Status code is 200", function () {
pm.response.to.have.status(200);
});

pm.test("Response has JSON body", function () {
pm.response.to.be.json;
});
**Advanced Validation:**
pm.test("Response has correct structure", function () {
const jsonData = pm.response.json();
pm.expect(jsonData).to.have.property('status');
pm.expect(jsonData).to.have.property('data');
pm.expect(jsonData.data).to.have.property('access_token');
pm.expect(jsonData.data.access_token).to.be.a('string');
});

pm.test("Token is valid JWT format", function () {
const jsonData = pm.response.json();
const token = jsonData.data.access_token;
const parts = token.split('.');
pm.expect(parts.length).to.equal(3);
});
### API Test Matrix

| Endpoint | Method | Auth Required | Test Cases |
|----------|--------|---------------|------------|
| `/api/v1/auth/login` | POST | No | 5 |
| `/api/v1/users/profile` | GET | Yes | 3 |
| `/api/v1/products` | GET | No | 4 |
| `/api/v1/orders` | POST | Yes | 6 |

### Environment Variables
{
"baseUrl": "https://api.example.com",
"testUserEmail": "test@example.com",
"testUserPassword": "TestPass123",
"adminToken": "{{admin_token}}"
}
### Postman Collection Structure
My API Tests/
├── Authentication/
│ ├── Login
│ ├── Register
│ └── Logout
├── Users/
│ ├── Get Profile
│ ├── Update Profile
│ └── Delete Account
└── Products/
├── List Products
├── Get Product Details
└── Search Products

### Testing Checklist
- [ ] Verify status codes
- [ ] Validate response schema
- [ ] Check error handling
- [ ] Test rate limiting
- [ ] Verify CORS headers
- [ ] Validate pagination
- [ ] Test filtering/sorting
