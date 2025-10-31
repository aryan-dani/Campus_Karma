# CampusKarma ⚡ — The AI-Powered Campus Automation Brain

**CampusKarma** is a no-code automation system built for the 48-Hour Unstop No-Code Hackathon. It acts as a central nervous system for campus communications, intelligently routing, logging, and announcing submissions from students and faculty without writing a single line of code.


---

## 🎯 Problem Statement

On any campus, information is chaotic and siloed.
* **Students** don't know where to find announcements for events or placements.
* **Faculty** waste time manually emailing forms and attendance sheets.
* **Admin** staff struggle to track maintenance requests sent via multiple channels.

This manual process is slow, prone to error, and creates a disconnect between departments. **CampusKarma** solves this by creating a single, intelligent, and automated pipeline for all campus information.

---

## ✨ Features

* **Single Point of Entry:** One simple Google Form handles all submissions: Events, Placements, Maintenance, Attendance, and General Notices.
* **AI-Powered Classification (WIP):** An AI node (WorqHat AI / OpenAI) intelligently classifies the *intent* of submissions, even if the user selects the wrong category.
* **Intelligent Routing:** The workflow automatically routes information to the correct stakeholder.
    * **Events** → Create a Google Calendar event.
    * **Placements** → Email the Training & Placement (T&P) cell.
    * **Maintenance** → Log a ticket and alert admin (with urgency).
    * **Attendance** → Notify the concerned faculty or coordinator.
* **Automated Announcements:** Instantly posts clear, well-formatted announcements to a central **Telegram channel**.
* **Automated Logging:** (WIP) Creates a "source of truth" by logging every submission into its own categorized Google Sheet.
* **Daily Digest:** A scheduled workflow runs daily to send an admin a summary of all campus activities (e.g., "3 new events, 1 placement, 2 urgent maintenance tickets").

---

## ⚙️ How It Works: The Automation Flow

The entire system is built on **WorqHat** and connected to essential Google services.

1.  **Trigger (Input):** A student or faculty member fills out the central **Google Form**.
2.  **Webhook:** Google Forms (via an Apps Script) sends the new submission data to a **WorqHat Webhook Trigger** instantly.
3.  **Route (Logic):** An **If/Else Condition** node reads the `Submission_Type` (e.g., "Event").
4.  **Act (Actions):** The workflow executes a specific branch:
    * **Event Branch:**
        1.  **If/Else (Guard):** Checks if an `Event_DateTime` was provided.
        2.  **Google Calendar:** Creates a new calendar event with the title, description, and date.
        3.  **HTTP Request (Telegram):** Formats and sends a public announcement to the campus Telegram group.
    * **Placement Branch:**
        1.  **Gmail:** Sends a formatted email to the `T&P-Cell@school.edu` with all details.
        2.  **HTTP Request (Telegram):** Posts the placement drive details to the Telegram group.
    * **Maintenance Branch:**
        1.  **Gmail:** Sends a high-urgency alert to the `admin@school.edu` with the issue details.
5.  **Scheduled Trigger (Summary):** A separate workflow runs at 8:00 PM daily, reads the master log, and sends a summary report.

---

## 🛠️ Tech Stack (No-Code)

* **Workflow Automation:** **WorqHat**
* **Input / Trigger:** **Google Forms**
* **Database / Logging:** **Google Sheets**
* **Scheduling / Events:** **Google Calendar**
* **Notifications:** **Telegram API** & **Gmail**
* **Connecting Layer:** **Google Apps Script** (to send the webhook from the sheet)
* **AI Classification (WIP):** **WorqHat AI / OpenAI**

---

## 🚀 Future Roadmap

* **WhatsApp Integration:** Use Twilio to send critical alerts via WhatsApp for wider reach.
* **Approval Step:** Add a manual approval step where an admin must click "Approve" in an email before a `General Notice` is posted publicly.
* **Voice Submissions:** Integrate a voice-to-text AI so users can *call in* a maintenance request.

---

## 👤 Contact

**Aryan Dani**
* AI & Data Science Student, MIT World Peace University
* 📧 `daniaryan212@gmail.com`
