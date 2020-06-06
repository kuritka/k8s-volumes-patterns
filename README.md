
Important is that both objects has status bound
They are bounded via StorageClass name. **Storage class is not k8s object, just ID to bound objects together**  
```shell script
C02XR6YRJGH6:kuritka ab011th$ k get pv
NAME    CAPACITY   ACCESS MODES   RECLAIM POLICY   STATUS   CLAIM            STORAGECLASS   REASON   AGE
ps-pv   1Gi        RWO            Retain           Bound    default/ps-pvc   ps-fast                 8m30s
C02XR6YRJGH6:kuritka ab011th$ k get pvc
NAME     STATUS   VOLUME   CAPACITY   ACCESS MODES   STORAGECLASS   AGE
ps-pvc   Bound    ps-pv    1Gi        RWO            ps-fast        2m11s
```

`k describe sc-pod` and check if volumes are bounded


```
Volumes:
   htmlvol:
     Type: Lo      PersistentVolumeClaim (a reference to a PersistentVolumeClaim in the same namespace)
     ClaimName:  pvc-htmlvol
```

andc reate `index.htlm` for nginx;

```shell script
C02XR6YRJGH6:pv ab011th$ k exec -it sc-pod -c helper-ctr /bin/bash
kubectl exec [POD] [COMMAND] is DEPRECATED and will be removed in a future version. Use kubectl kubectl exec [POD] -- [COMMAND] instead.
root@sc-pod:/# echo 'HELllo world ' > ./data/index.html && exit
C02XR6YRJGH6:pv ab011th$ kubectl port-forward sc-pod 8080:80
```


in the browser `localhost:8080` you will see message!
