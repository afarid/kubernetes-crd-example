# kubernetes-crd-example
Guide for autogeneratng  client codes for Kubernetes Custom Resource Definitions (CRD)

# Steps 1:

- Disable go modules 
```bash
export GO111MODULE=off
```

- Download the generator repository
```bash
 go get k8s.io/code-generator
```

- Download this repository
```bash
 got get github.com/afarid/kubernetes-crd-example
```

- Run this command inside this project directory:
```bash 
cd $GOPATH/src/github.com/afarid/kubernetes-crd-example
../../../k8s.io/code-generator/generate-groups.sh all "github.com/afarid/kubernetes-crd-example/pkg/clients" "github.com/afarid/kubernetes-crd-example/pkg/apis" "foo.com:v1" -h ../../../k8s.io/code-generator/hack/boilerplate.go.txt
```