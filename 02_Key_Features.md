# Key Features Specification

This document details the functional specifications for the core modules of the **Internship Management Platform**. Each module consists of specific features characterized by their descriptions, inputs, outputs, validation rules, and business benefits.

---

## 1. Feature Prioritization (MoSCoW Matrix)

To ensure an iterative and risk-managed development lifecycle, the platform features are prioritized using the MoSCoW methodology.

| Priority | Feature / Capability | Module | Core Business Rationale |
| :--- | :--- | :--- | :--- |
| **Must Have** | User Registration & Login | Authentication | Foundation for secure Role-Based Access Control (RBAC). |
| **Must Have** | Profile Management | Student | Essential for candidate representation. |
| **Must Have** | Resume Upload (PDF) | Student | Mandatory document for job application and evaluation. |
| **Must Have** | Internship Posting | Recruiter | Primary data entity required to enable placement cycles. |
| **Must Have** | Internship Search | Student | Core user interaction for candidate discovery. |
| **Must Have** | Application Tracking | Student | Centralized hiring lifecycle visibility. |
| **Must Have** | Candidate Review & Shortlisting| Recruiter | Allows employer screening and decision log. |
| **Must Have** | Recruiter Verification | Placement Officer | Prevents fraudulent job postings and spam. |
| **Must Have** | User Account Control | Admin | Basic operations and administrative governance. |
| **Should Have**| Password Recovery (OTP/Reset Link)| Authentication | Key usability and account security self-service. |
| **Should Have**| Interview Scheduling | Recruiter | Coordinates meetings and records dates on-platform. |
| **Should Have**| Monitoring Dashboard | Placement Officer | High-level analytical representation of placement statistics. |
| **Should Have**| Reporting & Exports | Placement Officer | Enables printing and archiving statistics. |
| **Should Have**| System Logs & Health | Admin | Audits system performance and errors. |
| **Could Have**| AI-powered Candidate Matching | Student / Recruiter| Auto-matches resumes with job descriptions. |
| **Could Have**| In-app Direct Messaging | Student / Recruiter| Direct communication tool (currently out of scope). |
| **Won't Have** | Automated Stipend Payroll | Recruiter | Out of scope; managed externally by company HR. |
| **Won't Have** | Direct Video Interview Hosting | Recruiter | Out of scope; platform integrates external links instead. |

---

## 2. Authentication Module

### 2.1 Registration
* **Description**: Allows Students and Recruiters to create secure system accounts by providing identifying credentials.
* **Inputs**: First Name, Last Name, Email Address, Password, Confirm Password, Role Selector (Student/Recruiter), Institution/Company Identifier.
* **Outputs**: Account creation success flag, system activation email notification, database User record.
* **Validation Rules**:
  * Email must be unique and conform to standard format (e.g., student emails must belong to the university domain `*.edu` or `*.ac.in`).
  * Password must be a minimum of 8 characters, containing at least 1 uppercase letter, 1 number, and 1 special character.
  * Passwords must match exactly.
* **Business Benefits**: Restricts platform access to legitimate actors, establishing a secure baseline for academic placement operations.

### 2.2 Login
* **Description**: Verifies user identity via credentials to issue secure sessions and redirect users to role-specific dashboards.
* **Inputs**: Email Address, Password.
* **Outputs**: JSON Web Token (JWT), session cookies, redirection to role-specific home page.
* **Validation Rules**:
  * Email and password cannot be empty.
  * Account must not be suspended/deactivated.
  * Implements account lockout (e.g., lock account for 15 minutes after 5 consecutive failed attempts).
* **Business Benefits**: Protects sensitive student records and proprietary corporate posting details from unauthorized access.

### 2.3 Password Recovery
* **Description**: Provides a self-service workflow for users to securely reset forgotten passwords.
* **Inputs**: Registered Email Address.
* **Outputs**: Unique, time-sensitive (15-minute expiry) password reset link or One-Time Password (OTP) sent via email.
* **Validation Rules**:
  * Email must exist in the active users database (silently fail to prevent email harvesting).
  * Password reset token can only be used once.
