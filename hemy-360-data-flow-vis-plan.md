# Hemy 360 Data Flow Visualization: Detailed Project Plan

## 1. Executive Summary
This document outlines the plan to implement the Hemy 360 Data Flow Visualization project. The goal is to create a central, visual, and intelligent model of the data flows between our key enterprise applications. This will reduce operational risk, improve change management, and provide clear visibility into our data landscape.

## 2. Detailed Project Phases

### Phase 1: Discovery and Metadata Collection
*   **Objective:** To gather all necessary information about the source systems, their data, and existing integrations.
*   **Instructional Steps:**
    *   [ ] **Step 1.1: Finalize Scope & Schedule Workshops:** Confirm the list of in-scope systems and schedule discovery workshops with the subject matter experts (SMEs) and technical owners for each one.
        *   **Systems:** Dynamics 365, Business Central, Autodesk Construction Cloud, BIM 3D Models.
    *   [ ] **Step 1.2: Create Metadata Template:** Define a standardized template (e.g., in Excel or a JSON schema) to ensure consistent information gathering.
        *   **Fields:** System, Entity, Field Name, Data Type, Max Length, Description, Is Primary Key, Is Foreign Key, Related Entity.
    *   [ ] **Step 1.3: Extract Technical Metadata:** Use system APIs, database queries, or backend access to extract lists of entities and fields from the source applications.
    *   [ ] **Step 1.4: Map Existing Integrations:** Analyze integration artifacts (e.g., source code, API logs, middleware configurations) to trace how data currently moves between systems.
    *   [ ] **Step 1.5: Consolidate Findings:** Populate the metadata template with the collected information, creating a consolidated inventory for analysis.

### Phase 2: Business Concept Ontology Definition
*   **Objective:** To define a canonical set of business concepts that will form the core of the intelligence model.
*   **Instructional Steps:**
    *   [ ] **Step 2.1: Analyze and Group Fields:** Review the metadata from Phase 1 and group fields from different systems that represent the same business idea (e.g., `proj_id`, `ProjectIdentifier`, `d365_project`).
    *   [ ] **Step 2.2: Draft Ontology:** For each group, define a clear and concise "Business Concept" name and description.
        *   **Example:** Concept: `Project ID`, Definition: "The unique identifier for a construction or business project used across all Hemy systems."
    *   [ ] **Step 2.3: Formalize Ontology Document:** Create a formal document listing each Business Concept, its definition, expected data type, and examples of the source fields it relates to.
    *   [ ] **Step 2.4: Review and Validate:** Conduct a workshop with business analysts and data owners to review, refine, and formally approve the ontology.

### Phase 3: Technology Stack Setup
*   **Objective:** To provision, configure, and model the required Microsoft Fabric and Dataverse components.
*   **Instructional Steps:**
    *   [ ] **Step 3.1: Provision Dataverse Environment:** Create a new Dataverse solution (e.g., `HemyDataFlowIntelligence`) to house the model.
    *   [ ] **Step 3.2: Model Dataverse Tables:** Within the solution, create the custom tables to store the model's components:
        *   `dfl_SourceSystem` (Name, Description)
        *   `dfl_BusinessConcept` (Name, Definition, Data_Type)
        *   `dfl_SourceField` (Name, TechnicalName, System, Entity)
        *   `dfl_FieldMapping` (Lookup to SourceField, Lookup to BusinessConcept, Confidence)
    *   [ ] **Step 3.3: Set Up Fabric Workspace:** Create a new Microsoft Fabric workspace (e.g., `Hemy 360 Data & Analytics`) and provision a Lakehouse within it (e.g., `DataFlowIntelligenceLH`).
    *   [ ] **Step 3.4: Configure Access:** Implement Role-Based Access Control (RBAC) in both Dataverse and Fabric to grant appropriate permissions to the project team.

### Phase 4: Data Ingestion and Mapping
*   **Objective:** To populate the Dataverse repository and Fabric Lakehouse with the collected metadata and mappings.
*   **Instructional Steps:**
    *   [ ] **Step 4.1: Develop Ingestion Pipelines:** Use Fabric Dataflows Gen2 or Notebooks to build pipelines that extract metadata from the source systems (or the consolidated inventory from Step 1.5).
    *   [ ] **Step 4.2: Populate Core Tables:** Execute the pipelines to populate the `dfl_SourceSystem` and `dfl_SourceField` tables in Dataverse.
    *   [ ] **Step 4.3: Load Ontology:** Write a script or manual process to load the approved Business Concepts from the ontology document (Step 2.3) into the `dfl_BusinessConcept` table.
    *   [ ] **Step 4.4: Create Mapping Interface:** Build a simple Power App or use Dataverse views to enable a data steward to create the `dfl_FieldMapping` records, establishing the links between source fields and concepts.
    *   [ ] **Step 4.5: Synchronize to Lakehouse:** Create a Fabric Data Pipeline to copy data from the Dataverse tables into the Lakehouse on a recurring schedule.

### Phase 5: Visualization and Intelligence Layer
*   **Objective:** To build the interactive visualization and analysis layer for business and technical users.
*   **Instructional Steps:**
    *   [ ] **Step 5.1: Connect and Model in Power BI:** Connect Power BI to the Lakehouse tables and create a user-friendly semantic model.
    *   [ ] **Step 5.2: Design Core Dashboard:** Build the main dashboard with two primary views:
        *   **Concept-to-System View:** Allow users to select a Business Concept and see all the systems and fields that map to it.
        *   **System-to-Concept View:** Allow users to select a Source System and see all the Business Concepts it contains.
    *   [ ] **Step 5.3: Implement Visuals and Search:** Use a network graph or Sankey diagram visual to show the flow. Add a search bar to find any field, concept, or system.
    *   [ ] **Step 5.4: (Stretch Goal) Build Impact Analysis Report:** Create a report page where a user can select a field and see a dependency tree of all connected fields and systems via the shared business concepts.
    *   [ ] **Step 5.5: Publish and Share:** Publish the Power BI report to the Fabric workspace and create a Power BI App to share with end-users.

### Phase 6: Governance and Maintenance
*   **Objective:** To establish a long-term process for maintaining the accuracy and relevance of the data flow model.
*   **Instructional Steps:**
    *   [ ] **Step 6.1: Integrate with Change Management:** Update the corporate Change Management policy to require that any project involving cross-system data integration must update the Data Flow Intelligence Model.
    *   [ ] **Step 6.2: Define Roles and Responsibilities:** Formally define the "Data Steward" role and assign individuals to own the accuracy of the mappings.
    *   [ ] **Step 6.3: Create Health Dashboard:** Build a Power BI report that monitors the model's health, showing metrics like "Unmapped Source Fields" or "Concepts with No Mappings."
    *   [ ] **Step 6.4: Establish Review Cadence:** Schedule a quarterly meeting with Data Stewards to review the model's accuracy and plan for upcoming changes.
    *   [ ] **Step 6.5: Create Documentation Hub:** Set up a central location (e.g., SharePoint page) with links to the Power BI reports, user guides, and contact information for the Data Stewards.