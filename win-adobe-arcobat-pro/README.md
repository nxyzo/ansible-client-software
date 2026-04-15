Role Name
=========

Ansible Role Wrapper for Adobe Reader Install and Uninstall (PSADT v4) from Jason Berger

Role Variables
--------------


- `package_name`  
  Name of the software package and folder inside the software repository.  
  **Default:** `Notepad++`  
  **Used for:** Building `package_source_path` and detection/installation paths.

- `latest_version`
  The latest software release version.
  **Used for:** Building detection script.

- `software_deployment_root`  
  Root folder of the local software deployment structure on the target host.  
  **Default:** `C:\SWSETUP\softwareDeployment`  
  **Used for:** Building `software_repository_path`.

- `software_repository_path`  
  Path to the local software repository that contains all package folders.  
  **Default:** `{{ software_deployment_root }}\\ansibleRepository`  
  **Used for:** Building `package_source_path`. Normally not overridden unless your layout differs.

- `package_source_path`  
  Path to the source folder of the current software package on the target host.  
  **Default:** `{{ software_repository_path }}\\{{ package_name }}`  
  **Note:** This is a derived variable and usually not set directly; it is used by tasks to locate scripts and installers.

- `deployment_type`  
  Defines the action to perform for this software package. Typical values are `install`, `repair`, or `uninstall`.  
  **Default:** `install`  
  **Used for:** Controlling which deployment path is executed inside the role (e.g. installation vs. uninstallation logic).

Example Playbook
----------------

```yml
- hosts: localhost
  remote_user: root
  roles:
    - role: win-adobereader
      vars:
        # Defines the action to perform for this software package: install, repair, or uninstall
        deployment_type: install
```

Get installation files
----------------------

To obtain the Adobe Acrobat installer, download the installation package from the following URL:  
https://trials.adobe.com/AdobeProducts/APRO/Acrobat_HelpX/win32/Acrobat_DC_Web_x64_WWMUI.zip

After downloading, extract the contents of the ZIP file. And place the Files in: win-adobereader/files/Files

Ensure that AcroRead.mst remains in the folder. This is the Config file for Adobe Reader. It disables auto updates. 

Once extracted, the **Files** directory should contain a structure similar to the following:

- Transforms  
- ABCPY.INI  
- AcrobatDCx64Updxxxxxxxxxx.msp  
- AcroPro.msi  
- AlfSdPack.cab  
- Core.cab  
- Extras.cab  
- Intermediate.cab  
- Languages.cab  
- Optional.cab  
- setup.exe  
- setup.ini  
- WindowsInstaller-KB893803-v2-x86.exe  

The deployment process will locate and execute the required installer files directly from this path during installation.


License
-------

MIT

Author Information
------------------

Author: Philipp Ruland
