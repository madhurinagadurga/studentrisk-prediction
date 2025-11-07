# Student Risk Prediction Dashboard

A modern, interactive web-based analytics dashboard for predicting and analyzing student academic risk levels using real-time data visualizations.

## 🚀 Features

### Interactive Visualizations
- **Risk Distribution Donut Chart** - Visual breakdown of high/medium/low risk students
- **Department GPA Analysis** - Compare average GPA across departments
- **GPA vs Risk Scatter Plot** - Correlation between academic performance and risk
- **Attendance vs GPA Bubble Chart** - Three-dimensional data visualization
- **Gender-based Risk Comparison** - Stacked bar charts for demographic analysis
- **Semester Trend Analysis** - Track GPA trends over time
- **Risk Heatmap** - Department and semester risk patterns
- **Risk Score Distribution** - Histogram of risk score ranges

### Dynamic Filtering
- Filter by Department
- Filter by Gender
- Filter by Risk Category (High/Medium/Low)
- Filter by Semester
- Search students by name or ID
- Reset all filters instantly

### Student Profiles
- Click any student to view detailed profile
- Animated modal with complete student information
- Radar chart showing performance metrics
- Risk score calculation breakdown

### KPI Dashboard
- Average GPA
- Average Attendance
- High Risk Student Percentage
- Total Students Count

## 📁 File Structure

```
student-risk-dashboard/
│
├── index.html              # Main dashboard layout
├── style.css              # Modern academic styling
├── script.js              # Dashboard logic & visualizations
├── data/
│   └── Student_Risk_Dataset_2200.csv
└── README.md              # This file
```

## 🔧 Technology Stack

- **HTML5** - Structure and layout
- **CSS3** - Modern styling with gradients, animations, and responsive design
- **JavaScript (ES6+)** - Interactive functionality
- **Chart.js 4.4.0** - Data visualizations
- **PapaParse 5.4.1** - CSV file parsing

## 🎨 Design Features

- Navy blue and gold academic color scheme
- Smooth animations and transitions
- Responsive design for all screen sizes
- Glass morphism effects
- Hover animations on interactive elements
- Modern gradient backgrounds
- Professional typography (Inter + Poppins)

## 📊 Risk Calculation Formula

The system calculates student risk scores using the following weighted formula:

```javascript
Risk Score = (0.5 × GPA_Score + 0.3 × Attendance_Score + Financial_Flag) × 100

Where:
- GPA_Score = (4 - Student_GPA) / 4
- Attendance_Score = (100 - Student_Attendance) / 100
- Financial_Flag = 0.15 if Fee Balance > 0, else 0

Risk Categories:
- Low Risk: Score < 30
- Medium Risk: Score 30-60
- High Risk: Score > 60
```

## 🚀 Deployment Instructions

### Method 1: GitHub Pages (Recommended)

1. **Create a new GitHub repository**
   ```bash
   git init
   git add .
   git commit -m "Initial commit: Student Risk Dashboard"
   ```

2. **Push to GitHub**
   ```bash
   git remote add origin https://github.com/yourusername/student-risk-dashboard.git
   git branch -M main
   git push -u origin main
   ```

3. **Enable GitHub Pages**
   - Go to your repository on GitHub
   - Click on **Settings** → **Pages**
   - Under "Source", select branch: **main**
   - Click **Save**
   - Wait 1-2 minutes for deployment

4. **Access your dashboard**
   ```
   https://yourusername.github.io/student-risk-dashboard/
   ```

### Method 2: Local Development

1. **Clone or download the repository**
   ```bash
   git clone https://github.com/yourusername/student-risk-dashboard.git
   cd student-risk-dashboard
   ```

2. **Start a local server**
   
   Using Python:
   ```bash
   python -m http.server 8000
   ```
   
   Using Node.js:
   ```bash
   npx http-server -p 8000
   ```

3. **Open in browser**
   ```
   http://localhost:8000
   ```

### Method 3: Netlify Deploy

1. **Drag and drop deployment**
   - Visit [Netlify Drop](https://app.netlify.com/drop)
   - Drag your project folder
   - Get instant deployment URL

2. **Or use Netlify CLI**
   ```bash
   npm install -g netlify-cli
   netlify deploy --prod
   ```

## 📝 Using Your Own Dataset

1. **Prepare your CSV file**
   - Required columns: `StudentID`, `Name`, `Department`, `Gender`, `GPA`, `Attendance`, `FeeBalance`, `Semester`
   - Save as `Student_Risk_Dataset_2200.csv`

2. **Replace the data file**
   - Place your CSV in the `data/` directory
   - The dashboard will automatically load and process it

3. **CSV Format Example**
   ```csv
   StudentID,Name,Department,Gender,GPA,Attendance,FeeBalance,Semester
   STU0001,John Smith,Computer Science,Male,3.45,88,0,3
   STU0002,Emma Johnson,Engineering,Female,2.89,75,1200,5
   ```

## 🎯 Key Features Implementation

### Sorting & Filtering
- Click any column header to sort table
- Use dropdown filters for instant data filtering
- Search bar for quick student lookup

### Responsive Design
- Mobile-first approach
- Breakpoints at 768px
- Touch-friendly interface

### Performance Optimization
- Chart caching and destruction
- Efficient data filtering
- Pagination for large datasets (20 students per page)

### Accessibility
- High contrast colors
- Clear visual hierarchy
- Keyboard navigation support

## 🔒 Data Privacy

- All data processing happens in the browser
- No data is sent to external servers
- Suitable for sensitive student information

## 🐛 Troubleshooting

### Charts not displaying
- Ensure Chart.js CDN is loading correctly
- Check browser console for errors
- Verify CSV file path is correct

### CSV not loading
- Check that the file is in `data/` directory
- Verify CSV format matches required columns
- Look for parsing errors in console

### GitHub Pages 404 Error
- Ensure index.html is in repository root or configured directory
- Check that GitHub Pages is enabled in settings
- Wait a few minutes after enabling Pages

## 📧 Support

For issues or questions, please:
1. Check browser console for errors
2. Verify all files are properly uploaded
3. Ensure CSV format matches requirements

## 📄 License

© 2025 Nexus Strategies | Student Risk Prediction System

---

**Built with ❤️ for educational institutions to improve student success outcomes**
