# getFoldStatus

## getFoldStatus

```TypeScript
function getFoldStatus(): FoldStatus
```

获取可折叠设备当前的折叠状态。

**起始版本：** 10

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Window.SessionManager

**返回值：**

| 类型 | 说明 |
| --- | --- |
| FoldStatus | FoldStatus对象，返回当前可折叠设备的折叠状态。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [1400003](../../errorcode-universal.md#1400003-This) | This display manager service works abnormally. |

**示例：**

```TypeScript
let data: display.FoldStatus = display.getFoldStatus();
console.info(`Succeeded in obtaining fold status. Data: ${data}`);

```

