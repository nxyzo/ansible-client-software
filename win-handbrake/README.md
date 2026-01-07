Role Name
=========

Ansible Role Wrapper for Handbrake Install and Uninstall (PSADT v4) from Jason Berger

Role Variables
--------------

- `package_name`  
  Name of the software package and folder inside the software repository.  
  **Default:** `Handbrake`  
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
    - role: win-handbrake
      vars:
        # Defines the action to perform for this software package: install, repair, or uninstall
        deployment_type: install
```

Get installation files
----------------------

To obtain the HandBrake installer, download the latest .exe file from the official HandBrake website
. Place the HandBrake-x.y.z-x86_64-Win_GUI.exe file in the win-handbrake/files/Files directory. The deployment role will locate and execute the installer from this path during the installation process.

To obtain the .NET Desktop Runtime installer, download the latest .exe file from the official .NET website
. Place the windowsdesktop-runtime-8.0.x-win-x64.exe file in the win-handbrake/files/Files directory. The deployment role will locate and execute the installer from this path during the installation process.

License
-------

MIT

Author Information
------------------

Author: Philipp Ruland
