# Technical Guide - AI Automation Discovery Tool

**For developers, architects, and technical teams implementing or customizing this system.**

---

## 📐 Architecture Overview

### Technology Stack
- **Frontend:** Vanilla JavaScript (no frameworks)
- **Storage:** Browser localStorage (JSON)
- **Export:** CSV generation (client-side)
- **Styling:** CSS3 with CSS variables
- **Responsive:** Mobile-first grid layout

### Three Core HTML Files
1. **index.html** (Landing Page)
   - Portfolio website
   - Neuronal eye image
   - Hero section with CTAs

2. **scorecard.html** (Assessment)
   - 10-question form
   - 5-section layout
   - Score calculations
   - Results display

3. **discovery-tool.html** (Main App)
   - 5-step discovery flow
   - CRM database
   - ROI calculations
   - Proposal generation
   - Google Sheets export

---

## 🗂️ File Structure

```
Automation_discovery/
├── index.html                      # Landing page
├── scorecard.html                  # Assessment tool
├── discovery-tool.html             # Main application
├── assets/
│   ├── neuronal-eye.png           # Eye image (user-provided)
│   ├── neuronal-eye.svg           # SVG fallback
│   └── README.txt
├── README.md                       # User guide
├── TECHNICAL-GUIDE.md             # This file
└── CLEANUP-PLAN.md                # Documentation
```

---

## 🗄️ Data Structure

### Scorecard Assessment Data
**Storage Key:** `assessmentResults` (sessionStorage)

```javascript
{
  aiReadiness: 65,           // 0-100
  manualProcesses: 72,       // 0-100
  automationUpside: 69,      // 0-100
  timestamp: "2024-12-06T15:30:00Z"
}
```

**Question Responses:** `assessmentData` (sessionStorage)
```javascript
{
  q1: "100",  // Radio value
  q2: "67",
  q3: "50",
  // ... q4 through q10
}
```

### CRM Lead Record
**Storage Key:** `crm-data` (localStorage)

```javascript
{
  prospectName: "John Smith",
  prospectEmail: "john@company.com",
  prospectPhone: "+1-555-1234",
  email: "john@company.com",  // Normalized

  // Company Info
  companyName: "Acme Corp",
  industry: "Finance",
  companySize: "51-200",
  role: "Director",

  // Assessment Data
  pain: {
    category: "Sales Automation",
    description: "Manual lead entry is killing our team..."
  },

  // Scores
  scores: {
    aiReadiness: 65,           // 0-100
    automationPotential: 78,   // 0-100%
    complexity: 45             // Calculation
  },

  // Financial Metrics
  metrics: {
    monthlyImpact: 8500,       // $ impact/month
    annualSavings: 102000,     // $ annual savings
    paybackWeeks: 6.2,         // Weeks to ROI
    teamSize: 5,               // People affected
    hoursPerWeek: 20,          // Hours/week manual work
    dealValue: 800,            // $$ per customer
    revenueAtRisk: 5000        // Revenue at risk
  },

  // Status & Follow-up
  insights: ["Foundation", "Infrastructure"],  // Top 3
  timestamp: "2024-12-06T15:30:00.000Z",
  status: "Insights Shared",
  alertFlag: "High Priority Lead",  // If > $50k savings
  followUpDue: "12/9/2024",

  // Metadata
  date: "12/6/2024",
  lastUpdated: "2024-12-06T16:45:00.000Z"
}
```

---

## 💾 LocalStorage Schema

### Current Implementation
```javascript
localStorage.getItem('crm-data')        // Array of lead objects
localStorage.getItem('discovery-data')  // Current discovery session
localStorage.getItem('discovery-step')  // Current step number
sessionStorage.getItem('assessmentResults')  // From scorecard
sessionStorage.getItem('assessmentData')     // Question responses
```

### Adding Persistent Login (Future)
```javascript
localStorage.setItem('user-settings', JSON.stringify({
  calendlyUrl: 'https://calendly.com/...',
  emailSignature: 'Your Name',
  brandColor: '#0066cc'
}));
```

