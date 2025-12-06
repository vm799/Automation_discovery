# AI Automation Discovery Tool

**Enterprise-grade lead generation system for AI automation consultants. Scorecard → Discovery → CRM → Google Sheets.**

---

## 🎯 What It Does

Complete sales funnel that turns prospects into leads:
1. **Scorecard** (2 min) - Quick AI readiness assessment
2. **Discovery** (30 min) - Deep-dive questionnaire with ROI calculations
3. **CRM** (Auto) - All data stored locally, organized by metrics
4. **Export** (1 click) - Download to Google Sheets for pipeline management

---

## 🚀 Quick Start

### Step 1: Share Scorecard
Send link to prospects: `scorecard.html`
- 10 questions, 5 sections with big icons
- Shows: AI Readiness, Automation Potential, Complexity

### Step 2: Full Discovery
Route to: `discovery-tool.html`
- 5-step guided interview
- Automatic data saving
- Real-time ROI calculations

### Step 3: Review CRM
Click "📇 CRM" tab
- See all prospects with key metrics
- Dashboard with 6 performance indicators

### Step 4: Export & Share
Click "📊 Export to CSV"
- Choose: Comprehensive (25 fields) or Summary (10 fields)
- Download as CSV
- Import to Google Sheets (File → Import → Upload)

---

## 💾 How It Works

### Scorecard (scorecard.html)
**5 Sections with Icons:**
- 📊 Processes & Operations (Q1, Q4, Q5, Q10)
- 🎯 Strategy & Vision (Q2, Q8)
- 👥 Team Readiness (Q3, Q7)
- 💼 Resources & Budget (Q6, Q9)
- 🚀 Ready to Calculate? (Results)

**Results Calculated:**
- AI Readiness Score (0-100)
- Automation Potential (0-100%)
- Complexity Assessment (1-10)

### Discovery Tool (discovery-tool.html)
**Step 1: Company Basics**
- Name, email, phone
- Company, industry, size, role

**Step 2: Current State**
- Main pain points
- What systems they use
- Manual work description

**Step 3: Integration Analysis**
- Which tools don't talk to each other
- How many hours wasted manually

**Step 4: Future Vision & ROI**
- Team size affected
- Hours/week spent on manual work
- Deal value per customer
- Revenue at risk

**Step 5: Review & Generate**
- View calculated ROI
- Generate proposal
- Export to PDF
- Send follow-up email

### CRM Database
**Automatic Storage:** Browser localStorage (no servers)

**Dashboard Metrics:**
- 📊 Total Prospects
- 💰 Total Opportunity ($M)
- 🎯 High Priority Leads (>$50k)
- 📈 Avg. Automation Potential (%)
- ⚡ Ready-to-Act Leads (Readiness >70)
- 📄 Conversion Rate (%)

**Export Formats:**
1. **Comprehensive** (25 columns)
   - All scores, financials, insights, timestamps
   - Best for: Detailed analysis, archiving

2. **Summary** (10 columns)
   - Key metrics only
   - Best for: Quick reviews, dashboards

---

## 📊 Features

| Feature | Details |
|---------|---------|
| **Auto-save** | Every 30 seconds |
| **Database** | Browser localStorage (~5-10MB) |
| **Export** | CSV to Google Sheets |
| **CRM** | Up to 500-1000 prospects |
| **Backup** | Download CSV weekly |
| **Mobile** | Fully responsive |
| **Dark Mode** | Built in |

---

## 🔧 Setup & Customization

### Add Your Calendly Link
File: `discovery-tool.html` → Line ~1819

```javascript
const calendlyUrl = 'https://calendly.com/YOUR-USERNAME/30min';
```

### Update Email Signature
File: `discovery-tool.html` → Function `generateFollowUpEmail()` (~line 1678)

Change: `Vaishali Mehmi` → Your name

### Add Your Eye Image
File: `assets/neuronal-eye.png` (1000x1000px PNG recommended)
- System tries PNG → falls back to SVG → CSS fallback

### Change Brand Colors
File: Top of HTML files (CSS variables):
```css
--accent-cyan: #00d9ff
--accent-pink: #ff006e
--bg-primary: #0a0e1a
--text-primary: #e6edf3
```

---

## 📈 Using the System

### Running a Discovery Call

**Before:**
1. Send scorecard link → Get their assessment
2. Review their scores → Note readiness level
3. Plan focus areas → What to dig into

**During:**
1. Open discovery-tool.html
2. Go through 5 steps
3. Fill in details as they answer
4. (Auto-saves every 30 seconds)

**After:**
1. Click "Generate Proposal" button
2. View strategic insights (5 recommendations)
3. Share insights link with prospect
4. Mark as "Insights Shared" in CRM
5. Follow up per auto-generated email

### Exporting to Google Sheets

**Step 1:** Click "📊 Export to CSV"
**Step 2:** Choose type:
- OK = Comprehensive (all data)
- Cancel = Summary (key metrics)
**Step 3:** File downloads
**Step 4:** Go to google.com/sheets
**Step 5:** File → Import → Upload
**Step 6:** Your prospects are in Google Sheets

### In Google Sheets

**Sort by Opportunity:**
- Data → Sort range → Annual Savings → Highest first

**Filter High-Priority:**
- Data → Create filter → Alert Flag = High Priority

