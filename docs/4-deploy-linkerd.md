# Installing Linkerd


To install Linkerd execute the following command:

## 2. Deploy using Helm

To deploy Linkerd execute the following command:

```
$ make deploy-linkerd
```

You should see:

```
NAME            READY     STATUS    RESTARTS   AGE
linkerd-4hv44   2/2       Running   0          6m
linkerd-648cl   2/2       Running   0          6m
linkerd-cl4sw   2/2       Running   0          6m
linkerd-h2c1q   2/2       Running   0          6m
linkerd-phs0k   2/2       Running   0          6m
```

You can also execute:

```
$ helm list
```

You should see:

```
NAME        REVISION        UPDATED                 STATUS         CHART           NAMESPACE
linkerd     1               Tue Oct3 11:30:26 2017  DEPLOYED       linkerd-0.3.0   default 
```

## Update hostfile (local machine)

We need to edit our hostfile to allow access to linkerd.

Please follow the steps below to make the necessary changes.

```
$ sudo nano /etc/hosts
```

Add the following lines to the file (where 35.196.109.8  is the External IP address of your ingress node):

Note: To get External ip, execute the following:

```
kubectl get service
```

You should see:

```                  
NAME         CLUSTER-IP    EXTERNAL-IP    PORT(S)                                       AGE
kubernetes   10.27.240.1     <none>       443/TCP                                       1h
linkerd      10.27.241.134  35.196.109.8  4140:32130/TCP,4141:31306/TCP,80:30919/TCP    8m
```

You can copy the external IP of the linkerd service, and paste down below:

```
35.196.109.8 linkerd.example.com
```

## Validate installation (from your local machine)

To validate everything has been successfully installed browse to the following URL:

[linkerd.example.com](http://linkerd.example.com)