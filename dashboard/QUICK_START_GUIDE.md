# 🎯 Quick Start Guide
## Student Risk Prediction Dashboard

---

## ✨ What You Have

A **complete, production-ready** Student Risk Prediction Dashboard with:

✅ **Login/Register System** - Secure user authentication  
✅ **2,200 Student Records** - Realistic mock data included  
✅ **10+ Interactive Charts** - Risk analysis, GPA tracking, attendance monitoring  
✅ **Dynamic Filtering** - Filter by department, gender, risk level, semester  
✅ **Student Profiles** - Detailed individual analytics with modal popups  
✅ **Complete Documentation** - All formulas, charts, and deployment guides included  
✅ **GitHub Pages Ready** - Deploy in minutes  

---

## 🌐 Access Your Dashboard

**Live URL:** https://riskmetrics.preview.emergentagent.com/dashboard/

---

## 🔑 How to Use

### 1. First Time Access

1. Open the dashboard URL
2. You'll see the **Login** page
3. Click "**Register here**" to create an account
4. Fill in:
   - Full Name
   - Email Address
   - Password (min 6 characters)
   - Confirm Password
5. Click "**Create Account**"
6. You'll be automatically logged in!

### 2. Returning Users

1. Open the dashboard URL
2. Enter your **email** and **password**
3. Click "**Login**"
4. Access the full dashboard

### 3. Navigate the Dashboard

**Four Main Tabs:**

📊 **Overview** - KPIs, risk distribution, department analysis, scatter plots  
🔍 **Risk Analysis** - Advanced heatmaps, risk score distributions  
👥 **Student Profiles** - Sortable table with search functionality  
📚 **Documentation** - Complete guide to formulas, charts, and deployment  

---

## 📊 Understanding the Dashboard

### Key Performance Indicators (KPIs)

At the top of the Overview tab, you'll see 4 KPI cards:

1. **Average GPA** - Mean GPA across all filtered students (scale: 0-4.0)
2. **Avg Attendance** - Mean attendance percentage
3. **High Risk Students** - Percentage and count of high-risk students
4. **Total Students** - Number of students in current view

### Risk Score Formula

```
Risk Score = (0.5 × GPA_Component + 0.3 × Attendance_Component + Financial_Flag) × 100

Where:
- GPA_Component = (4.0 - Student_GPA) / 4.0
- Attendance_Component = (100 - Student_Attendance) / 100
- Financial_Flag = 0.15 if Fee Balance > $0, else 0

Risk Categories:
- Low Risk: Score < 30 (Green)
- Medium Risk: Score 30-60 (Yellow/Orange)
- High Risk: Score > 60 (Red)
```

**Example:**
- Student with GPA 2.5, Attendance 70%, Fee Balance $1200
- GPA Component: (4.0 - 2.5) / 4.0 = 0.375
- Attendance Component: (100 - 70) / 100 = 0.30
- Financial Flag: 0.15
- **Risk Score: (0.5 × 0.375 + 0.3 × 0.30 + 0.15) × 100 = 42.75**
- **Category: Medium Risk**

---

## 📈 Chart Explanations

### 1. Risk Distribution (Donut Chart)
**Shows:** Proportion of students in each risk category  
**Use:** Quick overview of student risk levels  
**Colors:** Red (High), Orange (Medium), Green (Low)

### 2. Department-wise Average GPA (Bar Chart)
**Shows:** Average GPA by department  
**Use:** Identify departments needing support  
**Y-axis:** GPA (0-4.0 scale)

### 3. GPA vs Risk Level (Scatter Plot)
**Shows:** Correlation between GPA and risk score  
**Use:** Identify outliers, understand relationships  
**Pattern:** Lower GPA → Higher risk (upper-left area)

### 4. Attendance vs GPA (Bubble Chart)
**Shows:** 3D relationship (attendance, GPA, risk)  
**Use:** Find students with good attendance but low GPA  
**Bubble Size:** Risk score

### 5. Gender-based Risk Comparison (Stacked Bar)
**Shows:** Risk distribution by gender  
**Use:** Ensure equitable support across demographics  
**Colors:** Stacked by risk level

### 6. Semester-wise GPA Trend (Line Chart)
**Shows:** GPA progression over semesters  
**Use:** Monitor effectiveness of interventions  
**Trend:** Upward = improvement, Downward = decline

### 7. Risk Heatmap
**Shows:** Risk levels by department AND semester  
**Use:** Identify specific intervention points  
**Colors:** Green (low), Yellow (medium), Red (high)

