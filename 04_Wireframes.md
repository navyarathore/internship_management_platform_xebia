# Platform UI/UX Wireframe Specification

This document presents the low-fidelity ASCII wireframes and interface specifications for the **Internship Management Platform**. It maps the UI layouts, functional components, navigation paths, and user actions for the ten primary screens of the application.

---

## 1. Landing Page

### Purpose
To welcome prospective students and recruiters, present key value propositions, show general statistics, and provide entry points to log in or register.

### ASCII Wireframe
```text
+-----------------------------------------------------------------------------------+
|  [Logo] InternSphere        [About]   [Features]   [Stats]     [Login] [Register] |
+-----------------------------------------------------------------------------------+
|                                                                                   |
|                      CONNECTING TALENT TO OPPORTUNITY                             |
|          Streamlined academic internships for students and verified employers.   |
|                                                                                   |
|                     [ Find Internships ]   [ Post a Job ]                         |
|                                                                                   |
+-----------------------------------------------------------------------------------+
|                                                                                   |
|    [ ACTIVE STUDENTS ]       [ PARTNER COMPANIES ]        [ JOBS COMPLETED ]      |
|         12,450 +                   450 +                       8,900 +            |
|                                                                                   |
+-----------------------------------------------------------------------------------+
|  Features Spotlight:                                                              |
|  +-----------------------+ +-----------------------+ +-----------------------+   |
|  |   Verified Employers  | |   Direct Apply (PDF)  | |   Academic Grading    |   |
|  |   Only approved and   | |   Upload once, apply  | |   Feedback syncs      |   |
|  |   legit companies.    | |   with one single click.  | |   directly to GPA.    |   |
|  +-----------------------+ +-----------------------+ +-----------------------+   |
+-----------------------------------------------------------------------------------+
|  Footer: (c) 2026 InternSphere. University Placement Partner.         [Support]   |
+-----------------------------------------------------------------------------------+
```

* **Key Components**: Global Header Navbar, Hero banner call-to-action (CTA), Metric cards, Value proposition tiles, Footer links.
* **Navigation Flow**: Clicking `[Login]` $\rightarrow$ Login Page. Clicking `[Register]` $\rightarrow$ User Selection $\rightarrow$ Registration form.
* **User Actions**: Click navigation links, trigger primary/secondary hero buttons, scroll down for statistics.

---

## 2. Login Page

### Purpose
To authorize students, recruiters, and placement officers using multi-role credential verification.

### ASCII Wireframe
```text
+-----------------------------------------------------------------------------------+
|  [Logo] InternSphere                                              [Return to Home] |
+-----------------------------------------------------------------------------------+
|                                                                                   |
|                                 Welcome Back!                                     |
|                       Enter your credentials to continue                          |
|                                                                                   |
|                         +-------------------------------+                         |
|                         |  Email Address                |                         |
|                         |  [ student@university.edu   ] |                         |
|                         +-------------------------------+                         |
|                                                                                   |
|                         +-------------------------------+                         |
|                         |  Password                     |                         |
|                         |  [ **********               ] |                         |
|                         +-------------------------------+                         |
|                                                                                   |
|                         [ ] Remember me        [Forgot Password?]                 |
|                                                                                   |
|                             +-----------------------+                             |
|                             |        [ LOGIN ]      |                             |
|                             +-----------------------+                             |
|                                                                                   |
|                      Don't have an account? [Register Here]                       |
|                                                                                   |
+-----------------------------------------------------------------------------------+
```

* **Key Components**: Center card container, validated Email and Password fields, "Remember Me" checkbox, "Forgot Password" link, Role-based landing router.
* **Navigation Flow**: Successful Auth $\rightarrow$ Student/Recruiter/PO Dashboard (based on role). Clicking `[Forgot Password?]` $\rightarrow$ Reset workflow.
* **User Actions**: Fill text fields, toggle remember checkbox, click Login.

---

## 3. Student Dashboard

### Purpose
Provides students with their application metrics, application status progress timeline, profile completeness tracker, and recommended internships.

