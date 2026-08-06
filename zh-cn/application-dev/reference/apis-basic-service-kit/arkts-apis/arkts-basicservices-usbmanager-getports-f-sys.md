# getPorts（系统接口）

## getPorts

```TypeScript
function getPorts(): Array<USBPort>
```

获取所有物理USB端口描述信息。开发者模式关闭时，如果没有设备接入，接口可能返回\_\_\_INLINE\_CODE\_DESC\_USD\_0\_\_\_，注意需要对接口返回值做判空处理。

**起始版本：** 9

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为9。

**废弃版本：** 12

**替代接口：** [usbManager.getPortList](arkts-basicservices-usbmanager-getportlist-f-sys.md#getportlist)()

<!--Device-usbManager-function getPorts(): Array<USBPort>--><!--Device-usbManager-function getPorts(): Array<USBPort>-End-->

**系统能力：** SystemCapability.USB.USBManager

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Array&lt;USBPort&gt; | USB端口描述信息列表。 |

