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

`watch crictl ps` : see if kube-apiserver pod is running

`crictl ps`

`crictl logs`

`vim /etc/kubernetes/manifests/kube-apiserver.yaml` : edit apiserver manifest and debug accordingly, i.e check apiServer version, check flags, check addresses and ports
