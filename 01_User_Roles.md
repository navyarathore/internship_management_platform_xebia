# User Roles and Permissions Specification

This document details the definition, responsibilities, dashboard requirements, user stories, and granular permissions for the four primary user roles of the **Internship Management Platform**: **Student**, **Recruiter**, **Placement Officer**, and **Admin**.

---

## 1. Global Role Matrix & Permissions Comparison

To ensure a robust security model and clean role-based access control (RBAC), the platform defines distinct permission tiers. The following table provides an executive-level summary of access permissions across major platform operations.

| Platform Action / Entity | Student | Recruiter | Placement Officer | Administrator |
| :--- | :---: | :---: | :---: | :---: |
| **User Management** | None | None | None | **Full CRUD** |
| **Verify Recruiter Profiles** | None | None | **Update / Write** | **Full CRUD** |
| **Manage Student Profiles** | **Own Profile Only** | Read Only | **Read / Update** | **Full CRUD** |
| **Upload Resume (PDF)** | **Own Profile Only** | None | Read Only | **Full CRUD** |
| **Post / Edit Internship Openings**| None | **Own Postings Only** | **Approve / Read / Edit**| **Full CRUD** |
| **Apply to Internships** | **Write (Submit)** | None | None | None |
| **Shortlist & Interview Candidates**| None | **Own Applicants Only** | Read Only | **Full CRUD** |
| **Issue Selection / Rejection** | None | **Own Applicants Only** | Read Only | **Full CRUD** |
| **Assign Performance Ratings** | None | **Own Interns Only** | Read Only | **Full CRUD** |
| **Assign Academic Grades** | None | None | **Full CRUD** | **Full CRUD** |
| **System Audit Logs & Configuration**| None | None | None | **Full CRUD** |

---

## 2. Granular Role Specifications

### 2.1 Student Role

#### Purpose
To empower university candidates to maintain professional digital profiles, discover matched career openings, submit applications, track screening phases, and complete internship evaluations.

#### Key Responsibilities
* Maintain up-to-date academic transcripts, skill tags, and contact details.
* Upload verified professional resumes in standard PDF format.
* Actively track and respond to recruiter interview invites.
* Participate in self-evaluations during active placements.

#### Dashboard Features
* **Active Status Tracker**: Graphical progress bar indicating application progress (`Applied` $\rightarrow$ `Shortlisted` $\rightarrow$ `Interviewing` $\rightarrow$ `Selected/Rejected`).
* **Smart Search Portal**: Job filter dashboard featuring keyword search by technology stack, stipend brackets, and job type (Remote/On-site).
* **Profile Completeness Index**: Gamified visual indicator reminding students to upload resumes and complete mandatory profile fields.
* **Notifications Center**: Instant alert panel for interview invitations, application status updates, and placement team messages.

#### Granular Permissions & Access Rights
* **Read**:
  * Approved Internship postings.
  * Own profile details and resume.
  * Own application history and status.
  * Performance scorecards assigned by mentors (once finalized).
* **Write**:
  * Create own profile.
  * Submit internship applications.
  * Upload resume (PDF format, $\le$ 5MB).
* **Update**:
  * Edit own profile details, skills, and password.
  * Replace resume document.
* **Delete**:
  * Retract/cancel own pending applications.

#### User Stories
* **US-ST-01 (Profile Management)**:  
  *As a* student, *I want to* upload my latest PDF resume to my profile, *so that* recruiters can review my qualifications immediately when I apply.
* **US-ST-02 (Application Submission)**:  
  *As an* eligible student, *I want to* search for "React JS" internships and apply with a single click, *so that* I can participate in the ongoing placement cycle.
* **US-ST-03 (Status Tracking)**:  
  *As an* anxious applicant, *I want to* receive in-app alerts when my status transitions from `Shortlisted` to `Interview Scheduled`, *so that* I can prepare for the meeting in time.

---

### 2.2 Recruiter Role

#### Purpose
To provide verified corporate employers with a portal to publish open vacancies, review matched student credentials, coordinate screening rounds, select qualified candidates, and evaluate intern performance.

#### Key Responsibilities
* Provide valid corporate credentials and company documentation during registration.
* Author and update high-quality internship job descriptions.
* Review candidate profiles and resume PDFs within the allocated screening deadlines.
* Standardize interview scheduling and submit timely applicant status updates.
* Rate interns during the performance evaluation cycles.

#### Dashboard Features
* **Job Management Center**: List of all job listings created by the recruiter with metrics showing total views, applicants, and shortlists per job.
* **Applicant Screening Interface**: A visual kanban-style pipeline representing applicants under different hiring stages.
* **Scheduler Module**: Scheduling panel to log interview slots and share virtual links (Zoom/Google Meet) with candidates.
* **Evaluation Portal**: Form scorecard interface featuring standardized skill rating rubrics to evaluate active interns.

#### Granular Permissions & Access Rights
* **Read**:
  * Registered student profiles (only candidates who have applied to their jobs).
  * Candidate resumes and matching scores.
  * Own published internship details.
