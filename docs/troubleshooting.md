# Troubleshooting

## When loxilight agent run without loxilight namespace
---
* Issue - Output description of loxilight agent pod
```
Events:
  Type     Reason       Age                   From               Message
  ----     ------       ----                  ----               -------
  Normal   Scheduled    4m47s                 default-scheduler  Successfully assigned kube-system/test-loxi-agent-ebpf-6kz68 to node3
  Warning  FailedMount  2m44s                 kubelet            Unable to attach or mount volumes: unmounted volumes=[loxi-netns], unattached volumes=[loxi-cni-bin-dir kube-api-access-282ds loxi-log-dir loxi-netns loxi-conf-dir loxi-cni-conf-dir]: timed out waiting for the condition
  Warning  FailedMount  37s (x10 over 4m47s)  kubelet            MountVolume.SetUp failed for volume "loxi-netns" : hostPath type check failed: /var/run/netns/loxilight is not a file
  Warning  FailedMount  31s                   kubelet            Unable to attach or mount volumes: unmounted volumes=[loxi-netns], unattached volumes=[loxi-log-dir loxi-netns loxi-conf-dir loxi-cni-conf-dir loxi-cni-bin-dir kube-api-access-282ds]: timed out waiting for the condition
```

* Solution - Restart Loxilight service
```
$ systemctl restart loxilight
```

## When loxilight route table informations mis-sync
---
* Issue - loxilight agent's status is Error

* Solution - remove corrupted routing table informations and restart
```
$ rm -rf /etc/loxilight/routev4
$ systemctl restart loxilight
```
