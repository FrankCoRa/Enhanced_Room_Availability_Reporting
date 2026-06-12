# Room Availability Report Optimization

## Project Overview

Academic scheduling teams rely on room availability reports to identify available classroom space for course scheduling, event planning, and operational decision-making. While Coursedog provides a Room Availability Report, the exported report required significant manual review and offered limited usability for day-to-day scheduling activities.

This project enhances the standard Coursedog Room Availability Report through Python-based automation, transforming raw availability data into a structured, scheduler-friendly report that improves room visibility, navigation, and decision-making.

The solution was developed within a higher education scheduling environment to support more efficient classroom utilization and reduce manual effort during the scheduling process.

---

## Business Problem

### Background

Academic scheduling requires quickly identifying rooms that are available during standard instructional time blocks. The original Coursedog export provided room availability information but presented several operational challenges.

### Original Report Limitations

| Challenge | Impact |
|------------|----------|
| Raw availability ranges | Difficult to determine whether a room was available for a specific class period |
| Limited filtering capabilities | Increased manual review time |
| Large volume of room records | Reduced usability |
| Duplicate room records | Created unnecessary complexity |
| No direct alignment with academic meeting blocks | Required manual interpretation |
| Limited visibility into scheduling opportunities | Slower decision-making |

---

## Project Goals

The primary objectives of this project were to:

- Improve visibility of room availability
- Reduce manual scheduling effort
- Standardize room availability information
- Align availability with academic scheduling blocks
- Improve report readability and usability
- Create a repeatable automated workflow
- Support faster scheduling and room assignment decisions

---

# Google PACE Framework

---

# 🟦 Plan

## Business Need

Scheduling staff frequently needed to answer questions such as:

- Which rooms are available on Tuesday at 10:05 AM?
- Which classrooms can accommodate a new section?
- What rooms are available for special events?
- Which rooms should be considered during room reassignment?

Answering these questions often required manually reviewing large exports and interpreting availability windows.

The goal was to create a solution that would automatically convert raw room availability data into a more practical scheduling tool.

---

## Success Criteria

The solution should:

- Reduce manual review time
- Improve room availability visibility
- Support scheduling decision-making
- Produce a reusable report
- Maintain data accuracy
- Integrate easily into existing scheduling workflows

---

# 🟨 Analyze

## Review of the Original Report

The original report contained:

- Room identifiers
- Weekday availability
- Availability time ranges
- Building information
- Room characteristics

However, availability was stored as free-form time ranges, making it difficult to quickly determine whether a room was available during standard academic meeting periods.

Example:

```text
MT413 | Monday | 09:00AM - 05:00PM
```

A scheduler still needed to manually determine whether the room was available during:

- 8:30–9:50
- 10:05–11:25
- 11:40–1:00
- 1:15–2:35

and other institutional meeting blocks.

---

## Operational Challenges

### Manual Interpretation

Each room required manual comparison between:

- room availability
- course meeting times

### Large Dataset

The report contained hundreds of room entries across multiple campuses and weekdays.

### Data Quality Issues

The export included:

- duplicate room entries
- inconsistent formatting
- rooms hidden from scheduling

### Limited Decision Support

The report answered:

> "When is the room available?"

but not:

> "Can I schedule a class in this room during a standard meeting block?"

---

## User Needs

The scheduling team required:

- Faster room searches
- Easier room filtering
- Consistent room information
- Availability aligned to instructional periods
- Improved visibility of available classrooms

---

# 🟩 Construct

## Technical Solution

A Python-based data processing workflow was developed to automate room availability analysis and standardization.

The workflow transforms raw Coursedog exports into an enhanced availability matrix aligned with academic scheduling periods.

---

## Solution Architecture

```text
Coursedog Export
       │
       ▼
Data Cleaning
       │
       ▼
Room Validation
       │
       ▼
Availability Parsing
       │
       ▼
Academic Time Block Mapping
       │
       ▼
Availability Matrix Creation
       │
       ▼
Enhanced Room Availability Report
```

