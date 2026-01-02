# Checklist: Creating an Ansible Role

## Preparation
- [x] Define role name (lowercase, with hyphens)
- [x] Clarify purpose and scope of the role

## Directory Structure
- [x] Create main directory
- [x] Create `tasks/main.yml`
- [x] Create `handlers/main.yml`
- [x] Create `templates/` directory
- [x] Create `files/` directory
- [x] Create `vars/main.yml`
- [x] Create `defaults/main.yml`
- [x] Create `meta/main.yml`

## Implementation
- [x] Define handlers
- [x] Set variables in defaults
- [x] Set application name in vars file
- [ ] Create installation detection script
- [ ] Place psadt files in files/
- [x] Update role metadata

## Documentation
- [ ] Write `README.md`
- [ ] Document variables
- [ ] Provide examples

## Testing
- [ ] Validate syntax
- [ ] Test locally
- [ ] Integrate in playbook
- [ ] Perform end-to-end test

## Finalization
- [ ] Code review
- [ ] Commit to repository