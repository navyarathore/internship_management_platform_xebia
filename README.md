# Internship Management Platform - Engineering & Design Specifications

Welcome to the official repository for the **Internship Management Platform**. This repository contains high-fidelity software engineering design documentation, workflow definitions, wireframe layouts, and MVP scope requirements mapping the system architecture.

---

## 📄 Table of Specifications

The design specifications are structured across the following core documents:

### 1. [System Workflow Overview](workflow.md)
* **Goal**: Executive overview of user lifecycles and roles.
* **Content**: Comprehensive step-by-step lifecycles for Students, Recruiters, Placement Officers, and Administrators. Includes a beautiful high-fidelity combined master interaction flowchart.
* **Key Diagram**: Embedded modern high-fidelity infographic illustrating cross-role interactions.

### 2. [User Roles and Permissions Specification (01_User_Roles.md)](01_User_Roles.md)
* **Goal**: Define access privileges and user narratives.
* **Content**: Granular details for all four system roles (Purpose, Responsibilities, Dashboard Features, CRUD permissions, and Agile User Stories).
* **Key Table**: Comprehensive Role-Based Access Control (RBAC) Comparison Matrix.

### 3. [Key Features Specification (02_Key_Features.md)](02_Key_Features.md)
* **Goal**: Functional module breakdowns and criteria.
* **Content**: Inputs, outputs, validation business rules, and business benefits for Authentication, Student, Recruiter, Placement Officer, and Admin modules.
* **Key Framework**: MoSCoW Feature Prioritization Matrix.

### 4. [System Workflow and Sequence Diagrams (03_Workflow_Diagram.md)](03_Workflow_Diagram.md)
* **Goal**: Technical visual diagrams and error path definitions.
* **Content**: Black-and-white professional Mermaid flowcharts for every user role, detailed step-by-step logic, exception and error code definitions, and an end-to-end multi-party sequence diagram.

### 5. [Platform UI/UX Wireframe Specification (04_Wireframes.md)](04_Wireframes.md)
* **Goal**: SaaS-inspired low-fidelity interface layouts.
* **Content**: Interactive ASCII wireframe mockups for 10 core screens (Dashboards, Job Listings, Details Pages, Interview Schedulers, and Admin Panels) with user action flows.

### 6. [Minimum Viable Product (MVP) Definition (05_MVP_Definition.md)](05_MVP_Definition.md)
* **Goal**: Strategic launch boundaries and timeline.
* **Content**: Core MVP goal, included/excluded features lists, MoSCoW matrix, Success metrics KPIs, User Acceptance Criteria (UAC) validations, and Gantt-chart-backed 12-week development roadmap.

### 7. [Software Requirements Specification (SRS_Internship_Management_Platform.md)](SRS_Internship_Management_Platform.md)
* **Goal**: Core requirements baseline.
* **Content**: Problem statements, technology stack selection, and three-tier structural architecture overview.

---

## 🛠️ Technology Stack Selection

The platform operates on a **Three-Tier Architecture**:
* **Frontend**: React.js SPA (HTML, Vanilla CSS, JS)
* **Backend**: Node.js & Express.js REST API
* **Database**: MySQL (Persistent Relation Management)
* **Storage**: PDF File Storage (Resume Hosting, size limited $\le$ 5MB)
