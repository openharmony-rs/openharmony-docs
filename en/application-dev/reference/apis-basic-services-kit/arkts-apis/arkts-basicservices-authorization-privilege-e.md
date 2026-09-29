# Privilege

```TypeScript
enum Privilege
```

Enumerates the privileges that can be authorized. Before requesting authorization for these privileges, ensure that the current application and runtime environment meet the authorization policy requirements. For detailed definitions of each privilege (including authorization policies), see [Privilege Appendix](../../../reference/apis-basic-services-kit/appendix-osAccount-authorization-privileges.md).

**Since:** 26.0.1

<!--Device-authorization-enum Privilege--><!--Device-authorization-enum Privilege-End-->

**System capability:** SystemCapability.Account.OsAccount

## PRIVILEGE_OPERATE_RAW_NET_PACKETS

```TypeScript
PRIVILEGE_OPERATE_RAW_NET_PACKETS = 'ohos.privilege.operate_raw_net_packets'
```

Privilege for operating the raw network packets.

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

<!--Device-Privilege-PRIVILEGE_OPERATE_RAW_NET_PACKETS = 'ohos.privilege.operate_raw_net_packets'--><!--Device-Privilege-PRIVILEGE_OPERATE_RAW_NET_PACKETS = 'ohos.privilege.operate_raw_net_packets'-End-->

**System capability:** SystemCapability.Account.OsAccount

## PRIVILEGE_MONITOR_RAW_USB_PACKETS

```TypeScript
PRIVILEGE_MONITOR_RAW_USB_PACKETS = 'ohos.privilege.monitor_raw_usb_packets'
```

Privilege for monitoring the raw USB packets.

After authorization, allows the application to capture raw USB traffic at the kernel level via the usbmon interface. This includes:  
- Raw Packet Capture: Directly reading the complete binary byte stream on the USB bus,  
including PID (Packet Identifier), token packets, data packets, and handshake packets at the transaction layer.  
- URB Lifecycle Tracking: Exposing the submission and completion events of USB Request Blocks (URBs)  
in the kernel, with detailed metadata such as timestamps, endpoint addresses, transfer types (Control, Interrupt, Isochronous, or Bulk), status codes, and actual payload data buffers.

These capabilities are intended for USB packet sniffing, low-level protocol analysis, and bus performance benchmarking.

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

<!--Device-Privilege-PRIVILEGE_MONITOR_RAW_USB_PACKETS = 'ohos.privilege.monitor_raw_usb_packets'--><!--Device-Privilege-PRIVILEGE_MONITOR_RAW_USB_PACKETS = 'ohos.privilege.monitor_raw_usb_packets'-End-->

**System capability:** SystemCapability.Account.OsAccount
