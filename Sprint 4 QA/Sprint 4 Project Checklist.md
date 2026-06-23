# 🛒 Urban Grocers API Testing Tracker - Sprint 4 Project

## 🏗️ Phase 1: Environment Setup & Prep
- [x] Ping server address to confirm status: `https://tripleten-services.com`
- [x] Set up a global environment variable in Postman called `baseUrl`
- [x] Open the API documentation (`/docs/`) and review required payload schemas
- [x] Sync spreadsheet columns with standard QA template guidelines

## 🧪 Phase 2: Test Case Execution — "Working with Kits"
*Endpoint:* `POST {{baseUrl}}/api/v1/kits/:id/products`

### 🟢 Positive Flows
- [x] **TC-01:** Add 1 valid product ID to an existing kit (`200 OK` / `201 Created`)
- [x] **TC-02:** Add exactly 30 unique product IDs to an existing kit (Upper boundary limit)
- [x] **TC-03:** Add a product with multiple items of the same ID (Verifying unique array sizing)

### 🔴 Negative Flows
- [x] **TC-04:** Add 31 unique products to an existing kit (`400 Bad Request` boundary error)
- [x] **TC-05:** Add a non-existent product ID (`400 Bad Request`)
- [x] **TC-06:** Send request to a non-existent kit ID (`404 Not Found`)
- [x] **TC-07:** Submit request body missing structural layout / `productsList` wrapper (`400 Bad Request`)
- [x] **TC-08:** Pass invalid data types like strings instead of integer IDs (`400 Bad Request`)

## 🚚 Phase 3: Test Case Execution — "Working with Deliveries"
*Endpoint:* `POST {{baseUrl}}/fast-delivery/v3.1.1/calculate-delivery.xml`
*Headers Required:* `Content-Type: application/xml`

- [x] **TC-09:** Submit a valid XML delivery request matching the Shipping Price Calculations rules (`200 OK`)
- [x] **TC-10:** Send an XML request containing unclosed or malformed tags (`400 Bad Request`)
- [x] **TC-11:** Send an XML request missing mandatory elements from the Couriers documentation (`400 Bad Request`)

## 🐛 Phase 4: Defect Logging & Project Wrap-up
- [x] Double check Jira access settings to ensure domain uses `tripleten.com` instead of `tripleten-team.com`
- [x] Draft bug reports in Jira for all Postman response discrepancies 
- [x] Map Jira bug tracking ticket URLs back to the Google Sheets spreadsheet rows
- [x] Draft final high-level text Summary Report outlining the status of tested modules
- [x] Move into the project "Submission" tab and execute final delivery package push
