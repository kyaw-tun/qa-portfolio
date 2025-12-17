# Bug Report: Login Button Not Responding on Mobile Safari

**Bug ID:** BUG-LOGIN-015  
**Severity:** High  
**Priority:** Medium  
**Status:** Open  
**Environment:** iPhone 12, iOS 15, Safari 15  
**Reported By:** Kyaw Kyaw Tun  
**Date:** 2025-12-17  

## 🐛 Bug Description
The login button becomes unresponsive when tapped on Safari browser on iOS devices. The button visual feedback works (changes color), but no login action is triggered.

## 📱 Steps to Reproduce
1. Open Safari browser on iPhone 12 (iOS 15)
2. Navigate to https://app.example.com/login
3. Enter valid credentials (any)
4. Tap the "Login" button
5. Observe: Button changes color but login doesn't proceed

**Reproducibility:** 100% (5/5 attempts)

## 🎯 Expected Behavior
User should be logged in and redirected to dashboard upon tapping the login button.

## 🚨 Actual Behavior
Login action does not trigger. User remains on login page with no error message.

## 📸 Evidence
- **Screenshot 1:** Login form with credentials filled
- **Screenshot 2:** Network tab shows no POST request sent
- **Console Error:** `TypeError: null is not an object (evaluating 'e.preventDefault')`

## 🔧 Technical Details
- **Browser Console Error:** `TypeError: null is not an object (evaluating 'e.preventDefault') (anonymous function)(login.js:45)`
- **Network:** No HTTP request sent to `/api/login`
- **User Agent:** `Mozilla/5.0 (iPhone; CPU iPhone OS 15_0 like Mac OS X) AppleWebKit/605.1.15 (KHTML, like Gecko) Version/15.0 Mobile/15E148 Safari/604.1`

## 🌍 Affected Platforms
- ✅ iPhone 12 (iOS 15, Safari 15)
- ✅ iPhone 13 (iOS 15, Safari 15)
- ❌ Android Chrome (Works fine)
- ❌ Desktop Chrome (Works fine)

## 💡 Suggested Fix
Check the event handler in `login.js:45`. Likely the event object is null in Safari's touch events. Consider using `if (e) e.preventDefault()` or using passive event listeners.

## 📎 Attachments
- [login-error-safari.png] (Screenshot)
- [console-log.txt] (Error log)