---

## Technologies Used

| Technology | Purpose |
|------------|----------|
| Python | Automation and processing |
| Pandas | Data transformation |
| Datetime | Time parsing and comparisons |
| CSV | Data input/output |

---

## Key Data Transformations

### Room Standardization

The script:

- standardizes room names
- removes duplicates
- filters only approved scheduling rooms

---

### Availability Parsing

Availability windows such as:

```text
09:00AM - 05:00PM
```

are converted into machine-readable time values.

This allows automated comparison against academic meeting blocks.

---

### Academic Time Block Generation

The solution creates standard scheduling blocks such as:

| Block | Time |
|---------|---------|
| S1 | 8:30 AM – 9:50 AM |
| S2 | 10:05 AM – 11:25 AM |
| S3 | 11:40 AM – 1:00 PM |
| S4 | 1:15 PM – 2:35 PM |
| S5 | 2:50 PM – 4:10 PM |
| S6 | 4:20 PM – 5:40 PM |

Additional extended instructional blocks are also evaluated.

---

### Availability Validation Logic

For each room and weekday combination, the system determines:

```text
Can the room fully support this academic time block?
```

The output becomes a simple True/False availability matrix.

Example:

| Room | Weekday | S1 | S2 | S3 |
|--------|---------|----|----|----|
| MT413 | Monday | True | True | False |

This format dramatically improves report usability.

---

## Key Features

### Automated Data Cleaning

- Removes duplicate room entries
- Standardizes room names
- Validates scheduling eligibility

### Availability Slot Optimization

- Converts availability windows into scheduling-friendly blocks
- Supports both short and long instructional periods

### Enhanced Reporting

- Improves report readability
- Reduces manual interpretation
- Simplifies room searches

### Scheduling Decision Support

- Identifies room availability instantly
- Supports scheduling and event planning activities

---

# 🟥 Execute

## Final Deliverable

The final output is an optimized room availability report that converts raw scheduling data into an actionable scheduling resource.

Output file:

```text
room_availability_slots.csv
```

---

## Results Achieved

### Operational Improvements

- Reduced manual room availability analysis
- Improved scheduling workflow efficiency
- Simplified room reassignment processes
- Increased visibility into available classroom inventory

### User Experience Improvements

- Easier navigation
- Better filtering opportunities
- Improved readability
- Faster room identification

### Data Quality Improvements

- Removed duplicate room entries
- Standardized room information
- Improved consistency across reports

---

## Business Impact

This solution enables scheduling teams to spend less time interpreting room availability reports and more time making informed scheduling decisions.

### Benefits

- Faster scheduling decisions
- Improved room utilization
- Reduced manual effort
- Increased operational efficiency
- Better support for course scheduling and event planning

---

# Future Enhancements

Potential future improvements include:

### Interactive Dashboard

Develop a dashboard using:

- Plotly
- Dash
- Power BI
- Tableau

### Real-Time Availability

Connect directly to scheduling data sources for real-time room availability updates.

### Advanced Search Features

Add:

- campus filters
- room capacity filters
- room feature filters

### Room Recommendation Engine

Recommend optimal rooms based on:

- availability
- capacity
- location
- room characteristics

---

# Skills Demonstrated

This project demonstrates experience in:

### Data Analytics

- Data cleaning
- Data transformation
- Process analysis
- Workflow optimization

### Python Development

- Automation scripting
- Time-based logic
- Data processing
- Report generation

### Business Analysis

- Problem identification
- Process improvement
- Operational efficiency
- Stakeholder-focused solutions

### Higher Education Operations

- Academic scheduling
- Room utilization
- Resource planning
- Scheduling optimization

---

# Conclusion

The Room Availability Report Optimization project demonstrates how Python automation and data analytics can improve operational workflows in higher education. By transforming a raw scheduling export into a structured decision-support tool, the solution reduces manual effort, improves room visibility, and enhances the overall scheduling process.

This project highlights the intersection of data analytics, automation, and business process improvement to solve a real-world operational challenge.
