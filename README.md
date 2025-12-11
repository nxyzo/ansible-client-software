# ansible-client-software

Repository of Ansible roles used to install, repair, and remove Windows client software with the PowerShell App Deployment Toolkit (PSADT). Each subdirectory under `win-*` contains a self-contained role, including defaults, handlers, and PSADT payload files.

## Prerequisites
- Ansible 2.9 or newer with the `ansible.windows` collection.
- Access to the Windows targets (WinRM enabled) and permissions to deploy software.

## Repository Structure
- `renovate.json` – Renovate configuration for tracking upstream software releases.
- `win-template/` – Example role that contains the default role structur.
- `LICENSE` – Licensing information for this repository and third-party assets bundled with PSADT.

## Using the Roles
1. Clone the repository and get the latest version of the desired software.
2. Add the role to your Ansible inventory and playbooks (see each role's README for variables and deployment types).
3. Run the playbook from a control node that can reach the Windows targets:

	```bash
	ansible-playbook -i inventories/production install-notepad.yml
	```

4. Monitor the Ansible output for success messages or PSADT return codes.

## Maintaining Software Packages
- Store vendor installers in `files/Files` to ensure PSADT can locate the payload during execution.
- Keep the role-specific README current with any additional prerequisites, silent switches, or known issues.

## Checklist for Adding New Software
- Create a new role by copying `win-template/` or using `ansible-galaxy init` to match the existing layout.
- Document role variables, deployment types, and required files in a role-specific README.
- Populate `files/Files` with the installers and support scripts needed for PSADT.
- After adding new software, implement a software version check for Renovate.
- Add the role to internal playbooks and perform a dry run against a non-production host.
- Capture any organization-specific configuration (registry edits, shortcuts) in `tasks/install.yml` or supporting templates.

## License

This repository is released under the MIT License. Third-party tools bundled with the roles retain their original licenses; see `COPYING.Lesser` files within the PSADT directories for details.