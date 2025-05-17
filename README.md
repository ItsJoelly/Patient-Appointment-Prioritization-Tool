# 🏥📊 Patient Appointment Prioritization Tool (Excel-based)

An intelligent urgency scoring system built in Excel to help NHS administrators prioritize patients for cancelled or available appointment slots. Designed to streamline scheduling based on real-world clinical and administrative factors.

---

### ✨ Project Overview

Manually managing patient reschedules and appointment slots is inefficient and prone to error. This project introduces a scoring system that combines:

🧠 Weighted patient factors (urgency, diagnostics, admin changes)
📅 Dynamic penalty for upcoming appointments
📈 Conditional formatting to highlight high-priority cases
📊 Test sheets to validate logic and edge cases

This Excel tool automates patient prioritization — helping scheduling teams make faster, more data-driven decisions.

---

### 👨‍⚕️ Key Features

**Scoring Logic Includes:**

* 🔴 Urgency level (Urgent vs Routine)
* ⏳ Days waited since referral
* 📆 Appointment offered and reschedule status
* 🧪 Diagnostic completion
* ❗ Penalty for short-term upcoming appointments

**Excel Enhancements:**

* 🎨 Conditional formatting with urgency-based color scales
* 📄 VLOOKUP + helper columns for clean weight management
* 🔍 Testing with yes/no matrix and dynamic date simulation
* 🧮 Robust formula with automatic 0-score for past dates

### 🧪 Testing Strategy

Two sheets were created to validate functionality:

**1. Feature Logic Testing ("Cancellation List 1.xlsx")**

* Tests every combination of:

  * Priority (Urgent/Routine)
  * Diagnostics done
  * Patient/Admin reschedules
  * Slot offered
* Ensures scores match expected logic

**2. Date-based Penalty Testing ("Cancellation List 2.xlsx")**

* Uses dynamic formulas like `=TODAY()+N` to simulate date proximity
* Validates penalty reduction as appointments move further into the future
* Ensures appointments in the past are scored `0`

---

### ⚙️ Formula Logic (Simplified)

```excel
=ROUNDUP(
  IF(AppointmentDate<TODAY(), 0,
  (
    PriorityWeight
    + WaitingTimeWeight
    + ...
    - Penalty (based on how soon appt is)
  )), 0)
```

---

### 🔧 Tools & Stack

* **Microsoft Excel**
* **Formulas Used**: `IF()`, `VLOOKUP()`, `MAX()`, `ROUNDUP()`, `Conditional Formatting`
* **Helper Columns**: For display-only scores, formatting targets, and calculations
* **Version Control**: Git & GitHub for tracking logic changes and test results
