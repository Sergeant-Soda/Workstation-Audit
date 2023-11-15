# Workstation-Audit
Workstation-Audit connects to a line-delimited text file of Windows workstations to retrieve specific domain and local configurations.

### REQUIREMENTS
The following requirements are required for this script's execution:
* PowerShell version 3 on the machine which will execute the script
    * The version of PowerShell installed can be discovered with the following command: `$PSVersionTable.PSVersion`.
* Adminstrative access to fully access all hosts
    * This is most commonly domain adminstrator.

### CONTACT
Please perform the following before contacting others for assistance:
1. For initial troubleshooting please see the `Troubleshooting` section below.

### USAGE
The following sections will explain Workstation-Audit usage:
##### Install Instructions
Please perform the following to install Workstation-Audit:
1. Extract the .zip to a folder titled `Workstation-Audit` on the Desktop.
2. Open a PowerShell command prompt running with administrative access to all devices
3. Run the following commands to change to the script's directory and import the script into the current PowerShell session:
```
cd $HOME\Desktop\Workstation-Audit
Import-Module .\Workstation-Audit.psd1
```

* The PowerShell module is now activated in the current PowerShell session. Once the terminal is closed it will not be accessible unless imported again.
* If you receive an error about not being able to execute scripts, use the following command to set the execution policy for this current PowerShell session only.

```
Set-ExecutionPolicy -Scope Process -ExecutionPolicy Unrestricted
```

##### Required Parameters
The following required parameters exist:
* `-WorkstationList`: A text file containing a single hostname or IP per line.

##### Optional Parameters
The following optional parameters exist:
* `-NoDATADIR`: Will not run PowerExporter sections such as UserRights, AccountPolicy, and AuditPolicy
* `-QuickScan`: Perform a quick version on the script only pulling a few specific registries and network information

##### Example
The following command is an example Workstation-Audit usage:
```
Start-WorkstationAudit -WorkstationList .\WorkstationList.txt -NoDATADIR
```

##### Removal Instructions
Please perform the following to remove Workstation-Audit:
1. Zip up the `Workstation-Audit` folder
2. Delete the `Workstation-Audit` folder

##### Troubleshooting
1. Validate that the correct path was used for the `-WorkstationList` and that the workstation list is one hostname per line with no commas or extra characters
2. Confirm PowerShell Version 3 or higher is used with `$PSVersionTable.PSVersion`
3. If issues continue, try using the `-NoDATADIR` flag; you will recieve less information, but the script will limit the utilized procedures.
4. If all else fails, try `-QuickScan` flag which eliminates all but a few key registry calls.