* **Business Benefits**: Minimizes administrative overhead by allowing users to manage credentials without opening IT support tickets.

---

## 3. Student Module

### 3.1 Profile Management
* **Description**: Enables students to build and maintain a professional digital portfolio showcasing academic and technical qualifications.
* **Inputs**: Profile Picture, Current GPA, Expected Graduation Date, List of Skills (Tag array), Professional Summary/Bio.
* **Outputs**: Updated student profile page visible to matching recruiters, database Profile record.
* **Validation Rules**:
  * GPA must be a numeric value between 0.0 and 4.0 (or matching the university scale).
  * Mandatory fields (Skills, Graduation Date) cannot be blank.
* **Business Benefits**: Standardizes candidate presentation, making it easier for recruiters to evaluate prospective interns.

### 3.2 Resume Upload
* **Description**: Allows students to upload their official resume document for direct recruiter access during applications.
* **Inputs**: Document file attachment.
* **Outputs**: PDF file stored securely in backend storage, active document path mapped to the student profile record.
* **Validation Rules**:
  * Document must strictly be in PDF format.
  * File size must not exceed 5 Megabytes (5MB).
* **Business Benefits**: Ensures clean resume rendering across different browser environments while safeguarding database storage boundaries.

### 3.3 Internship Search
* **Description**: Provides students with advanced query tools to locate suitable internship vacancies based on custom criteria.
* **Inputs**: Keywords, Skill filters, Location tags, Minimum Stipend amount, Work Arrangement (Remote/On-site).
* **Outputs**: Filtered array of active and approved internship postings.
* **Validation Rules**:
  * Search keywords must be sanitized to prevent SQL injection or cross-site scripting (XSS).
* **Business Benefits**: Increases application success rates by connecting students with postings matching their skills and interests.

### 3.4 Application Tracking
* **Description**: Offers real-time visibility into the hiring lifecycle, from initial application submission to final placement selection.
* **Inputs**: Student selection of a target internship post.
* **Outputs**: Interactive timeline representing the application state transition (`Applied` $\rightarrow$ `Shortlisted` $\rightarrow$ `Interview Scheduled` $\rightarrow$ `Offer Extended` $\rightarrow$ `Accepted/Declined`).
* **Validation Rules**:
  * Students cannot apply to the same internship listing more than once.
  * Students cannot apply to new listings once their status is set to `Selected/Placement Finalized`.
* **Business Benefits**: Alleviates candidate anxiety and eliminates chaotic communication channels by centralizing recruitment status changes.

---

## 4. Recruiter Module

### 4.1 Company Registration
* **Description**: Handles the formal onboarding of corporate partners, establishing corporate identity and validating legitimacy.
* **Inputs**: Company Name, Corporate Registration Number/Tax ID, Corporate Website URL, Primary Contact Number, Corporate Address.
* **Outputs**: Pending verification recruiter account, notifications sent to Placement Officers.
* **Validation Rules**:
  * Website URL must be a valid, active domain.
  * Email must match the company domain (e.g., name@company.com).
* **Business Benefits**: Ensures that only legitimate business enterprises can engage with university students, mitigating risk.

### 4.2 Internship Posting
* **Description**: Allows verified recruiters to compose and publish job descriptions defining active internship listings.
* **Inputs**: Job Title, Role Description, Required Technical Skills (tags), Duration (in months), Stipend Amount, Application Deadline.
* **Outputs**: Internship listing record created with status `Pending Approval` (invisible to students until Placement Officer verifies it).
* **Validation Rules**:
  * Application deadline must be set in the future.
  * Duration must be a positive integer (e.g., 1 to 6 months).
* **Business Benefits**: Ensures high-quality posting standards and consistency across all available listings.

