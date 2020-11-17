# Cloud Pak Acceleration Team  - CPAT
# Template and Example Usage Guide
#### Use this guide with an Openshift or Kubernetes cluster after you have installed the Tekton Pipeline Operator. 
#### This directory contains templates and examples for creating PipelineResources, and a Secret for use with a private IBM git repository.

**Please note:** Any space containing carrots should be *replaced* ( Carrots should be removed as well )

Example:
```yaml
metadata:
  name: <secret name>
```
Should become
```yaml
metadata:
  name: git-infra-secret
```

## Pipeline Resource Examples
  - *template-git-src.yaml* (git)
    1. cp template-git-src.yaml git-src.yaml
    2. One can rename the metadata/name field to fit your project needs
    3. The url value points to the target repository
    4. The revision value points to the target branch
    
  - *template-git-infra.yaml* (git)
    1. cp template-git-infra.yaml git-infra.yaml
    2. Your Tekton pipeline git. One can rename the metadata/name field to fit your project needs
    3. The url value points to the target repository
    4. The revision value points to the target branch
        
## Secret Template
  - *template-git-secret.yaml*
    1. cp template-git-secret.yaml git-secret.yaml
    2. Replace the metadata/name field
    3. The annotation -
    
       ```yaml
       annotations:
         tekton.dev/git-0: https://github.ibm.com
       ```
       Is necessary for accessing any private IBM repo
    4. Replace the username field with your IBM e-mail address
    5. Provide a GitHub personal access token in the password field **( MUST HAVE READ:PACKAGES ACCESS )**
    
        NOTE: to protect your credentials, git-secret.yaml has already been added to the .gitignore file.
        
        TODO: ADD A PRE-COMMIT GIT HOOK

## ServiceAccount
  - Use the OOB OCP ServiceAccount called pipeline. The command below will link your new secret.
  
    ```bash
    oc secret link pipeline <secret-name>
    ```
