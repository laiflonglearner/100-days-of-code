### 1. Project Scope

The inventory management app will allow users to manage materials and stock with the following core features:

- **View Materials**: Display a list of materials with details (e.g., ID, name, description, quantity).
- **Add Material**: Create a new material entry.
- **Update Stock**: Adjust stock quantity for existing materials (e.g., increase/decrease).
- **Delete Material**: Remove a material from the inventory.
- **Basic Filtering**: Filter materials by name or quantity in the UI.

The app will use **SAP CAP** for the backend (data model and services) and **SAP Fiori Elements** for a low-code, standards-compliant UI. It will be deployed to **SAP BTP Cloud Foundry** using your trial account. The focus is on simplicity and demonstrating proficiency with SAP tools, not enterprise-level complexity.

---

### 2. Finalized List of Tools

Below is the definitive list of tools to use, what to install, and what to skip, with reasoning:

#### Tools to Install/Use:

- **Visual Studio Code (VS Code)**:

  - **Why**: Your preferred IDE, supports local CAP development, and integrates with SAP tools via extensions. It’s lightweight and sufficient for a solo project.
  - **Install**: Already installed (per your input).
  - **Extensions to Install**:
    - **SAP CDS Language Support**: For CDS file editing and autocompletion.
    - **SAP Fiori Tools Extension Pack**: For generating Fiori Elements apps and annotations.
    - **Cloud Foundry CLI (cf CLI)**: For deploying to SAP BTP Cloud Foundry.
    - Install with: `npm install -g @sap/cds-dk` (includes CDS tools) and follow SAP’s guide for cf CLI (see resources below).

- **Node.js**:

  - **Why**: Required for CAP’s Node.js runtime and local development.
  - **Install**: Download and install Node.js (LTS version, e.g., 18.x) from nodejs.org if not already installed.

- **SQLite**:

  - **Why**: Default database for local CAP development in the BTP Trial. SAP HANA is available in BTP, but SQLite simplifies local testing and avoids setup complexity for a portfolio project.
  - **Install**: Included with CAP’s Node.js runtime, no separate installation needed.

- **SAP BTP Trial Account**:

  - **Why**: Provides the Cloud Foundry environment for deployment and access to SAP HANA (if needed later).
  - **Status**: Already set up (per your input).

- **Cloud Foundry CLI (cf CLI)**:
  - **Why**: Essential for deploying the app to SAP BTP Cloud Foundry.
  - **Install**: Follow SAP’s guide (see resources) to install cf CLI globally.

#### Tools to Skip:

- **SAP Business Application Studio (BAS)**:
  - **Why Skip**: BAS is a cloud-based IDE optimized for SAP development, but it’s not strictly necessary since VS Code with extensions supports CAP and Fiori development locally. BAS requires additional setup in BTP and is less flexible for a solo project. Your preference for VS Code aligns with keeping things lightweight.
- **Eclipse**:
  - **Why Skip**: You mentioned it’s optional, and it’s less relevant for CAP/Fiori development compared to VS Code. Eclipse is more suited for ABAP or Java-heavy projects, which aren’t needed here.
- **SAP Web IDE**:
  - **Why Skip**: Deprecated in favor of BAS or VS Code with Fiori Tools. It’s outdated and unnecessary.
- **SAP HANA (local)**:
  - **Why Skip**: While SAP HANA is used in BTP deployment, SQLite is sufficient for local development and testing in a trial account to avoid setup complexity.

#### Why This Toolset?

This combination (VS Code, Node.js, SQLite, cf CLI, SAP BTP Trial) is the **minimal viable stack** for CAP-based app development. It avoids duplicate tools (e.g., BAS vs. VS Code), aligns with your preference for local development, and ensures compatibility with the SAP BTP Trial. Fiori Tools extensions simplify UI development, and SQLite keeps the database setup straightforward for a portfolio project.

---

### 3. Day-by-Day Plan (10 Days)

This 10-day plan assumes you’re working a few hours daily and focuses on building, testing, and deploying the app. Each day includes clear tasks, tools used, and deliverables.

# 10-Day Plan for SAP Inventory Management App

## Day 1: Setup Development Environment

