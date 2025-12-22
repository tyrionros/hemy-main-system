# Hemy 360 Data Flow Visualization: Project Plan

## 1. Executive Summary
This document outlines the plan to implement the Hemy 360 Data Flow Visualization project. The goal is to create a central, visual, and intelligent model of the data flows between our key enterprise applications. This will reduce operational risk, improve change management, and provide clear visibility into our data landscape.

## 2. Project Phases

### Phase 1: Discovery and Metadata Collection
*   **Objective:** To gather all necessary information about the source systems, their data, and existing integrations.
*   **Tasks:**
    *   [ ] Finalize the list of in-scope systems (Dynamics 365, Business Central, Autodesk Construction Cloud, BIM 3D Models).
    *   [ ] For each system, identify and document key data entities and fields involved in integrations.
    *   [ ] Analyze existing APIs, middleware, and integration jobs to understand current data flow paths.
    *   [ ] Store the collected metadata in a temporary staging area for analysis.

### Phase 2: Business Concept Ontology Definition
*   **Objective:** To define a canonical set of business concepts that will form the core of the intelligence model.
*   **Tasks:**
    *   [ ] Analyze the metadata from Phase 1 to identify recurring business concepts (e.g., Customer, Project, Address, Status).
    *   [ ] Create a formal dictionary/ontology for these concepts, including a clear definition for each.
    *   [ ] Validate the ontology with business and technical stakeholders to ensure accuracy and completeness.
    *   [ ] Initial concepts to define: `Customer ID`, `Project ID`, `Project Status`.

### Phase 3: Technology Stack Setup
*   **Objective:** To provision and configure the required Microsoft Fabric and Dataverse components.
*   **Tasks:**
    *   [ ] Provision a Microsoft Dataverse environment to serve as the metadata repository.
    *   [ ] Design and create the Dataverse tables to store:
        *   Source Systems
        *   Source Entities & Fields
        *   Business Concepts (Ontology)
        *   Field-to-Concept Mappings
    *   [ ] Set up a Microsoft Fabric workspace and a Lakehouse for data storage and analytics.
    *   [ ] Configure access and permissions for the development team.

### Phase 4: Data Ingestion and Mapping
*   **Objective:** To populate the Dataverse repository and Fabric Lakehouse with the collected metadata and mappings.
*   **Tasks:**
    *   [ ] Develop data ingestion pipelines (using Fabric Dataflows or other tools) to extract metadata from source systems and load it into Dataverse.
    *   [ ] Load the defined Business Concept Ontology (from Phase 2) into Dataverse.
    *   [ ] Implement the logic to map source fields to their corresponding business concepts in Dataverse.
    *   [ ] Create a pipeline to synchronize the mapped data from Dataverse to the Fabric Lakehouse.

### Phase 5: Visualization and Intelligence Layer
*   **Objective:** To build the interactive visualization and analysis layer.
*   **Tasks:**
    *   [ ] Connect Microsoft Fabric IQ (or Power BI) to the data in the Lakehouse.
    *   [ ] Design and build the primary visualization dashboard, allowing users to explore data flows from a system-centric or concept-centric view.
    *   [ ] Implement search functionality to easily find systems, fields, or concepts.
    *   [ ] (Stretch Goal) Develop an impact analysis report that shows dependencies for a selected field or concept.

### Phase 6: Governance and Maintenance
*   **Objective:** To establish a long-term process for maintaining the accuracy of the data flow model.
*   **Tasks:**
    *   [ ] Define a process for updating the model when new integrations are built or existing ones are modified.
    *   [ ] Assign ownership and responsibilities for maintaining the system.
    *   [ ] Create documentation and training materials for users and administrators.
