# EventFlow Data Architecture

This document defines the data schemas, state management plan, and data 
transformation logic for the EventFlow application.

## 1. Data Schemas

### Session Schema

A `Session` object represents a single event talk or workshop. Its structure 
is as follows:

```json
{
  "id": 1,
  "title": "Introduction to React Hooks",
  "speaker": "Jane Doe",
  "description": "A deep dive into the power and flexibility of React Hooks.",
  "startTime": "2023-10-26T09:00:00Z",
  "endTime": "2023-10-26T10:00:00Z",
  "attendees": [
    {
      "id": 101,
      "name": "Alice Johnson",
      "checkInTime": "2023-10-26T08:55:00Z"
    }
  ]
}
```
### Attendee Schema
An Attendee object represents a single person checked into a session.
```json
{
  "id": 101,
  "name": "Alice Johnson",
  "checkInTime": "2023-10-26T08:55:00Z"
}
```
## 2. State Management Plan
The application will follow a centralized state management pattern. 
The "single source of truth" for all core application data will reside in 
the state of the top-level App.js component.

This state will be responsible for tracking three key pieces of information:

sessions: The complete, unfiltered array of all Session objects loaded into 
the application.
filters: An object representing the currently active filter criteria. 
This object will have the following shape:

```json
{
  "speaker": "all",
  "date": "",
  "searchTerm": ""
}
```

view: A string that determines which main view is currently rendered. 
The possible values are 'dashboard' or 'list'.

This centralized structure ensures a predictable, unidirectional data flow 
throughout the application.

## 3. Data Transformations
Raw session data must be processed to derive analytics for the dashboard. 
These calculations will take the sessions array as input and produce 
formatted data as output.

### Attendance Tracking Flow
Individual Session Attendance: For any given session object, the attendance 
count is calculated by getting the length of its attendees array 
(session.attendees.length).

### Analytics Calculations
Total Attendance: The sum of session.attendees.length for all currently 
filtered sessions.
Average Attendance: The calculated Total Attendance divided by the number 
of currently filtered sessions.
Session Popularity (for Bar Chart):
Input: An array of Session objects.
Transformation Logic:
Create a new array by mapping over the input sessions.
For each session, return a new object with the shape { name: session.title, 
attendance: session.attendees.length }.
Output: A data structure like [{ name: 'Intro to React', attendance: 85 }, 
{ name: 'Advanced CSS', attendance: 62 }]. This output is ready to be passed 
directly to the AttendanceChart component.
Attendance Over Time (for Line Chart):
Input: An array of Session objects.
Transformation Logic:
Group sessions by their start date.
For each date, sum the attendance of all sessions on that day.
Create an array of objects with the shape { date: '2023-10-26', totalAttendance: 350 }.
Output: A data structure like [{ date: '2023-10-26', totalAttendance: 350 }, 
date: '2023-10-27', totalAttendance: 410 }].

## 4. Integration Verification.
This data architecture supports the following connections:

### PLAN.md Integration
- Data schemas support the core features identified in PLAN.md
- State management aligns with the component hierarchy from PLAN.md
- Transformation logic enables the analytics requirements from PLAN.md

### COMPONENTS.md Integration
- Session and Attendee schemas provide data for all component props
- State structure matches App component specifications
- Transformation outputs match the data types expected by child components

### Implementation Readiness
- All component props from COMPONENTS.md have corresponding data sources
- State management pattern is clearly defined for Module 2 implementation
- Analytics calculations are documented for visualization components