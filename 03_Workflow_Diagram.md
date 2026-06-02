# Internship Management Platform Workflows

This document contains the core workflow diagrams and sequence diagrams for the Internship Management Platform using Mermaid syntax.

---

## 1. System Overview Flowchart

This flowchart illustrates the high-level interactions between the Student, Recruiter, Placement Officer, and Admin. The Placement Officer monitors the overall placement process, while the Admin manages system users and recruiters.

```mermaid
flowchart TD
    Student[Student] -->|Apply for Internship| Apply[Apply]
    Apply --> Review[Recruiter Reviews]
    Review --> Decision{Select / Reject}
    Decision -->|Status Update| Result[Student Receives Result]
    
    PO[Placement Officer] -.->|Monitors Activity| Apply
    PO -.->|Monitors Activity| Review
    
    Admin[Admin] -.->|Manages Users & Recruiters| Student
    Admin -.->|Manages Users & Recruiters| Review
```

---

## 2. Student Application Workflow

This diagram outlines the step-by-step workflow for a student, from initial registration to the final selection or rejection outcome.

```mermaid
flowchart TD
    Register[Register] --> Profile[Create Profile]
    Profile --> Resume[Upload Resume]
    Resume --> Browse[Browse Internships]
    Browse --> Apply[Apply]
    Apply --> Review[Application Review]
    Review --> Interview[Interview]
    Interview --> Outcome{Interview Outcome}
    Outcome -->|Success| Selected[Selected]
    Outcome -->|Failure| Rejected[Rejected]
```

---

## 3. Recruiter Workflow

This flowchart details the recruiter lifecycle, showing the mandatory verification check after registration and the decision logic for the final candidate selection.

```mermaid
flowchart TD
    Register[Register] --> Verification{Verification}
    Verification -->|Approved| Post[Post Internship]
    Verification -->|Rejected| End[End]
    Post --> Review[Review Applications]
    Review --> Shortlist[Shortlist Candidates]
    Shortlist --> Interview[Conduct Interview]
    Interview --> Selection{Final Selection}
    Selection -->|Select| SelectCandidate[Select Candidate]
    Selection -->|Reject| RejectCandidate[Reject Candidate]
```

---

## 4. System Sequence Diagram

This sequence diagram displays the chronological messages exchanged between the Student, Platform, and Recruiter during the application and review cycle.

```mermaid
sequenceDiagram
    actor Student
    participant Platform
    actor Recruiter

    Student->>Platform: Log in
    Platform-->>Student: Confirm session
    Student->>Platform: Apply for internship
    Platform->>Platform: Store application
    Recruiter->>Platform: Review application
    Recruiter->>Platform: Update status
    Platform-->>Student: Notify student of status update
```
