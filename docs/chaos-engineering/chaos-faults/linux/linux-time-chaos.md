---
id: linux-time-chaos
title: Linux Time Chaos
---
Linux Time Chaos injects chaos to change the time of the linux machine

## Use cases

- Induces Time chaos on the target Linux machines.
- It changes the time of the linux machine

:::note

- This fault has been tested for compatibility in Ubuntu 16 or higher, Debian 10 or higher, CentOS 7 or higher, RHEL 7 or higher, and openSUSE LEAP 15.4 or higher.
- The `linux-chaos-infrastructure` systemd service should be in an active state and the infrastructure should be in a `CONNECTED` state.
:::

## Fault tunables

  <h3>Mandatory fields</h3>
    <h3>Optional fields</h3>
    <table>
      <tr>
        <th> Variables </th>
        <th> Description </th>
        <th> Notes </th>
      </tr>
       <tr>
        <td> offset </td>
        <td> Time offset to increment and decrement the system time</td>
        <td> Offset should be provided in (+/-)[(numeric-offset)(unit)]+ format. It supports m,s,h units. eg: <code>+[1m]</code> </td>
      </tr>
      <tr>
      <td> disableNTP </td>
      <td> Set it to disable the ntp server </td>
      <td> It supports boolean values </td>
      </tr>
      <tr>
        <td> duration </td>
        <td> Duration through which chaos is injected into the target resource (in seconds). </td>
        <td> Defaults to 30 </td>
      </tr>
      <tr>
        <td> rampTime </td>
        <td> Period to wait before and after injecting chaos (in seconds). </td>
        <td> Defaults to 0. </td>
      </tr>
    </table>


### Offset

It contains the time offset to increment and decrement the system time. It should be provided in (+/-)[(numeric-offset)(unit)]+ format. Tune it by using the `offset` input.

Use the following example to tune the offset:

[embedmd]:# (./static/manifests/linux-time-chaos/offset.yaml yaml)
```yaml
# time offset
apiVersion: litmuchaos.io/v1alpha1
kind: LinuxFault
metadata:
  name: linux-time-chaos
  labels:
    name: time-chaos
spec:
  timeChaos/inputs:
    offset: '+1h30m'
```

### DisableNTP

It prevents the fault to disable the ntp server. Tune it by using the `disableNTP` input.

Use the following example to tune the offset:

[embedmd]:# (./static/manifests/linux-time-chaos/disable-ntp.yaml yaml)
```yaml
# disable the ntp server
apiVersion: litmuchaos.io/v1alpha1
kind: LinuxFault
metadata:
  name: linux-time-chaos
  labels:
    name: time-chaos
spec:
  timeChaos/inputs:
    disableNTP: 'true'
```