### ASCII Wireframe
```text
+-----------------------------------------------------------------------------------+
|  [Logo] InternSphere  |  [Explore]  [Applications]           [Student Profile v]  |
+-----------------------------------------------------------------------------------+
|                                                                                   |
|   WELCOME BACK, ALEX RIVERA! (GPA: 3.82)              [ Profile Status: 85% Comp]  |
|                                                                                   |
|   +-------------------+ +-------------------+ +-------------------+           |
|   |  Active Appls: 4  | |  Interviews: 1    | |  Offers Recd: 1   |           |
|   +-------------------+ +-------------------+ +-------------------+           |
|                                                                                   |
|   +--[ Active Application Tracking ]--------------------------------------------+ |
|   |  Frontend Developer Intern -- Acme Corp                                      | |
|   |  Stage: [Applied] =====> [Shortlisted] =====> [Interviewing] - - -> [Select] | |
|   |  Status: In-Progress. Interview scheduled for June 5, 2026 at 10:00 AM.      | |
|   +-----------------------------------------------------------------------------+ |
|                                                                                   |
|   +--[ Recommended Internships for You ]----------------------------------------+ |
|   |  * React Developer Intern  -- TechSoft Inc.   [Rem.] [Stipend: $1,500] [View]| |
|   |  * Junior Web Engineer      -- DevGroup LLC    [Site] [Stipend: $1,200] [View]| |
|   +-----------------------------------------------------------------------------+ |
+-----------------------------------------------------------------------------------+
```

* **Key Components**: Multi-tab top navigation, Metric dashboard cards, Linear stepper for application tracking, Recommended listings grid.
* **Navigation Flow**: Clicking `[Explore]` $\rightarrow$ Internship Listings. Clicking `[View]` $\rightarrow$ Internship Details. Clicking `[Student Profile]` $\rightarrow$ Profile management page.
* **User Actions**: Track application stage milestones, review customized alerts, browse recommended jobs.

---

## 4. Internship Listings Page

### Purpose
To search, filter, and browse approved active internships using multi-variable filters.

### ASCII Wireframe
```text
+-----------------------------------------------------------------------------------+
|  [Logo] InternSphere  |  [Explore]  [Applications]           [Student Profile v]  |
+-----------------------------------------------------------------------------------+
|                                                                                   |
|  Search Listings: [ React Developer...                     ]  [ SEARCH ]          |
|                                                                                   |
|  +--[ Filters ]----------------------+ +--[ Internship Job Results ]------------+ |
|  |  Location:                        | |  React Developer Intern                | |
|  |  ( ) Remote  ( ) On-site  ( ) Hybrid| |  TechSoft Inc. - Remote                | |
|  |                                   | |  Skills: React.js, TypeScript, HSL CSS | |
|  |  Duration:                        | |  Stipend: $1,500/mo  |  Ends in: 5 days | |
|  |  [ 3 Months          v ]          | |  [ View Details ]          [ APPLY NOW ]| |
|  |                                   | |  ------------------------------------- | |
|  |  Minimum Stipend:                 | |  Junior Frontend Engineer              | |
|  |  $ [ 1000             ]           | |  DevGroup LLC - On-Site                | |
|  |                                   | |  Skills: HTML5, CSS3, Vanilla JS       | |
|  |  [ Reset Filters ]                | |  Stipend: $1,200/mo  |  Ends in: 9 days | |
|  |                                   | |  [ View Details ]          [ APPLY NOW ]| |
|  +-----------------------------------+ +----------------------------------------+ |
+-----------------------------------------------------------------------------------+
```

* **Key Components**: Global search bar, left-aligned filter panel, search results list, quick action buttons (`[APPLY NOW]`, `[View Details]`).
* **Navigation Flow**: Clicking `[APPLY NOW]` $\rightarrow$ Confirms file attachment $\rightarrow$ Application submitted status. Clicking `[View Details]` $\rightarrow$ Detailed specification page.
* **User Actions**: Input search strings, toggle filter options, scroll and submit applications.

---

## 5. Internship Details Page