### 4.3 Candidate Review
* **Description**: Provides an interface for recruiters to inspect, filter, and screen candidate submissions.
* **Inputs**: Recruiter selection of a specific applicant profile.
* **Outputs**: Candidate profile rendering, downloadable resume document, status adjustment selectors.
* **Validation Rules**:
  * Candidate records must only be accessible to recruiters whose postings the students applied to.
* **Business Benefits**: Streamlines the vetting workflow, allowing recruiters to process candidates efficiently.

### 4.4 Interview Scheduling
* **Description**: Coordinates the scheduling of candidate screening rounds and tracks date/time slots.
* **Inputs**: Interview Date, Interview Time, Platform Selector (e.g., Zoom/Google Meet), Meeting Link, Assessment Notes.
* **Outputs**: Candidate dashboard notification, email alert with ICS calendar attachment.
* **Validation Rules**:
  * Interview date and time must be set in the future.
  * Meeting URL must be a valid HTTPS web link.
* **Business Benefits**: Eliminates time-consuming back-and-forth emails, ensuring a reliable timeline for recruitment rounds.

---

## 5. Placement Officer Module

### 5.1 Recruiter Verification
* **Description**: A dedicated validation interface for Placement Officers to confirm recruiter identities and active listings.
* **Inputs**: Approval/Rejection action selector, verification comment block.
* **Outputs**: Recruiter account status change (`Active` or `Rejected`), automated notification emails.
* **Validation Rules**:
  * Rejection action must require a mandatory explanation comment in the text field.
* **Business Benefits**: Acts as the system's human-in-the-loop security gatekeeper, keeping the student job board clean and authentic.

### 5.2 Monitoring
* **Description**: High-level analytical view that tracks general recruitment activity, KPIs, and student placement rates.
* **Inputs**: None (automated system aggregation).
* **Outputs**: Graphical charts displaying placement percentage by department, top hiring companies, and outstanding unplaced student lists.
* **Validation Rules**:
  * Data visualizations must compile live database counts with caching systems to protect server loads.
* **Business Benefits**: Empowers university leaders with real-time operational metrics to optimize placement strategies.

### 5.3 Reporting
* **Description**: Allows coordinators to export clean datasets summarizing recruitment history and performance metrics.
* **Inputs**: Date Range, Department Filter, File Format Selector (CSV, XLSX, PDF).
* **Outputs**: Generated downloadable file compiling filtered records.
* **Validation Rules**:
  * File generation size limits must be enforced to prevent memory crashes on excessive data.
* **Business Benefits**: Provides standardized documentation for accreditation audits, university boards, and future planning.

---

## 6. Admin Module

### 6.1 User Management
* **Description**: Root dashboard to supervise, edit, suspend, or reactivate user accounts across all platform roles.
* **Inputs**: User ID, status override toggles, account edit forms.
* **Outputs**: Immediate database record updates, security logs, notification of status updates.
* **Validation Rules**:
  * System must prevent an administrator from deleting their own account or removing the final administrator record (preventing system lockouts).
* **Business Benefits**: Ensures full compliance, governance, and rapid resolution of account exceptions.

### 6.2 System Monitoring
* **Description**: Diagnostic center monitoring background storage limits, latency metrics, and API health.
* **Inputs**: Diagnostic thresholds, backup schedule selectors.
* **Outputs**: CPU/RAM utilization graphs, real-time alert logs, storage capacities.
* **Validation Rules**:
  * Triggers immediate high-priority alerts to system support teams if storage reaches 90% or API latency exceeds 1000ms.
* **Business Benefits**: Guarantees platform stability, preventing system crashes during peak student application windows.

### 6.3 Access Control
* **Description**: The core framework managing the mapping of permissions, route access security, and global parameters.
* **Inputs**: Security token mappings, global system parameter adjustments (e.g., maximum resume upload file size).
* **Outputs**: Dynamic authorization changes, updated configuration files.
* **Validation Rules**:
  * Access rights changes must require secondary multi-factor authentication (MFA) input from the administrator.
* **Business Benefits**: Solidifies application security, guaranteeing strict enforcement of role limits and preventing privilege escalations.
