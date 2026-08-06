# getFoldDisplayMode

## getFoldDisplayMode

```TypeScript
function getFoldDisplayMode(): FoldDisplayMode
```

获取可折叠设备当前的显示模式。

**起始版本：** 10

**ArkTS模式：** ArkTS-Dyn起始版本为10；ArkTS-Sta起始版本为23。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-display-function getFoldDisplayMode(): FoldDisplayMode--><!--Device-display-function getFoldDisplayMode(): FoldDisplayMode-End-->

**系统能力：** SystemCapability.Window.SessionManager

**返回值：**

| 类型 | 说明 |
| --- | --- |
| \_\_\_MD\_LINK\_USD\_0\_\_\_ | FoldDisplayMode对象，返回可折叠设备当前的显示模式。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [1400003](../errorcode-display.md#1400003-系统服务工作异常) | This display manager service works abnormally. |

**示例：**

```TypeScript
let data: display.FoldDisplayMode = display.getFoldDisplayMode();
console.info(`Succeeded in obtaining fold display mode. Data: ${data}`);
```