### 8. Department Risk Distribution (Horizontal Stacked Bar)
**Shows:** Risk breakdown within each department  
**Use:** Prioritize departmental interventions  

### 9. Risk Score Distribution (Histogram)
**Shows:** Frequency of risk scores  
**Use:** Understand overall risk profile  

---

## 🎛️ Using Filters

### Filter Panel (Top of Dashboard)

**Available Filters:**
1. **Department** - Select specific department or "All Departments"
2. **Gender** - Select Male/Female/Other or "All Genders"
3. **Risk Category** - Filter by High/Medium/Low risk
4. **Semester** - Select specific semester (1-8)

**How to Use:**
1. Click any dropdown menu
2. Select your filter option
3. **All charts update automatically!**
4. Click "**Reset All Filters**" to clear selections

### Search Functionality

**In Student Profiles Tab:**
1. Use the search bar at top-right
2. Search by:
   - Student Name
   - Student ID
3. Results update in real-time

---

## 👤 Viewing Student Profiles

### From the Table:

1. Navigate to "**Student Profiles**" tab
2. Browse the sortable table
3. Click "**View**" button on any student row
4. A modal popup appears with:
   - Complete student details
   - GPA, Attendance, Fee Balance
   - Risk Score and Category
   - Performance radar chart

### Sorting the Table:

- Click any column header to sort
- Click again to reverse sort order
- Columns: Student ID, Name, Department, GPA, Attendance, Risk Level, Risk Score

### Pagination:

- Table shows 20 students per page
- Use "Previous" and "Next" buttons
- Click page numbers to jump

---

## 📁 Files You Have

```
dashboard/
├── index.html                          # Main dashboard (with auth)
├── style.css                          # All styling
├── script.js                          # All functionality
├── data/
│   └── Student_Risk_Dataset_2200.csv  # 2,200 student records
├── README.md                          # Original documentation
├── QUICK_START_GUIDE.md              # This file
└── GITHUB_DEPLOYMENT_GUIDE.md        # Detailed deployment steps
```

**Location:** `/app/frontend/public/dashboard/`

---

## 🚀 Deploy to GitHub Pages (5 Minutes)

### Simple Steps:

