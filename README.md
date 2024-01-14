# Stworzono repozytorium prywatne na dockerhubie, secret i poda.
kubectl create secret generic regcred --from-file=.dockerconfigjson=/home/kamil/.docker/config.json --type=kubernetes.io/dockerconfigjson
secret/regcred created
kamil@kamil-VirtualBox:~$ kubectl get secret regcred --output=yaml
apiVersion: v1
data:
  .dockerconfigjson: ewoJImF1dGhzIjogewf3CSJodHRwczovL2luZGV4LmRvY2tlci5pby92MS8iOiB7CgkJCSJhdXRoIjogImEyRnRhV3d1Y25sMFpXeEFjRzlzYkhWaUxtVmtkUzV3YkRwQlpHcHpkWGhvY3praCIKCQl9Cgl9Cn0=
kind: Secret
metadata:
  creationTimestamp: "2024-01-14T17:12:19Z"
  name: regcred
  namespace: default
  resourceVersion: "16956"
  uid: f4150275-79f7-4f10-8065-3279195fa833
type: kubernetes.io/dockerconfigjson
kamil@kamil-VirtualBox:~$ kubectl apply -f lab12-pod.yaml
pod/test12 created



# kubectl describe pod test12
Name:             test12
Namespace:        default
Priority:         0
Service Account:  default
Node:             minikube/192.168.49.2
Start Time:       Sun, 14 Jan 2024 18:17:05 +0100
Labels:           <none>
Annotations:      cni.projectcalico.org/containerID: 1b60e6be80fef9df03cbe440114700c259a4c77fc08bd6bcd39abc63e34fbf9d
                  cni.projectcalico.org/podIP: 10.244.120.74/32
                  cni.projectcalico.org/podIPs: 10.244.120.74/32
Status:           Running
IP:               10.244.120.74
IPs:
  IP:  10.244.120.74
Containers:
  private-reg-container:
    Container ID:   docker://a2ece884f2796b107bcd20fbecd3dd2397869899f7d314aa74df475fe87052be
    Image:          kamil4/lab12:lab12
    Image ID:       docker-pullable://kamil4/lab12@sha256:4669f6671aca20a34c3dfcd017e84fb3cae40788ea664866eaea698e3dfe241c
    Port:           <none>
    Host Port:      <none>
    State:          Running
      Started:      Sun, 14 Jan 2024 18:18:18 +0100
    Ready:          True
    Restart Count:  0
    Environment:    <none>
    Mounts:
      /var/run/secrets/kubernetes.io/serviceaccount from kube-api-access-86lm8 (ro)
Conditions:
  Type              Status
  Initialized       True 
  Ready             True 
  ContainersReady   True 
  PodScheduled      True 
Volumes:
  kube-api-access-86lm8:
    Type:                    Projected (a volume that contains injected data from multiple sources)
    TokenExpirationSeconds:  3607
    ConfigMapName:           kube-root-ca.crt
    ConfigMapOptional:       <nil>
    DownwardAPI:             true
QoS Class:                   BestEffort
Node-Selectors:              <none>
Tolerations:                 node.kubernetes.io/not-ready:NoExecute op=Exists for 300s
                             node.kubernetes.io/unreachable:NoExecute op=Exists for 300s
Events:
  Type    Reason     Age   From               Message
  ----    ------     ----  ----               -------
  Normal  Scheduled  93s   default-scheduler  Successfully assigned default/test12 to minikube
  Normal  Pulling    88s   kubelet            Pulling image "kamil4/lab12:lab12"
  Normal  Pulled     22s   kubelet            Successfully pulled image "kamil4/lab12:lab12" in 1m6.868971042s (1m6.869009945s including waiting)
  Normal  Created    21s   kubelet            Created container private-reg-container
  Normal  Started    20s   kubelet            Started container private-reg-container
kamil@kamil-VirtualBox:~$ 

