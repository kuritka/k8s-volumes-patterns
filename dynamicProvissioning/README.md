
```shell script
C02XR6YRJGH6:pv ab011th$ k get sc
NAME                 PROVISIONER                    RECLAIMPOLICY   VOLUMEBINDINGMODE      ALLOWVOLUMEEXPANSION   AGE
ps-fast (default)    kubernetes.io/no-provisioner   Delete          WaitForFirstConsumer   false                  9s
standard (default)   rancher.io/local-path          Delete          WaitForFirstConsumer   false                  52m
```

it is not good idea to have both of them (default), so I can 

`k edit sc standard` and edit annotations `storageclass.kubernetes.io/is-default-class: ""`


