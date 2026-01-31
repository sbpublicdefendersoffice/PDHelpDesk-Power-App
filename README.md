# PDHelpDesk-Power-App
This folder contains everything necessary to setup the PDHelpDesk for whatever reason.

There are 2 folders, one is .msapp file this is the Power App saved as a proprietary file type that the Power APP
Studio can read and import. The other is the Power App with everything extracted from it into Yaml files. With the
Yaml files, the entire folder will need to be repackaged with the Power Platform CLI (more on this later) into a
.msapp file

Inorder to completely restructure with the least amount of errors

1.Create the sharepoint site, remember the name you gave it
2.Create the sharepoint groups
3.Import the schemas one by one, create the document libraries accordingly (refer to the schema list in the folder)

Flows
4.Import each flow one by one refer to the flow list
  4a. Each flow was exported to be created as a new flow in a new environment
  4b. As a result new connections will need to be made when importing these
  4c. This is why it is important to create the sharepoint site first

Power App
5. Once the environment is setup import the app from the .msapp file


Troubleshooting
The Automate flows in the app might throw errors or have strange names follow the names or conventions when importing
 -You can recreate the flows with proper names later and removes these when you do and change the old flow to the new one
  -While this is extra work, there are quirks to using the Power Platform this is unfortunately one of them
This also applies to the sharepoint site and its lists
 -The CSV files have the headers at the end of the file

Future Back-ups

A good rule of thumb is to create a back up every 3 months or sooner

To begin in the Power App studio, select the application to edit.
From here you will hover over the save icon, there should be a small downward chevron to the bottom right
Expand it and you will see options, what we are interested is in Download A Copy
It can be named however you Like, but take note of what it is called

Download VSCode "Link to VSCode"
Setup VSCode however you like
Download the Power Platform CLI extension from the library (there is a note that the pack and unpack commands will be deprecated, another solution will be provided)
Ensure that your terminal is PAC enabled
"Give pac command to test"
After you have ensured that everything is working, navigate to the folder you will be working in to unpack the application
Take note of the path
Open a new terminal
You may now use this command to unpack the application
pac canvas unpack --msapp "C:\examplepathtofile\NameOfApp.msapp" --sources "C:\exampledestinationpath\NameOfApp"

The terminal will work, and the result will be the extracted contents in the destination folder provided

To repackage the application specify the output path and name, then provide the source folder
pac canvas pack --msapp "C:\exampleoutputpath\NewNameOfApp.msapp" --sources "C:\examplepathtosourcefolder\NameOfApp"
