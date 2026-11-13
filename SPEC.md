# SPEC.md — PERFORMANCE MANAGEMENT SYSTEM (PMS)

## 1. PRODUCT PURPOSE

Develop a modern, interactive Performance Management System (PMS) for managing employee, team, and department performance.

The system combines two main evaluation dimensions:

- KPI (Key Performance Indicators): quantitative performance measurement.
- Competency Assessment: professional, behavioral, and leadership competency evaluation.

The platform must support the complete performance management cycle, including goal setting, evaluation, performance reviews, analytics, skill gap identification, and employee development.

This is an educational demonstration project. Use fictional employees, departments, positions, and performance records. Do not use real personal data.

The product must be a functional application, not just a static interface.

### Business Objectives

1. Standardize employee performance evaluation.
2. Improve transparency and consistency.
3. Measure performance using quantitative and qualitative indicators.
4. Identify high and low performers.
5. Compare employees, teams, and departments.
6. Identify competency gaps.
7. Monitor performance trends.
8. Support evidence-based HR decisions.
9. Provide management with accurate performance analytics.

The platform is a decision-support tool. It must never automatically make employment decisions.

---

## 2. USER ROLES

The application must support:

- System Administrator
- HR Administrator
- HR Specialist
- Department Manager
- Team Leader
- Employee
- Top Management

### System Administrator
- Full system access.
- Manage users and roles.
- Configure permissions.
- Manage organizational structure.
- Configure system settings.

### HR Administrator
- Access all employee profiles.
- Create evaluation models.
- Configure KPI and competencies.
- Create evaluation periods.
- Assign evaluators.
- Approve assessments.
- Access all reports.
- Configure scoring formulas.

### HR Specialist
- Manage employee records.
- Monitor evaluation completion.
- Review results.
- Add HR comments.
- Analyze competency gaps.
- Generate reports.

### Department Manager
- View department employees.
- Collaborate with HR on evaluation criteria.
- Complete Manager Assessments.
- Review team performance.
- Compare employee results.

### Team Leader
- View assigned employees.
- Evaluate team members.
- Monitor KPI achievement.
- Provide feedback.

### Employee
- View personal profile.
- View assigned KPIs.
- Complete Self-Assessment.
- View approved results.
- Track development progress.

### Top Management
- View organizational analytics.
- Compare departments.
- Monitor performance trends.
- Access aggregated reports.

Implement Role-Based Access Control (RBAC).

---

## 3. MAIN FUNCTIONAL MODULES

### 3.1 Dashboard

Create a professional analytical dashboard.

KPI cards:

- Total Employees
- Evaluated Employees
- Pending Reviews
- Average Performance Score
- High Performers
- Low Performers
- Evaluation Completion Rate
- Average KPI Achievement
- Average Competency Score
- Employees with Critical Skill Gaps

Charts:

1. Performance Distribution.
2. KPI vs Competency Comparison.
3. Department Performance Comparison.
4. Quarterly Performance Trend.
5. Top Performing Teams.
6. Performance Category Distribution.
7. Skill Gap Distribution.

Filters:

- Evaluation Period
- Department
- Team
- Position
- Manager
- Employee Status

All dashboard elements must update dynamically when filters change.

Display exact numbers and percentages.

### 3.2 Employee Database

Employee fields:

- Employee ID
- Full Name
- Email
- Position
- Department
- Team
- Direct Manager
- Employment Date
- Employment Status
- Employment Type
- Previous Position
- Evaluation History

Functions:

- Add employees.
- Edit employee records.
- Deactivate employees.
- Search and filter.
- View employee profiles.
- Export employee records to CSV.
- Import employee records from CSV.

Historical evaluations must remain unchanged when employee information changes.

### 3.3 Organizational Structure

Allow authorized users to:

- Create departments.
- Create teams.
- Create positions.
- Assign managers.
- Assign employees.
- View organizational hierarchy.

### 3.4 Position-Based Evaluation Models

Each position must have its own evaluation template.

Example positions:

- Sales Representative
- Junior Sales Representative
- Cashier
- Store Manager
- Department Manager
- HR Specialist

HR and authorized managers can:

- Create evaluation templates.
- Add KPI indicators.
- Add competencies.
- Define weights.
- Set target values.
- Define required competency levels.
- Configure evaluation scales.
- Edit templates for future periods.

KPI weights must total 100%.

Competency weights must total 100%.

Completed historical evaluations must not be modified by template changes.

