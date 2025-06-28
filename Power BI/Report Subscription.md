### **Project 1: Automated Report Subscription with Dynamic Recipients**  

#### **Objective**:  
Instead of manually emailing Power BI reports to different stakeholders, automate the process by sending customized reports to recipients based on conditions (e.g., department, region, or role) with **Power Automate**.  

---

### **How It Works**:  
1. **Trigger**: When a Power BI report refreshes (or on a schedule).  
2. **Fetch Recipient List**: Get a dynamic list of recipients from **SharePoint/Excel/Teams**.  
3. **Filter & Personalize**: Only send reports to relevant users (e.g., "Sales Team" gets Sales Dashboard).  
4. **Export & Attach**: Convert the Power BI report to **PDF/PNG** and attach it to emails.  
5. **Send Email**: Distribute via Outlook or Gmail.  

---

### **Step-by-Step Setup**:  

#### **1. Prepare Your Data**  
- **Store Recipient List**:  
  - Use **SharePoint List / Excel Online** with columns:  
    - *Email*  
    - *Department* (e.g., Sales, Finance)  
    - *Region* (e.g., North, South)  
    - *ReportName* (which report they should receive)  

#### **2. Create the Power Automate Flow**  
**Trigger**:  
- Option A: **"When a file is modified in SharePoint"** (if report refresh updates a file).  
- Option B: **"Scheduled Trigger"** (e.g., every Monday at 9 AM).  

**Actions**:  
1. **Get Recipients**:  
   - Use **"Get Items"** (SharePoint) or **"List Rows"** (Excel Online) to fetch your recipient list.  

2. **Filter Recipients** (Optional):  
   - Use **"Filter Array"** to select only relevant recipients (e.g., `Department eq 'Sales'`).  

3. **Export Power BI Report**:  
   - Use the **Power BI "Export to File" API** (via HTTP action) to generate a PDF/PNG.  
   - *Alternative*: If API is complex, use **UI Flows (RPA)** to manually export.  

4. **Send Email with Attachment**:  
   - Use **"Send an Email (V2)"** (Office 365 Outlook).  
   - Customize subject/body (e.g., `Hi {Name}, here's your {ReportName} report!`).  
   - Attach the exported file.  

---

### **Example Flow Structure**:  
1. **Trigger**: Recurrence (every Monday at 9 AM).  
2. **Get Data**: Fetch recipients from SharePoint.  
3. **Apply Filter**: Only Sales team members.  
4. **For Each Recipient**:  
   - Export Power BI report as PDF.  
   - Send email with attached report.  

---

### **Why This is Useful**:  
✅ **Saves Time** – No manual emailing.  
✅ **Dynamic Distribution** – Different reports for different teams.  
✅ **Audit Trail** – Logs sent emails in SharePoint.  
