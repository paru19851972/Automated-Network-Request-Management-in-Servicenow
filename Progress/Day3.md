🚀 Project Progress – Day 3 (Flows & Automation)
📌 Objective

Day 3 was focused on automating the Network Request process using ServiceNow Flow Designer. The goal was to integrate the catalog item, variable sets, custom table, and approval mechanism into a seamless workflow.

🔧 Work Completed
1. Catalog Variables Integration

Configured the Get Catalog Variables action to capture all required inputs from the Network Request catalog item:

Requestor Information (Name, Email ID, Department)

Network Details (Location, Device Type, Justification)

Validated data mapping to ensure correct transfer into subsequent actions.

2. Record Creation

Implemented the Create Record action targeting the custom table:

Table Name: u_network_database_table

Fields populated dynamically using catalog variables

Ensured consistency between catalog input and database schema.

3. Email Notification Setup

Configured Send Email action:

Target Record: Created record in u_network_database_table

Recipients: Requestor (dynamic), Approver (dynamic/static)

Subject & Body: Dynamic values pulled from catalog variables

Verified email sending (noted warning: “Email sending property is currently disabled” → resolved by enabling email properties in instance).

4. Approval Workflow

Added Ask for Approval action:

Target Record: Created record in u_network_database_table

Approval Reason: "Waiting for approval"

Rules Configured: Approve, Reject, Approve/Reject

Approval Mode: Configured as “Anyone Approves”

Connected approval state to flow logic.

5. Flow Logic

Implemented If Condition:

If Approved → Proceed with updating the record

If Rejected → Terminate flow with rejection status

Created Update Record action:

Target: Same created record

Status field dynamically updated to Approved or Rejected

6. Testing & Debugging

Validated end-to-end flow:

Catalog submission → Record created → Email sent → Approval triggered → Record updated

Encountered and resolved issues:

Duplicate variable naming error (resolved by renaming to ensure uniqueness).

Journal field approval_history warning (ignored as field not in custom table).

Email sending disabled (enabled mail sending in instance properties).

✅ Outcome

Fully functional Network Request Flow established.

Automated:

Data capture from catalog variables

Record creation in custom table

Email notifications

Approval process

Record updates post-approval

Flow tested successfully without critical errors.