### 3.5 KPI Management

Each KPI must contain:

- KPI ID
- KPI Name
- Description
- Assigned Position
- Target Value
- Actual Value
- Weight
- Measurement Unit
- Evaluation Period
- Responsible Manager
- KPI Type
- Comments

Example KPIs:

- Sales Target Achievement
- Revenue
- Conversion Rate
- Customer Satisfaction
- Attendance
- Productivity
- Task Completion Rate
- Average Transaction Value

Supported calculation types:

1. Higher Is Better
2. Lower Is Better
3. Exact Target
4. Percentage-Based
5. Numeric

Calculation rules:

Higher Is Better:
Achievement = Actual / Target × 100

Lower Is Better:
Achievement = Target / Actual × 100

Exact Target:
Achievement = 100% when Actual equals Target. Otherwise calculate deviation from the target using a clearly defined tolerance configured for that KPI.

Percentage-Based:
Calculate achievement using the target and actual percentage values.

Numeric:
Calculate achievement according to the configured KPI direction.

Weighted KPI Score:

KPI Score = SUM(Individual KPI Achievement × KPI Weight)

Normalize KPI results to a 0–100 scale.

Prevent division by zero and handle missing values correctly.

Display:

- Target
- Actual
- Achievement %
- Weight %
- Weighted Contribution
- Performance Status

### 3.6 Competency Assessment

Create a competency library.

Professional Competencies:
- Professional Knowledge
- Product Knowledge
- Technical Skills
- Quality of Work
- Productivity

Behavioral Competencies:
- Communication
- Teamwork
- Responsibility
- Discipline
- Problem Solving
- Customer Orientation
- Adaptability

Leadership Competencies:
- Decision Making
- Leadership
- Strategic Thinking
- Conflict Management
- People Management

Each competency must contain:

- Competency Name
- Description
- Behavioral Indicators
- Required Level
- Actual Level
- Weight
- Evaluator Comments

Use a 1–5 assessment scale:

1 — Unsatisfactory
2 — Needs Improvement
3 — Meets Expectations
4 — Exceeds Expectations
5 — Outstanding

Convert the assessment scale into percentages:

1 = 20%
2 = 40%
3 = 60%
4 = 80%
5 = 100%

Allow HR to create custom competencies.

### 3.7 Skill Gap Analysis

This is a core module of the application.

The system must compare the required competency level for a position with the employee's actual competency level.

Formula:

Skill Gap = Required Competency Level - Actual Competency Level

Example:

Communication:
Required: 90%
Actual: 70%
Gap: 20 percentage points.

Product Knowledge:
Required: 100%
Actual: 85%
Gap: 15 percentage points.

Leadership:
Required: 80%
Actual: 45%
Gap: 35 percentage points.

Display:

- Required Competency Level (%)
- Actual Competency Level (%)
- Skill Gap (percentage points)
- Competency Weight (%)
- Gap Severity
- Development Priority

Gap severity:

- 0 pp: No Gap
- 1–10 pp: Low Gap
- 11–20 pp: Moderate Gap
- 21–30 pp: High Gap
- Above 30 pp: Critical Gap

Create a visual Skill Gap Dashboard.

Include:

- Average Competency Level.
- Average Required Competency Level.
- Total Competency Gaps.
- Critical Gaps.
- Competencies Meeting Expectations.
- Top 5 Development Priorities.

Allow filtering by employee, department, position, and evaluation period.

Do not treat an unassessed competency as zero. Display it as Not Assessed.

The system must calculate weighted competency results using assigned competency weights.

### 3.8 Performance Review

Implement a complete Performance Review workflow.

Stages:

1. HR creates an evaluation period.
2. HR and managers approve evaluation criteria.
3. Evaluators are assigned.
4. Employee completes Self-Assessment.
5. Manager completes Manager Assessment.
6. HR reviews the assessment.
7. Results are approved.
8. Employee can view final results.

Statuses:

- Draft
- Pending Self-Assessment
- Pending Manager Review
- Pending HR Review
- Returned for Revision
- Approved
- Completed

Functions:

- Save incomplete assessments.
- Return assessments for revision.
- Add comments.
- Record evaluation dates.
- Maintain assessment history.
- Record the author of each change.

### 3.9 Performance Score Calculation

Default scoring model:

- KPI Weight: 60%
- Competency Weight: 40%

These values must be configurable.

Formula:

