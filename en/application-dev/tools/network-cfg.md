# network-cfg

<!--Kit: Network Kit-->
<!--Subsystem: Communication-->
<!--Owner: @wmyao_mm-->
<!--Designer: @guo-min_net-->
<!--Tester: @tongxilin-->
<!--Adviser: @zhang_yixin13-->
network-cfg (cfg is short for config) is a tool provided for setting network parameters, for example, setting a proxy for Wi-Fi.
>**NOTE**
>
>network-cfg is supported since API version 20.

## Environment Requirements

<!--RP1-->

Before using this tool, you must obtain [hdc](../dfx/hdc.md) and run the **hdc shell** command.

<!--RP1End-->

## Commands

| Command| Description|
| -------- | -------- |
| help | Displays the commands supported by the tool.|
| set | Sets network parameters.|

## help

```bash
# Display the help information.
network-cfg help
network-cfg -h
```

## Setting Network Parameters

- Display the commands supported by **set**.

```bash
network-cfg set -h
```

- Set or cancel the current Wi-Fi proxy.

```bash
network-cfg set http_proxy [ip:port]
```

> **NOTE**
>
> - The proxy can be set only when the Wi-Fi is connected.
> - The value range of the port number is [1, 65535]. If the port number is not specified or exceeds the value range, the default value **8080** is used.
> - The proxy takes effect only for the current Wi-Fi. You need to set the proxy again after switching the Wi-Fi.

Example:

```bash
# Set a proxy for the current Wi-Fi. The host name is localhost, and the port number is 8080.
network-cfg set http_proxy 127.0.0.1:8080
# Set a proxy for the current Wi-Fi. The host name is ip6-localhost, and the port number is 8080.
network-cfg set http_proxy [::1]
# Cancel the current Wi-Fi proxy.
network-cfg set http_proxy 0
```
