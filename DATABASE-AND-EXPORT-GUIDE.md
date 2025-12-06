# Database & Export Guide - AI Automation Discovery Tool

## Overview
The AI Automation Discovery Tool includes a complete database management system that automatically stores all prospect data in your browser's local storage and provides seamless export to Google Sheets.

---

## Database Features

### 1. **Automatic Data Storage**
- All prospect data is automatically saved to browser's `localStorage` under the key `crm-data`
- Data persists across browser sessions
- Stores comprehensive assessment data including:
  - Contact information (name, email, phone, company)
  - Industry and company size
  - Pain points and current state assessment
  - Financial metrics (annual savings, payback period, ROI)
  - AI Readiness scores
  - Automation potential percentages
  - Alert flags for high-value opportunities

### 2. **What Gets Stored**
Each prospect record includes:

```javascript
{
  prospectName: "John Smith",
  prospectEmail: "john@company.com",
  prospectPhone: "+1-555-1234",
  companyName: "Acme Corp",
  industry: "Finance",
  companySize: "51-200",
  role: "Director",

  pain: {
    category: "Sales Process",
    description: "Manual lead entry and follow-up"
  },

  scores: {
    aiReadiness: 65,
    automationPotential: 78,
    complexity: 45
  },

  metrics: {
    monthlyImpact: 8500,
    annualSavings: 102000,
    paybackWeeks: 6.2,
    teamSize: 5,
    hoursPerWeek: 20
  },

  timestamp: "2024-12-06T15:30:00.000Z",
  status: "Insights Shared",
  alertFlag: "High Priority Lead",
  followUpDue: "12/9/2024"
}
```

---

## Export to Google Sheets

### **Two Export Options**

#### **Option 1: Comprehensive Export** (All Data)
Includes **25 columns**:
- Date Added, Prospect Name, Email, Phone
- Company Name, Industry, Company Size, Role
- Pain Category & Description
- AI Readiness Score, Automation %, Complexity
- Monthly Impact, Annual Savings, Payback Period
- Team Size, Hours/Week, Deal Value, Revenue at Risk
- Key Insights, Alert Flags, Follow-up Due Date
- Status, Last Updated

**Best for**: Detailed analysis, CRM import, comprehensive follow-up

#### **Option 2: Summary Export** (Key Metrics Only)
Includes **10 columns**:
- Date, Prospect, Company, Email, Industry
- AI Readiness, Automation %, Annual Savings
- Alert Flag, Status

**Best for**: Quick reviews, management dashboards, quick wins identification

### **How to Export**

1. **Open Discovery Tool** → Navigate to the **CRM** tab
2. **Click "📊 Export to CSV"** button
3. **Choose export type**:
   - **OK** → Comprehensive data export
   - **Cancel** → Summary data export
4. **File downloads** automatically as `CRM-Comprehensive-[DATE].csv` or `CRM-Summary-[DATE].csv`

### **Import to Google Sheets**

1. Go to **google.com/sheets**
2. Click **"+ Create"** to start a new sheet
3. Click **File → Import**
4. Select **"Upload"** tab
5. **Choose your CSV file** from downloads
6. Click **"Import data"** button
7. Select **"Replace spreadsheet"** (or "Append to current sheet")
8. Your prospect data is now in Google Sheets! 🎉

---

## CRM Dashboard Metrics

The dashboard automatically calculates and displays:

| Metric | Description |
|--------|------------|
| **📊 Total Prospects** | Number of completed discovery calls |
| **💰 Total Opportunity** | Sum of all annual savings potential |
| **🎯 High Priority Leads** | Prospects with >$50k annual savings potential |
| **📈 Avg. Automation Potential** | Average % of processes that can be automated |
| **⚡ Ready-to-Act Leads** | Prospects with AI Readiness score >70 |
| **📄 Conversion Rate** | % of prospects who received proposals |

---

## Data Management

### **View All Prospects**
1. Click **"📇 CRM"** tab in header
2. See all prospects with key details
3. Sorted by most recent first

### **Download Data**
- **CSV Export**: Click "📊 Export to CSV" button
- **PDF Proposal**: Individual prospect proposals can be downloaded from results page
- **Email Follow-up**: Pre-generated follow-up emails based on assessment scores

### **Clear Data**
⚠️ **Warning**: This permanently deletes all stored data

