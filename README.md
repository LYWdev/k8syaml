# k8syaml

## gVisor

```yaml
apiVersion: v1
kind: Pod
metadata:
  name: gvisor3
spec:
  runtimeClassName: gvisorclass
  containers:
  - name: gvisor3
    image: ubuntu:latest
    command: [ "bin/bash", "-c", "--"]
    args: ["while true; do sleep 30; done;"]
    volumeMounts:
    - name: tracingpath
      mountPath: /data/shared
    - name : programpath
      mountPath: /program
  volumes:
  - name : tracingpath
    hostPath:
      path: /sys/kernel/debug/tracing
      type: Directory
  - name : programpath
    hostPath:
      path: /home/workernode2/container_volume2
      type : Directory
```
