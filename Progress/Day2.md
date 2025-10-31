# Day 2 Progress – ServiceNow Project

## Module Completed: Table, Field & Related List Creation

### Tasks Completed:
1. **Created a custom table**:  
   - Table Label: Network Database Table  
   - Table Name: u_network_database_table  
   - Application: Global  

2. **Added fields to the table**:  
   - Customer Address (String)  
   - Request Number (String)  
   - Requested For (String)  
   - Assignment Group (Reference → Group table)  
   - Work Status (String)  
   - Device Details (String)  
   - Updates (Integer)  
   - Assigned To (Reference → User table)  
   - Date Of Enquiry (Date)  
   - Customer Document (String)  
   - (Plus system-generated fields like Sys ID, Created, Updated, etc.)  

3. **Created a Relationship (Approval Request)**:  
   - Navigate to **System Definition > Relationships**  
   - Created a new Relationship:  
     - Name: Approval Request  
     - Applies To Table: Network Database Table  
     - Queries From Table: Approval [sysapproval_approver]  
     - Script to refine query:  

     ```javascript
     (function refineQuery(current, parent) {
         current.addQuery('source', parent.getTableName());
         current.addQuery('document_id', parent.sys_id);
     })(current, parent);
     ```

4. **Added Related List to the form**:  
   - Opened **Form Designer** for Network Database Table.  
   - Added **Approval Request** related list.  
   - Verified that the related list appears on the table form.  

---

### Evidence:
Screenshots have been uploaded to `/screenshots/module2/`:
- `Network Database Table.png` – table creation  
- `Creation Of Fields.png` – field creation  
- `Created Relationship.png` – relationship definition  
- `Adding List To Table.png` – related list added to form  

---

### Deliverables:
- Update Set exported: `update-sets/NetworkDatabaseTable_Module2.xml`  
- Screenshots: `/screenshots/module2/`  
- Documentation: Updated `Day2.md`  

---

✅ **Module 2 (Table, Field & Related List Creation) completed successfully.**
