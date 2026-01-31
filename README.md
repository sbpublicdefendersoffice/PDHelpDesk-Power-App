# PDHelpDesk-Power-App
Power App Deployment & Restoration Guide
This guide outlines the process for restructuring and deploying the application into a new environment with minimal errors.

📋 Prerequisites
Before starting, ensure you have the following tools installed and configured:

Visual Studio Code: Download here

Power Platform CLI Extension: Available in the VS Code Marketplace.

PAC CLI Verification: Open your terminal and run the following command to ensure the CLI is active:

PowerShell
pac
🚀 Step-by-Step Installation
1. SharePoint Environment Setup
Create the SharePoint Site: Note the exact name used.

Create SharePoint Groups: Ensure permissions align with the previous environment.

Import Schemas: Create Document Libraries one by one according to the schema list provided in the /schemas folder.

2. Power Automate (Flows)
Import Flows: Import each flow individually according to the flow list.

Connections: Since flows are exported as "Create as New," you must manually establish new connections during the import process.

Note: This is why the SharePoint site must be created first—so the connections have a destination to point to.

3. Power App Restoration
Once the backend and flows are ready, import the application using the .msapp file located in this repository.

🛠️ Troubleshooting & Quirks
Flow Naming: Flows may appear with strange names or GUIDs after import. Follow the naming conventions provided in the documentation.

Workaround: You can recreate flows with proper names later, swap them in the app, and delete the "quirky" versions.

SharePoint Lists: Note that the provided CSV files for data migration have headers located at the end of the file.

Platform Quirks: Power Platform can be temperamental during environment migrations; manual reconnection is often required.

💾 Backup Procedures
Frequency: It is a best practice to create a full backup every 3 months or after any major milestone.

How to Download a Local Copy
Open the Power Apps Studio and edit your application.

Locate the Save icon in the top right.

Click the downward chevron (v) next to the icon.

Select Download a copy.

How to Unpack for Version Control
To see the source code (YAML) and track changes in Git, use the Power Platform CLI:

Open a terminal in your project directory.

Run the unpack command (using quotes for paths with spaces):

PowerShell
pac canvas unpack --msapp "C:\path\to\App Name.msapp" --sources "C:\destination\Folder Name"
[!WARNING] The pack and unpack commands may be deprecated in future CLI versions. An updated solution will be provided in this README when the official transition occurs.
