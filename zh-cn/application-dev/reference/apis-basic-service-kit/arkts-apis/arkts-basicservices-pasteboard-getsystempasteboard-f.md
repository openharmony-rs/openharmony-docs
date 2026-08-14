# getSystemPasteboard

## getSystemPasteboard

```TypeScript
function getSystemPasteboard(): SystemPasteboard
```

获取系统剪贴板对象，返回剪贴板服务的单例实例。调用此方法后，返回的系统剪贴板对象可用于访问剪贴板的读写、监听等功能。 每次调用返回同一实例，调用前剪贴板系统服务需要正常运行。在进行任何剪贴板读写操作前，都需要先调用此方法获取系统剪贴板对象。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-pasteboard-function getSystemPasteboard(): SystemPasteboard--><!--Device-pasteboard-function getSystemPasteboard(): SystemPasteboard-End-->

**系统能力：** SystemCapability.MiscServices.Pasteboard

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [SystemPasteboard](arkts-basicservices-pasteboard-systempasteboard-i.md) | 系统剪贴板对象。 |

## 示例

```TypeScript
const systemPasteboard: pasteboard.SystemPasteboard = pasteboard.getSystemPasteboard();
```

