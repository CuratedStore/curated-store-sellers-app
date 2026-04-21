# Curated Store Sellers App: Required Modules and Features

This list is derived from the current web application implementation in CuratedStore (routes + controllers + vendor views).

## 1. Authentication and Access
- Login with email + OTP flow
- OTP verification with expiry and attempt limits
- Register (email + password)
- Email verification with code
- Resend verification code
- Forgot password flow (email)
- Reset password via token link
- Logout

## 2. Seller Onboarding and KYC
- Vendor onboarding form:
  - Brand name
  - Contact person
  - Email
  - Phone
  - Location
  - Categories
  - Requested category
  - Consent
- Vendor KYC submission:
  - Business name
  - Legal name
  - KYC type (individual/company/partnership/proprietorship)
  - ID number
  - Tax number
  - Business address
  - Identity document upload
  - Address document upload
  - Consent
- KYC status tracking page

## 3. Seller Dashboard
- KPI cards/modules:
  - Total products
  - Pending review
  - Approved products
  - Rejected products
  - Low stock products
- Recent products list
- Recent notifications list
- Unread notifications count

## 4. Product Management
- Products list (paginated)
- Create product
- Edit product
- Update product
- Delete product
- Product fields:
  - Name
  - Slug
  - Category
  - Short description
  - Description
  - Price
  - Stock quantity
  - Low stock threshold
  - Tags
- Product review workflow behavior:
  - New/updated products go to pending review
  - Product activation tied to review approval
- Delete constraint:
  - Disallow delete if product has order history

## 5. Seller Orders and Fulfillment
- Orders list (vendor-scoped)
- Fulfillment status update
- Allowed transitions:
  - processing/confirmed -> packed or rejected_by_vendor
  - packed -> out_for_delivery
  - out_for_delivery -> delivered
- Rejection reason required for rejected_by_vendor
- Concurrency guard (expected current status check)
- Status timeline/event logging behavior

## 6. Notifications
- Notifications list (paginated)
- Mark all notifications as read
- Unread counter support

## 7. API-Level Endpoints Present for Seller Domain
- Auth: register/login/logout
- Products: list/create/update/delete
- Categories: list
- Orders: list/detail/update status/reject
- Analytics: sales/top-products/revenue
- Account: profile, update profile, bank details

## Notes for Flutter Implementation
- Seller app must include onboarding + KYC flow before/alongside dashboard access.
- Product workflow must retain pending-review lifecycle after create/update.
- Fulfillment transitions must enforce same validation rules as web.
- Include analytics module (sales/top products/revenue) as seller-facing section.
