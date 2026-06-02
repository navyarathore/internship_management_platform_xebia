# System Workflow Overview

This document provides a comprehensive overview of the key workflows within the **Internship Management Platform**. It details the step-by-step processes for the four primary user roles: **Students**, **Recruiters**, **Placement Officers**, and **Administrators**.

## Master System Workflow

Below is the high-level interaction diagram showing how all four user roles securely interact and collaborate within the platform.

```mermaid
flowchart TD
    %% Subgraphs for roles to make it highly structured and readable
    subgraph Admins ["🛡️ Administrators"]
        A_Manage[Manage Users & System Settings]
        A_Approve[Approve & Verify Recruiters]
    end

    subgraph Officers ["💼 Placement Officers"]
        PO_Verify[Verify & Approve Recruiters]
        PO_Monitor[Monitor Postings & Applications]
        PO_Reports[Generate Performance & Placement Reports]
    end

    subgraph Recruiters ["🏢 Recruiters"]
        R_Register[Register & Request Verification]
        R_Post[Post Internship Openings]
        R_Review[Review Resumes & Applications]
        R_Interview[Schedule & Conduct Interviews]
        R_Select[Select Candidates / Issue Offers]
    end

    subgraph Students ["🎓 Students"]
        S_Register[Register & Complete Profile]
        S_Upload[Upload PDF Resume]
        S_Browse[Browse & Search Openings]
        S_Apply[Apply to Internships]
        S_Track[Track Application Status]
        S_Accept[Accept Offer & Begin Internship]
    end

    %% Key Interactions
    R_Register -->|Pending Account| PO_Verify
    A_Approve -.->|Override Verification| R_Register
    
    PO_Verify -->|Approval| R_Post
    R_Post -->|Published Openings| S_Browse
    
    S_Register --> S_Upload --> S_Browse
    S_Browse -->|Select & Submit| S_Apply
    S_Apply -->|Receive Applications| R_Review
    
    R_Review --> R_Interview
    R_Interview --> R_Select
    
    R_Select -->|Selection Notification| S_Track
    S_Track -->|Offer Accepted| S_Accept
    
    S_Apply -.->|Activity Feeds| PO_Monitor
    R_Select -.->|Placement Outcomes| PO_Reports

    %% Theme and Styling
    classDef admin fill:#faf5ff,stroke:#7c3aed,stroke-width:1.5px;
    classDef officer fill:#fff7ed,stroke:#ea580c,stroke-width:1.5px;
    classDef recruiter fill:#ecfeff,stroke:#0891b2,stroke-width:1.5px;
    classDef student fill:#f0fdf4,stroke:#16a34a,stroke-width:1.5px;

    class A_Manage,A_Approve admin;
    class PO_Verify,PO_Monitor,PO_Reports officer;
    class R_Register,R_Post,R_Review,R_Interview,R_Select recruiter;
    class S_Register,S_Upload,S_Browse,S_Apply,S_Track,S_Accept student;
```

### Visual Workflow Infographic

Here is a visual presentation of the platform workflows and interactions:

![System Workflow Overview Infographic](system_workflow_diagram.png)

---

## 1. Student Workflow

The Student Workflow outlines how candidates engage with the platform from their initial registration to tracking the final status of their applications.

### Workflow Diagram

```mermaid
flowchart TD
    %% Node Definitions
    Start([Start: Student Entry]) --> Reg[1. Registration]
    Reg --> Prof[2. Profile Creation]
    Prof --> Res[3. Resume Upload]
    Res --> Browse[4. Browse Internships]
    Browse --> Apply[5. Apply to Internship]
    Apply --> Track[6. Track Status]
    
    Track --> Decision{Application Status}
    Decision -->|Shortlisted| Interview[7. Interview Process]
    Decision -->|Rejected| Browse
    
    Interview --> Outcome{Interview Outcome}
    Outcome -->|Selected| Accept[8. Selection & Internship]
    Outcome -->|Rejected| Browse
    
    Accept --> End([End: Placement Complete])

    %% Styling and Classes
    classDef startEnd fill:#e0f2fe,stroke:#0284c7,stroke-width:2px,rx:10px,ry:10px;
    classDef process fill:#f0fdf4,stroke:#16a34a,stroke-width:1px;
    classDef decision fill:#fffbeb,stroke:#d97706,stroke-width:2px;
    
    class Start,End startEnd;
    class Reg,Prof,Res,Browse,Apply,Track,Interview,Accept process;
    class Decision,Outcome decision;
```

### Detailed Steps

1. **Registration**: 
   Students register on the platform using their unique university-issued credentials. This guarantees that only enrolled and authorized students gain access to the internship search capabilities.
2. **Profile Creation**: 
   Once registered, students construct their digital profile. They input crucial academic details including current GPA, graduation year, core technical or business skills, and areas of interest.
3. **Resume Upload**: 
   Students upload their professional resume in PDF format. The system enforces strict security and file constraints (e.g., maximum file size of 5MB) to ensure system reliability and uniform storage.
4. **Browse Internships**: 
   Students can search, filter, and explore active job postings. They can filter opportunities based on domains, technologies, geographic location, stipend range, and duration.
5. **Apply**: 
   Upon finding a suitable internship, the student submits a formal application. This action creates a record connecting the Student's profile to the Recruiter's job post.
6. **Track Status**: 
   Students can monitor the real-time lifecycle of their applications (e.g., `Applied`, `Shortlisted`, `Under Interview Review`, or `Selected/Rejected`) directly via their dashboard notifications.

---

## 2. Recruiter Workflow

