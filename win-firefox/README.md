Role Name
=========

Ansible Role Wrapper for Firefox Install and Uninstall (PSADT v4) from Jason Berger

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
    - role: win-firefox
      vars:
        # Defines the action to perform for this software package: install, repair, or uninstall
        deployment_type: install
```

Get installation files
----------------------

To obtain the Mozilla Firefox installer, navigate to the official Firefox download page:  
https://www.mozilla.org/en-US/firefox/all/

Download the installer in the required format and architecture, and copy it to the corresponding directory:

- Download and copy the **32-bit EXE** installer to:  
  `C:\Temp\Firefox\Files\x86`

- Download and copy the **64-bit EXE** installer to:  
  `C:\Temp\Firefox\Files\x64`

**Alternatively:**

- Download and copy the **32-bit MSI** installer to:  
  `C:\Temp\Firefox\Files\x86`

- Download and copy the **64-bit MSI** installer to:  
  `C:\Temp\Firefox\Files\x64`

The deployment process will locate and execute the appropriate installer from these paths during installation.

License
-------

MIT

Author Information
------------------

Author: Philipp Ruland