---

## 🔧 Key Functions

### scorecard.html

**Main Functions:**
```javascript
switchSection(sectionIndex)      // Navigate between sections
calculateScores(event)           // Calculate all 3 scores
updateProgress()                 // Update progress bar
saveResults()                    // Save to sessionStorage
resetAssessment()                // Clear form
```

**Score Calculation Logic:**
```javascript
const aiReadinessQuestions = [1, 4, 5, 10];
const manualProcessQuestions = [1, 4, 5, 10];

const aiReadiness = Math.round(sum / count);
const automationUpside = Math.round(
  (manualProcesses + (100 - aiReadiness)) / 2
);
```

### discovery-tool.html

**Main App Object Methods:**
```javascript
// Navigation
nextStep()                    // Go to next step
previousStep()                // Go to previous step
goToStep(num)                // Jump to specific step

// Data Management
saveStepData()               // Save current step data
autosave()                   // Auto-save every 30s
resetAll()                   // Clear everything

// Discovery Logic
updateROI()                  // Recalculate ROI
calculateROI()               // Detailed ROI math

// CRM Operations
loadCRM()                    // Load from localStorage
renderCRM()                  // Display CRM table
saveToCRM()                  // Add prospect to CRM

// Export
exportCRMToSheets()          // Show export options
exportComprehensiveCRM()     // Export all 25 fields
exportSummaryCRM()           // Export 10 fields
downloadCSV()                // Generate CSV file

// Insights
generateStrategicInsights()  // Main generator
getPersonalizedInsights()    // 5 recommendations
generateFollowUpEmail()      // Email template
generateEnhancedCRMData()    // CRM record creation

// Proposals
downloadProposal()           // Export as PDF
downloadContract()           // Contract template

// UI
updateUI()                   // Refresh display
showCRM()                    // Display CRM tab
renderDashboard()            // Calculate metrics
```

---

## 🧮 Calculation Formulas

### AI Readiness Score
```javascript
// Scale: 0-100
// Questions 1, 4, 5, 10 (Processes focus)
aiReadiness = (q1 + q4 + q5 + q10) / 4

// Interpretation:
// 0-33: Low (minimal AI adoption)
// 34-66: Medium (some foundation)
// 67-100: High (ready for advanced)
```

### Automation Potential
```javascript
// Scale: 0-100%
// Based on pain points, manual work, processes
// Formula: (1 - (aiReadiness/100)) + (manualWorkHours/168*100)
// Result: % of processes that can be automated
```

### ROI Calculation
```javascript
// Inputs from Step 4:
- teamSize (# people)
- hoursPerWeek (manual hours)
- dealValue ($ per customer)
- volumePerWeek (deals/week)

// Calculations:
monthlyImpact = (hoursPerWeek * 4.33 * hourlyRate) +
                (volumePerWeek * dealValue * conversionLift)

annualSavings = monthlyImpact * 12

paybackWeeks = implementationCost / (monthlyImpact / 4.33)

complexity = (1 - aiReadiness/100) * 100
```

### High-Priority Lead Flag
```javascript
if (annualSavings > 50000) {
  alertFlag = "High Priority Lead"
} else {
  alertFlag = "Standard Follow-up"
}
```

---

## 🎨 CSS Architecture

### Color Variables (Root)
```css
:root {
  --bg-primary: #0a0e1a;        /* Dark background */
  --bg-secondary: #1a1f2e;      /* Cards/panels */
  --text-primary: #e6edf3;      /* Main text */
  --text-secondary: #b8c5d0;    /* Secondary text */
  --text-muted: #6e7681;        /* Muted text */
  --accent-primary: #0066cc;    /* CTA buttons */
  --accent-cyan: #00d9ff;       /* Neon cyan */
  --accent-pink: #ff006e;       /* Neon pink */
  --border: #2d3540;            /* Borders */
  --shadow: 0 4px 12px rgba...  /* Shadows */
}
```

