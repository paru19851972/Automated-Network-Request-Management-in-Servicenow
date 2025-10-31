# Automated-Network-Request-Management-in-Servicenow

## 📝 Project Description
The **Network Request Automation** project is designed to digitize and automate the process of submitting, approving, and tracking **network service requests** in ServiceNow.  
Traditionally, these requests were handled manually (emails, spreadsheets, calls), causing **delays, inefficiencies, and lack of traceability**.  

This project introduces a **self-service catalog item** that allows employees to submit requests, which are then automatically:
- Stored in a **custom table**,
- Routed for **approvals**,
- Sent as **email notifications**,
- Updated in **real-time with final status**.  

This solution is scalable, reusable, and production-oriented – a perfect demonstration of **ServiceNow Flow Designer, Catalog Items, Notifications, and Approvals**.

---

## 🎯 Objectives
- Provide a **centralized catalog item** for all network-related requests.  
- Reduce manual interventions by automating **approvals, record creation, and notifications**.  
- Ensure **data consistency** via a custom database table.  
- Deliver **real-time communication** using automated emails.  
- Design with **scalability and reusability** in mind.  

---

## 🏗️ Architecture & Workflow


Employee Submits Request (Service Catalog)
│
▼
Variable Set (Requestor Information + Network Details)
│
▼
Flow Designer
├── Get Catalog Variables
├── Create Record (u_network_database_table)
├── Send Email Notification
├── Ask for Approval (Manager/Approver)
├── Evaluate Approval Result
└── Update Record (Status: Approved/Rejected)


---

## 📂 Project Structure


📁 Network Request Automation
│
├── 📄 README.md # Project Documentation (this file)
├── 📄 Flow_Chart.png # Flow design (workflow diagram)
├── 📄 Network_Database_Table.png # Custom table design
├── 📄 Variable_Set_Config.png # Variable set configuration
├── 📄 Relationships.png # Relationship mapping
└── 📄 Update_Set_Export.xml # Update set for import into ServiceNow


---

## ⚙️ Key Components

### 1️⃣ Service Catalog Item – *Network Request*
- Entry point for end users.  
- Linked with **Requestor Information variable set**.  
- Captures:
  - Requestor Name  
  - Email Address  
  - Department  
  - Device Type  
  - Location  
  - Justification  

---

### 2️⃣ Variable Set – *Requestor Information*
- Reusable variable set across catalog items.  
- Ensures consistency & avoids duplication.  
- Designed with **unique internal variable names** to prevent conflicts.  

---

### 3️⃣ Custom Table – *u_network_database_table*
- Dedicated table to store all requests.  
- Fields:
  - Requestor Name  
  - Email ID  
  - Department  
  - Device Type  
  - Location  
  - Status (Pending / Approved / Rejected)  

---

### 4️⃣ Flow Designer Automation
A powerful flow was built with the following actions:
- **Get Catalog Variables** – Capture inputs from catalog form.  
- **Create Record** – Insert data into `u_network_database_table`.  
- **Send Email** – Notify requestor & approver dynamically.  
- **Ask for Approval** – Routed to manager/approver.  
- **If Condition** – Check outcome (Approved/Rejected).  
- **Update Record** – Change status accordingly.  

---

### 5️⃣ Notifications
- Configured **email templates** for requestor & approvers.  
- Emails include:
  - Requestor name  
  - Request ID  
  - Request status  
- Supports **To, CC, BCC** (both static & dynamic).  

---

### 6️⃣ Approvals
- Approval type: **Anyone Approves**.  
- Can be configured for **static approvers** or **dynamic (from requestor’s department)**.  
- Tracks decision in the request record.  

---

## 🧪 Testing Journey & Issues Faced

### ✅ Successful Validations
- Record creation mapped correctly in custom table.  
- Email notifications triggered after enabling properties.  
- Approval flow correctly updated status in table.  

### ⚠️ Issues & Fixes
1. **Duplicate variable conflict**  
   - ❌ Error: Variables with same names overwrote values.  
   - ✔️ Fix: Assigned unique internal names in variable set.  

2. **Journal field warning**  
   - ❌ Error: “Journal field ‘approval_history’ is not valid in table.”  
   - ✔️ Fix: Ignored, since table didn’t require journal fields.  

3. **Email sending disabled**  
   - ❌ Error: “Email sending property is currently disabled.”  
   - ✔️ Fix: Enabled in **System Properties > Email** (`glide.email.smtp.active`).  

4. **Flow stuck in pending**  
   - ❌ Cause: Approval action not configured with correct approver.  
   - ✔️ Fix: Assigned dynamic approver properly.  

---

## 🚀 Outcomes
- Fully automated **Network Request lifecycle**.  
- Eliminated manual tracking with **real-time updates**.  
- Boosted efficiency via **self-service catalog & automated approvals**.  
- Proved expertise in:
  - ServiceNow Catalog Development  
  - Flow Designer Automation  
  - Notifications & Approvals  
  - Custom Table Design  

---

## 🛠️ Setup & Deployment

### 1️⃣ Import into ServiceNow
1. Navigate to **System Update Sets > Retrieved Update Sets**.  
2. Import `Update_Set_Export.xml`.  
3. Preview & Commit the update set.  

### 2️⃣ Enable Email Notifications
- Navigate to **System Properties > Email**.  
- Enable:
  - `glide.email.smtp.active` → **true**  
  - `glide.email.read.active` → **true**  

### 3️⃣ Test End-to-End Flow
1. Submit request from **Service Catalog**.  
2. Record created in `u_network_database_table`.  
3. Email notifications sent to requestor/approver.  
4. Approve/Reject → Status auto-updated.  

---

## 📚 Learnings
- Best practices for **variable set reuse**.  
- Handling **email configurations** in ServiceNow.  
- Building **robust flows** with condition-based logic.  
- Debugging common issues (naming conflicts, disabled properties).  

---

## 🌟 Why This Project is Recruiter & Mentor Ready
✔️ Covers **end-to-end automation** use case.  
✔️ Solves a **real ITSM problem**.  
✔️ Documents **design → build → test → fix → outcome** clearly.  
✔️ Demonstrates **ServiceNow development skills**.  
✔️ Professional **README + update set + screenshots** for verification.  

---

## 👨‍💻 Author
**Jahanavi Madugula**  
*Full Stack Developer | ServiceNow Enthusiast | AI-Driven Solutions Builder*  
🔗 [LinkedIn](https://www.linkedin.com/in/jahanavi-madugula-75a1252a9/) | 🔗 [GitHub](https://github.com/Jahanavi27/)  
