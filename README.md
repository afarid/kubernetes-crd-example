# kubernetes-crd-example
Guide for autogeneratng  client codes for Kubernetes Custom Resource Definitions (CRD)

# Steps:

- take the configuration in directory in `pkg/apis/foo.com/` as template to define the new crd" 

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
go get github.com/afarid/kubernetes-crd-example/pkg/apis/foo.com/v1
```

- Run this command inside this project directory:
```bash 
cd $GOPATH/src/github.com/afarid/kubernetes-crd-example
../../../k8s.io/code-generator/generate-groups.sh all "github.com/afarid/kubernetes-crd-example/pkg/clients" "github.com/afarid/kubernetes-crd-example/pkg/apis" "foo.com:v1" -h ../../../k8s.io/code-generator/hack/boilerplate.go.txt
```

- use generated package in your code, this is an example of how to use the generated package

```go
package main

import (
	clientset "github.com/afarid/kubernetes-crd-example/pkg/clients/clientset/versioned"
)

func main() {
	_, _ = clientset.NewForConfig(nil)
}
```