# EventFlow Component Specifications

This document defines the responsibility and props (the "contract") for each 
component in the EventFlow application.

## App Component

-   **Responsibility:** The root component of the application. It fetches data, 
manages all primary application state (sessions, filters, view), and renders 
the appropriate child components (`Dashboard` or `SessionList`). It acts as 
the central orchestrator.

-   **State Management:**
    -   `sessions`: The full array of session data objects.
    -   `filters`: An object representing the currently active filter criteria.
    -   `view`: A string ('dashboard' or 'list') to control which main
     component is visible.
-   **Props:** None.

---

## Dashboard Component

-   **Responsibility:** A container component that lays out all the analytics
and visualization components. It receives filtered data from `App` and passes
processed data down to its children.

-   **Props:**

| Prop Name  | Type    | Description                                       |
| ---------- | ------- | ------------------------------------------------- |
| `sessions` | `Array` | The array of session data to be visualized. |

---

### MetricsDisplay Component

-   **Responsibility:** A presentational component that displays key 
aggregate numbers (e.g., Total Attendance, Average Rating).

-   **Props:**

| Prop Name     | Type     | Description                                     |
| ------------- | -------- | ----------------------------------------------- |
| `metricsData` | `Object` | An object containing the calculated metric values. |

---

### AttendanceChart Component

-   **Responsibility:** A presentational component that renders a bar or line
chart using a library like `recharts`.

-   **Props:**

| Prop Name     | Type    | Description                                    |
| ------------- | ------- | -----------------------------------------------|
| `chartData`   | `Array` | An array of data objects specifically formatted 
for the chart library. |

---

## SessionList Component

-   **Responsibility:** A container component that displays a list of
`SessionItem` components based on the filtered data it receives from `App`. 
It also renders the `FilterControls`.

-   **Props:**

| Prop Name  | Type    | Description                                  |
| ---------- | ------- | -------------------------------------------- |
| `sessions` | `Array` | The filtered array of session data to display. |

---

### FilterControls Component

-   **Responsibility:** A presentational component that renders the UI for 
filtering (e.g., dropdowns, text inputs). It does not manage the filter state
itself but communicates user actions up to the `App` component.

-   **Props:**

| Prop Name         | Type       | Description                            |
| ----------------- | ---------- | ---------------------------------------|
| `filters`         | `Object`   | The current filter object, used to set 
the value of the input controls.     |
| `onFilterChange`  | `Function` | A callback function passed from `App` 
that is triggered when a user changes a filter. |

---

### SessionItem Component

-   **Responsibility:** A presentational component that displays the 
details for a single event session.

-   **Props:**

| Prop Name | Type     | Description                                |
| --------- | -------- | ------------------------------------------ |
| `session` | `Object` | A single session object containing all its details. |

---

## ErrorBoundary Component

-   **Responsibility:** A special component that catches JavaScript errors 
in its child component tree, logs those errors, and displays a fallback UI. 
This prevents the entire application from crashing.

-   **State Management:**
    -   `hasError`: A boolean that becomes `true` when an error is caught.
-   **Props:**

| Prop Name  | Type   | Description                                  |
| ---------- | ------ | ---------------------------------------------|
| `children` | `Node` | The child components that this boundary is 
protecting (prop from React). |