# PDHelpDesk-Power-App
This repository provides both the .msapp file and an extract version of the `.msapp` file.
---
# Power App Deployment & Restoration Guide

This guide outlines the process for restructuring and deploying the application into a new environment with minimal errors.

---

## 🚀 Step-by-Step Installation

### 1. SharePoint Environment Setup
> **Note:** It is critical to create the SharePoint site first to ensure connections are ready for the flows.

1.  **Create the SharePoint Site:** Remember the exact name you gave it.
2.  **Create SharePoint Groups:** Set up groups as required for app permissions.
3.  **Import Schemas:** Create Document Libraries one by one. Refer to the schema list in the project folder to ensure libraries are created accordingly.

### 2. Power Automate (Flows)
1.  **Import Flows:** Import each flow one by one, referring to the provided flow list.
2.  **New Environment Settings:** Each flow was exported to be created as a **new flow** in a new environment.
3.  **Connections:** New connections will need to be established during the import process. 

### 3. Power App Restoration
1.  Once the environment (SharePoint and Flows) is fully set up, import the application using the `.msapp` file.

---

## 🛠️ Troubleshooting & Quirks
* **Flow Names:** Automated flows in the app might throw errors or show strange names (GUIDs). Follow the established naming conventions during import.
* **Recreating Flows:** You can recreate flows with proper names later, swap them within the app, and then remove the old versions. While this is extra work, it helps resolve common Power Platform quirks.
* **SharePoint Lists:** Be aware that the provided CSV files for data migration contain the **headers at the end of the file**.

---

## 💾 Future Backups
A good rule of thumb is to create a backup every **3 months** or sooner.

### How to Download a Copy
1.  In Power Apps Studio, select the application to edit.
2.  Hover over the **Save** icon in the top right.
3.  Click the small **downward chevron (v)** at the bottom right of the icon.
4.  Select **Download a Copy**. You can name it whatever you like, but keep track of the filename.

---

## 💻 Technical Setup (VS Code & PAC CLI)

1.  **Download VS Code:** [Official Download Link](https://code.visualstudio.com/)
2.  **Install Extension:** Download the **Power Platform CLI** extension from the VS Code Marketplace.
3.  **Note on Deprecation:** There is a known note that `pack` and `unpack` commands may be deprecated; an updated solution will be provided when necessary.
4.  **Verify PAC:** Ensure your terminal is PAC-enabled by running:
    ```powershell
    pac
    ```
5.  **Unpack the Application:**
    Navigate to your working folder, take note of your file paths, and run the following command in a new terminal:
    ```powershell
    pac canvas unpack --msapp "C:\path\to\your\App Name.msapp" --sources "C:\destination\path\AppFolder"
    ```
6. **Repack the Application**
    Navigate to your working folder, and remember the paths, in a new terminal run the following:
    ```powershell
    pac canvas pack --msapp "C:\exampleoutputpath\NewNameOfApp.msapp" --sources "C:\examplepathtosourcefolder\NameOfApp"
    ```


---
## Alternative Solution
Provided is a link to an older version of the microsoft power apps tooling follow that guide to achieve a the same results, this action might be necessary because we might not be able to use the built-in Git Integration.
https://github.com/MSYuey/PowerApps-Language-Tooling
