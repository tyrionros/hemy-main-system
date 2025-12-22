# Project Timeline and Learning Plan

This document provides a frank and realistic timeline for the "Hemy 360 Data Flow Visualization" project, specifically accounting for the learning curve associated with Microsoft Fabric and related technologies. It also includes a suggested learning path with resources and practice exercises.

## 1. Realistic Project Timeline

Given that you are new to Microsoft Fabric, a significant portion of the timeline is dedicated to foundational learning. Rushing the technical phases without this will lead to frustration and rework.

**Total Estimated Duration:** Approximately 4 Months

| Phase | Estimated Duration | Key Activities & Considerations |
| :--- | :--- | :--- |
| **Phase 1: Discovery** | 2-3 Weeks | Business analysis, SME workshops, data archaeology. Low dependency on Fabric skills. |
| **Phase 2: Ontology Definition** | 1-2 Weeks | Business analysis, stakeholder validation. No dependency on Fabric skills. |
| **--- Foundational Learning ---** | **3-4 Weeks** | **(Crucial Step)** Dedicated time to go through the learning plan below *before* starting technical implementation. |
| **Phase 3: Tech Setup** | 1 Week | Provisioning resources, creating Dataverse solution. Requires basic Fabric & Dataverse knowledge. |
| **Phase 4: Ingestion & Mapping** | 3-5 Weeks | High learning curve. Building first dataflows, debugging, creating a simple mapping app. |
| **Phase 5: Visualization** | 2-4 Weeks | Building Power BI reports on the new model. Learning to use graph visuals. |
| **Phase 6: Governance** | 1 Week | Process definition. Can run in parallel with the end of Phase 5. |

---

## 2. Recommended Learning Path & Practice Builds

This path is designed to build your skills sequentially, from theory to hands-on practice.

### Step 1: Understand the Core Concepts (Theory)

Before touching the technology, grasp the "why." Your project is based on a modern data modeling paradigm.

*   **What is an Ontology?**
    *   **Resource:** [Introduction to Ontology Modeling](https://www.blindata.io/blog/introduction-to-ontology-modeling)
    *   **Goal:** Understand that you are defining business concepts (`Project ID`) and their relationships, not just database tables.
*   **What is a Graph Database?**
    *   **Resource:** [Graph Databases for Beginners](https://neo4j.com/graph-database-for-beginners/)
    *   **Goal:** Understand why a graph is perfect for this project. It stores *relationships* as a primary citizen, making it fast and intuitive to ask "what's connected to what?"

### Step 2: Microsoft Fabric Fundamentals (Hands-On)

Get comfortable in the Fabric environment.

*   **Learning Path:**
    *   **Resource:** [Get started with Microsoft Fabric](https://learn.microsoft.com/en-us/fabric/get-started/fabric-trial) - Start your free trial here.
    *   **Resource:** [Microsoft Fabric Learn paths & modules](https://learn.microsoft.com/en-us/fabric/get-started/browse-learning-paths) - Focus on the "Get started with..." modules.
*   **Practice Build: "My First Lakehouse"**
    1.  Create a new Fabric Workspace.
    2.  Create a **Lakehouse**.
    3.  Download a simple CSV file (e.g., sample sales data).
    4.  Use the "Get Data" -> "Files" wizard to upload the CSV to your Lakehouse.
    5.  Create a Power BI report directly from the Lakehouse data.

### Step 3: Dataverse for Beginners (Hands-On)

Dataverse will be your metadata hub where you define the concepts.

*   **Learning Path:**
    *   **Resource:** [YouTube Tutorial: Intro to Dataverse in Power Apps](https://www.youtube.com/watch?v=s_wcl3a2aT8)
    *   **Goal:** Learn how to create tables, columns, and relationships within a "Solution".
*   **Practice Build: "Mini-Ontology Model"**
    1.  In Power Apps, create a new **Solution**.
    2.  Inside the solution, create the three custom tables from your project plan: `SourceSystem`, `BusinessConcept`, and `FieldMapping`.
    3.  Add 2-3 sample columns to each (e.g., `Name`, `Description`).
    4.  Manually enter a few rows of sample data (e.g., System: "D365 CRM", Concept: "Project ID").

### Step 4: Connecting the Dots (Hands-On)

This is a critical step: bringing your metadata model into Fabric.

*   **Learning Path:**
    *   **Resource:** [Tutorial on Dataflow Gen2](https://learn.microsoft.com/en-us/fabric/data-factory/tutorial-get-started-dataflow-gen2)
    *   **Goal:** Understand how to extract data from a source (for this practice, Dataverse) and land it in your Fabric Lakehouse.
*   **Practice Build: "Sync to Fabric"**
    1.  In the Fabric workspace, create a new **Dataflow Gen2**.
    2.  Use the "Get data" connector for **Dataverse**.
    3.  Connect to your environment and select the three "Mini-Ontology" tables you created.
    4.  For the "Data destination," choose your "My First Lakehouse".
    5.  Run the dataflow and verify that the tables now appear in your Lakehouse.

### Step 5: Visualization with Fabric IQ Concepts

With the data in Fabric, you can now visualize it.

*   **Learning Path:**
    *   **Resource:** [Official Fabric IQ Documentation](https://learn.microsoft.com/en-us/fabric/iq/) (Bookmark this, it will be updated often).
    *   **Resource:** [Power BI network graph custom visuals](https://appsource.microsoft.com/en-us/marketplace/apps?search=network%20graph&page=1) (Explore these options).
*   **Practice Build: "Visualize the Connections"**
    1.  Create a new Power BI report from the Lakehouse tables you just synced.
    2.  Create a simple table or matrix visual showing the relationships between your sample systems and concepts.
    3.  Add a "Network Navigator" or similar custom visual from the marketplace.
    4.  Configure the visual to show `SourceSystem` as one node and `BusinessConcept` as another, linked by the `FieldMapping` data.
    5.  This will give you a basic, interactive graph—a miniature version of your final goal.
