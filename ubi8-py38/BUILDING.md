* This Dockerfile requires the parent directory as the context since it pulls
some files from there. To build, use this command

podman build -f ./Dockerfile ..

From an OpenShift buildConfig, do something like this to leave the context
set in the parent directory but change the Dockerfile path

```
  source:
    git:
      ref: master
      uri: https://github.com/red-hat-data-services/s2i-thoth
    type: Git
  strategy:
    dockerStrategy:
      dockerfilePath: ubi8-py38/Dockerfile
      from:
        kind: ImageStreamTag
        name: mygreatimage
      noCache: true
    type: Docker
```
