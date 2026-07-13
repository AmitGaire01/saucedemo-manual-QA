# Bug Reports — SauceDemo (problem_user / visual_user)

**Application Under Test:** https://www.saucedemo.com/
**Tester:** Amit Gaire
**Environment:** Chrome (latest), Windows/Linux
**Login used:** `problem_user` / `secret_sauce` (unless noted)

> Note: These bugs are intentionally seeded by SauceDemo for practice — that's exactly why this login exists. Each report below follows a real bug-report format: Steps to Reproduce, Expected vs Actual, Severity, Priority.

---

### BUG-001: Product images do not match product names
**Severity:** Medium | **Priority:** P2
**Steps to Reproduce:**
1. Log in as `problem_user`
2. Go to Products page
3. Compare each product's image to its name/description

**Expected Result:** Each product displays its own distinct, correct image.
**Actual Result:** Multiple/all products display the same incorrect image (e.g., the same dog photo appears across different items).
**Screenshot:** *screenshots/bug001*

---

### BUG-002: Sorting by price does not reorder items correctly
**Severity:** High | **Priority:** P1
**Steps to Reproduce:**
1. Log in as `problem_user`
2. On Products page, open the sort dropdown
3. Select "Price (low to high)"
4. Observe the order of listed prices

**Expected Result:** Products reorder from lowest to highest price.
**Actual Result:** Order does not change / is incorrect relative to selected sort option.
**Screenshot:** *screenshots/bug002*

---

### BUG-003: Cannot remove item from cart on Products page
**Severity:** High | **Priority:** P1
**Steps to Reproduce:**
1. Log in as `problem_user`
2. Add an item to cart from Products page
3. Click "Remove" on the same item

**Expected Result:** Item is removed, cart badge count decreases.
**Actual Result:** Button state or cart badge does not update correctly (record exact behavior observed during test run — this can vary by SauceDemo build, so confirm before filing).
**Screenshot:** *screenshots/bug003_1  screenshots/bug003_2*

---

### BUG-004: Layout/visual misalignment (visual_user)
**Severity:** Low | **Priority:** P3
**Login used:** `visual_user` / `secret_sauce`
**Steps to Reproduce:**
1. Log in as `visual_user`
2. Navigate through Products, Cart, and Checkout pages
3. Observe layout, image sizing, and element alignment

**Expected Result:** Layout is visually consistent with standard_user experience.
**Actual Result:** Visual inconsistencies present (e.g., misaligned elements or oversized images — record specifics observed).
**Screenshot:** *screenshots/bug004*

---

## How I found these
I ran the Module 1 & 2 test cases (see `test_cases.md`) against `problem_user` and `visual_user` instead of `standard_user`, since SauceDemo seeds these accounts with intentional defects for QA practice. Any test case that passed under `standard_user` but failed here was written up as a bug above.


