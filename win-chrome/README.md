Role Name
=========

Ansible Role Wrapper for Google Chrome Install and Uninstall (PSADT v3) from Jason Berger

Role Variables
--------------

- `package_name`  
  Name of the software package and folder inside the software repository.  
  **Default:** `Notepad++`  
  **Used for:** Building `package_source_path` and detection/installation paths.

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
    - role: win-chrome
      vars:
        # Defines the action to perform for this software package: install, repair, or uninstall
        deployment_type: install
```

Get installation files
----------------------

To obtain the Google Chrome Enterprise installers, download the MSI packages from the official Google Chrome Enterprise download page
. Select the Stable Channel, choose MSI as the file type, and download both architecture variants. Download googlechromestandaloneenterprise.msi (32-bit) and googlechromestandaloneenterprise64.msi (64-bit). Place both installers in the following directory on the target system: win-chrome/files/Files. These MSI files can then be used for automated deployment via your installation or configuration management process.

License
-------

MIT

Author Information
------------------

Author: Philipp Ruland
