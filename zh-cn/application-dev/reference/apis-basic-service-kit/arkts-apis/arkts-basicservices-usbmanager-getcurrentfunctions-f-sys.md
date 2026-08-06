# getCurrentFunctions（系统接口）

## getCurrentFunctions

```TypeScript
function getCurrentFunctions(): FunctionType
```

在设备模式下，获取当前的USB功能列表的数字组合掩码。开发者模式关闭时，如果没有设备接入，接口可能返回\_\_\_INLINE\_CODE\_DESC\_USD\_0\_\_\_，注意需要对接口返回值做判空处理。

**起始版本：** 9

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为9。

**废弃版本：** 12

**替代接口：** [usbManager.getDeviceFunctions](arkts-basicservices-usbmanager-getdevicefunctions-f-sys.md#getdevicefunctions)()

<!--Device-usbManager-function getCurrentFunctions(): FunctionType--><!--Device-usbManager-function getCurrentFunctions(): FunctionType-End-->

**系统能力：** SystemCapability.USB.USBManager

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| \_\_\_MD\_LINK\_USD\_0\_\_\_ | 当前的USB功能列表的数字组合掩码。 |

