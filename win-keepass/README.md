Role Name
=========

Ansible Role Wrapper for KeePass Install and Uninstall (PSADT v3) from Jason Berger

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
    - role: win-keepass
      vars:
        # Defines the action to perform for this software package: install, repair, or uninstall
        deployment_type: install
```

Get installation files
----------------------

To obtain **KeePass**, download the latest **EXE installer** from the [official KeePass download page](https://keepass.info/download.html). Download the installer named: **KeePass Password Safe** and the installation file name: **KeePass-x.xx-Setup.exe**. Place the installer in the PSAppDeployToolkit directory on your Ansible host (for example, `win-keepass/files/Files`).

To enforce the update settings, create a KeePass configuration file and store it alongside your deployment files. Create a new file named **KeePass.config.enforced.xml** with the following content and save it to `win-keepass/files/SupportFiles`:

```xml
<?xml version="1.0" encoding="utf-8"?>
<Configuration xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:xsd="http://www.w3.org/2001/XMLSchema">
	<Application>
		<Start>
			<CheckForUpdate>false</CheckForUpdate>
			<CheckForUpdateConfigured>true</CheckForUpdateConfigured>
		</Start>
	</Application>
</Configuration>
```

To add additional KeePass languages, download the desired language files from the [official KeePass translations page](https://keepass.info/translations.html) and place them in `win-keepass/files/SupportFiles`.


License
-------

MIT

Author Information
------------------

Author: Philipp Ruland