* **Write**:
  * Post new internship job listings (default status: `Pending Approval`).
  * Create interview schedules.
  * Submit intern performance ratings.
* **Update**:
  * Modify own job postings.
  * Update candidate application statuses (`Applied`, `Shortlisted`, `Selected`, `Rejected`).
  * Edit corporate contact details.
* **Delete**:
  * Cancel own job listings (deactivates visibility to students).

#### User Stories
* **US-REC-01 (Job Publishing)**:  
  *As a* recruiter, *I want to* post a "Node.js Developer" internship listing with a stipend amount, *so that* qualified students can start applying.
* **US-REC-02 (Screening & Shortlist)**:  
  *As a* hiring manager, *I want to* filter applications by "GPA > 3.5" and download their resumes, *so that* I can shortlist the top candidates.
* **US-REC-03 (Intern Evaluation)**:  
  *As a* corporate mentor, *I want to* submit a score of "4.5 out of 5" for my active intern on the performance scorecard, *so that* their placement officer can assign their final academic grade.

---

### 2.3 Placement Officer Role

#### Purpose
To act as the primary operational coordinator overseeing all student preparation, verifying corporate recruiters, supervising job matches, and translating recruiter feedback into final academic grades.

#### Key Responsibilities
* Conduct rigorous verification of corporate emails, websites, and business records for new recruiter signups.
* Audit and approve/deny pending internship listings to maintain job quality.
* Monitor placement progress rates across all departments.
* Convert corporate performance scores into academic grades at the end of the semester.

#### Dashboard Features
* **Verification Queue**: Dedicated list of pending recruiters and jobs requiring immediate authorization.
* **Platform Analytics Dashboard**: High-level charts tracking total jobs posted, placement percentages, active interviews, and unplaced students.
* **Report Generator**: File export tool to extract Excel/PDF reports on average stipends, top recruiters, and student evaluation summaries.
* **Grading Console**: Grade sheet grid showing final employer ratings and input fields to assign academic grades.

#### Granular Permissions & Access Rights
* **Read**:
  * All student profiles, resumes, and application histories.
  * All recruiter profiles, business metadata, and job listings.
  * Global analytics, reports, and grading sheets.
* **Write**:
  * Generate and export statistical reports.
  * Assign academic grades to students.
* **Update**:
  * Approve/Reject recruiter profile registrations.
  * Approve/Reject pending internship job listings.
  * Edit student academic details or eligibility statuses in case of corrections.
* **Delete**:
  * None (All actions are soft-archived for audit safety).

#### User Stories
* **US-PO-01 (Recruiter Verification)**:  
  *As a* placement officer, *I want to* review the business license of a newly registered recruiter, *so that* I can activate their account and protect students from spam postings.
* **US-PO-02 (Analytics Monitoring)**:  
  *As a* director of placements, *I want to* view a chart showing the percentage of placed vs. unplaced students by department, *so that* I can plan targeted outreach to employers.
* **US-PO-03 (Academic Grading)**:  
  *As an* academic coordinator, *I want to* view the scorecard submitted by a student's employer and assign a final letter grade of "A", *so that* it can be logged in the university's academic system.

---

### 2.4 Administrator Role

#### Purpose
To serve as the root system authority, managing global database tables, setting system limits, auditing platform logs, managing user privileges, and resolving software exceptions.

#### Key Responsibilities
* Manage database schemas, user privileges, and security settings.
* Manage user accounts across all roles (activate, deactivate, reset).
* Diagnose platform exceptions and maintain system availability target of 99.5%.
* Review global audit logs to protect data integrity and transmission security.

#### Dashboard Features
* **System Health Monitor**: Live charts displaying API latency, storage consumption (PDF file storage), and network load.
* **User Accounts Manager**: Centralized table of all registered students, recruiters, and placement officers with toggle switches to suspend/reactivate accounts.
* **Security & Auditing Console**: Chronological table showing global audit logs (login attempts, failed access attempts, profile edits, system updates).
* **Settings & Config Panel**: Centralized module to set storage thresholds (e.g., maximum resume file size) and database backup schedules.

#### Granular Permissions & Access Rights
* **Read**:
  * Complete database entries, configurations, security parameters, and audit trails.
* **Write**:
  * Create new administrator accounts.
  * Trigger database backups.
* **Update**:
  * **Full Override Capability**: Update any record, profile, or job posting in the platform.
  * Modify global system configuration values.
* **Delete**:
  * **Full Hard Delete Rights**: Permanently purge records, user profiles, or corrupted files (restricted to Admins to maintain platform compliance).

#### User Stories
* **US-ADM-01 (Account Management)**:  
  *As a* system administrator, *I want to* temporarily suspend a recruiter's account who was flagged for spamming students, *so that* the integrity of the platform remains intact.
* **US-ADM-02 (Configuration Control)**:  
  *As a* system administrator, *I want to* update the global maximum resume size from 5MB to 2MB, *so that* we can optimize cloud storage budgets.
* **US-ADM-03 (Security Audit)**:  
  *As a* security officer, *I want to* search the system audit logs for all failed login attempts, *so that* I can identify and block malicious login attempts.