Performance Score =
(KPI Score × KPI Weight) +
(Competency Score × Competency Weight)

Both components must be normalized to 0–100.

If one component is not assigned, calculate the score using the available component and its normalized weight.

If neither component is available, display Not Evaluated.

Example performance categories:

90–100: Outstanding
80–89.99: Exceeds Expectations
65–79.99: Meets Expectations
50–64.99: Needs Improvement
0–49.99: Unsatisfactory

Display:

- Overall Performance Score
- KPI Score
- Competency Score
- Performance Category
- Previous Period Score
- Performance Change

All calculations must use real application data.

### 3.10 Team and Department Performance

Calculate:

- Average Performance Score.
- Average KPI Score.
- Average Competency Score.
- Number of employees by performance category.
- Evaluation completion rate.
- Skill gap distribution.
- Performance trends.

Support:

- Arithmetic Average.
- Weighted Average.

The aggregation method must be configurable.

Compare employees using normalized scores rather than comparing raw KPI values across different positions.

### 3.11 Employee Performance Profile

Each employee must have a dedicated profile.

Display:

- Personal Information.
- Position.
- Department.
- Team.
- Direct Manager.
- Current Performance Score.
- KPI Results.
- Competency Results.
- Skill Gap Analysis.
- Self-Assessment.
- Manager Comments.
- Evaluation History.
- Performance Trend.
- Development Recommendations.

Use charts to display performance changes across evaluation periods.

### 3.12 Talent Management — 9-Box Matrix

Create a 9-Box Matrix based on:

- Performance
- Potential

Use three levels for each dimension:

- Low
- Medium
- High

Create nine categories.

Allow authorized evaluators to manually assign Potential levels.

Display employee names inside matrix cells.

Clicking a cell must show the list of employees in that category.

Allow filtering by department and evaluation period.

Maintain the history of changes.

AI-generated potential suggestions, if implemented, must remain advisory.

### 3.13 Development Plans

Create an Individual Development Plan module.

Functions:

- Create development goals.
- Identify competency gaps.
- Recommend training activities.
- Assign responsible managers.
- Set deadlines.
- Track completion.
- Monitor competency improvement.

Display:

- Development Goal
- Target Competency
- Current Level
- Target Level
- Progress %
- Responsible Manager
- Deadline
- Status

### 3.14 AI Performance Analytics

AI Analytics is an advanced module and is not mandatory for the initial MVP.

Prepare the architecture for future AI integration.

Potential features:

- Performance Trend Analysis.
- Competency Gap Analysis.
- Risk Detection.
- Development Recommendations.
- Department Performance Summaries.
- Natural Language Questions.

Example questions:

- Which department has the highest performance?
- Which employees demonstrate declining performance?
- What are the most common competency gaps?
- Which teams have the lowest KPI achievement?
- How has performance changed over the last three quarters?

AI must use only data the current user is authorized to access.

AI recommendations must include supporting metrics.

AI must never automatically change scores, employee statuses, KPI targets, or employment decisions.

If AI integration is not configured, display an informative demo state rather than pretending to generate real AI analysis.

### 3.15 Notifications

Create internal notifications for:

- New evaluation periods.
- Assigned assessments.
- Pending Self-Assessments.
- Pending Manager Assessments.
- Pending HR approvals.
- Completed reviews.
- Upcoming deadlines.

Notifications must be visible within the application.

### 3.16 Reports and Export

Report types:

1. Individual Performance Report.
2. Department Performance Report.
3. Team Performance Report.
4. KPI Achievement Report.
5. Competency Assessment Report.
6. Skill Gap Report.
7. Performance Trend Report.
8. Talent Analysis Report.

Support:

- CSV Export.
- Excel Export.
- PDF Export.
- Print.

Reports must respect active filters and user permissions.

---

## 4. NUMERICAL ACCURACY AND ANALYTICS

All analytical modules must display clear numerical results.

Use percentages, exact employee counts, and percentage-point differences.

Examples:

- KPI Achievement: 87.5%
- Competency Score: 76%
- Overall Performance: 82.4 / 100
- Evaluation Completion: 45 / 50 employees (90%)
- High Performers: 18 employees (36%)
- Low Performers: 7 employees (14%)
- Average Department Score: 81.6%
- Average Skill Gap: 23 percentage points

Distinguish between:

- Percentage (%)
- Percentage Points (pp)
- Absolute Number
- Score (0–100)

All averages must exclude missing or unassessed values.

