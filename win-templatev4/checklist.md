# Checklist: Creating an Ansible Role

## Preparation
- [ ] Define role name (lowercase, with hyphens)
- [ ] Clarify purpose and scope of the role

## Directory Structure
- [ ] Create main directory
- [ ] Create `tasks/main.yml`
- [ ] Create `handlers/main.yml`
- [ ] Create `templates/` directory
- [ ] Create `files/` directory
- [ ] Create `vars/main.yml`
- [ ] Create `defaults/main.yml`
- [ ] Create `meta/main.yml`

## Implementation
- [ ] Define handlers
- [ ] Set variables in defaults
- [ ] Set application name in vars file
- [ ] Create installation detection script
- [ ] Place psadt files in files/
- [ ] Update role metadata

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