1. Click **"🔄 Reset All"** button
2. Confirm the warning dialog
3. All data, including stored CRM, will be cleared

---

## Data Backup Best Practices

### **Recommended Backup Schedule**
- **Weekly**: Export comprehensive CRM data
- **Store in**: Google Drive, Dropbox, or cloud storage
- **Label as**: `CRM-Backup-[DATE].csv`

### **Backup Steps**
1. Every Friday (or your preference):
   - Open Discovery Tool → CRM tab
   - Click "📊 Export to CSV"
   - Choose "Comprehensive" export
2. Download the file
3. Upload to Google Drive or cloud storage
4. Add to folder like "AI Automation CRM Backups"

---

## Google Sheets Tips & Tricks

### **Once Data is in Sheets**

#### **1. Create a Summary Dashboard**
```
Column A: Total Prospects = COUNTA(A:A) - 1
Column B: Total Revenue = SUM(M:M)
Column C: High Priority Count = COUNTIF(I:I, "High Priority Lead")
```

#### **2. Sort by Opportunity Value**
- Click **Data → Sort range**
- Sort by "Annual Savings ($)" column
- Highest values first

#### **3. Filter for High Priority Leads**
- Click **Data → Create a filter**
- Click filter icon on "Alert Flag" column
- Select "High Priority Lead"

#### **4. Add Conditional Formatting**
- Select "Annual Savings ($)" column
- Click **Format → Conditional formatting**
- Color scale: Red (low) → Green (high)
- Quickly spot high-value opportunities

#### **5. Create Follow-up List**
- Filter for Status = "Insights Shared"
- Add follow-up date column
- Sort by "Follow-up Due Date"
- Export to PDF for team sharing

---

## Database Limits

| Aspect | Details |
|--------|---------|
| **Max Prospects** | Unlimited (localStorage typically supports ~5-10MB) |
| **Practical Limit** | ~500-1000 prospects before considering archival |
| **Storage Location** | Browser localStorage (local machine only) |
| **Backup Method** | Export to CSV / Google Sheets |

### **When to Archive**
- If you have >500 prospects, consider:
  1. Exporting data to Google Sheets
  2. Clearing old data (>1 year)
  3. Keeping "active" prospects in discovery tool
  4. Archiving "closed" deals in separate Sheet

---

## Integration with Other Tools

### **Zapier / Make Integration** (Advanced)
You can set up workflows to:
- Export CSV → Automatically upload to Google Sheets weekly
- CRM data → Sync to HubSpot, Salesforce, Pipedrive
- Follow-up emails → Send via Gmail automatically
- Alerts → Notify via Slack when high-priority leads appear

**Contact technical support for custom integrations.**

---

## Data Privacy & Security

### **Data Location**
- ✅ Stored locally in your browser
- ✅ No data sent to external servers
- ❌ Not synced to cloud automatically (you control exports)

### **Best Practices**
1. **Secure your exports**: Store CSVs in password-protected folders
2. **Limit sharing**: Only share aggregated data, not individual emails
3. **Regular backups**: Weekly exports to Google Drive
4. **Clear sensitive data**: Use Reset if device is shared

---

## Troubleshooting

### **Issue: Data disappeared after clearing browser cache**
- localStorage is cleared when you clear browser history
- **Solution**: Always export before clearing cache
- **Prevention**: Enable automatic backups to Google Sheets

### **Issue: Export file is empty**
- No prospects have been added yet
- **Solution**: Complete at least one discovery call first

### **Issue: CSV won't import to Google Sheets**
- Check file format is .csv (not .xlsx)
- Check first row has headers
- **Solution**: Re-export from the tool

### **Issue: Special characters show as ???**
- Ensure UTF-8 encoding when importing
- In Google Sheets: **File → Import → More options**
- Select "UTF-8" under "Character encoding"

---

## Contact & Support

For questions about:
- **Data export**: Check this guide or test with small dataset first
- **Google Sheets integration**: See "Integration" section above
- **Technical issues**: Clear browser cache, try incognito mode
- **Feature requests**: Use the "Feedback" section in the tool

---

## Version History

| Version | Date | Changes |
|---------|------|---------|
| 1.0 | Dec 2024 | Initial database & export system |
| Features | | Comprehensive/summary export, CRM dashboard, auto-save |

---

**Last Updated**: December 6, 2024
**System**: AI Automation Discovery Tool v1.0