The Recruiter Workflow defines how employer representatives register, get verified, list vacancies, evaluate applicant profiles, and execute recruitment outcomes.

### Workflow Diagram

```mermaid
flowchart TD
    %% Node Definitions
    Start([Start: Recruiter Registration]) --> Reg[1. Registration]
    Reg --> Verification[2. Verification Request]
    Verification --> ApprDecision{Approved by PO/Admin?}
    
    ApprDecision -->|No| Denied([End: Registration Denied])
    ApprDecision -->|Yes| Post[3. Post Internship]
    
    Post --> Review[4. Review Applicants]
    Review --> Shortlist[5. Shortlist Candidates]
    Shortlist --> Interview[6. Interview Process]
    Interview --> SelectDecision{Recruitment Choice}
    
    SelectDecision -->|Select| Offer[7. Select / Issue Offer]
    SelectDecision -->|Reject| Decline[7. Reject Candidate]
    
    Offer --> End([End: Position Filled])
    Decline --> Review

    %% Styling and Classes
    classDef startEnd fill:#ecfeff,stroke:#0891b2,stroke-width:2px,rx:10px,ry:10px;
    classDef process fill:#fef2f2,stroke:#b91c1c,stroke-width:1px;
    classDef decision fill:#fffbeb,stroke:#d97706,stroke-width:2px;
    classDef success fill:#f0fdf4,stroke:#16a34a,stroke-width:1px;
    
    class Start,End,Denied startEnd;
    class Reg,Verification,Post,Review,Shortlist,Interview,Decline process;
    class ApprDecision,SelectDecision decision;
    class Offer success;
```

### Detailed Steps

1. **Registration**: 
   Recruiters sign up using their official corporate email addresses and provide key corporate identification details, such as company name, industry segment, and recruiter credentials.
2. **Verification**: 
   The recruiter account enters a pending state. It must undergo manual verification by either the Placement Officer or a System Administrator to prevent fraudulent accounts.
3. **Post Internship**: 
   Verified recruiters create detailed internship listings, defining roles and responsibilities, required skills, work location, compensation details, and applicant eligibility parameters.
4. **Review Applicants**: 
   Recruiters view the applicants' dashboard where they can read profile details, cross-reference skill matches, and download candidate resumes.
5. **Shortlist**: 
   Recruiters tag promising profiles as `Shortlisted`, signaling to students that their application has successfully cleared the initial screening phase.
6. **Interview**: 
   Recruiters organize and hold interviews. Since video calling is out-of-scope for the native system, external links (e.g., Zoom, Google Meet) are shared and logged within the system's scheduling module.
7. **Select/Reject**: 
   Based on interview performance, recruiters update the status to `Selected` or `Rejected`. The platform triggers instant notifications to candidates and Placement Officers.

---

## 3. Placement Officer Workflow

The Placement Officer (or Coordinator) serves as the primary operational authority, verifying external entities, monitoring placement statistics, and generating official analytics.

### Workflow Diagram

```mermaid
flowchart TD
    %% Node Definitions
    Start([Start: PO Dashboard]) --> Verify[1. Verify Recruiters]
    Verify --> Decision{Verification Action}
    
    Decision -->|Approve| Act[Activate Recruiter Account]
    Decision -->|Reject| Deny[Deny Recruiter Access]
    
    Act --> Monitor[2. Monitor Applications]
    Monitor --> Reports[3. Generate Reports]
    Reports --> End([End: Cycle Completed])

    %% Styling and Classes
    classDef startEnd fill:#fff7ed,stroke:#ea580c,stroke-width:2px,rx:10px,ry:10px;
    classDef process fill:#fcfaf2,stroke:#ca8a04,stroke-width:1px;
    classDef decision fill:#fffbeb,stroke:#d97706,stroke-width:2px;
    
    class Start,End startEnd;
    class Verify,Act,Deny,Monitor,Reports process;
    class Decision decision;
```

### Detailed Steps

1. **Verify Recruiters**: 
   Placement Officers perform background checks on newly registered recruiters, evaluating company credentials, websites, and job validity before granting backend access.
2. **Monitor Applications**: 
   Placement Officers supervise active internships, seeing total applicant numbers, monitoring which recruiters are actively hiring, and identifying students who have yet to secure placements.
3. **Generate Reports**: 
   Placement Officers compile and export statistical reports detailing overall placement percentages, performance reviews submitted by employers, and student eligibility.

---

## 4. Admin Workflow

Administrators control the core system stability, manage permissions, resolve system exceptions, and audit global platform activities.

### Workflow Diagram

```mermaid
flowchart TD
    %% Node Definitions
    Start([Start: Admin Panel]) --> Manage[1. Manage Users]
    Manage --> Approve[2. Approve Recruiters]
    Approve --> Monitor[3. Monitor Platform]
    Monitor --> End([End: Routine Audit Complete])

    %% Styling and Classes
    classDef startEnd fill:#faf5ff,stroke:#7c3aed,stroke-width:2px,rx:10px,ry:10px;
    classDef process fill:#fdfbf7,stroke:#b45309,stroke-width:1px;
    
    class Start,End startEnd;
    class Manage,Approve,Monitor process;
```

### Detailed Steps

1. **Manage Users**: 
   Administrators oversee all user roles, resolve credential resets, deactivate accounts violating policies, and re-assign roles when university staff changes occur.
2. **Approve Recruiters**: 
   Administrators retain secondary/override approval rights on recruiters to support the placement officer staff during high-volume recruitment cycles.
3. **Monitor Platform**: 
   Administrators track total storage consumption (resumes), monitor API response metrics, and check background logs to ensure the system is operating optimally and securely.
