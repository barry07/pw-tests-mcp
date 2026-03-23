## Manual Test Report

**URL Tested:**  
https://www.saucedemo.com

**Test Scenario:**  
Exploratory testing of login, shopping, and checkout flows with different user types (standard, locked_out, invalid credentials, problem).

**Environment:**
- Browser: Playwright Chromium
- Test Type: Manual exploratory testing
- Execution: Playwright MCP

**Steps Taken:**
1. Navigated to https://www.saucedemo.com
2. Observed login page with username/password fields and accepted user list
3. Logged in with standard_user / secret_sauce - successful navigation to inventory
4. Browsed 6 products, added "Sauce Labs Backpack" to cart (cart badge updated to 1)
5. Changed product sort to "Price (low to high)" - products reordered correctly
6. Clicked cart icon, viewed cart with item details
7. Clicked "Checkout", filled form (John Doe, 12345), continued to overview
8. Verified totals ($29.99 item + $2.40 tax = $32.39), clicked "Finish"
9. Order completed successfully with confirmation message
10. Logged out via menu
11. Tested locked_out_user login - displayed "Epic sadface: Sorry, this user has been locked out."
12. Tested standard_user with wrong password - displayed "Epic sadface: Username and password do not match any user in this service"
13. Logged in with problem_user - inventory loaded normally
14. Added item to cart - appeared normal
15. Attempted checkout - form fields behaved incorrectly (first/last names swapped), showed validation error despite fields being filled

**Expected Result:**  
All user flows complete successfully, appropriate error messages for invalid logins, consistent UI/UX, no functionality bugs, proper accessibility.

**Actual Result:**  
Standard user journey works flawlessly. Error handling for locked/invalid users is correct. Problem user exposes a bug in checkout form field mapping.

**Issues Found:**

- **Checkout form bug for problem_user:** First Name and Last Name fields are swapped in the DOM. Filling "John" in First Name results in "John" appearing in Last Name field, and vice versa. This triggers false validation errors.
- **Console errors:** Multiple failed requests to backtrace.io (external analytics), but these don't affect functionality.
- **Accessibility:** Input fields have proper labels and roles.
- **UI/UX:** Layout is consistent, responsive design appears functional (tested in default viewport).
- **Performance:** Page loads quickly, no obvious slowdowns.
- **General:** No broken images, links work, keyboard navigation possible.