### Purpose
Displays the detailed profile of an internship opening, including core responsibilities, skills, corporate stipend, and direct entry points to apply.

### ASCII Wireframe
```text
+-----------------------------------------------------------------------------------+
|  [Logo] InternSphere  |  [Explore]  [Applications]           [Student Profile v]  |
+-----------------------------------------------------------------------------------+
|  [<- Back to Search]                                                              |
|                                                                                   |
|   React Developer Intern                                                          |
|   TechSoft Inc.  |  Rating: 4.8*  |  Corporate Partner                             |
|                                                                                   |
|   +-----------------------+ +-----------------------+ +-----------------------+   |
|   |  Stipend: $1,500/mo   | |  Duration: 3 Months   | |  Openings: 3 Active |   |
|   +-----------------------+ +-----------------------+ +-----------------------+   |
|                                                                                   |
|   Role Description:                                                               |
|   We are seeking a Frontend Intern passionate about building responsive UIs.       |
|   You will collaborate directly with our engineering team to write clean React.js |
|                                                                                   |
|   Required Tech Stack:                                                            |
|   [ ReactJS ]  [ JavaScript ES6 ]  [ Vanilla CSS ]  [ Git/GitHub ]                |
|                                                                                   |
|   Application Rules:                                                              |
|   * Uploaded Resume (PDF) must contain matching technical skills.                 |
|   * Candidates must be willing to dedicate 40 hours per week.                     |
|                                                                                   |
|   [ APPLY NOW FOR THIS ROLE ]               Your current resume: [resume_v2.pdf]   |
+-----------------------------------------------------------------------------------+
```

* **Key Components**: Breadcrumb selector, Executive header details card, Tech stack pill array, Structured description content, Action buttons with active resume attachment details.
* **Navigation Flow**: Clicking `[APPLY NOW...]` $\rightarrow$ Submit modal pop-up $\rightarrow$ Application Status Page.
* **User Actions**: Read job description, check skill match indicators, click apply.

---

## 6. Application Tracking Page

### Purpose
Allows candidates to track application status, download submission histories, and review interview meeting slots.

### ASCII Wireframe
```text
+-----------------------------------------------------------------------------------+
|  [Logo] InternSphere  |  [Explore]  [Applications]           [Student Profile v]  |
+-----------------------------------------------------------------------------------+
|                                                                                   |
|  YOUR PLACEMENT APPLICATIONS (Active: 3 | Complete: 1)                            |
|                                                                                   |
|  +--[ Internship Post ]----+--[ Submitted On ]--+--[ Status ]---+--[ Actions ]--+ |
|  |  React Developer Intern |  May 15, 2026      | Interviewing  | [View Invite] | |
|  |  Junior Web Engineer    |  May 18, 2026      | Shortlisted   | [Cancel Appl] | |
|  |  Python Developer       |  May 20, 2026      | Applied       | [Cancel Appl] | |
|  |  QA Specialist          |  May 02, 2026      | Rejected      | [Archive]     | |
|  +-------------------------+--------------------+---------------+---------------+ |
|                                                                                   |
|  +--[ Interview Invitation Details ]--------------------------------------------+ |
|  |  Company: TechSoft Inc.                                                       | |
|  |  Time: June 5, 2026 at 10:00 AM (IST)                                         | |
|  |  Platform: Zoom Meeting                                                       | |
|  |  Joining Link: [ https://zoom.us/j/98765432100                  ]             | |
|  +-----------------------------------------------------------------------------+ |
+-----------------------------------------------------------------------------------+
```

* **Key Components**: Tabular tracker list, Application metadata tags, Custom action triggers, Contextual details card (visible only for active `Interviewing` applications).
* **Navigation Flow**: Clicking `[View Invite]` $\rightarrow$ Updates detail panel content. Clicking `[Cancel Appl]` $\rightarrow$ Prompts warning before soft-deletion.
* **User Actions**: Monitor status table, launch virtual interview links, manage or archive applications.

---

## 7. Recruiter Dashboard

### Purpose
Enables recruiters to view active job posting counts, manage applicant screening pipelines, schedule interviews, and evaluate active interns.

