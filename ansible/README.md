## Playbooks

### Build Strapi

Options: 
- `PR` <number> this should be an open Pull Request number
- `force_build` <boolean> (defaults to `false`) skip checking if previous build commit matches current head commit in PR 

Usage:

`ansible-playbook build-strapi.yaml -e PR=<pr num>`


