# Hemy 360 Data Flow Visualization
## 1. Background
Our organisation uses multiple enterprise applications, including:
- Dynamics 365 CRM
- Business Central
- Autodesk Construction Cloud
- BIM 3D Models
These systems are connected through APIs and integrations, and data flows across them at field level (for example: Customer ID, Project ID, Project Status).
As the number of integrations increases, it becomes difficult to clearly understand:
- Which systems are connected
- How data flows between systems
- Which fields represent the same business meaning across applications
- What the impact is when a field or integration changes
## 2. Problem Statement
Currently:
- Data connections are spread across code, APIs, and technical documentation
- There is no single, visual, or authoritative view of end-to-end data flow
- Field-to-field mapping does not scale when fields are involved
- Understanding dependencies requires manual analysis by technical teams
This results in:
- Increased operational risk
- Uncertainty when making changes
- Dependence on individual knowledge rather than shared visibility
## 3. Proposed Solution (High Level)
We propose creating a central data-flow intelligence model using:
- Dataverse as a metadata repository
- Microsoft Fabric / Lakehouse for storage and analytics
- Microsoft Fabric IQ (Ontology) for visualisation and intelligence
Instead of mapping every field directly to other fields, the solution uses a business-concept-based approach.
## 4. Key Idea (Simple Explanation)
Rather than defining connections like:
“Field A in System 1 connects to Field B in System 2”
 
We define shared business concepts, such as:
Customer ID
Project ID
Project Status
Each system’s field is mapped to a common business concept.
This creates a single source of truth for understanding how data is connected across systems, without unnecessary complexity.
