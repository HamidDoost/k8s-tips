## Troubleshooting

### API Server troubleshooting

**Logs**

**Log locations:**

`/var/log/pods` : pods logs

`/var/log/containers` : container logs

`/var/log/syslog` : kubelet logs

**Check logs**

`cat /var/log/pods/kube-system_kube-apiserver` : if API server is created but pod has problem

`cat /var/log/syslog |grep apiserver` : If kubelet did not create api server

or

`journalctl |grep apiserver`

``

**Trobleshooting API Server**

- always make a backup !
`cp /etc/kubernetes/manifests/kube-apiserver.yaml ~/kube-apiserver.yaml.ori`

- make the change
`vim /etc/kubernetes/manifests/kube-apiserver.yaml`

- wait till container restarts
`watch crictl ps`

- check for apiserver pod
`k get po -n kube-system `

- check pod logs
`cat /var/log/pods/kube-system_kube-apiserver-controlplane_4e1eda320f6ceb861441aa1dcbc1ab1d/kube-apiserver/1.log`

- restore the backup if needed
`cp ~/kube-apiserver.yaml.ori /etc/kubernetes/manifests/kube-apiserver.yaml`


**Tips**

- `watch crictl ps` : see if kube-apiserver pod is running

- `crictl ps`

- `crictl logs`

- `vim /etc/kubernetes/manifests/kube-apiserver.yaml` : edit apiserver manifest and debug accordingly, i.e check apiServer version, check flags, check addresses and ports