**Add Conditional Colors:**
- Select Annual Savings column
- Format → Conditional → Color scale
- Red (low) → Green (high)

**Build Follow-up List:**
- Filter by Status = "Insights Shared"
- Sort by Follow-up Due Date
- Export to PDF for team

---

## 🛡️ Data & Security

### Storage
- **Location:** Browser localStorage (local machine only)
- **Servers:** None (no cloud sync)
- **Backup:** CSV export to Google Drive
- **Limit:** ~500-1000 prospects

### Best Practices
1. **Export weekly** - Every Friday ideal
2. **Store in Google Drive** - Label with dates
3. **Secure CSVs** - Password-protect folder
4. **Don't clear cache** - Unless you exported first

### Warning ⚠️
Clearing browser cache = deleting all data
- Always export before clearing history
- Keep backups in cloud storage
- Label backups: `CRM-Backup-YYYY-MM-DD.csv`

---

## 🆘 Troubleshooting

**Q: Eye image not showing?**
A: Make sure `assets/neuronal-eye.png` exists. Falls back to SVG or CSS if missing.

**Q: Export file empty?**
A: Complete at least one discovery call first (needs data to export).

**Q: CSV won't import to Google Sheets?**
A: Check file is .csv (not .xlsx). In Google Sheets Import → More options → UTF-8 encoding.

**Q: Data disappeared?**
A: Probably cleared browser cache. Always export first. Now keep weekly backups.

**Q: Buttons not working?**
A: Hard refresh browser (Ctrl+Shift+R or Cmd+Shift+R).

**Q: Can multiple people use this?**
A: Yes - each person gets own local database. To share data: both export CSVs, merge in Google Sheets.

---

## 📱 Technical Requirements

| Requirement | Detail |
|-------------|--------|
| Browser | Chrome, Firefox, Safari, Edge (modern versions) |
| Storage | ~5-10MB localStorage capacity |
| Internet | Only needed for Google Sheets import |
| Server | Any HTTP hosting (no special requirements) |
| Hosting | FTP upload or GitHub Pages works fine |

---

## 🚀 Deployment

### File Structure
```
your-domain.com/
├── index.html                 # Landing page
├── scorecard.html             # Assessment (2 min)
├── discovery-tool.html        # Discovery + CRM
├── assets/
│   ├── neuronal-eye.png       # Your eye image
│   ├── neuronal-eye.svg       # Fallback
│   └── README.txt
└── README.md                  # This file
```

### Deploy Steps
1. Upload HTML files to web server
2. Add `assets/neuronal-eye.png` (your image)
3. Update Calendly link in discovery-tool.html (line ~1819)
4. Test in browser
5. Share links with prospects

### No Backend Needed
- No database server required
- No API integration needed
- No authentication system
- Everything runs in browser

---

## 📊 Success Metrics

Track these once live:
- Scorecard completions/week
- Assessment → Discovery conversion rate
- Average AI Readiness score
- Average automation potential %
- Discovery → Proposal conversion
- Average opportunity value
- High-priority lead count
- Days from assessment to follow-up

---

## 📞 Support

**For help:**
1. Check "Troubleshooting" section above
2. Review "Setup & Customization" for configuration
3. See TECHNICAL-GUIDE.md for developer details

**Common Questions:**
- **Can I migrate data?** Yes, via CSV export
- **How often export?** Weekly minimum (recommended Fridays)
- **Storage limits?** ~500-1000 prospects before archiving
- **Multiple users?** Each gets local database; merge in Google Sheets

---

## 📝 What's Included

### Core Files
✅ **index.html** - Landing page with neuronal eye
✅ **scorecard.html** - 10-question AI readiness assessment
✅ **discovery-tool.html** - Discovery + CRM + Export

### Images
✅ **assets/neuronal-eye.png** - Your actual eye image (optional)
✅ **assets/neuronal-eye.svg** - Backup SVG fallback

### Documentation
✅ **README.md** - This file (everything you need)
✅ **TECHNICAL-GUIDE.md** - Developer reference

---

## 🎯 Next Steps

1. **Test scorecard** → Open `scorecard.html` → Complete it
2. **Test discovery** → Open `discovery-tool.html` → Run 5 steps
3. **Test export** → Go to CRM → Export → Import to Google Sheets
4. **Customize** → Add eye image, update Calendly link, adjust colors
5. **Deploy** → Upload to your domain
6. **Launch** → Share scorecard link with prospects

---

## 📊 Example Workflow

```
Prospect Visits Site
    ↓
Clicks "Quick Assessment"
    ↓
Completes Scorecard (2 min)
    ↓
Sees Results: AI Readiness 65%, Automation 78%
    ↓
Button: "Start Discovery Call"
    ↓
Goes to Discovery Tool
    ↓
Answers 5 Steps (30 min)
    ↓
Views Strategic Insights & ROI ($102k/year savings)
    ↓
You Get CRM Entry (Auto-saved)
    ↓
You Export to Google Sheets (1 click)
    ↓
You Review Pipeline & Follow-up
```

---

## 🎉 You're Ready!

Everything is set up and production-ready.
Share the scorecard link and start generating qualified leads!

For technical details, see [TECHNICAL-GUIDE.md](TECHNICAL-GUIDE.md)