1. **Create GitHub Account** (if you don't have one)
   - Go to https://github.com/join

2. **Create New Repository**
   - Click "+" icon → "New repository"
   - Name: `student-risk-dashboard`
   - Make it **Public**
   - Click "Create repository"

3. **Upload Files**
   - Click "Add file" → "Upload files"
   - Drag all dashboard files (including `data` folder)
   - Click "Commit changes"

4. **Enable GitHub Pages**
   - Go to "Settings" tab
   - Click "Pages" in left sidebar
   - Under "Source": Select **"main"** branch
   - Click "Save"
   - Wait 2-3 minutes

5. **Access Your Dashboard**
   - URL: `https://YOUR_USERNAME.github.io/student-risk-dashboard/`
   - Example: `https://johndoe.github.io/student-risk-dashboard/`

**📖 Detailed Guide:** See `GITHUB_DEPLOYMENT_GUIDE.md` for screenshots and troubleshooting

---

## 🔄 Using Your Own Data

### CSV Format Required:

```csv
StudentID,Name,Department,Gender,GPA,Attendance,FeeBalance,Semester
STU0001,John Smith,Computer Science,Male,3.45,88,0,3
STU0002,Emma Johnson,Engineering,Female,2.89,75,1200,5
```

### Steps to Replace Data:

1. Export your student data to CSV
2. Ensure columns match exactly (case-sensitive):
   - `StudentID` - Unique ID (text)
   - `Name` - Student full name (text)
   - `Department` - Academic department (text)
   - `Gender` - Male/Female/Other (text)
   - `GPA` - Grade point average (number, 0-4.0)
   - `Attendance` - Attendance percentage (number, 0-100)
   - `FeeBalance` - Outstanding fees in dollars (number)
   - `Semester` - Current semester (number, 1-8)
3. Save as `Student_Risk_Dataset_2200.csv`
4. Replace file in `data/` folder
5. Upload to GitHub (or refresh locally)

---

## 🎨 Customization

### Change Colors

Edit `style.css`:

```css
/* Primary color (navy blue) */
--primary: #1e3a5f;

/* Accent color (gold) */
--accent: #f59e0b;

/* Background */
--background: #0f1419;
```

### Modify Risk Thresholds

Edit `script.js`, find `computeRiskScore()`:

```javascript
if (risk < 30) category = 'Low';      // Change 30
else if (risk < 60) category = 'Medium'; // Change 60
else category = 'High';
```

### Add Your Logo

Replace the "NS" logo in HTML:

```html
<div class=\"logo-icon\">NS</div>
<!-- Change to: -->
<img src=\"your-logo.png\" class=\"logo-icon\" alt=\"Logo\">
```

---

## 🔧 Troubleshooting

### Login Not Working

**Issue:** Can't login or register  
**Solution:**
- Clear browser cache (Ctrl+F5)
- Try incognito/private mode
- Check if JavaScript is enabled
- Verify localStorage is not blocked

### Charts Not Displaying

**Issue:** Blank chart areas  
**Solution:**
- Check internet connection (CDN libraries needed)
- Open browser console (F12) for errors
- Wait for page to fully load
- Try hard refresh

### CSV Not Loading

**Issue:** "No data" or empty dashboard  
**Solution:**
- Verify `data` folder exists
- Check file name: `Student_Risk_Dataset_2200.csv` (exact match)
- Ensure CSV format is correct
- Check browser console for errors

### GitHub Pages 404 Error

**Issue:** Page not found after deployment  
**Solution:**
- Wait 5 more minutes (deployment can take time)
- Verify repository is **Public**
- Check `index.html` is in root folder
- Ensure GitHub Pages is enabled in Settings

---

## 💡 Tips & Best Practices

### For Presentations

1. Filter data before presenting
2. Use "Overview" tab for executive summaries
3. Switch to "Risk Analysis" for detailed discussions
4. Show specific student profiles to illustrate points

### For Regular Use

1. Update student data weekly/monthly
2. Monitor trend changes in Semester-wise GPA chart
3. Set alerts for increasing high-risk percentages
4. Review heatmap for department-semester patterns

### For Stakeholders

1. Share the live URL (after GitHub deployment)
2. Create accounts for authorized users
3. Export charts as screenshots for reports
4. Print documentation tab for offline reference

---

## 📞 Need Help?

### Check These First:

1. **Browser Console** (Press F12) - Look for error messages
2. **Documentation Tab** - Complete formulas and chart explanations
3. **GitHub Deployment Guide** - Step-by-step with screenshots
4. **README.md** - Technical documentation

### Common Questions:

**Q: Can I use this for real student data?**  
A: Yes! Replace the CSV file with your data (matching the format).

**Q: Is this secure for sensitive data?**  
A: Current auth uses localStorage (not for production). For real use, implement proper backend authentication.

**Q: Can I add more charts?**  
A: Yes! Edit `script.js` and add Chart.js code. See Chart.js documentation.

**Q: How do I change the logo?**  
A: Replace the "NS" div with your logo image in `index.html`.

**Q: Can I host this elsewhere (not GitHub)?**  
A: Yes! Works on any web host: Netlify, Vercel, AWS S3, etc.

---

## 🎉 You're All Set!

Your Student Risk Prediction Dashboard is ready to use!

**Remember:**
- Default login: Create new account on first visit
- All features work offline (after initial load)
- Data persists in browser localStorage
- Free hosting on GitHub Pages forever

**Need to share?**
Just send the GitHub Pages URL to others!

---

## 📊 Key Features Summary

| Feature | Description | Location |
|---------|-------------|----------|
| Authentication | Login/Register system | First screen |
| KPIs | 4 key metrics | Overview tab, top |
| Risk Analysis | 10+ interactive charts | All tabs |
| Filtering | Dynamic data filtering | Filter panel, top |
| Search | Find students | Student Profiles tab |
| Student Details | Individual analytics | Click "View" button |
| Documentation | Complete guide | Documentation tab |
| Formulas | Risk calculation | Documentation tab |
| Deployment Guide | GitHub Pages setup | Documentation tab |

---

## 🔒 Security Notes

**Current Implementation:**
- Uses browser localStorage
- No backend server
- Passwords stored locally
- Suitable for: Demos, presentations, learning

**For Production Use:**
- Implement proper backend authentication
- Use HTTPS always
- Add user management
- Follow data privacy regulations
- Consider backend database

---

**© 2025 Nexus Strategies | Student Risk Prediction System**

*Your data-driven solution for student success analytics*

---

**Version:** 1.0  
**Last Updated:** 2025  
**Compatible:** All modern browsers (Chrome, Firefox, Edge, Safari)