Clearly display the denominator when showing percentages.

Use consistent rounding to one decimal place.

Every chart must be based on actual stored or calculated data.

---

## 5. DATABASE ARCHITECTURE

Use PostgreSQL through Supabase.

Create relational tables:

- users
- roles
- permissions
- employees
- departments
- teams
- positions
- kpi_templates
- employee_kpis
- competency_library
- position_competencies
- evaluation_periods
- performance_reviews
- kpi_results
- competency_results
- self_assessments
- manager_assessments
- development_plans
- development_goals
- talent_assessments
- notifications
- comments
- audit_logs

Use UUID primary keys.

Use foreign keys and appropriate indexes.

Store evaluation snapshots so historical results remain unchanged when employee positions or evaluation templates change.

Implement Supabase Row Level Security (RLS).

Never expose service-role keys in frontend code.

Create database migrations and seed scripts.

---

## 6. DEMONSTRATION DATA

Create a fictional retail organization named "Nova Retail Group".

Include at least 10 fictional employees.

Example departments:

- Retail Operations
- Sales
- Human Resources
- Finance

Example teams:

- Sales Team A
- Sales Team B
- Store Operations
- HR Team

Example employees:

1. Emma Wilson — Sales Representative — Sales
2. Daniel Carter — Store Manager — Retail Operations
3. Sophia Martinez — HR Specialist — Human Resources
4. James Anderson — Cashier — Sales
5. Olivia Brown — Department Manager — Retail Operations
6. Ethan Taylor — Junior Sales Representative — Sales
7. Isabella Davis — Sales Representative — Sales
8. Lucas Miller — HR Administrator — Human Resources
9. Amelia Johnson — Cashier — Sales
10. Noah Wilson — Team Leader — Retail Operations

Generate realistic but fictional:

- KPI targets.
- Actual KPI results.
- Competency assessments.
- Performance reviews.
- Skill gaps.
- Evaluation histories.
- Development plans.
- Department analytics.

Ensure all demo data is internally consistent.

The dashboard totals, employee profiles, team analytics, and charts must derive from the same dataset.

Seed data must be reproducible and must not create duplicates when executed again.

Clearly label the environment as DEMO.

---

## 7. UI/UX DESIGN

Create a premium enterprise SaaS dashboard.

Design direction:

- Clean professional interface.
- Modern HR analytics.
- White background in Light Mode.
- Dark Mode support.
- Red accent: #E4202E
- Orange accent: #FF7A1F
- Red-to-orange gradient for primary actions and selected elements.
- Montserrat typography.
- Rounded cards.
- Subtle shadows.
- Clean tables.
- Consistent spacing.
- Responsive layout.

Create a sidebar with:

1. Dashboard
2. Employees
3. Organization
4. KPI Management
5. Competency Library
6. Performance Reviews
7. Team Performance
8. Department Analytics
9. Skill Gap Analysis
10. Talent & 9-Box
11. Development Plans
12. AI Analytics
13. Reports
14. Notifications
15. Settings

UI requirements:

- Sidebar navigation.
- Top navigation bar.
- Search.
- User profile menu.
- Notification indicator.
- Breadcrumbs.
- Data tables with sorting.
- Searchable filters.
- Modal dialogs.
- Confirmation dialogs.
- Form validation.
- Loading states.
- Empty states.
- Error states.
- Toast notifications.

Provide Light and Dark themes.

Persist the selected theme.

All interface text must be in English.

Use consistent professional HR terminology.

The application must be fully responsive for desktop, tablet, and mobile.

---

## 8. TECHNOLOGY STACK

Use the following technologies:

### Frontend

- React
- TypeScript
- Vite
- Tailwind CSS
- Recharts
- Lucide React icons

### Backend and Database

- Supabase
- PostgreSQL
- Supabase Authentication
- Supabase Row Level Security

### Development Requirements

- Use reusable React components.
- Use TypeScript types and interfaces.
- Separate UI components, business logic, and data access.
- Create reusable hooks.
- Use a centralized Supabase client.
- Validate forms.
- Handle loading and error states.
- Avoid unnecessary dependencies.
- Keep the architecture modular.

### Deployment

Prepare the project for Vercel deployment.

Provide:

- README.md
- .env.example
- Supabase SQL migrations.
- Seed scripts.
- Installation instructions.
- Deployment instructions.

Use environment variables for all secret configuration.

Do not expose private API keys.

---

## 9. MVP SCOPE

