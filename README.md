# metric-server for k8s

Add "hostnetwork=true" to metric-server for running on top baremetal k8s using VM.

## Before

```bash
$ kubectl top nodes
Error from server (ServiceUnavailable): the server is currently unable to handle the request (get nodes.metrics.k8s.io)
$ kubectl top pod -n kube-system
Error from server (ServiceUnavailable): the server is currently unable to handle the request (get nodes.metrics.k8s.io)
```

## Install metric-server

```bash
$ git clone https://github.com/invaleed/metric-server.git
$ cd metric-server
$ kubectl apply -f kubernetes
```

## After

```bash
$ kubectl top nodes
NAME         CPU(cores)   CPU%   MEMORY(bytes)   MEMORY%   
k8s-master   167m         8%     1328Mi          36%       
k8s-node1    73m          3%     848Mi           23%       
k8s-node2    74m          3%     796Mi           21%       
k8s-node3    73m          3%     688Mi           18%       

$ kubectl top pod -n kube-system
NAME                                 CPU(cores)   MEMORY(bytes)   
coredns-66bff467f8-kwh4j             5m           12Mi            
coredns-66bff467f8-mgbtn             5m           12Mi            
etcd-k8s-master                      19m          66Mi            
kube-apiserver-k8s-master            55m          325Mi           
kube-controller-manager-k8s-master   23m          44Mi            
kube-flannel-ds-amd64-fvcsm          4m           12Mi            
kube-flannel-ds-amd64-ljsjs          3m           9Mi             
kube-flannel-ds-amd64-mfr5x          4m           11Mi            
kube-flannel-ds-amd64-z96vn          3m           11Mi            
kube-proxy-2g4l7                     1m           12Mi            
kube-proxy-48drn                     1m           12Mi            
kube-proxy-fkm65                     1m           12Mi            
kube-proxy-mnxdb                     1m           12Mi            
kube-scheduler-k8s-master            5m           17Mi            
metrics-server-96dcd945d-b47b7       1m           10Mi 
```
