 
Tekton Pipelines


# What we need ?
 1. Pipeline Resources: Git Repo's, Git Secret
 2. OCP cluster/CP4A
 
# What we can do ?
 Build and Deploy Nodejs app using Tekton
 
# Steps to follow
1. Create PipelineResources 
2. Create Tasks 
3. Create Pipeline 
4. Apply all to OCP
5. Run the Pipeline


# Create the pipeline artifacts

  
```bash
    oc secret link pipeline git-secret-ma   
    oc apply -f resources/git-resources.yaml -n $NAMESPACE
    oc apply -f tasks/ -n $NAMESPACE
    oc apply -f pipelines/ -n $NAMESPACE
```

# Run the pipeline
```bash
    tkn pipeline start cp4a-nodejs-pipeline --showlog \
    -r source=cp4a-git \
    -r infra=cp4a-git-infra \
    -s pipeline
    -n $NAMESPACE
```
# Debug 
```bash
    tkn taskrun ls -n $NAMESPACE
    tkn pipelinerun ls -n $NAMESPACE
    oc get imagestream -n $NAMESPACE
    tkn resources ls -n $NAMESPACE (shortcut: tkn res ls -n $NAMESPACE)
    tkn task ls -n $NAMESPACE
    tkn pipeline ls -n $NAMESPACE
```
