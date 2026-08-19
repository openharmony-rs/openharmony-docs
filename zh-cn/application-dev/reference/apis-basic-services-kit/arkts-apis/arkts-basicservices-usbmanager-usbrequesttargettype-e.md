# USBRequestTargetType

请求目标类型。

**起始版本：** 23

<!--Device-usbManager-export enum USBRequestTargetType--><!--Device-usbManager-export enum USBRequestTargetType-End-->

**系统能力：** SystemCapability.USB.USBManager

## USB_REQUEST_TARGET_DEVICE

```TypeScript
USB_REQUEST_TARGET_DEVICE = 0
```

将控制请求的目标设置为USB设备本身，用于对整个设备进行控制操作（如设置设备地址、获取设备描述符等）。

**起始版本：** 23

<!--Device-USBRequestTargetType-USB_REQUEST_TARGET_DEVICE = 0--><!--Device-USBRequestTargetType-USB_REQUEST_TARGET_DEVICE = 0-End-->

**系统能力：** SystemCapability.USB.USBManager

## USB_REQUEST_TARGET_INTERFACE

```TypeScript
USB_REQUEST_TARGET_INTERFACE = 1
```

将控制请求的目标设置为USB设备的某个接口，用于对接口进行控制操作（如设置接口特性、获取接口描述符等）。

**起始版本：** 23

<!--Device-USBRequestTargetType-USB_REQUEST_TARGET_INTERFACE = 1--><!--Device-USBRequestTargetType-USB_REQUEST_TARGET_INTERFACE = 1-End-->

**系统能力：** SystemCapability.USB.USBManager

## USB_REQUEST_TARGET_ENDPOINT

```TypeScript
USB_REQUEST_TARGET_ENDPOINT = 2
```

将控制请求的目标设置为USB设备的某个端点，用于对端点进行控制操作（如清除端点停止状态、获取端点状态等）。

**起始版本：** 23

<!--Device-USBRequestTargetType-USB_REQUEST_TARGET_ENDPOINT = 2--><!--Device-USBRequestTargetType-USB_REQUEST_TARGET_ENDPOINT = 2-End-->

**系统能力：** SystemCapability.USB.USBManager

## USB_REQUEST_TARGET_OTHER

```TypeScript
USB_REQUEST_TARGET_OTHER = 3
```

将控制请求的目标设置为其他单元，用于对非标设备、接口或端点的单元进行控制操作。

**起始版本：** 23

<!--Device-USBRequestTargetType-USB_REQUEST_TARGET_OTHER = 3--><!--Device-USBRequestTargetType-USB_REQUEST_TARGET_OTHER = 3-End-->

**系统能力：** SystemCapability.USB.USBManager

