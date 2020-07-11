# Strapi application

A quick description of your strapi application


## Dependencies
- redhat container catalog pull secret to pull the nodejs 12 image
  > navigate to https://access.redhat.com/terms-based-registry/#/accounts for more details
- ansible 
- python >= 2.7
  - pip modules:
    - openshift
    - pyYAML
    - kubernetes

## Setup

1. Run the `redhat-conatiner-catalog-sa.yaml` secret template with your service account token `oc process -f templates/redhat-container-catalog-sa.yaml -p REDHAT_CATALOG_TOKEN=... | oc apply -f - -n <tools namespace>`