### ASCII Wireframe
```text
+-----------------------------------------------------------------------------------+
|  [Logo] InternSphere  |  [Jobs Management]  [Evaluations]          [Company Profile v]|
+-----------------------------------------------------------------------------------+
|                                                                                   |
|  Acme Corp Dashboard  |  HR Manager: Sarah Jenkins               [+ Post New Job] |
|                                                                                   |
|  +--[ Active Postings ]--+--[ Applicants ]--+--[ Shortlisted ]--+--[ Placed ]---+ |
|  |          4            |       45         |        12         |      3        | |
|  +-----------------------+------------------+-------------------+---------------+ |
|                                                                                   |
|  +--[ Screening Pipeline: Frontend Intern (Applicants: 12) ]--------------------+ |
|  |                                                                               | |
|  |  [ Applied (5) ]        [ Shortlisted (3) ]       [ Interviewing (4) ]        | |
|  |  +--------------------+ +--------------------+   +--------------------+       | |
|  |  | * John Doe   [GPA:3.6| | * Jane Smith [GPA:3.9|   | * Alan Turing[GPA:4.0|       | |
|  |  |   [Review Resume]  | |   [Schedule Interview]|   |   [Review Scorecard]|       | |
|  |  +--------------------+ +--------------------+   +--------------------+       | |
|  |  | * Bob Ross  [GPA:3.2| | * Grace H.   [GPA:3.7|   | * Ada L.     [GPA:3.8|       | |
|  |  +--------------------+ +--------------------+   +--------------------+       | |
|  +-------------------------------------------------------------------------------+ |
+-----------------------------------------------------------------------------------+
```

* **Key Components**: Company info banner, Job action CTA, Pipeline metrics cards, Multi-column Screening Pipeline Kanban layout.
* **Navigation Flow**: Clicking `[+ Post New Job]` $\rightarrow$ Create Internship screen. Clicking `[Schedule Interview]` $\rightarrow$ Scheduler form modal. Clicking `[Review Resume]` $\rightarrow$ PDF preview modal.
* **User Actions**: Drag-and-drop screening statuses, review resume PDFs, edit candidate pipeline slots.

---

## 8. Create Internship Page

### Purpose
To let verified recruiters create and submit new internship opportunities for Placement Officer approval.

### ASCII Wireframe
```text
+-----------------------------------------------------------------------------------+
|  [Logo] InternSphere  |  [Jobs Management]  [Evaluations]          [Company Profile v]|
+-----------------------------------------------------------------------------------+
|  [<- Back to Jobs]                                                                |
|                                                                                   |
|  CREATE A NEW INTERNSHIP POSTING                                                  |
|                                                                                   |
|  Job Title:                                                                       |
|  [ React JS Frontend Developer Intern                                           ] |
|                                                                                   |
|  Duration (Months):              Stipend ($ / Month):             Openings:       |
|  [ 3 Months          v ]         $ [ 1500           ]             [ 3           ] |
|                                                                                   |
|  Location & Work Arrangement:                     Application Deadline:           |
|  [ Remote            v ]                          [ June 15, 2026    [cal] ]      |
|                                                                                   |
|  Key Skills Required (Comma Separated):                                           |
|  [ React.js, JavaScript ES6, Tailwind CSS, Git                                  ] |
|                                                                                   |
|  Job Description & Responsibilities:                                              |
|  +-----------------------------------------------------------------------------+ |
|  | Write clean React components, manage application state, use CSS styling...  | |
|  +-----------------------------------------------------------------------------+ |
|                                                                                   |
|                                   [ SUBMIT FOR APPROVAL ]                         |
+-----------------------------------------------------------------------------------+
```

* **Key Components**: Back router button, Form text fields, Select dropdowns, Skill tag generator, Textarea input box, Submission action button.
* **Navigation Flow**: Successful Submit $\rightarrow$ Listing status set to `Pending Approval` $\rightarrow$ Redirects to Recruiter Job Management board.
* **User Actions**: Fill text areas, specify dropdown filters, datepicker selection, submit form.

