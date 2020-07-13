## Playbooks

### Dependancies

- ansible 2.9.10
- python >= 2.7
  - pip modules: kubernetes, openshift (`pip install kubernetes openshift`)
- access to an openshift cluster
- logged into openshift
- access to multiple namespaces as defined the group vars file
- oc >= 3.11

Prior to starting please modify the vars example file `cp group_vars/all/vars.example.yaml group_vars/all/vars.yaml`

### Build Strapi
Builds the Strapi Image from an open pull request. The Build is optimized to not retrigger builds of the buildconfig `git commit` matches the PR `head commit`. This is so that this script may be utilized in a ci/cd pipeline. 

Options: 
- `PR` <number> this should be an open Pull Request number
- `force_build` <boolean> (defaults to `false`) skip checking if previous build commit matches current head commit in PR 

Usage:

`ansible-playbook build-strapi.yaml -e PR=<pr num>`


### Deploy Strapi

Deploys the strapi image to the development namespace. It will also check to see if the PR based image exists prior to building. 

Options:
- `PR` <number> this should be the open pull request number

Usage:
`ansible-playbook deploy-strapi.yaml -e PR=<pr num>`

### Deploy Mongo

Deploys a mongo replica set that is annoted with the PR number. This is because the mongo datbase should always be coupled with a strapi deployment. 

Options:
- `PR` <number> this should be the open pull request number

Usage:
`ansible-playbook deploy-mongo.yaml -e PR=<pr num>`

### Backup and Restore Mongo
Create a pod in Openshift to perform a back and restore process. This will target a specific mongo stateful set for the backup. And attempt to restore it with the backup pod as verification. 

Options:
- `PR` <number> this should be the open pull request number

Usage:
`ansible-playbook backup-restore-mongo.yaml -e PR=<pr num>`

