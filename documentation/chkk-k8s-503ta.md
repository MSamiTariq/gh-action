---
title: Calico-felix fails to start after an upgrade can cause a downtime
category: 655c49ff76fdad0024723139
---

## How to fix it, long-term fix? (Remediation)

Do not upgrade from an older version to `v3.23.0` - `v3.23.3`. Upgrade to `v3.23.4` or above.  
Or apply the mitigation given below before upgrading to `v3.23.0` - `v3.23.3`.

## How to fix it, short-term workaround? (Mitigation)

Modify the _default-ipv4-ippool_ or_ ippools.crd.projectcalico.org_ object to add  
_vxlanMode: Never_

Get the IPPool yaml file.

_$ calicoctl get ippools -o yaml_ 

Update and reapply the manifest after making the following changes.

```yaml k8s manifest (etcd mode)
apiVersion: projectcalico.org/v3
kind: IPPool
metadata:
  name: my.ippool-1
spec:
  cidr: 10.1.0.0/16
  ipipMode: CrossSubnet
  natOutgoing: true
  disabled: false
+ vxlanMode: Never
  nodeSelector: all()
  allowedUses:
  - Workload
  - Tunnel
```
```yaml k8s manifest (CRD mode)
apiVersion: v1
items:
- apiVersion: crd.projectcalico.org/v1
  kind: IPPool
  spec:
    blockSize: 26
    cidr: 100.96.0.0/11
    ipipMode: CrossSubnet
  + vxlanMode: Never
    natOutgoing: true
```

## What is the impact? (Availability Impact)

Calico-felix fails to start, preventing IP tables and routing rules to be programmed on the host; lack of these rules will make calico drop the packets instead of passing them to containers.

## Why does this exist? (Root Cause)

[block:html]
{
  "html": "<div>\n<span title=\"Component responsible for writing routing table of OS and manipulating IP tables on the host. \">Felix</span> functionality has been updated in the 3.23 release such that it now uses the existing IP Pools to determine whether IPIP and/or VXLAN encapsulations should be enabled or not. To do that a new field ‘VXLANMode’ is introduced in the manIfest. If the pool was created prior to that field existing or created / edited with an older version of calicoctl that isn't aware of the field, the value of this field is empty. However the change made in the code assumes it be set to ‘Never’ as default. Not properly handling the difference between vxlanMode: \"\" and vxlanMode: Never for older clusters causes Felix to crash.\n</div>\n"
}
[/block]


## Who is impacted and when? (Trigger Conditions)

_Note: If you are doing a fresh installation of calico `v3.23.0` - `v3.23.3` you will not hit this LAR._

Upgrading from a version older than `3.23.0` to Calico version  `v3.23.0` - `v3.23.3` version will create and trigger this Latent Availability Risk.

_Affected versions_

`v3.23.0` - `v3.23.3`

_Affected Images_

All calico-node container image tags for the above versions are affected.

## Additional Resources

Details of the exact GitHub issue can be found [here](https://github.com/projectcalico/calico/issues/6442) 

To read more about calico refer to the following links

[Calico Felix](https://www.tigera.io/blog/kubernetes-networking-with-calico/)  
[IPPools configurations](https://projectcalico.docs.tigera.io/reference/resources/ippool)  
Calico's [IPIP ](https://projectcalico.docs.tigera.io/reference/resources/ippool#ipip)and [VXLAN](https://projectcalico.docs.tigera.io/reference/resources/ippool#vxlan) encapsulations  
 [Etcd mode with calicoctl](https://projectcalico.docs.tigera.io/archive/v3.12/reference/calicoctl/overview)