### Grid Layouts
```css
/* Main layout: Sidebar + Content */
.assessment-wrapper {
  display: grid;
  grid-template-columns: 300px 1fr;  /* Sidebar + content */
  gap: 30px;
}

/* Responsive */
@media (max-width: 1024px) {
  grid-template-columns: 1fr;  /* Stack on mobile */
}
```

### Theme Toggle
```javascript
// In index.html
function toggleTheme() {
  const html = document.documentElement;
  const currentTheme = html.getAttribute('data-theme');
  const newTheme = currentTheme === 'dark' ? 'light' : 'dark';
  html.setAttribute('data-theme', newTheme);
  localStorage.setItem('theme', newTheme);
}

// Apply on load
const savedTheme = localStorage.getItem('theme') || 'dark';
document.documentElement.setAttribute('data-theme', savedTheme);
```

---

## 🔐 Security Considerations

### What's Not Implemented (By Design)
- ❌ User authentication (localStorage is per-device)
- ❌ Encryption (data stored plain in localStorage)
- ❌ Server-side validation (client-side only)
- ❌ API calls (standalone application)

### Security Best Practices Applied
- ✅ No inline onclick handlers → Event delegation
- ✅ CSV escaping for special characters
- ✅ Form input validation (email regex)
- ✅ No hardcoded secrets (email config)

### Deployment Security
- Use HTTPS for production (encrypt in transit)
- No sensitive data in URLs
- localStorage only accessible from same domain
- Clear cache policies for shared devices

---

## 🚀 Customization Guide

### Add Custom Questions to Scorecard

**In scorecard.html, find the question section:**
```html
<!-- Q1 -->
<div class="question">
  <label class="question-label">1. Your question here?</label>
  <div class="radio-group">
    <div class="radio-option">
      <input type="radio" name="q1" value="0" id="q1a">
      <label for="q1a">Option 1</label>
    </div>
    <!-- More options... -->
  </div>
</div>
```

**Add scoring in JavaScript:**
```javascript
// Find the calculateScores function
// Add your new question to the appropriate scoring array
const myNewQuestions = [11, 12];
const myNewSum = (document.querySelector('[name="q11"]:checked')?.value || 0)
               + (document.querySelector('[name="q12"]:checked')?.value || 0);
```

### Add Custom Insights

**In discovery-tool.html, function `getPersonalizedInsights()`:**
```javascript
getPersonalizedInsights(readiness, roi) {
  const insights = [];

  // Add custom insight:
  if (readiness.readiness < 40) {
    insights.push({
      title: "Your Custom Title",
      description: "Your description here...",
      effort: "Low",
      impact: "High",
      action: "Action steps...",
      callback: true  // Show booking button
    });
  }

  return insights;
}
```

### Modify Export Fields

**In discovery-tool.html, function `exportComprehensiveCRM()`:**
```javascript
// Change headers array:
const headers = [
  'Field1', 'Field2', 'Field3',  // Your custom fields
  // ...
];

// Match with data extraction:
const rows = this.crm.map(entry => [
  entry.field1Value,
  entry.field2Value,
  entry.field3Value,
  // ...
]);
```

---

## 🧪 Testing Checklist

### Functionality Tests
- [ ] Scorecard: All 10 questions answer correctly
- [ ] Scorecard: Score calculations accurate
- [ ] Discovery: All 5 steps navigate properly
- [ ] Discovery: Data saves every 30 seconds
- [ ] CRM: Prospect added after discovery
- [ ] CRM: Dashboard metrics calculate correctly
- [ ] Export: CSV downloads with all fields
- [ ] Export: CSV imports to Google Sheets
- [ ] Import: Google Sheets shows all data
- [ ] Proposal: PDF generates correctly

### Browser Tests
- [ ] Chrome (latest)
- [ ] Firefox (latest)
- [ ] Safari (latest)
- [ ] Edge (latest)
- [ ] Mobile Safari (iOS)
- [ ] Chrome Mobile (Android)

