# ACME Dispatcher — UiPath REFramework

A UiPath RPA project that automates the extraction, filtering, and queueing of work items from the ACME web application using the Robotic Enterprise Framework (REFramework).

## Overview

This project implements the **Dispatcher component** of an RPA workflow. It collects work items from the ACME website, filters records based on their type, and uploads the eligible transactions to a UiPath Orchestrator queue for downstream processing.

The project follows the REFramework structure to organize initialization, transaction processing, exception handling, and application cleanup.

## Key Features

* **Web Automation:** Launches the browser, logs into the ACME application, and navigates to the Work Items section.
* **Data Extraction:** Retrieves work-item records from the website.
* **Data Filtering:** Selects work items with type `WI5`.
* **Queue Integration:** Uploads filtered transactions to a UiPath Orchestrator queue using bulk queue operations.
* **Secure Credential Retrieval:** Retrieves login credentials from a credential asset in Orchestrator instead of hardcoding passwords.
* **Configuration Management:** Uses a configuration workbook to manage application settings, asset references, queue information, and delay values.
* **REFramework Structure:** Organizes the automation into reusable workflows and framework components.

## Workflow Overview

1. **Initialize:** Load configuration settings and prepare the automation environment.
2. **Launch and Login:** Open the ACME website and retrieve the required credentials from Orchestrator.
3. **Extract Work Items:** Navigate to the Work Items page and collect the available records.
4. **Filter Transactions:** Identify work items matching the `WI5` type.
5. **Upload to Queue:** Add the filtered transactions to the designated Orchestrator queue.
6. **Close Applications:** Complete the application cleanup process.

## Project Structure

```text
ACME Dispatcher REFramework/
├── Chrome/
│   ├── Chrome_ACMEWebPage_Launch.xaml
│   ├── Chrome_ACMEWebPage_Login.xaml
│   ├── Chrome_ACMEWebPage_ClickWorkItems.xaml
│   ├── Chrome_ACMEWebPage_ExtractWorkItems.xaml
│   ├── Chrome_ACMEWebPage_FilterWorkItems.xaml
│   ├── Chrome_ACMEWebPage_Logout.xaml
│   └── Chrome_Orchestrator_BulkQueue.xaml
├── Framework/
│   ├── InitAllApplications.xaml
│   ├── InitAllSettings.xaml
│   ├── GetTransactionData.xaml
│   ├── Process.xaml
│   ├── SetTransactionStatus.xaml
│   └── ...
├── Tests/
│   └── REFramework test workflows
├── Main.xaml
├── project.json
├── project.uiproj
└── README.md
```

## Technologies and Tools

* UiPath Studio
* UiPath REFramework
* UiPath Orchestrator
* UiPath Queues and Credential Assets
* Web Automation
* Excel-based Configuration

## Prerequisites

To configure and run this project, you need:

* UiPath Studio with compatible project dependencies.
* Access to the ACME test application.
* A UiPath Orchestrator folder with the required credential asset and queue.
* A locally configured `Data/Config.xlsx` workbook containing the settings expected by the workflows.

The configuration workbook is intentionally excluded from this repository. Configure the required asset names, queue name, and other settings in your local environment before execution.

## Security Considerations

* Credentials are retrieved from UiPath Orchestrator rather than stored as hardcoded passwords in the login workflow.
* The configuration workbook is excluded from version control.
* Before sharing or publishing the project, review workflow files and screenshots for credentials, tokens, personal information, or other sensitive data.

## Project Goal

This project demonstrates practical RPA development skills, including web automation, structured data extraction, record filtering, reusable workflow design, Orchestrator integration, and configuration management within the REFramework architecture.
