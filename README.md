# microbiome-kubernetes

Originally taken from https://github.com/galaxyproject/galaxy-helm. 

Setting-up Helm charts to run microbiome cluster that can process QIIME 2 
workflows on Galaxy.

To run:
    Start a kubernetes service (Minikube in the case of local development)
    cd galaxy-helm/galaxy
    helm dependency update
    helm install [NAME] .

To update service following modifications:
    helm update [NAME] .
    
Potential Roadblocks:
    *  Unable to pull Docker image in a pod.
       Fix: Pull the image before and add it to the cache
            minikube cache add galaxy/galaxy-k8s:19.09 (may not be minikube)
    *  Not enough memory available to deploy POD
       Fix: Inspect size of VMs and the values.yaml to determine if the request
            is greater than the available memory. 