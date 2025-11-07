# 🎯 Complete Features & Website Flow
## Student Risk Prediction Dashboard

---

# TABLE OF CONTENTS

1. [All Features List](#all-features-list)
2. [User Journey Flows](#user-journey-flows)
3. [Feature Details](#feature-details)
4. [Interaction Patterns](#interaction-patterns)

---

# 1. ALL FEATURES LIST

## Authentication Features

### ✅ Feature 1.1: User Registration
**What it does:** Allows new users to create accounts

**Components:**
- Full Name input field
- Email input field
- Password input field (minimum 6 characters)
- Confirm Password input field
- Create Account button
- Validation messages

**Validation Rules:**
- All fields required
- Email must be valid format (contains @)
- Password minimum 6 characters
- Passwords must match
- Email must be unique (not already registered)

**Data Storage:**
```javascript
{
  name: "John Doe",
  email: "john@example.com",
  password: "password123",  // Plain text (demo only)
  createdAt: "2025-01-07T10:30:00.000Z"
}
```

**Success Action:**
- Account created in localStorage
- Automatic login
- Redirect to main page

---

### ✅ Feature 1.2: User Login
**What it does:** Authenticates returning users

**Components:**
- Email input field
- Password input field
- Login button
- "Register here" link

**Validation:**
- Email and password required
- Must match stored credentials
- Case-sensitive password
- Case-insensitive email

**Success Action:**
- Session stored in localStorage
- Redirect to main page
- Show user name in navigation

**Error Handling:**
- Shows alert: "Invalid email or password"
- Stays on login page
- Doesn't reveal which field is wrong (security)

---

### ✅ Feature 1.3: Session Persistence
**What it does:** Remembers logged-in users

**Mechanism:**
- Checks localStorage on page load
- If currentUser exists → auto-login
- If not → show login page

**Benefits:**
- No need to login every time
- Survives page refresh
- Survives browser close/reopen
- Only cleared on manual logout

---

### ✅ Feature 1.4: Logout
**What it does:** Ends user session

**Components:**
- Logout button (top-right corner)
- Confirmation dialog

**Process:**
1. User clicks "Logout"
2. Confirmation: "Are you sure?"
3. If yes: Clear session, reload page
4. If no: Cancel, stay logged in

**Data Cleared:**
- currentUser from localStorage
- User accounts remain (can login again)

---

## Navigation Features

### ✅ Feature 2.1: Tab Navigation
**What it does:** Switches between different sections

**Tabs Available:**
1. **Overview** - Main dashboard with KPIs and primary charts
2. **Risk Analysis** - Advanced risk visualizations
3. **Student Profiles** - Student table with search
4. **Documentation** - Complete guide and formulas

**Behavior:**
- Click tab to switch content
- Active tab highlighted in gold
- Smooth fade transition (0.3s)
- URL doesn't change (single page app)
- Previous tab content hidden, not destroyed

---

### ✅ Feature 2.2: Navigation Bar
**What it does:** Persistent header with navigation and user info

**Components:**
- Logo (NS icon)
- System title
- Tab buttons
- User name display
- Logout button

**Responsive Behavior:**
- Desktop: Full horizontal layout
- Tablet: Stacked navigation
- Mobile: Compact with menu

---

## Data Filtering Features

### ✅ Feature 3.1: Department Filter
**What it does:** Shows only students from selected department

**Options:**
- All Departments (default)
- Computer Science
- Engineering
- Business
- Medicine
- Arts
- Science
- Mathematics
- Physics
- Chemistry
- Biology

**Effect:**
- Filters entire dataset
- Updates all charts
- Updates KPIs
- Updates student table
- Can combine with other filters

---

### ✅ Feature 3.2: Gender Filter
**What it does:** Shows only students of selected gender

**Options:**
- All Genders (default)
- Male
- Female
- Other

**Effect:**
- Same as department filter
- All visualizations update

---

### ✅ Feature 3.3: Risk Category Filter
**What it does:** Shows only students in selected risk level

**Options:**
- All Risk Levels (default)
- High Risk
- Medium Risk
- Low Risk

**Use Case:**
- Focus on high-risk students only
- View low-risk students for success patterns
- Isolate medium-risk for intervention planning

---

### ✅ Feature 3.4: Semester Filter
**What it does:** Shows only students in selected semester

**Options:**
- All Semesters (default)
- Semester 1 through Semester 8

**Use Case:**
- Analyze freshman (Semester 1-2)
- Focus on seniors (Semester 7-8)
- Compare specific cohorts

---

### ✅ Feature 3.5: Combined Filtering
**What it does:** Apply multiple filters simultaneously

**Example Combinations:**
- Computer Science + Female + High Risk
- Engineering + Semester 3 + Medium Risk
- All departments + Male + Low Risk

**Reset Functionality:**
- "Reset All Filters" button
- Clears all selections
- Returns to full dataset
- All dropdowns back to "All"

---

## KPI (Key Performance Indicator) Features

### ✅ Feature 4.1: Average GPA Card
**What it shows:** Mean GPA of filtered students

**Display:**
- Large number (e.g., 2.75)
- "Out of 4.0" subtitle
- Blue gradient background
- 📊 icon

**Calculation:**
```
Sum of all GPAs / Number of students
```

**Updates:**
- Real-time when filters change
- Animated number transition
- Tooltips on hover

---

### ✅ Feature 4.2: Average Attendance Card
**What it shows:** Mean attendance percentage

**Display:**
- Percentage (e.g., 73%)
- "Based on selected filters" subtitle
- Gold/Orange gradient background
- 📈 icon

**Calculation:**
```
Sum of all attendance / Number of students
```

---

### ✅ Feature 4.3: High Risk Students Card
**What it shows:** Percentage and count of high-risk students

**Display:**
- Main: Percentage (e.g., 0.1%)
- Sub: Count (e.g., "3 students")
- Red gradient background
- ⚠️ icon

**Calculation:**
```
(High risk count / Total students) × 100
```

**Visual Alert:**
- Turns darker red if > 20%
- Indicates critical situation

---

### ✅ Feature 4.4: Total Students Card
**What it shows:** Count of students in current view

**Display:**
- Number (e.g., 2,200)
- "In dataset" subtitle
- Green gradient background
- 👥 icon

**Purpose:**
- Shows filtered count
- Helps understand filter impact
- Quick reference for sample size

---

## Chart Features

### ✅ Feature 5.1: Risk Distribution Donut Chart
**Type:** Doughnut chart

**What it shows:**
- Proportion of students in each risk category
- Color-coded segments
- Percentages on hover

**Interaction:**
- Hover to see exact percentages
- Click legend to toggle segments
- Animated on first load

**Colors:**
- Red: High Risk
- Orange: Medium Risk
- Green: Low Risk

---

### ✅ Feature 5.2: Department GPA Bar Chart
**Type:** Vertical bar chart

**What it shows:**
- Average GPA for each department
- Bars scaled 0-4.0

**Interaction:**
- Hover to see exact GPA
- Bars animate on load
- Responsive to window resize

**Use Case:**
- Compare departments
- Identify struggling departments
- Budget allocation

---

### ✅ Feature 5.3: GPA vs Risk Scatter Plot
**Type:** Scatter plot

**What it shows:**
- Each dot = one student
- X-axis: GPA
- Y-axis: Risk Score
- Color: Risk category

**Pattern Analysis:**
- Should show negative correlation
- Lower left = low GPA, high risk
- Upper right = high GPA, low risk
- Outliers indicate special cases

**Interaction:**
- Hover shows student details
- Pan and zoom disabled (too many points)

---

### ✅ Feature 5.4: Attendance vs GPA Bubble Chart
**Type:** Bubble chart

**What it shows:**
- X-axis: Attendance %
- Y-axis: GPA
- Bubble size: Risk score
- Color: Risk category

**Special Feature:**
- Shows 3D data (attendance, GPA, risk)
- Limited to first 100 students (performance)

**Analysis:**
- Upper right = ideal students
- Upper left = trying but struggling (need tutoring)
- Lower right = talented but disengaged
- Lower left = high risk

---

### ✅ Feature 5.5: Gender Risk Comparison
**Type:** Stacked bar chart

**What it shows:**
- Each bar = gender group
- Sections = risk categories
- Height = student count

**Use Case:**
- Check for gender equity
- Ensure fair support distribution
- Demographic analysis

---

### ✅ Feature 5.6: Semester GPA Trend
**Type:** Line chart with filled area

**What it shows:**
- X-axis: Semesters 1-8
- Y-axis: Average GPA
- Line connects averages

**Pattern Analysis:**
- Upward trend = improvement
- Downward trend = decline
- Flat = stable
- Dips indicate problematic semesters

**Use Case:**
- Monitor intervention effectiveness
- Identify difficult semesters
- Plan support timing

---

### ✅ Feature 5.7: Risk Heatmap
**Type:** Custom HTML/CSS grid

**What it shows:**
- Rows: Departments
- Columns: Semesters 1-8
- Cells: Average risk score
- Colors: Risk level

**Color Coding:**
- Green < 30 (low risk)
- Yellow 30-60 (medium risk)
- Red > 60 (high risk)

**Use Case:**
- Pinpoint exact problem areas
- Department-semester combinations
- Resource allocation

**Interaction:**
- Hover highlights cell
- Shows exact risk score
- Scrollable on narrow screens

---

### ✅ Feature 5.8: Department Risk Distribution
**Type:** Horizontal stacked bar chart

**What it shows:**
- Each bar = department
- Sections = risk categories (horizontal)
- Length = student count

**Key Insight:**
- Compare proportions, not counts
- Longer red section = more high-risk
- Use percentages for fair comparison

---

### ✅ Feature 5.9: Risk Score Distribution
**Type:** Histogram

**What it shows:**
- X-axis: Risk score ranges (10-point bins)
- Y-axis: Number of students
- 10 bars total (0-10, 10-20, ..., 90-100)

**Distribution Patterns:**
- Normal curve = healthy population
- Left-skewed = mostly low risk
- Right-skewed = mostly high risk
- Bimodal = two distinct groups

---

### ✅ Feature 5.10: Student Performance Radar
**Type:** Radar chart (in modal)

**What it shows:**
- 4 axes: GPA, Attendance, Financial, Overall Risk
- Polygon shape showing balance
- All metrics scaled 0-100

**Appears:**
- Only in student detail modal
- Generated per student
- Interactive tooltips

**Interpretation:**
- Larger polygon = better performance
- Irregular shape = unbalanced metrics

---

## Table Features

### ✅ Feature 6.1: Student Data Table
**Type:** Sortable, paginated table

**Columns:**
1. Student ID
2. Name
3. Department
4. GPA
5. Attendance %
6. Risk Level (badge)
7. Risk Score
8. Actions (View button)

**Display:**
- 20 students per page
- Zebra striping (alternating rows)
- Hover highlighting
- Responsive design

---

### ✅ Feature 6.2: Column Sorting
**How it works:**
- Click column header to sort
- First click: Descending
- Second click: Ascending
- Third click: Back to default

**Sort indicator:**
- ↓ symbol for descending
- ↑ symbol for ascending
- ↕ symbol for unsorted

**Sortable columns:**
- All columns except Actions

---

### ✅ Feature 6.3: Table Pagination
**Components:**
- Previous button
- Page numbers (1, 2, 3, ...)
- Next button
- Shows 5 page numbers at a time

**Behavior:**
- Previous disabled on page 1
- Next disabled on last page
- Current page highlighted gold
- Smooth page transitions

**Navigation:**
- Click page number to jump
- Previous/Next for sequential
- Wraps at boundaries

---

### ✅ Feature 6.4: Student Search
**Type:** Real-time text search

**Search Fields:**
- Student name
- Student ID

**Behavior:**
- Updates on every keystroke
- Case-insensitive
- Partial matching
- Instant results
- Filters table rows

**Interaction:**
- Type in search box
- Table filters automatically
- Shows "No students found" if no matches
- Clear box to see all

---

## Modal Features

### ✅ Feature 7.1: Student Detail Modal
**Trigger:** Click "View" button on any student

**Layout:**
- Header: Name + Risk badge + Close button
- Body: 8 data fields in grid
- Footer: Performance radar chart

**Data Fields:**
1. Student ID
2. Department
3. Gender
4. Semester
5. GPA (highlighted)
6. Attendance (highlighted)
7. Fee Balance
8. Risk Score (highlighted)

**Interaction:**
- Click X to close
- Click outside modal to close
- Press Escape key to close
- Smooth animations (fade + slide)

---

### ✅ Feature 7.2: Modal Animations
**Opening:**
- Background fades to dark (0.3s)
- Modal slides up from bottom (0.3s)
- Chart animates rendering (0.5s)

**Closing:**
- Modal slides down (0.2s)
- Background fades to clear (0.2s)
- Chart destroyed

---

## Documentation Features

### ✅ Feature 8.1: Risk Formula Section
**Content:**
- Main formula display
- Component breakdowns
- Example calculations
- Category definitions

**Formatting:**
- Code blocks for formulas
- Colored boxes for examples
- Step-by-step calculations
- Visual badges for categories

---

### ✅ Feature 8.2: Chart Explanations
**Content:**
- All 9 charts explained
- Purpose of each
- How to read
- Use cases
- Example interpretations

**Structure:**
- Numbered sections
- Consistent format
- Visual hierarchy
- Easy to scan

---

### ✅ Feature 8.3: Deployment Guide
**Content:**
- Step-by-step instructions
- GitHub Pages setup
- Troubleshooting tips
- Multiple methods
- Screenshots descriptions

**Format:**
- Clear numbered steps
- Code blocks
- Warning boxes
- Success messages

---

## Additional Features

### ✅ Feature 9.1: Responsive Design
**Breakpoints:**
- Desktop: 1200px+
- Tablet: 768px - 1199px
- Mobile: < 768px

**Adaptations:**
- Single column on mobile
- Stacked navigation
- Simplified charts
- Touch-friendly buttons
- Readable text sizes

---

### ✅ Feature 9.2: Loading States
**Indicators:**
- Empty chart containers on initial load
- "Loading..." text
- Smooth fade-in when data ready
- Progressive rendering

**Duration:**
- CSV load: 1-2 seconds
- Risk calculation: 0.5 seconds
- Chart rendering: 2-3 seconds
- Total: 3-5 seconds

---

### ✅ Feature 9.3: Error Handling
**Scenarios Handled:**
- CSV file not found → Generate mock data
- Invalid data → Skip row, log error
- Chart render failure → Show error message
- Storage quota exceeded → Alert user

---

### ✅ Feature 9.4: Browser Compatibility
**Tested Browsers:**
- Chrome 90+
- Firefox 88+
- Safari 14+
- Edge 90+

**Fallbacks:**
- Modern font with system fallback
- CSS Grid with Flexbox fallback
- localStorage with cookie fallback

---

# 2. USER JOURNEY FLOWS

## Flow 1: New User Registration

```
START: User opens dashboard URL
  ↓
Step 1: Login Page Loads
  - See Nexus Strategies branding
  - Email and password fields
  - "Register here" link visible
  ↓
Step 2: User Clicks "Register here"
  - Form transitions to registration
  - Animation: slide/fade (0.3s)
  ↓
Step 3: Registration Form Appears
  - 4 input fields visible
  - All fields empty
  - Create Account button
  ↓
Step 4: User Fills Form
  - Types full name
  - Types email
  - Types password (min 6 chars)
  - Confirms password
  ↓
Step 5: User Clicks "Create Account"
  - JavaScript validates inputs
  - Checks all fields filled
  - Checks email format
  - Checks passwords match
  - Checks email not already used
  ↓
Step 6A: Validation Success
  - Create user object
  - Save to localStorage['users']
  - Set localStorage['currentUser']
  - Hide login modal (fade out)
  - Show main
  - Redirect to overview tab
  ↓
Step 6B: Validation Failure
  - Show error alert
  - Stay on registration page
  - Keep form filled
  - Highlight error field
  ↓
Step 7: Load (see Flow 2)
  ↓
END
```

---

## Flow 2: Dashboard Initial Load

```
START: User authenticated
  ↓
Step 1: HTML Structure Loads
  - Navigation bar renders
  - Filter panel renders
  - Empty chart containers appear
  - Tab structure ready
  - Duration: 0.5 seconds
  ↓
Step 2: CSS Styles Apply
  - Gradients render
  - Layout positions
  - Colors applied
  - Animations prepared
  - Duration: 0.2 seconds
  ↓
Step 3: JavaScript Executes
  - Check authentication
  - Verify currentUser exists
  - If not → redirect to login
  - Initialize variables
  - Duration: 0.1 seconds
  ↓
Step 4: Load External Libraries
  - Chart.js loads from CDN
  - PapaParse loads from CDN
  - Google Fonts load
  - Duration: 0.5-1 second
  ↓
Step 5: Fetch CSV Data
  - Request data/Student_Risk_Dataset_2200.csv
  - PapaParse processes file
  - Parse 2,200 rows
  - Duration: 1-2 seconds
  ↓
Step 6: Calculate Risk Scores
  - For each student (2,200 iterations):
    * Calculate GPA component
    * Calculate attendance component
    * Determine financial flag
    * Compute final risk score
    * Assign risk category
  - Duration: 0.3-0.5 seconds
  ↓
Step 7: Initialize Filters
  - Extract unique departments (10)
  - Extract unique genders (3)
  - Extract unique semesters (8)
  - Populate dropdown options
  - Duration: 0.1 seconds
  ↓
Step 8: Calculate and Display KPIs
  - Calculate average GPA
  - Calculate average attendance
  - Count high-risk students
  - Calculate percentage
  - Render 4 KPI cards
  - Animate numbers (count up)
  - Duration: 0.5 seconds
  ↓
Step 9: Render Charts (Sequential)
  - Chart 1: Risk donut (0.3s)
  - Chart 2: Department GPA bars (0.3s)
  - Chart 3: GPA scatter (0.4s)
  - Chart 4: Attendance bubbles (0.4s)
  - Chart 5: Gender comparison (0.3s)
  - Chart 6: Semester trend (0.3s)
  - Total duration: 2-3 seconds
  - Each chart animates on render
  ↓
Step 10: Render Student Table
  - Sort by risk score (default)
  - Take first 20 students
  - Populate table rows
  - Generate pagination buttons
  - Duration: 0.2 seconds
  ↓
Step 11: Dashboard Ready
  - All interactive
  - Filters active
  - Charts complete
  - User can interact
  - Total load time: 5-8 seconds
  ↓
END: User sees complete
```

---

## Flow 3: Using Filters

```
START: User on page
  ↓
Step 1: User Clicks Filter Dropdown
  - Example: Department filter
  - Dropdown expands
  - Shows all options
  ↓
Step 2: User Selects Option
  - Example: "Computer Science"
  - Dropdown closes
  - Selection shows in field
  ↓
Step 3: JavaScript Detects Change
  - onChange event fires
  - Get selected value
  - Call applyFilters() function
  - Duration: <0.01 seconds
  ↓
Step 4: Filter Dataset
  - Create copy of allStudents array
  - Apply filter logic:
    filteredStudents = allStudents.filter(s =>
      s.Department === "Computer Science"
    )
  - Result: 221 students (from 2,200)
  - Duration: 0.01 seconds
  ↓
Step 5: Update KPIs
  - Recalculate average GPA (221 students)
  - Recalculate average attendance
  - Recount high-risk students
  - Animate number transitions
  - Duration: 0.3 seconds
  ↓
Step 6: Update Charts
  - For each chart:
    * Destroy old Chart.js instance
    * Recalculate data (221 students)
    * Create new chart with new data
    * Animate transition
  - Process all 6 charts
  - Duration: 1.5-2 seconds
  ↓
Step 7: Update Student Table
  - Filter table to 221 students
  - Resort by current sort column
  - Reset to page 1
  - Show first 20 students
  - Recalculate pagination (12 pages now)
  - Duration: 0.2 seconds
  ↓
Step 8: Update Complete
  - All visualizations show Computer Science only
  - KPIs reflect filtered data
  - User can add more filters
  - Or click "Reset" to clear
  ↓
END: Filtered view active
```

---

## Flow 4: Viewing Student Details

```
START: User viewing student table
  ↓
Step 1: Table Displays Students
  - 20 rows visible (page 1)
  - Each row has "View" button
  - Rows show basic info
  ↓
Step 2: User Hovers Over Row
  - Row highlights (background change)
  - Cursor changes to pointer over button
  - Visual feedback
  ↓
Step 3: User Clicks "View" Button
  - Click event fires
  - Gets student ID from row
  - Example: StudentID = "STU0123"
  ↓
Step 4: Retrieve Student Data
  - Search allStudents array
  - Find student by ID
  - Extract full student object:
    {
      StudentID: "STU0123",
      Name: "John Doe",
      Department: "Computer Science",
      GPA: 3.2,
      Attendance: 85,
      FeeBalance: 0,
      Semester: 3,
      RiskScore: 25,
      RiskCategory: "Low"
    }
  - Duration: <0.01 seconds
  ↓
Step 5: Prepare Modal
  - Set modal display to flex
  - Add 'active' class
  - Start animations
  ↓
Step 6: Animate Modal Opening
  - Background: transparent → dark (0.3s)
  - Modal: translateY(50px) → 0 (0.3s)
  - Opacity: 0 → 1 (0.3s)
  ↓
Step 7: Populate Modal Content
  - Set student name in header
  - Set risk badge (colored by category)
  - Fill all 8 data fields
  - Format fee balance as currency
  - Duration: 0.05 seconds
  ↓
Step 8: Generate Radar Chart
  - Calculate metrics:
    * GPA (scaled): (3.2 / 4.0) × 100 = 80
    * Attendance: 85
    * Financial: 100 (no debt)
    * Overall: 100 - 25 = 75
  - Create Chart.js radar chart
  - Animate polygon drawing
  - Duration: 0.5 seconds
  ↓
Step 9: Modal Fully Displayed
  - All data visible
  - Chart complete
  - User can review details
  - Close button active
  - Background clicks enabled
  ↓
Step 10: User Reviews Student Info
  - Reads data fields
  - Views radar chart
  - Understands risk factors
  ↓
Step 11: User Closes Modal
  - Options:
    A) Click X button
    B) Click outside modal
    C) Press Escape key
  - Close event fires
  ↓
Step 12: Animate Modal Closing
  - Modal: translateY(0) → 50px (0.2s)
  - Opacity: 1 → 0 (0.2s)
  - Background: dark → transparent (0.2s)
  ↓
Step 13: Cleanup
  - Destroy radar chart
  - Remove 'active' class
  - Set display to none
  - Free memory
  ↓
Step 14: Return to Table View
  - Table still visible
  - Same page, same filters
  - User can view another student
  ↓
END: Back to student list
```

---

## Flow 5: Searching for Student

```
START: User on "Student Profiles" tab
  ↓
Step 1: See Student Table
  - Full table visible
  - 2,200 students total
  - 20 visible on current page
  - Search box at top-right
  ↓
Step 2: User Clicks Search Box
  - Input field focuses
  - Cursor in search box
  - Placeholder text fades
  ↓
Step 3: User Types First Character
  - Example: Types "e"
  - keyup event fires
  - Duration: <0.01 seconds
  ↓
Step 4: Search Filter Runs
  - Get search term: "e"
  - Convert to lowercase: "e"
  - Filter students:
    results = allStudents.filter(s =>
      s.Name.toLowerCase().includes("e") ||
      s.StudentID.toLowerCase().includes("e")
    )
  - Many matches (Emma, Steven, etc.)
  - Duration: 0.02 seconds
  ↓
Step 5: Update Table
  - Show matched students
  - Still paginated (20 per page)
  - Reset to page 1
  - Update pagination
  - Duration: 0.1 seconds
  ↓
Step 6: User Types More Characters
  - Types "m" → search term "em"
  - Filter runs again
  - Fewer matches (Emma, Emily, etc.)
  ↓
Step 7: User Types Complete Name
  - Types "ma" → search term "emma"
  - Filter runs again
  - Results: "Emma Johnson", "Emma Davis"
  - Only 2 students match
  ↓
Step 8: Refined Results Display
  - Table shows 2 rows
  - No pagination needed (< 20 results)
  - Matches highlighted (optional)
  ↓
Step 9: User Finds Target Student
  - Sees "Emma Johnson"
  - Clicks "View" button
  - Modal opens (see Flow 4)
  ↓
Step 10: User Finishes, Clears Search
  - Closes modal
  - Clears search box (backspace or clear button)
  - Search term becomes empty ""
  ↓
Step 11: Return to Full Table
  - All students visible again
  - Back to full 2,200 students
  - Pagination restored
  - Same page as before search (if possible)
  ↓
END: Full table view restored
```

---

## Flow 6: Sorting Table

```
START: User viewing student table
  ↓
Step 1: Table Displayed
  - Default sort: Risk Score descending
  - Headers show ↕ symbols
  - Rows in current order
  ↓
Step 2: User Clicks Column Header
  - Example: Clicks "GPA" header
  - Click event fires
  - Gets column name: "GPA"
  ↓
Step 3: Determine Sort Direction
  - Check current sort column
  - If same column:
    * Toggle direction (asc ↔ desc)
  - If different column:
    * Set to descending (default)
  - Example: First click on GPA → descending
  ↓
Step 4: Sort Data
  - Copy filteredStudents array
  - Apply sort:
    students.sort((a, b) => {
      if (sortDirection === 'desc') {
        return a.GPA < b.GPA ? 1 : -1
      }
    })
  - Duration: 0.05 seconds
  ↓
Step 5: Update Table Display
  - Clear table body
  - Get current page students (20 rows)
  - Populate rows in new order
  - Duration: 0.1 seconds
  ↓
Step 6: Update Header Visual
  - Remove indicators from other headers
  - Add ↓ to GPA header (descending)
  - Highlight active sort column
  ↓
Step 7: Table Re-rendered
  - Highest GPAs at top
  - Example: 4.0, 3.9, 3.8, ...
  - Pagination still works
  - Same page number
  ↓
Step 8: User Clicks Same Header Again
  - Toggle to ascending
  - Header shows ↑
  - Lowest GPAs at top
  - Example: 1.5, 1.6, 1.7, ...
  ↓
Step 9: User Clicks Different Header
  - Example: Clicks "Attendance"
  - Sorts by attendance (descending)
  - Header shows ↓ on Attendance
  - GPA header back to ↕
  ↓
END: Table sorted by chosen column
```

---

## Flow 7: Changing Tabs

```
START: User on "Overview" tab
  ↓
Step 1: Current Tab Active
  - Overview tab highlighted gold
  - Overview content visible
  - Other tabs grayed out
  - All charts rendered
  ↓
Step 2: User Clicks "Risk Analysis" Tab
  - Click event fires
  - Get target tab: "risk-analysis"
  ↓
Step 3: JavaScript Handles Switch
  - Remove 'active' class from Overview tab
  - Remove 'active' class from Overview content
  - Add 'active' class to Risk Analysis tab
  - Add 'active' class to Risk Analysis content
  - Duration: <0.01 seconds
  ↓
Step 4: CSS Transitions
  - Overview content: opacity 1 → 0 (0.2s)
  - Overview content: display none
  - Risk Analysis content: display block
  - Risk Analysis content: opacity 0 → 1 (0.3s)
  ↓
Step 5: Risk Analysis Tab Loads
  - Check if charts already rendered
  - If not: Create charts now
    * Risk heatmap (HTML grid)
    * Department risk (stacked bars)
    * Risk score histogram
  - Duration: 1-2 seconds (first time only)
  ↓
Step 6: Tab Fully Visible
  - Risk Analysis tab highlighted gold
  - Overview tab back to gray
  - All Risk Analysis charts interactive
  - Filters still apply
  ↓
Step 7: User Explores Risk Analysis
  - Views heatmap
  - Hovers over cells
  - Checks department risks
  ↓
Step 8: User Clicks "Student Profiles" Tab
  - Same switch process
  - Loads student table
  - Table content appears
  - Charts hidden (not destroyed)
  ↓
Step 9: User Clicks "Documentation" Tab
  - Same switch process
  - Loads documentation content
  - No charts in this tab
  - Text content scrollable
  ↓
Step 10: User Returns to "Overview" Tab
  - Charts already exist
  - Instant display (no re-render)
  - Same filter state preserved
  - Charts show current filtered data
  ↓
END: Back to Overview tab
```

---

## Flow 8: Complete Session

```
START: User opens URL
  ↓
PHASE 1: Authentication (2 minutes)
  - Load login page
  - Create account or login
  - Session established
  ↓
PHASE 2: Initial Exploration (5 minutes)
  - loads
  - Review KPI cards
  - View risk distribution
  - Check department GPAs
  - Understand overall status
  ↓
PHASE 3: Filtering Analysis (10 minutes)
  - Select Computer Science department
  - See dept-specific data
  - Add High Risk filter
  - View at-risk CS students
  - Reset filters
  - Try Engineering + Semester 3
  - Analyze results
  ↓
PHASE 4: Student Investigation (10 minutes)
  - Go to Student Profiles tab
  - Search for specific student
  - View student details (modal)
  - Check performance radar
  - Close modal
  - Sort by GPA (ascending)
  - View lowest GPA students
  - Click View on several
  - Identify intervention needs
  ↓
PHASE 5: Risk Analysis (8 minutes)
  - Go to Risk Analysis tab
  - Study heatmap
  - Find red cells (problem areas)
  - Check department risk bars
  - View risk score distribution
  - Take mental notes for action
  ↓
PHASE 6: Documentation Review (5 minutes)
  - Go to Documentation tab
  - Review risk formula
  - Understand chart meanings
  - Check deployment guide
  - Read troubleshooting tips
  ↓
PHASE 7: Logout (1 minute)
  - Click Logout button
  - Confirm logout
  - Redirected to login page
  - Session cleared
  ↓
END: Session complete
  Total time: ~40 minutes
```

---

# 3. FEATURE DETAILS

## Data Processing Pipeline

### Stage 1: CSV Loading
```
1. PapaParse fetch request
2. Receive CSV text (2200 rows × 8 columns)
3. Parse to JavaScript objects
4. Validate data types
5. Handle missing values
6. Store in allStudents array
```

### Stage 2: Risk Calculation
```
For each student:
1. Extract GPA → calculate component
2. Extract Attendance → calculate component
3. Extract Fee Balance → determine flag
4. Apply main formula
5. Calculate risk score
6. Assign risk category
7. Add to student object
```

### Stage 3: Data Aggregation
```
1. Group by department
2. Group by gender
3. Group by semester
4. Group by risk category
5. Calculate averages for groups
6. Count students per group
7. Prepare data for charts
```

### Stage 4: Visualization
```
1. Create Chart.js configs
2. Populate with processed data
3. Set colors and styles
4. Enable interactions
5. Render to canvas
6. Animate appearance
```

---

## Interaction Patterns

### Pattern 1: Hover States
**Elements with hover:**
- Navigation tabs
- Filter dropdowns
- KPI cards
- Chart elements
- Table rows
- Buttons
- Links

**Hover Effects:**
- Color change
- Shadow increase
- Scale up (1.02-1.05)
- Cursor changes to pointer
- Tooltip appears

---

### Pattern 2: Click Interactions
**Clickable Elements:**
- Tab buttons → Switch content
- Filter dropdowns → Open menu
- Filter options → Apply filter
- Reset button → Clear filters
- Table headers → Sort column
- View buttons → Open modal
- Modal close → Hide modal
- Pagination → Change page
- Logout → End session

---

### Pattern 3: Keyboard Interactions
**Keyboard Shortcuts:**
- Tab key → Navigate between inputs
- Enter key → Submit forms
- Escape key → Close modals
- Arrow keys → Navigate dropdowns
- Spacebar → Activate buttons

---

### Pattern 4: Touch Interactions (Mobile)
**Touch Gestures:**
- Tap → Same as click
- Scroll → Pan through content
- Pinch → Zoom (disabled for performance)
- Swipe → Navigate pages (optional)

---

## Performance Optimizations

### Optimization 1: Lazy Loading
- Risk Analysis charts load only when tab opened
- Documentation loads only when tab opened
- Modal chart creates only when modal opens

### Optimization 2: Data Caching
- Parse CSV once, store in memory
- Risk scores calculated once
- Chart instances reused when possible
- Filter results cached temporarily

### Optimization 3: DOM Management
- Pagination limits visible rows
- Charts limited to first 100 points (bubbles)
- Destroy old chart instances
- Remove event listeners on cleanup

### Optimization 4: Debouncing
- Search input debounced (300ms)
- Window resize debounced (200ms)
- Filter changes throttled

---

**End of Features & Flow Documentation**

All features are implemented and tested. The documentation describes the current state of the application as of the last update.
