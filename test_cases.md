# Test Cases — SauceDemo (Login & Checkout Flows)

**Application Under Test:** https://www.saucedemo.com/
**Tester:** Amit Gaire
**Date:** July 2026

Legend: **P1** = Critical, **P2** = Major, **P3** = Minor

---

## Module 1: Login

| ID | Title | Preconditions | Steps | Expected Result | Priority |
|----|-------|----------------|-------|------------------|----------|
| LOGIN-01 | Valid login | On login page | 1. Enter `standard_user` / `secret_sauce`<br>2. Click Login | User is redirected to Products (Inventory) page | P1 |
| LOGIN-02 | Locked out user | On login page | 1. Enter `locked_out_user` / `secret_sauce`<br>2. Click Login | Error message: "Sorry, this user has been locked out." | P1 |
| LOGIN-03 | Invalid password | On login page | 1. Enter `standard_user` / `wrongpass`<br>2. Click Login | Error message shown, user stays on login page | P1 |
| LOGIN-04 | Invalid username | On login page | 1. Enter `invalid_user` / `secret_sauce`<br>2. Click Login | Error message: "Username and password do not match..." | P1 |
| LOGIN-05 | Empty username field | On login page | 1. Leave username blank<br>2. Enter password<br>3. Click Login | Error message: "Username is required" | P2 |
| LOGIN-06 | Empty password field | On login page | 1. Enter username<br>2. Leave password blank<br>3. Click Login | Error message: "Password is required" | P2 |
| LOGIN-07 | Both fields empty | On login page | 1. Leave both fields blank<br>2. Click Login | Error message: "Username is required" | P2 |
| LOGIN-08 | SQL injection attempt | On login page | 1. Enter `' OR '1'='1` in username/password<br>2. Click Login | Login rejected, no unexpected access or error leakage | P1 |
| LOGIN-09 | Case sensitivity check | On login page | 1. Enter `Standard_User` / `secret_sauce`<br>2. Click Login | Login fails (username is case-sensitive) — verify actual behavior | P3 |
| LOGIN-10 | Field is masked | On login page | 1. Type into password field | Characters shown as dots/asterisks, not plain text | P2 |

---

## Module 2: Checkout Flow

| ID | Title | Preconditions | Steps | Expected Result | Priority |
|----|-------|----------------|-------|------------------|----------|
| CHK-01 | Add single item to cart | Logged in as standard_user | 1. Click "Add to cart" on any product | Cart icon badge shows "1"; button changes to "Remove" | P1 |
| CHK-02 | Add multiple items to cart | Logged in | 1. Add 3 different products to cart | Cart badge shows "3" | P1 |
| CHK-03 | Remove item from cart | Item already in cart | 1. Click "Remove" on a product | Item removed, badge count decreases by 1 | P1 |
| CHK-04 | View cart contents | Items in cart | 1. Click cart icon | Cart page lists exactly the items added, correct names/prices | P1 |
| CHK-05 | Checkout with empty cart | Logged in, cart empty | 1. Click cart icon<br>2. Click Checkout | Should not allow checkout / cart shows empty state (verify actual behavior) | P2 |
| CHK-06 | Complete checkout — valid info | Item in cart, on checkout Step One | 1. Enter First Name, Last Name, Zip<br>2. Click Continue | Proceeds to Step Two (Overview) with correct item/price summary | P1 |
| CHK-07 | Checkout with missing first name | On checkout Step One | 1. Leave First Name blank<br>2. Fill others<br>3. Click Continue | Error: "First Name is required" | P2 |
| CHK-08 | Checkout with missing last name | On checkout Step One | 1. Leave Last Name blank<br>2. Click Continue | Error: "Last Name is required" | P2 |
| CHK-09 | Checkout with missing zip/postal code | On checkout Step One | 1. Leave Zip blank<br>2. Click Continue | Error: "Postal Code is required" | P2 |
| CHK-10 | Price total calculation | Multiple items in cart, on Overview page | 1. Verify item total, tax, and total | Total = sum of item prices + tax, calculated correctly | P1 |
| CHK-11 | Cancel checkout mid-flow | On checkout Step One or Two | 1. Click Cancel | Returns to Products or Cart page, cart items preserved | P2 |
| CHK-12 | Complete order | On Overview page | 1. Click Finish | "Thank you for your order" confirmation page shown | P1 |
| CHK-13 | Cart persists after navigating away | Item in cart | 1. Add item<br>2. Navigate to a product page and back | Item remains in cart | P2 |
| CHK-14 | Cart badge disappears when empty | One item in cart | 1. Remove the only item | Cart badge icon disappears (no "0" shown) | P3 |
| CHK-15 | Sort products by price | On Products page | 1. Use sort dropdown → "Price (low to high)" | Products reorder correctly from lowest to highest price | P2 |
| CHK-16 | "Back Home" after order | On order confirmation page | 1. Click "Back Home" | Redirects to Products page, cart is now empty | P2 |

---

## Notes
- Steps marked "verify actual behavior" mean the expected result is what the tester expects logically — the actual system behavior should be recorded during execution, and any mismatch logged as a bug.
- Executed against `standard_user` unless otherwise noted. Bug-hunting pass (separate doc) uses `problem_user` and `visual_user`.
