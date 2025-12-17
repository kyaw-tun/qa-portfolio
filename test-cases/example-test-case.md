# Example Test Case: User Login Functionality

**Test ID:** TC-AUTH-001  
**Test Type:** Functional, Positive  
**Priority:** High  
**Module:** Authentication  

## 📋 Test Objective
Verify that a registered user can successfully log in with valid credentials.

## 🔧 Preconditions
1. User must be registered in the system
2. Application must be accessible
3. User must not be already logged in

## 📝 Test Steps
| Step | Action | Expected Data |
|------|--------|---------------|
| 1 | Navigate to login page | Login form displays |
| 2 | Enter valid email address | "user@example.com" |
| 3 | Enter valid password | "SecurePass123!" |
| 4 | Click "Login" button | - |

## ✅ Expected Results
1. User is redirected to dashboard/home page
2. Welcome message displays: "Welcome, [username]"
3. Login form disappears
4. Session cookie is set
5. URL changes to authenticated route

## ❌ Negative Test Cases
- **TC-AUTH-002:** Login with invalid password → Error message shown
- **TC-AUTH-003:** Login with non-existent email → Error message shown
- **TC-AUTH-004:** Login with empty fields → Form validation error

## 📊 Test Data
| Test Scenario | Username | Password | Expected Result |
|---------------|----------|----------|----------------|
| Valid login | user@example.com | SecurePass123! | Success |
| Invalid password | user@example.com | wrongpass | Error |
| Invalid email | fake@example.com | SecurePass123! | Error |

## 🏷️ Tags
#login #authentication #functional #positive-testing