- **Tasks**:
  - Verify Node.js installation (`node -v`, `npm -v`).
  - Install SAP CDS Development Kit globally: `npm install -g @sap/cds-dk`.
  - Install Cloud Foundry CLI (follow SAP’s guide: https://developers.sap.com/tutorials/cp-cf-download-cli.html).
  - Install VS Code extensions: SAP CDS Language Support, SAP Fiori Tools Extension Pack.
  - Log in to SAP BTP Trial via cf CLI: `cf login`.
  - Initialize a CAP project: `cds init inventory-app --add sample`.
- **Tools**: VS Code, Node.js, cf CLI, SAP BTP Trial.
- **Deliverable**: Project folder (`inventory-app`) with basic CAP structure (`db/`, `srv/`, `app/`).

## Day 2: Define Data Model

- **Tasks**:
  - In `db/schema.cds`, define entities for `Materials` (ID, name, description, quantity).
  - Add sample data in `db/data/my.namespace-Materials.csv`.
  - Test data model locally: `cds watch` (starts local server with SQLite).
- **Tools**: VS Code, SAP CDS Language Support.
- **Deliverable**: Data model (`schema.cds`) and sample data CSV.

## Day 3: Create CAP Service

- **Tasks**:
  - In `srv/inventory-service.cds`, define a service exposing `Materials` entity with CRUD operations.
  - Implement basic logic in `srv/inventory-service.js` (e.g., validation for stock updates).
  - Test service locally: `cds watch` and access `http://localhost:4004/inventory`.
- **Tools**: VS Code, SAP CDS Language Support.
- **Deliverable**: Functional CAP service with OData endpoints.

## Day 4: Add Fiori Elements UI

- **Tasks**:
  - Use Fiori Tools in VS Code: Run `Fiori: Application Generator` to create a List Report Object Page for `Materials`.
  - Place UI in `app/inventory/`, configure `manifest.json` for OData service.
  - Add basic annotations in `srv/inventory-service.cds` (e.g., `@UI.LineItem` for list display).
  - Test UI locally: `cds watch` and check Fiori preview.
- **Tools**: VS Code, SAP Fiori Tools Extension.
- **Deliverable**: Basic Fiori Elements UI in `app/inventory/`.

## Day 5: Enhance UI with Annotations

- **Tasks**:
  - Add Fiori annotations for filtering and field display (e.g., `@UI.SelectionFields` for name/quantity).
  - Customize UI layout in `app/inventory/annotations.cds` (e.g., field labels, visibility).
  - Test{IC0}Test UI: `cds watch` and verify changes in Fiori preview.
- **Tools**: VS Code, SAP Fiori Tools.
- **Deliverable**: Enhanced Fiori UI with filtering and improved display.

## Day 6: Implement Custom Logic

- **Tasks**:
  - Add custom logic in `srv/inventory-service.js` for stock updates (e.g., prevent negative quantities).
  - Test logic via HTTP requests (e.g., Postman or browser).
- **Tools**: VS Code.
- **Deliverable**: Service with validated stock update logic.

## Day 7: Finalize UI and Testing

- **Tasks**:
  - Refine UI annotations for better usability (e.g., add `@UI.Criticality` for low stock warnings).
  - Perform end-to-end testing: Create, update, delete materials via UI.
  - Fix any issues in data model, service, or UI.
- **Tools**: VS Code, SAP CDS/Fiori Tools.
- **Deliverable**: Fully functional local app.

## Day 8: Prepare for Deployment

- **Tasks**:
  - Create `mta.yaml` for Cloud Foundry deployment (use `cds add cf-manifest`).
  - Configure SQLite for local use and HANA for BTP (auto-handled by CAP in trial).
  - Test deployment locally: `cds build` and `cf push`.
- **Tools**: VS Code, cf CLI.
- **Deliverable**: Deployment-ready project with `mta.yaml`.

## Day 9: Deploy to SAP BTP

- **Tasks**:
  - Deploy app to BTP: `cf push`.
  - Verify app in BTP cockpit (check routes and services).
  - Test deployed app via BTP URL.
- **Tools**: cf CLI, SAP BTP Trial.
- **Deliverable**: App deployed and accessible on BTP.

## Day 10: Polish and Document

- **Tasks**:
  - Add final UI tweaks (e.g., adjust table columns).
  - Document project in a `README.md` (overview, setup, features).
  - Take screenshots/videos of app for portfolio.
- **Tools**: VS Code.
- **Deliverable**: Polished app and portfolio-ready documentation.

---

### 4. Setup Notes and Integration Flow

- **Setup**:
  - **Node.js**: Ensures CAP runtime and CLI tools work.
  - **VS Code Extensions**: Enable CDS editing and Fiori UI generation.
  - **cf CLI**: Connects to BTP for deployment.
  - **SAP BTP Trial**: Provides Cloud Foundry environment and HANA (if needed).
  - Run `npm install` in the project folder after `cds init` to install dependencies.
- **Integration Flow**:
  - **Data Model (CDS)**: Define entities in `db/schema.cds` using CDS syntax.
  - **Service (CAP)**: Expose OData services in `srv/inventory-service.cds` and add logic in `.js`.
  - **UI (Fiori Elements)**: Generate UI in `app/` using Fiori Tools, linked to OData service.
  - **Local Testing**: Use `cds watch` to run SQLite-based server and Fiori preview.
  - **Deployment**: Build with `cds build`, deploy with `cf push` to BTP Cloud Foundry.
- **Best Practices**:
  - Keep CDS models simple (avoid complex associations).
  - Use Fiori Elements for low-code UI to save time.
  - Validate inputs in service logic to ensure data integrity.
  - Test locally before deploying to catch errors early.

---

### 5. Sample Templates and Resources

- **SAP Samples on GitHub**:
  - [SAP-samples/cap-sflight](https://github.com/SAP-samples/cap-sflight): A travel management app using CAP and Fiori Elements. Use as a reference for project structure and Fiori setup.[](https://github.com/SAP-samples/cap-sflight)
  - [SAP-samples/btp-developer-guide-cap](https://github.com/SAP-samples/btp-developer-guide-cap): Guides for CAP development with Node.js.[](https://github.com/SAP-samples)
- **Official SAP Resources**:
  - [CAP Documentation (CAPire)](https://cap.cloud.sap/docs/): Comprehensive guide for CAP, CDS, and Fiori integration.[](https://cap.cloud.sap/docs/about/)
  - [SAP Fiori Tools Guide](https://developers.sap.com/tutorials/fiori-tools-cap-project.html): Steps for creating Fiori apps with CAP.
  - [SAP BTP Trial Setup](https://developers.sap.com/tutorials/btp-trial-account-setup.html): Guide for configuring your BTP Trial account.
  - [Cloud Foundry CLI](https://developers.sap.com/tutorials/cp-cf-download-cli.html): Installation instructions for cf CLI.
- **Templates**:
  - Use `cds init --add sample` to generate a sample CAP project with Fiori app templates.
  - Adapt the `bookshop` sample from CAP documentation for a simple data model and UI.

---

### 6. CLI Tools and IDE Usage

- **VS Code**: Primary IDE for all development tasks (CDS, JavaScript, Fiori UI).
  - Use for editing `schema.cds`, `inventory-service.cds`, `.js` files, and `mta.yaml`.
  - Run Fiori Tools commands via the VS Code command palette (Ctrl+Shift+P).
- **cf CLI**: Used only for BTP deployment (Days 8-9).
  - Commands: `cf login`, `cf push`.
- **CDS CLI**: Part of `@sap/cds-dk`, used for project initialization, building, and local testing.
  - Commands: `cds init`, `cds watch`, `cds build`.
- **No BAS**: All tasks are handled in VS Code to avoid redundant cloud IDE setup.

---

### Additional Notes

- **Why VS Code Over BAS**: VS Code is local, lightweight, and sufficient for CAP/Fiori development with extensions. BAS requires BTP setup and is overkill for a solo project in a trial account.
- **SQLite vs. HANA**: SQLite is used locally for simplicity; BTP Trial auto-configures HANA for deployment if needed.
- **Keeping It Simple**: Fiori Elements minimizes UI coding, and the scope (CRUD + filtering) ensures completion in 10 days.
- **Portfolio Focus**: Document your process (e.g., GitHub README, screenshots) to showcase CAP, Fiori, and BTP skills to employers.
