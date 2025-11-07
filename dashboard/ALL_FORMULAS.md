# 🧮 Complete Formula Documentation
## Every Mathematical Formula Used in the Dashboard

---

# TABLE OF CONTENTS

1. [Risk Score Calculation](#risk-score-calculation)
2. [Statistical Formulas](#statistical-formulas)
3. [Chart-Specific Calculations](#chart-specific-calculations)
4. [Data Aggregation Formulas](#data-aggregation-formulas)

---

# 1. RISK SCORE CALCULATION

## Master Formula

### Main Risk Score Formula
```
Risk_Score = (0.5 × GPA_Component + 0.3 × Attendance_Component + Financial_Flag) × 100
```

**Variables:**
- `Risk_Score` = Final risk score (0-100)
- `GPA_Component` = Normalized GPA measure (0-1)
- `Attendance_Component` = Normalized attendance measure (0-1)
- `Financial_Flag` = Binary financial status (0 or 0.15)

**Weights:**
- GPA: 50% of total score
- Attendance: 30% of total score
- Financial: 15% maximum impact (binary)
- Remaining 5%: Built into the scaling factor

---

## Sub-Formula 1: GPA Component

### Formula
```
GPA_Component = (4.0 - Student_GPA) / 4.0
```

**Input:**
- `Student_GPA` = Grade Point Average (range: 0.0 to 4.0)

**Output:**
- Value between 0.0 and 1.0
- Lower GPA → Higher component value
- Higher GPA → Lower component value

**Examples:**

| GPA | Calculation | Component | Interpretation |
|-----|-------------|-----------|----------------|
| 4.0 | (4.0 - 4.0) / 4.0 | 0.00 | Perfect (no risk) |
| 3.5 | (4.0 - 3.5) / 4.0 | 0.125 | Excellent |
| 3.0 | (4.0 - 3.0) / 4.0 | 0.25 | Good |
| 2.5 | (4.0 - 2.5) / 4.0 | 0.375 | Average |
| 2.0 | (4.0 - 2.0) / 4.0 | 0.50 | Below average |
| 1.5 | (4.0 - 1.5) / 4.0 | 0.625 | Poor |
| 1.0 | (4.0 - 1.0) / 4.0 | 0.75 | Failing |
| 0.0 | (4.0 - 0.0) / 4.0 | 1.00 | Complete failure |

**Mathematical Properties:**
- Linear inverse relationship
- Domain: [0, 4.0]
- Range: [0, 1.0]
- Continuous function
- Decreasing function (negative slope)

---

## Sub-Formula 2: Attendance Component

### Formula
```
Attendance_Component = (100 - Student_Attendance) / 100
```

**Input:**
- `Student_Attendance` = Attendance percentage (range: 0 to 100)

**Output:**
- Value between 0.0 and 1.0
- Perfect attendance → 0 component value
- Zero attendance → 1.0 component value

**Examples:**

| Attendance | Calculation | Component | Interpretation |
|-----------|-------------|-----------|----------------|
| 100% | (100 - 100) / 100 | 0.00 | Perfect |
| 95% | (100 - 95) / 100 | 0.05 | Excellent |
| 90% | (100 - 90) / 100 | 0.10 | Very good |
| 85% | (100 - 85) / 100 | 0.15 | Good |
| 80% | (100 - 80) / 100 | 0.20 | Acceptable |
| 75% | (100 - 75) / 100 | 0.25 | Concerning |
| 70% | (100 - 70) / 100 | 0.30 | Poor |
| 60% | (100 - 60) / 100 | 0.40 | Very poor |
| 50% | (100 - 50) / 100 | 0.50 | Critical |
| 0% | (100 - 0) / 100 | 1.00 | Never attends |

**Mathematical Properties:**
- Linear inverse relationship
- Domain: [0, 100]
- Range: [0, 1.0]
- Continuous function
- Decreasing function

---

## Sub-Formula 3: Financial Flag

### Formula
```
Financial_Flag = {
    0.15  if Fee_Balance > $0
    0     if Fee_Balance = $0
}
```

**Input:**
- `Fee_Balance` = Outstanding fee amount in dollars

**Output:**
- Binary value: 0.15 or 0
- Any debt → 0.15 penalty
- No debt → 0 penalty

**Examples:**

| Fee Balance | Flag Value | Interpretation |
|-------------|-----------|----------------|
| $0 | 0 | No financial risk |
| $1 | 0.15 | Financial obligation |
| $500 | 0.15 | Financial obligation |
| $1,200 | 0.15 | Financial obligation |
| $5,000 | 0.15 | Financial obligation |

**Mathematical Properties:**
- Step function (discontinuous at x=0)
- Domain: [0, ∞)
- Range: {0, 0.15}
- Constant for all positive values

**Note:** Amount of debt doesn't matter, only presence/absence

---

## Complete Worked Examples

### Example 1: Low Risk Student

**Student Profile:**
```
Name: Alice Johnson
GPA: 3.8
Attendance: 95%
Fee Balance: $0
```

**Step-by-Step Calculation:**

```
Step 1: Calculate GPA Component
GPA_Component = (4.0 - 3.8) / 4.0
              = 0.2 / 4.0
              = 0.05

Step 2: Calculate Attendance Component
Attendance_Component = (100 - 95) / 100
                     = 5 / 100
                     = 0.05

Step 3: Determine Financial Flag
Fee_Balance = $0
Financial_Flag = 0

Step 4: Calculate Final Risk Score
Risk_Score = (0.5 × 0.05 + 0.3 × 0.05 + 0) × 100
           = (0.025 + 0.015 + 0) × 100
           = 0.04 × 100
           = 4.0

Result: Risk Score = 4.0 → Low Risk Category (< 30)
```

---

### Example 2: Medium Risk Student

**Student Profile:**
```
Name: Bob Smith
GPA: 2.5
Attendance: 70%
Fee Balance: $1,200
```

**Step-by-Step Calculation:**

```
Step 1: Calculate GPA Component
GPA_Component = (4.0 - 2.5) / 4.0
              = 1.5 / 4.0
              = 0.375

Step 2: Calculate Attendance Component
Attendance_Component = (100 - 70) / 100
                     = 30 / 100
                     = 0.30

Step 3: Determine Financial Flag
Fee_Balance = $1,200 (greater than $0)
Financial_Flag = 0.15

Step 4: Calculate Final Risk Score
Risk_Score = (0.5 × 0.375 + 0.3 × 0.30 + 0.15) × 100
           = (0.1875 + 0.09 + 0.15) × 100
           = 0.4275 × 100
           = 42.75

Result: Risk Score = 42.75 → Medium Risk Category (30-59)
```

---

### Example 3: High Risk Student

**Student Profile:**
```
Name: Charlie Davis
GPA: 1.8
Attendance: 55%
Fee Balance: $3,500
```

**Step-by-Step Calculation:**

```
Step 1: Calculate GPA Component
GPA_Component = (4.0 - 1.8) / 4.0
              = 2.2 / 4.0
              = 0.55

Step 2: Calculate Attendance Component
Attendance_Component = (100 - 55) / 100
                     = 45 / 100
                     = 0.45

Step 3: Determine Financial Flag
Fee_Balance = $3,500 (greater than $0)
Financial_Flag = 0.15

Step 4: Calculate Final Risk Score
Risk_Score = (0.5 × 0.55 + 0.3 × 0.45 + 0.15) × 100
           = (0.275 + 0.135 + 0.15) × 100
           = 0.56 × 100
           = 56.0

Result: Risk Score = 56.0 → Medium Risk (borderline High Risk)

Note: At this calculation, student is still in Medium range, but very close
to High Risk threshold. Additional factors or slight decline would push to High Risk.
```

---

## Risk Category Assignment Formula

### Formula
```
Risk_Category = {
    "Low Risk"     if Risk_Score < 30
    "Medium Risk"  if 30 ≤ Risk_Score < 60
    "High Risk"    if Risk_Score ≥ 60
}
```

**Thresholds:**
- Low/Medium boundary: 30
- Medium/High boundary: 60

**Color Coding:**
- Low Risk: Green (#10b981)
- Medium Risk: Orange (#f59e0b)
- High Risk: Red (#ef4444)

---

# 2. STATISTICAL FORMULAS

## Mean (Average) Calculation

### Formula
```
Mean = Σ(x₁ + x₂ + ... + xₙ) / n

Where:
- Σ = Sum of all values
- xᵢ = Individual value
- n = Number of values
```

**Used For:**
- Average GPA
- Average Attendance
- Average Risk Score per department/semester

**Example:**
```
Student GPAs: [3.5, 2.8, 3.9, 2.5, 3.2]
Mean = (3.5 + 2.8 + 3.9 + 2.5 + 3.2) / 5
     = 15.9 / 5
     = 3.18
```

---

## Percentage Calculation

### Formula
```
Percentage = (Part / Whole) × 100
```

**Used For:**
- Risk category percentages
- Attendance rates
- Department distribution

**Example:**
```
High Risk Students: 33
Total Students: 2,200

High Risk % = (33 / 2,200) × 100
            = 0.015 × 100
            = 1.5%
```

---

## Count and Filter

### Formula
```
Count = Σ(1 for each item meeting condition)
```

**Used For:**
- Number of high-risk students
- Students per department
- Gender counts

**Example (JavaScript):**
```javascript
highRiskCount = students.filter(s => s.RiskCategory === "High").length
```

---

# 3. CHART-SPECIFIC CALCULATIONS

## Chart 1: Risk Distribution (Donut Chart)

### Formula
```
For each category (High, Medium, Low):
  Count = Number of students in category
  Percentage = (Count / Total_Students) × 100
  
Slice_Angle = (Percentage / 100) × 360°
```

**Example:**
```
Total Students: 2,200
High Risk: 3 students
Medium Risk: 1,047 students
Low Risk: 1,150 students

High % = (3 / 2,200) × 100 = 0.14%
Medium % = (1,047 / 2,200) × 100 = 47.59%
Low % = (1,150 / 2,200) × 100 = 52.27%

Verification: 0.14 + 47.59 + 52.27 = 100% ✓
```

---

## Chart 2: Department Average GPA (Bar Chart)

### Formula
```
For each department:
  Department_GPA = Σ(Student_GPAs_in_Department) / Students_Count

Bar_Height ∝ Department_GPA
```

**Example:**
```
Computer Science Department:
Students: [
  {name: "A", GPA: 3.5},
  {name: "B", GPA: 2.8},
  {name: "C", GPA: 3.2},
  {name: "D", GPA: 3.9}
]

Avg GPA = (3.5 + 2.8 + 3.2 + 3.9) / 4
        = 13.4 / 4
        = 3.35
```

---

## Chart 3: GPA vs Risk Scatter Plot

### Formula (Data Points)
```
For each student:
  Point = (x, y) where:
    x = Student_GPA
    y = Risk_Score
    color = Risk_Category_Color
```

**No aggregation** - plots individual student data points

**Expected Pattern:**
- Negative correlation
- Lower GPA → Higher risk (upper left)
- Higher GPA → Lower risk (lower right)

---

## Chart 4: Attendance vs GPA Bubble Chart

### Formula
```
For each student (limited to first 100):
  Bubble = (x, y, r) where:
    x = Attendance_Percentage
    y = Student_GPA
    r = Risk_Score / 5  (scaled for visibility)
    color = Risk_Category_Color
```

**Bubble Radius Scaling:**
```
radius = Risk_Score / 5

Examples:
  Risk_Score = 10 → radius = 2
  Risk_Score = 50 → radius = 10
  Risk_Score = 100 → radius = 20
```

---

## Chart 5: Gender Risk Comparison (Stacked Bar)

### Formula
```
For each gender:
  High_Count = Count(students where Gender = g AND Risk = "High")
  Med_Count = Count(students where Gender = g AND Risk = "Medium")
  Low_Count = Count(students where Gender = g AND Risk = "Low")
  
  Total_Bar_Height = High + Med + Low
```

**Example:**
```
Female Students: 1,100
  High Risk: 5 students
  Medium Risk: 520 students
  Low Risk: 575 students

Bar sections (bottom to top):
  Red section height: 5
  Orange section height: 520
  Green section height: 575
  Total bar height: 1,100
```

---

## Chart 6: Semester GPA Trend (Line Chart)

### Formula
```
For each semester (1-8):
  Semester_Avg_GPA = Σ(GPAs_in_Semester) / Count(Students_in_Semester)
  
Points = [(1, Sem1_GPA), (2, Sem2_GPA), ..., (8, Sem8_GPA)]
Connect points with line
```

**Example:**
```
Semester 1: 220 students, Total GPA = 572 → Avg = 2.6
Semester 2: 210 students, Total GPA = 588 → Avg = 2.8
Semester 3: 215 students, Total GPA = 623.5 → Avg = 2.9

Plot points: (1, 2.6), (2, 2.8), (3, 2.9)
Draw line connecting points
```

---

## Chart 7: Risk Heatmap

### Formula
```
For each (Department, Semester) combination:
  Students_in_Cell = Filter(students, dept AND semester)
  Avg_Risk = Σ(Risk_Scores) / Count(Students_in_Cell)
  
  Color = {
    Green if Avg_Risk < 30
    Yellow if 30 ≤ Avg_Risk < 60
    Red if Avg_Risk ≥ 60
  }
```

**Example:**
```
Engineering, Semester 3:
Students: [
  {risk: 45}, {risk: 52}, {risk: 38}, {risk: 61},
  {risk: 72}, {risk: 44}, {risk: 55}, {risk: 48},
  {risk: 50}, {risk: 39}
]

Sum = 504
Count = 10
Avg_Risk = 504 / 10 = 50.4 ≈ 50

Color = Yellow (Medium Risk, 30-60 range)
Display: "50"
```

---

## Chart 8: Department Risk Distribution (Horizontal Stacked Bar)

### Formula
```
For each department:
  High_Count = Count(students where Dept = d AND Risk = "High")
  Med_Count = Count(students where Dept = d AND Risk = "Medium")
  Low_Count = Count(students where Dept = d AND Risk = "Low")
  
  Total_Bar_Length = High + Med + Low
  
  High_Percentage = (High / Total) × 100
```

**Used for prioritization:**
```
Dept A: 500 students, 100 high-risk (20%)
Dept B: 100 students, 30 high-risk (30%)

Dept B needs MORE attention despite fewer absolute high-risk students
```

---

## Chart 9: Risk Score Distribution (Histogram)

### Formula
```
Create 10 bins: [0-9], [10-19], [20-29], ..., [90-100]

For each student:
  Bin_Index = FLOOR(Risk_Score / 10)
  If Bin_Index = 10: Bin_Index = 9  (edge case for score = 100)
  Bins[Bin_Index] += 1

Bar_Height[i] = Bins[i]
```

**Example:**
```
Student Risk Scores: [5, 15, 22, 28, 35, 42, 48, 65, 72, 95]

Binning:
  5 → Bin 0 (0-9)
  15 → Bin 1 (10-19)
  22 → Bin 2 (20-29)
  28 → Bin 2 (20-29)
  35 → Bin 3 (30-39)
  42 → Bin 4 (40-49)
  48 → Bin 4 (40-49)
  65 → Bin 6 (60-69)
  72 → Bin 7 (70-79)
  95 → Bin 9 (90-100)

Bin counts: [1, 1, 2, 1, 2, 0, 1, 1, 0, 1]
Draw bars with these heights
```

---

## Chart 10: Student Performance Radar (Modal)

### Formula
```
For individual student:
  
  Metric1_GPA = (Student_GPA / 4.0) × 100
  Metric2_Attendance = Student_Attendance
  Metric3_Financial = (Fee_Balance == 0) ? 100 : 50
  Metric4_Overall_Risk = 100 - Risk_Score

All metrics scaled to 0-100 range for fair comparison
```

**Example:**
```
Student Data:
  GPA: 3.2
  Attendance: 85%
  Fee Balance: $0
  Risk Score: 25

Radar Chart Values:
  GPA (scaled): (3.2 / 4.0) × 100 = 80
  Attendance: 85
  Financial: 100 (no debt)
  Overall: 100 - 25 = 75

Plot these 4 points on radar axes and connect
```

---

# 4. DATA AGGREGATION FORMULAS

## Grouping by Category

### Formula
```
For each unique value in grouping field:
  Group[value] = Filter(students, field == value)
  Count[value] = Group[value].length
  Aggregates[value] = Calculate metrics on Group[value]
```

**Example (Group by Department):**
```javascript
departments = {}
students.forEach(student => {
  if (!departments[student.Department]) {
    departments[student.Department] = []
  }
  departments[student.Department].push(student)
})

// Result:
departments = {
  "Computer Science": [student1, student2, ...],
  "Engineering": [student10, student11, ...],
  "Business": [student25, student26, ...]
}
```

---

## Multi-Dimensional Aggregation

### Formula (Heatmap)
```
For each (Dimension1_Value, Dimension2_Value) combination:
  Key = Dimension1_Value + "_" + Dimension2_Value
  Group[Key] = Filter(students, 
    field1 == Dimension1_Value AND 
    field2 == Dimension2_Value
  )
  Metric[Key] = Aggregate_Function(Group[Key])
```

**Example (Department × Semester):**
```javascript
heatmapData = {}
students.forEach(student => {
  key = student.Department + "_" + student.Semester
  if (!heatmapData[key]) {
    heatmapData[key] = []
  }
  heatmapData[key].push(student.RiskScore)
})

// Calculate averages
for (key in heatmapData) {
  scores = heatmapData[key]
  avgRisk = scores.reduce((a,b) => a+b) / scores.length
  heatmapData[key] = avgRisk
}
```

---

## Sorting Formula

### Formula
```
Sort_Function(a, b, column, direction) = {
  if direction == "ascending":
    return (a[column] > b[column]) ? 1 : -1
  else:
    return (a[column] < b[column]) ? 1 : -1
}
```

**Example:**
```
Sort students by GPA descending:
students.sort((a, b) => {
  return (a.GPA < b.GPA) ? 1 : -1
})

Result: [
  {name: "A", GPA: 3.9},
  {name: "B", GPA: 3.5},
  {name: "C", GPA: 3.2},
  {name: "D", GPA: 2.8}
]
```

---

## Pagination Formula

### Formula
```
Items_Per_Page = 20
Total_Pages = CEILING(Total_Items / Items_Per_Page)
Current_Page_Index = Page_Number - 1

Start_Index = Current_Page_Index × Items_Per_Page
End_Index = MIN(Start_Index + Items_Per_Page, Total_Items)

Page_Items = All_Items[Start_Index : End_Index]
```

**Example:**
```
Total Students: 2,200
Items Per Page: 20
Total Pages: CEILING(2,200 / 20) = 110 pages

Page 1:
  Start: 0
  End: 20
  Students: [0-19]

Page 2:
  Start: 20
  End: 40
  Students: [20-39]

Page 110:
  Start: 2,180
  End: 2,200
  Students: [2,180-2,199]
```

---

## Search Filter Formula

### Formula
```
Search_Term = User_Input.toLowerCase()

Matched_Students = Filter(All_Students, student => 
  student.Name.toLowerCase().includes(Search_Term) OR
  student.StudentID.toLowerCase().includes(Search_Term)
)
```

**Example:**
```
Search: "john"

Matches:
✓ "John Smith" (name contains "john")
✓ "Johnny Doe" (name contains "john")
✓ "Jane Johnson" (name contains "john")
✗ "Mike Davis" (no match)

Case-insensitive matching used
```

---

## Summary Statistics Formula

### Formula Set
```
Count = n

Mean = Σx / n

Minimum = MIN(x₁, x₂, ..., xₙ)

Maximum = MAX(x₁, x₂, ..., xₙ)

Range = Maximum - Minimum

Sum = x₁ + x₂ + ... + xₙ
```

**Example (GPA statistics):**
```
GPAs: [3.5, 2.8, 3.9, 2.5, 3.2, 2.9, 3.7, 3.1]

Count: 8
Sum: 25.6
Mean: 25.6 / 8 = 3.2
Min: 2.5
Max: 3.9
Range: 3.9 - 2.5 = 1.4
```

---

## Formula Reference Table

| Formula Name | Mathematical Expression | Purpose |
|--------------|------------------------|---------|
| Risk Score | (0.5×GPA_Comp + 0.3×Att_Comp + Fin_Flag)×100 | Main risk calculation |
| GPA Component | (4.0 - GPA) / 4.0 | Normalize GPA to 0-1 |
| Attendance Component | (100 - Attendance) / 100 | Normalize attendance to 0-1 |
| Financial Flag | 0.15 if debt > 0, else 0 | Binary financial risk |
| Mean | Σx / n | Average calculation |
| Percentage | (part / whole) × 100 | Proportion as percentage |
| Bin Index | FLOOR(value / bin_width) | Histogram binning |
| Scaled Radius | value / 5 | Bubble size scaling |
| Category Check | value < threshold | Risk category assignment |

---

## All Thresholds Used

| Threshold | Value | Purpose |
|-----------|-------|---------|
| Low/Medium Risk | 30 | Category boundary |
| Medium/High Risk | 60 | Category boundary |
| Perfect GPA | 4.0 | Maximum GPA scale |
| Perfect Attendance | 100% | Maximum attendance |
| Financial Flag Trigger | $0 | Debt presence check |
| Items Per Page | 20 | Table pagination |
| Bubble Chart Limit | 100 | Performance optimization |
| Histogram Bins | 10 | Score distribution |

---

**End of Formula Documentation**

All formulas are implemented in `script.js` and can be modified as needed for different risk models or institutional requirements.
