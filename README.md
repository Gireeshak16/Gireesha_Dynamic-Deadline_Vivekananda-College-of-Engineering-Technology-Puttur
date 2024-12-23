

---

# Dynamic Deadline Automation with Asana API

## Overview

This project automates task due date assignment and management in an Asana project based on task priority and section changes. Developed for **QScript Software Pvt Ltd**, it adheres to the task requirements and avoids third-party apps like Zapier while leveraging Asana's REST API for automation.

## Features

1. **Automated Due Date Assignment**:
   - Tasks are automatically assigned due dates based on their priority:
     - **Low Priority**: 14 days from the current date.
     - **Mid Priority**: 7 days from the current date.
     - **High Priority**: 2 days from the current date.

2. **Dynamic Due Date Extension**:
   - When a **High-priority task** is moved to the **In Progress** section:
     - The due dates of all other tasks in the same section are extended by **2 days**.

3. **Avoiding Redundant Extensions**:
   - Ensures that due date extensions are applied only once per status change event.

---

## Prerequisites

Before using this script, ensure the following:

1. **Asana Setup**:
   - Familiarize yourself with Asana terminology. Refer to the provided *Introduction to Asana* document.
   - Ensure your Asana project includes tasks and a section named **"In Progress"**.

2. **API Access**:
   - Generate a personal access token from your Asana account:
     1. Navigate to [Asana Personal Access Tokens](https://app.asana.com/0/120000000000000/120000000000000).
     2. Create a token and copy it for use in the script.

3. **Python Environment**:
   - Python 3.x must be installed on your system.
   - Install the required dependencies using `pip install requests`.

---

## Installation

### Step 1: Clone the Repository

```bash
git clone https://github.com/STUDENTNAME_TASKNAME_COLLEGENAME.git
cd STUDENTNAME_TASKNAME_COLLEGENAME
```

### Step 2: Install Dependencies

```bash
pip install requests
```

---

## Configuration

1. Open the script (`asana.py`) and update the following placeholders:
   - Replace `"your_asana_token_here"` with your **Asana Personal Access Token**.
   - Replace `"your_project_id_here"` with your **Asana Project ID**.

   ```python
   ASANA_TOKEN = "your_asana_token_here"
   ASANA_PROJECT_ID = "your_project_id_here"
   ```

2. Ensure that the section name **"In Progress"** matches the name in your Asana project.

---

## Running the Script

1. **Execute the Script**:

   ```bash
   python asana.py
   ```

2. **What Happens**:
   - The script fetches all tasks in the specified Asana project.
   - Assigns due dates automatically based on task priority.
   - Extends due dates of tasks in the **"In Progress"** section when a **High-priority task** is moved there.

---

## Example Output

```plaintext
Starting the script...
Processing task: Design Prototype (ID: 12345)
Priority for task Design Prototype: high
Due date for task 12345 set to 2024-11-27
Processing task: Backend Integration (ID: 67890)
Priority for task Backend Integration: low
Due date for task 67890 set to 2024-12-10
```

---

## Working Explanation

The script achieves dynamic deadline management using the following:

1. **REST API Integration**:
   - It fetches tasks and their details using the Asana API.
   - Due dates are assigned using the `PUT` endpoint for updating tasks.

2. **Priority Mapping**:
   - The `calculate_due_date` function maps task priority to due date intervals.

3. **Dynamic Adjustments**:
   - Tasks in the **"In Progress"** section are updated recursively to extend their deadlines when a high-priority task is moved there.

### Challenges and Solutions

- **Custom Fields Fetching**:
  - Ensuring that task priorities were extracted correctly from custom fields required precise field-name matching.
- **Error Handling**:
  - Added robust error handling for API responses to prevent crashes during runtime.
- **Redundant Extensions**:
  - Implemented checks to avoid duplicate due date extensions for tasks already adjusted.

---

## Demonstration

1. **Screen Recording**:
   - A demonstration video showcasing the script in action will be provided, showing:
     - Tasks being fetched.
     - Due dates being assigned.
     - Dynamic adjustments based on task movement.

2. **Real-Time Scenario**:
   - During the evaluation, additional scenarios can be demonstrated to showcase adaptability.

---

## Submission Instructions

1. **GitHub Repository**:
   - Push the code to a private GitHub repository following this naming convention:
     `STUDENTNAME_TASKNAME_COLLEGENAME`
   - Grant access to `gowdahmhrishikesh@gmail.com` under **Settings > Collaborators**.

2. **ReadMe File**:
   - Include this `README.md` file in the repository for ease of understanding.

3. **Screen Recording**:
   - Attach a screen recording demonstrating the project.

---

## Conclusion

This project successfully automates dynamic due date management in Asana, ensuring streamlined task prioritization and deadline adjustments. It avoids redundant extensions and adheres to the defined requirements.

--- 
