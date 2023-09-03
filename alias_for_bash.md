`alias k="kubect]"`

`alias v="vim"`

```bash
function ns () {
kubectl config set-context --current --namespace=$1
}
```
example: `k run test-pod --image=nginx $drc"


`export drc="-dry-run=client -oyaml"`

`export drs="-dry-run=server -oyaml"`

after adding aliases into `.bashrc` run `source ~/.bashrc`

### All commands together

```bash
alias k="kubectl"
alias v="vim"
alias kg="kubectl get"
alias kd="kubectl describe"

function ns () {
  kubectl config set-context --current --namespace=$1
}

export drc="--dry-run=client -oyaml"
export drs="--dry-run=server -oyaml"
```