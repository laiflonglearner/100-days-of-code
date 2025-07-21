### ✅ **Day 1: Project Setup & Requirements**

- [ ] Define core features (stock in/out, live inventory, low stock alert, reporting)
- [ ] Finalize integration method: **SAP OData (via Gateway)**
- [ ] Set up **Eclipse** with SAP ABAP Development Tools
- [ ] Confirm SAP backend access (SAP GUI or SAP Cloud Platform trial)
- [ ] Sketch simple UI layout (paper or mockup): List, Forms, Reports

---

### ✅ **Day 2: SAP Backend – Z Table + Sample Data**

- [ ] Create Z-table: `ZINV_MGMT` with fields like `MaterialID`, `Qty`, `MovementType`, `Location`, `Timestamp`
- [ ] Use **SE11** (or Eclipse) to create table and activate
- [ ] Add sample entries via SE16N for testing
- [ ] Document data structure (field names/types)

---

### ✅ **Day 3: Create Gateway Project in SEGW (OData)**

- [ ] Open **SEGW** in SAP GUI or Eclipse
- [ ] Create new project: `ZINV_MGMT_SRV`
- [ ] Define `Entity Type`: `Inventory` with same fields as Z-table
- [ ] Generate runtime artifacts (Model Provider, Data Provider Classes)
- [ ] Map to Z-table using code in `GET_ENTITYSET`, `CREATE_ENTITY`, etc.

---

### ✅ **Day 4: Implement ABAP Logic for OData**

- [ ] Code `GET_ENTITYSET` to fetch all inventory records from `ZINV_MGMT`
- [ ] Code `CREATE_ENTITY` to allow inserting a new stock transaction
- [ ] (Optional) Implement `DELETE` or `UPDATE` if needed
- [ ] Activate and register OData service via `/IWFND/MAINT_SERVICE`
- [ ] Test service in **/IWFND/GW_CLIENT**

---

### ✅ **Day 5: Create Frontend UI Skeleton**

- [ ] Choose frontend tech: **C#**, **JavaScript**, or **PHP**
- [ ] Build base layout:

  - Dashboard (table of inventory)
  - Stock In / Out Form
  - Report Page

- [ ] Set up local project in **Visual Studio** or **Eclipse Web Tools**

---

### ✅ **Day 6: Connect Frontend to OData (GET)**

- [ ] Use C# `HttpClient` / JS `fetch()` / PHP `cURL` to call OData
- [ ] Fetch and display inventory list
- [ ] Format SAP response (JSON) into clean table
- [ ] Add search by Material ID / filter by Location

---

### ✅ **Day 7: POST Logic – Stock In / Out**

- [ ] Build form for new stock transaction
- [ ] On submit, call `POST` to OData service
- [ ] Validate inputs before sending
- [ ] Display success/fail messages
- [ ] Confirm new data is inserted into SAP Z-table

---

### ✅ **Day 8: Add Business Rules & Alerts**

- [ ] Define threshold values (e.g., minimum stock per material)
- [ ] Highlight rows where stock is low
- [ ] Add alert indicator or warning badge in UI
- [ ] (Optional) Add timestamp filter (e.g., recent 7 days)

---

### ✅ **Day 9: Testing & Final Validation**

- [ ] End-to-end test: fetch → insert → re-fetch
- [ ] Try all error cases: blank field, wrong ID, SAP timeout
- [ ] Test OData URLs in browser/Postman
- [ ] Polish frontend (buttons, layout, loading spinner)

---

### ✅ **Day 10: Final Polish & Delivery**

- [ ] Add version info, footer, or company branding
- [ ] Document:

  - How to run frontend
  - API endpoints used
  - Required SAP setup (table, service)

- [ ] Package source files (frontend + any SAP transport requests)
- [ ] Do a full run-through and ✅ check off all features