The initial version must prioritize:

1. Authentication and demo access.
2. Role-based interface.
3. Employee Database.
4. Organizational Structure.
5. Position-Based Evaluation Models.
6. KPI Management.
7. Competency Library.
8. Skill Gap Analysis.
9. Evaluation Periods.
10. Self-Assessment.
11. Manager Assessment.
12. Automatic Performance Score Calculation.
13. Employee Performance Profiles.
14. Dashboard.
15. Team and Department Analytics.
16. Performance History.
17. CSV Export.

Advanced features such as AI Analytics, advanced Talent Management, and extensive Development Plans can be implemented in later phases.

However, the MVP must be functional, not a static mockup.

### Demo Access

Provide a convenient demonstration login or demo mode.

Include sample accounts for:

- HR Administrator
- HR Specialist
- Department Manager
- Team Leader
- Employee
- Top Management

Make it possible to explore the main modules without manually creating accounts.

Clearly distinguish demo access from production authentication.

---

## 10. ACCEPTANCE CRITERIA

The application is considered complete when:

1. The application launches successfully.
2. Users can access the demo environment.
3. Role-based views work correctly.
4. HR can add and edit employees.
5. Organizational structure can be managed.
6. Different evaluation models can be created for different positions.
7. KPI indicators can be configured.
8. Competencies can be configured.
9. KPI and competency weights are validated.
10. Employees can complete Self-Assessment.
11. Managers can complete Manager Assessment.
12. HR can review and approve evaluations.
13. Performance Scores are calculated automatically.
14. Skill Gaps are calculated correctly.
15. Skill Gap percentages and percentage-point differences are displayed.
16. Employee performance history is available.
17. Dashboard metrics reflect actual application data.
18. Filters update all relevant analytics.
19. Department and team comparisons work.
20. CSV export works.
21. The selected theme persists after refreshing.
22. Forms validate required fields.
23. Empty and missing data are handled correctly.
24. Unauthorized users cannot access restricted data.
25. Data persists in Supabase.
26. Historical evaluations are preserved.
27. The application works on mobile devices.
28. All primary buttons and actions work.
29. No fake AI analysis is displayed as real AI.
30. No automated employment decisions are made.

---

## 11. DEVELOPMENT INSTRUCTIONS FOR CLAUDE CODE

Before coding:

1. Read this entire SPEC.md.
2. Understand all business requirements.
3. Identify dependencies between modules.
4. Plan the database schema.
5. Create the project structure.
6. Explain any technical limitations before replacing required functionality.

Implementation rules:

- Build a complete working application.
- Do not create only a visual prototype.
- Implement real business logic.
- All forms must work.
- All buttons must perform meaningful actions.
- All charts must use actual application data.
- All calculations must be mathematically correct.
- Do not use random values to simulate analytics.
- Use fictional seed data.
- Implement proper validation.
- Implement role-based permissions.
- Protect sensitive information.
- Handle errors and empty states.
- Keep components reusable.
- Maintain a clean TypeScript architecture.

Prioritize the MVP modules before advanced features.

Do not leave important buttons non-functional.

Do not claim that an integration works unless it has been configured and tested.

Before finishing:

1. Run TypeScript checks.
2. Run the production build.
3. Test core user workflows.
4. Verify KPI calculations.
5. Verify competency calculations.
6. Verify Skill Gap calculations.
7. Verify dashboard aggregations.
8. Verify role permissions.
9. Verify Supabase database connectivity.
10. Fix all critical errors.

Create a README.md explaining:

- Project overview.
- Technologies.
- Installation.
- Environment configuration.
- Supabase setup.
- Database migrations.
- Demo access.
- Local development.
- Vercel deployment.

Create .env.example with required environment variable names but no real secrets.

Commit the completed work to the main branch.

Push the changes to the connected GitHub repository.

Provide a final implementation report describing:

- Completed modules.
- Database structure.
- Implemented calculations.
- Demo accounts.
- Testing results.
- Remaining limitations.

## FINAL PRODUCT VISION

The final product must be a modern, scalable Performance Management System that integrates:

- KPI Management
- Competency Assessment
- Performance Review
- Skill Gap Analysis
- Employee Performance Profiles
- Team and Department Analytics
- Talent Management
- Development Planing
- Performance Reporting

The application must demonstrate how an HR department can measure performance, identify competency gaps, monitor employee development, and make evidence-based decisions using accurate numerical data.
