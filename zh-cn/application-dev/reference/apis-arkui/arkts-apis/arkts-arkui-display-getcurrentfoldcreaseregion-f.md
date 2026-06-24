# getCurrentFoldCreaseRegion

## getCurrentFoldCreaseRegion

```TypeScript
function getCurrentFoldCreaseRegion(): FoldCreaseRegion
```

在当前显示模式下获取折叠折痕区域。

**起始版本：** 10

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Window.SessionManager

**返回值：**

| 类型 | 说明 |
| --- | --- |
| FoldCreaseRegion | FoldCreaseRegion对象，返回设备在当前显示模式下的折叠折痕区域。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [1400003](../../errorcode-universal.md#1400003-This) | This display manager service works abnormally. |

**示例：**

```TypeScript
let data: display.FoldCreaseRegion = display.getCurrentFoldCreaseRegion();
console.info(`Succeeded in obtaining current fold crease region. Data: ${JSON.stringify(data)}`);

```

