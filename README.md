# K8s-tools
Deploy:
This tool allows you to build Kustomize overlays with placeholders, deploy to google cloud, with status monitoring.
Watch:
This tool allows you to watch local files and rsync it with remote K8s container.

### Setup

##### Install Google Cloud SDK
```
curl https://sdk.cloud.google.com | bash
exec -l $SHELL
gcloud init
```

##### Install Kubernetes or enable Kubernetes via Docker Settings
```
brew install kubernetes-cli
```

##### Install Envsubst
We use it for filling placeholders
```
brew install gettext
```
For MacOS it should be already installed, so need only to link:
```
brew link --force gettext
```

##### Install Kustomize
We use it for reusability of K8s configurations
```
brew install kustomize
```

##### Install fswatch
We use it for the watcher syncing files from local to remote k8s
```
brew install fswatch
```

##### Install GNU-Core-Utils
We use it for timeout command (gtimeout for mac)
```
brew install coreutils
```


### Deploy
The following command will generate a new environment in Google Cloud
```
./bin/k8s-deploy kubernetes/overlays/ENV/APP \
-n NAMESPACE \
-t CONTAINER_REGISTRY_TAG
```
APP is the name of the overlay, 
ENV is dev or production
NAMESPACE can be your name (also in URL), 
and TAG is version (e.g. 1.0.0).

##### Sync Watcher:
Our current structure supports easy syncing between local dev files and remote cloud files.
For your convenience it is recommended to place it in your PATH:
```
export PATH=$PATH:PATH/TO/CLOUD/REPO/BIN
```
To make this permanent, add it to your ~/.bashrc or ~/.bash_profile and source it.

