# 🚀 Automated Tuition Matchmaking & Dispatch Pipeline

An entirely serverless, database-driven automation pipeline built natively within Airtable. This system handles end-to-end customer lead capture, executes logic-based relational matching, and manages multi-party email dispatching without human intervention.

## 🛠️ Architecture & Tech Stack
*   **Core Database & Logic:** Airtable (Relational Tables, Native Automations)
*   **External Integrations:** Gmail API (Automated Email Dispatch)
*   **User Interface:** Airtable Forms

## ⚙️ How It Works (The Automated Workflow)

### 1. Dynamic Lead Capture
The process begins when a parent submits their tuition requirements through a customized Airtable form. 
*   **Data Collected:** Parent Name, Parent Email, Level Needed, Subject Needed, and Budget.

### 2. The Database Layer
The system relies on a structured `Tutors` table that acts as the single source of truth.
*   It tracks essential tutor metadata, including their Active Status, Subjects Taught, Levels Taught, Preferred Locations, and Qualifications.

### 3. Intelligent Matching Algorithm
Upon form submission, an Airtable automation triggers immediately.
*   The system uses a **Find records** action to query the database and cross-reference the parent's specific `Subject Needed` and `Level Needed` against the tutors' profiles.
*   The query successfully isolates only the qualified candidates for the specific job.

### 4. Automated Dispatch via Looping
Instead of bulk-emailing, the pipeline utilizes a **Repeat for each** loop to iterate through the matched list of records.
*   Each matched tutor receives a personalized, formatted email via the Gmail integration detailing the opportunity.
*   The email securely passes the parent's specific requirements (e.g., Parent Name, Subject, Level) and provides direct contact instructions.

### 5. Closed-Loop Client Communication
Simultaneously, a secondary automation runs to acknowledge the client.
*   An automated email is fired back to the parent, dynamically injecting their requested Subject and Level, confirming that matched tutors have been notified.

## 📈 Business Impact
*   **Zero Latency:** Reduces the time-to-match from hours of manual database searching to under 60 seconds.
*   **Scalability:** The looping architecture ensures that whether the system finds 1 match or 50 matches, all notifications are handled instantly without breaking the flow.
*   **Operational Efficiency:** Eliminates double data entry and manual email drafting entirely.