### Data Tests
- [ ] localStorage persists after refresh
- [ ] sessionStorage clears on new tab
- [ ] CRM data exports to CSV correctly
- [ ] CSV special characters escape properly
- [ ] No errors in browser console

### UI Tests
- [ ] Dark mode loads on load
- [ ] Icons display correctly (28px sidebar, 64px header)
- [ ] Responsive layout on mobile
- [ ] Progress bar updates accurately
- [ ] Forms validate input (email regex)

---

## 🔄 Update & Maintenance

### Regular Tasks
1. **Weekly**: Export CRM to Google Drive backup
2. **Monthly**: Review and archive old prospects
3. **Quarterly**: Check localStorage size
4. **Yearly**: Consider data migration strategy

### Backup Strategy
```bash
# Manual backup workflow:
1. Open discovery-tool.html
2. Click "📊 Export to CSV"
3. Save to: "CRM-Backup-YYYY-MM-DD.csv"
4. Upload to Google Drive "Backups" folder
```

### Data Migration (1000+ prospects)
```javascript
// Archive old data:
const oldData = JSON.parse(localStorage.getItem('crm-data'));
const archived = oldData.filter(e =>
  new Date(e.timestamp) < new Date('2024-09-01')
);
// Export archived to CSV
// Clear from localStorage
// Continue with new data
```

---

## 🐛 Debugging

### Enable Console Logging
```javascript
// Add to any function for debugging:
console.log('Variable name:', variableName);
console.table(objectOrArray);  // Pretty print
console.error('Error message:', error);
```

### Check localStorage
```javascript
// In browser console:
JSON.parse(localStorage.getItem('crm-data'))  // View all leads
JSON.parse(sessionStorage.getItem('assessmentResults'))  // View scores
localStorage.clear()  // CAREFUL - deletes everything!
```

### Common Issues
```javascript
// Issue: App not defined
// Cause: Functions called before app object created
// Solution: See appProxy pattern in code

// Issue: Form not saving
// Cause: Form field IDs don't match
// Solution: Check `id="..."` matches JavaScript references

// Issue: Export empty
// Cause: No data in CRM yet
// Solution: Complete at least one discovery call first
```

---

## 📦 Performance Notes

- **Load time:** <2s (no external dependencies)
- **Memory:** ~100KB CSS + HTML, data scales with leads
- **Storage:** Each lead ~2-3KB (supports 500-1000)
- **Export:** <1s for 100 leads, <5s for 1000

### Optimization Opportunities
1. **Lazy load** images if adding many
2. **Minify CSS** for production
3. **Compress** old CRM data
4. **Archive** prospects >1 year old

---

## 🔗 Integration Points

### Future: Google Sheets API
```javascript
// When ready for direct integration:
// 1. OAuth2 authentication
// 2. Google Sheets API calls
// 3. Real-time sync instead of CSV
```

### Future: Email Integration
```javascript
// When ready:
// 1. SMTP service (SendGrid, AWS)
// 2. Generate follow-up emails
// 3. Track opens/clicks
```

### Future: CRM Sync
```javascript
// Connect to Salesforce, HubSpot, Pipedrive:
// 1. API authentication
// 2. Field mapping
// 3. Bi-directional sync
```

---

## 📚 Code Comments Convention

```javascript
// Single line comment for brief explanations

/**
 * Function description
 * @param {type} paramName - Description
 * @returns {type} Description
 */
function functionName(paramName) {
  // Implementation
}
```

---

## 🎯 Development Priorities

### Completed ✅
- Core discovery flow
- CRM database (localStorage)
- CSV export
- Strategic insights
- ROI calculations
- Dark mode UI

### Roadmap
- [ ] Google Sheets API integration (direct sync)
- [ ] Email sending (follow-ups automatic)
- [ ] User authentication (team collaboration)
- [ ] Salesforce/HubSpot integration
- [ ] Advanced analytics & reporting
- [ ] Mobile app (React Native)

---

**For user documentation, see README.md**
