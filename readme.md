## Purpose

1.  create a simple operator to create pods, and maintain the available replicas
do the similar job as deployment which backuped by kubernetes.

2.  the pods have a persistentVolume, if pods crash, the operator can recreate them
and bind them to the persistentVolume.

##before running

the operator binda the pod to a persistentVolume with the help of pvc
you should create the persistentVolume by the commond:

$kubectl create -f examples/pv.yaml

## Running

the default path to kubeconfig is $HOME/.kube/config
```sh

# create a CustomResourceDefinition
$ kubectl create -f examples/crd.yaml

# assumes you have a working kubeconfig, not required if operating in-cluster
$ go build -o app *.go
$ ./app

# create a custom resource of type Foo
$ kubectl create -f examples/example-foo.yaml

# check pods created through the custom resource
$ kubectl get pods
```
