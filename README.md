# Generate Yearly Report for Vendor

## Introduction
This project automates the process of generating a yearly report for vendors using UiPath RPA technology. The process is designed to speed up report processing, reduce manual intervention, and enhance the overall performance of the Finance and Accounting department at ACME Systems Inc.

## Purpose and Objectives
- **Purpose:**  
  Automate the manual process of downloading monthly reports, consolidating them into a yearly report Excel file, and uploading the report to the system.
- **Objectives:**  
  - Deliver faster processing by automating repetitive tasks.  
  - Reduce the duration of time-consuming manual activities.  
  - Improve reliability and performance within the Finance and Accounting department.

## Process Overview
The automated process (WI4) involves the following high-level steps:
1. **System Access:**  
   - Open the ACME System 1 web application.  
   - Log in using valid credentials (email and password).

2. **Work Items Retrieval:**  
   - Navigate to the Dashboard to view available work items.  
   - Select an activity of type WI4.

3. **Report Generation:**  
   - Retrieve the Vendor Tax ID from the activity’s details page.
   - Access the “Download Monthly Report” section to download all monthly reports for the previous year.
   - Merge the downloaded monthly reports into a single Excel file named in the format:  
     `Yearly-Report-[Year]-[Tax ID].xlsx`.

4. **Report Upload:**  
   - Navigate to the “Upload Yearly Report” section.  
   - Provide the Vendor Tax ID, select the correct year, and upload the generated Excel file.
   - Capture the unique Upload ID returned by the system.

5. **Work Item Update:**  
   - Return to the Work Item details and update the task status to "Completed" with a comment noting the Upload ID.

## Detailed Process Flow
1. **Login and Navigation:**  
   - **Step 1.1:** Open the ACME System 1 web application.  
   - **Step 1.2:** Log in with the required credentials.  
   - **Step 1.3:** Access the Dashboard to choose a specific menu item.
2. **Processing WI4 Activities:**  
   - **Step 1.4:** View the list of work items.  
   - **Step 1.5:** For each WI4 activity, execute the following:
     - **1.5.A:** Open the details page to retrieve the Vendor Tax ID.
     - **1.5.B:** Access the Download Monthly Report section.
     - **1.5.C:** Enter the Vendor Tax ID and download the monthly reports for the previous year.
     - **1.5.D:** Merge the monthly reports into one Excel file named `Yearly-Report-[Year]-[Tax ID].xlsx`.
     - **1.5.E:** Upload the consolidated report in the Upload Yearly Report section.
     - **1.5.F:** Capture and store the returned unique Upload ID.
     - **1.5.G:** Update the Work Item by marking it as "Completed" and including the Upload ID in the comments.
     - **1.5.H:** Move on to the next WI4 activity.

## Exception and Error Handling
The process includes robust exception and error handling mechanisms:
- **Login Failures:**  
  If an incorrect email or password is provided, an exception is handled and a notification is sent to `exceptions@acme-test.com`.
- **Missing Work Items:**  
  If no WI4 tasks are available, the process halts.
- **Application Issues:**  
  For scenarios like an unresponsive web application or pages not loading, the robot retries the action a predetermined number of times before closing and restarting the application.
- **Unhandled Exceptions:**  
  Any unexpected error triggers an email alert, including the original error message and a screenshot.

## System and Environment Details
- **Applications Involved:**  
  - **ACME System 1:** Web application accessed via a web browser.
  - **Microsoft Excel:** Used to merge monthly reports into the yearly report.
- **Environment:**  
  The development and testing environments are exact replicas of the production environment to ensure consistency.
- **Credentials Management:**  
  Use Windows Credential Manager or UiPath Orchestrator Assets to securely store and manage login details.

## Development Details
- **Framework:**  
  The project is built using UiPath’s REFramework, which provides a robust structure for configuration management, exception handling, and integration with Orchestrator queues.
- **Configuration:**  
  All key configurations, including Queue names and credentials, are maintained in the `config.xlsx` file.
- **Deployment:**  
  The project is deployed as an unattended process via UiPath Orchestrator, with separate Dispatcher and Performer components (if needed) to manage work item distribution and processing.

## Future Enhancements
- Integration of a Dispatcher component to populate work item queues if additional data sources or more complex distribution of tasks is required.
- Further refinement of exception handling and error logging mechanisms to enhance process robustness.

---

This README serves as a high-level overview and reference for the "Generate Yearly Report for Vendor" automation project. It is intended to be updated and expanded as the project evolves.
