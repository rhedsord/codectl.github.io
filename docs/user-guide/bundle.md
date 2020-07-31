---
layout: default
title: Bundle
parent: User Guide
nav_order: 1
---

# Bundle
## Red Hat OpenShift 4.5+ | Low Side | Artifact Collection
#### Koffer Collector Plugins [Infrastructure] - [Operators] - [Applications]   

#### 1. Create Platform Artifacts Staging Directory
```
 mkdir -p /tmp/platform ;
```
#### 2. Build Openshift Infrastructure Bundle
  - Paste [Quay.io Image Pull Secret] when prompted    
    
```
 sudo podman run \
     --volume /tmp/platform:/root/deploy:z     \
     --rm -it --entrypoint=/usr/bin/entrypoint \
   docker.io/ocpredshift/koffer:latest      \
   https://github.com/RedShiftOfficial/collector-infra.git latest
```
    
#### 3. Build Operator Selection Bundle
```
 sudo podman run -it --rm \
     --privileged --device /dev/fuse \
     --entrypoint=/usr/bin/entrypoint \
     --volume /tmp/platform:/root/deploy:z \
   docker.io/ocpredshift/koffer:nightlies \
   https://github.com/RedShiftOfficial/collector-operators.git master
```
    
#### 4. Build Application Images Bundle
```
 sudo podman run -it --rm \
     --entrypoint=/usr/bin/entrypoint \
     --volume /tmp/platform:/root/deploy:z \
     --volume /tmp/platform/secrets/docker/quay.json:/root/.docker/config.json:ro \
  docker.io/ocpredshift/koffer:latest \
  https://github.com/RedShiftOfficial/collector-apps.git latest
```
    
#### 5. Continue [Artifacts AirGap Pivot](./PIVOT.md)

------------------------------------------------------------------------------
# Demo
![bundle](./web/bundle.svg)

[Operators]:https://github.com/RedShiftOfficial/collector-operators
[Applications]:https://github.com/RedShiftOfficial/collector-apps
[Infrastructure]:https://github.com/RedShiftOfficial/collector-infra
[Quay.io Image Pull Secret]:https://cloud.redhat.com/openshift/install/metal/user-provisioned