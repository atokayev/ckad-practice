### Preparation
* Create aliases: k, kex, kc, kr, kn
* Set text editor
<details>
  <summary>Solution</summary> 
 
```
alias k=kubectl
alias kex="kubectl explain"
alias kc="kubectl create"
alias kr="kubectl run --restart=Never"
alias kn='kubectl config set-context --current --namespace '
export KUBE_EDITOR=nano
```

</details>

### Before starting the new task
* Switch context
* Switch and check namespace
* Get all namespace objects

<details>
  <summary>Solution</summary> 
 
```
k config use-context k8s
kn NAMESPACE
k get all
```
</details>

### Namespace
* Create namespace `scenario1`. All following objects are created inside this namespace
### Deployment
* Create deployment named `nginx` with image `nginx:1.16` with 2 replicas with attached service on port `80`
* Get service IP address
* Run busybox container and bash into it. Curl the service IP address. Note the output.
### ConfigMap
* Create ConfigMap `index` from file `index.html`
* Create ConfigMap `env-vars` from file `config.env`
* Create ConfigMap `env-title` with variable `title` equal to `CKAD is easy`
* Change deployment and mount `index` to `/usr/share/nginx/html` path
* Add environment variables from `env-vars`
* Add environment variable `title` from `env-title` as `TITLE` environment variable
* Add command that runs `echo "$HELLO. $TITLE. $BYE. " > /usr/share/nginx/html/hello.html; nginx -v >> /usr/share/nginx/html/hello.html`
* Bash into busybox container and curl service again. You should get different output. Add `/hello.html` to the url, you should see the generated text.