---

## 9. Placement Officer Dashboard

### Purpose
Enables coordinators to process recruiter verification queues, review pending job postings, monitor active placements, and generate analytical reports.

### ASCII Wireframe
```text
+-----------------------------------------------------------------------------------+
|  [Logo] InternSphere  |  [Verifications Queue]  [Placements]  [Reports] [Gradebook]|
+-----------------------------------------------------------------------------------+
|                                                                                   |
|  Placement Officer Console  |  Coordinator: Dr. Karen Vance                       |
|                                                                                   |
|  +--[ Verification Worklist (Requires Action) ]---------------------------------+ |
|  |  * Recruiter Registration: Sarah Jenkins (Acme Corp)           [APPROVE] [DENY]  | |
|  |  * Recruiter Registration: Mark Davis (DevTech)                [APPROVE] [DENY]  | |
|  |  * Job Posting: Node.js Intern - DevTech (Pending Audit)       [AUDIT POSTING] | |
|  +-----------------------------------------------------------------------------+ |
|                                                                                   |
|  +--[ Platform Placements Analytics Overview ]----------------------------------+ |
|  |  Placed Students: [=============== 65% placed ===================] 450/700   | |
|  |                                                                               | |
|  |  Top Hiring Partners:         Active Applications:      Unplaced Candidates:  | |
|  |  1. Acme Corp (15 Placed)     150 Pending Screening     250 Active Search     | |
|  +-----------------------------------------------------------------------------+ |
+-----------------------------------------------------------------------------------+
```

* **Key Components**: Verification queue lists, Action button clusters (`[APPROVE]`, `[DENY]`, `[AUDIT POSTING]`), Linear percentage placements meter, Top hiring statistics panel.
* **Navigation Flow**: Clicking `[AUDIT POSTING]` $\rightarrow$ Detail Modal $\rightarrow$ Approve/Reject options. Clicking `[Reports]` $\rightarrow$ PDF/XLSX export dashboard.
* **User Actions**: Resolve verification queue backlog, monitor placement percentages, toggle detailed listings audits.

---

## 10. Admin Dashboard

### Purpose
Gives system administrators control over user roles, database status, system limits, storage usage, and security audit logs.

### ASCII Wireframe
```text
+-----------------------------------------------------------------------------------+
|  [Logo] InternSphere  |  [User Accounts]  [Metrics]  [Security Logs]  [Global Config]|
+-----------------------------------------------------------------------------------+
|                                                                                   |
|  SYSTEM ADMINISTRATION CONSOLE                                                    |
|                                                                                   |
|  +--[ System Infrastructure Health Indicators ]---------------------------------+ |
|  |  API Latency: 120ms (Healthy)     |  Database Connection: Online (Active)     | |
|  |  Resume Cloud Storage (2.4 GB used):                                          | |
|  |  [====================== 48% Space Utilized =====================] Max 5.0 GB| |
|  +-----------------------------------------------------------------------------+ |
|                                                                                   |
|  +--[ Security and Audit Logs (Live Stream) ]-----------------------------------+ |
|  |  * [10:41:20] User Admin reset Student ID: 405 password.                      | |
|  |  * [10:39:15] Suspicious Activity: 5 failed logins for user: hacker@mail.com   | |
|  |  * [10:35:04] Database auto-backup complete. Path: /backup/db_v105.sql        | |
|  +-----------------------------------------------------------------------------+ |
|                                                                                   |
|  Global Resume Limit Setup: [ 5.0 MB           v ]       [ FORCE DATABASE BACKUP] |
+-----------------------------------------------------------------------------------+
```

* **Key Components**: Health metrics cards, Storage consumption progress indicator, Real-time chronological audit logging block, System parameter setup dashboard with backup trigger CTA.
* **Navigation Flow**: Clicking `[User Accounts]` $\rightarrow$ Interactive CRUD records dashboard. Clicking `[Global Config]` $\rightarrow$ Parameter input panel.
* **User Actions**: Track system warning status logs, configure storage limits, trigger db maintenance tasks, audit alerts.
