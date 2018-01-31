**_A tiny kubernetes client to include in basic Kuberentes utilities_**.

# Usage

```
package main

import (
	"fmt"
	"ioutil"
	
	"github.com/amitkumarj441/dotfiles/tkube"
)

func main() {
	// kubernetes token
	token := "asdfasdfasdf"
	// read in the kubernetes certificate authority
	ca, err := ioutil.ReadFile("ca.pem")
	if err != nil {
		panic()
	}
	// create a new skube client
	k := tkube.New("https://mykubernetes:6443", token, ca)
	
	// do tkube stuff with it. 
	deployments, err := k.ListDeployments("")
	
	if err != nil {
		panic()
	}
	
	for _, d := range deployments {
		fmt.Println(d)
	}
  ```
