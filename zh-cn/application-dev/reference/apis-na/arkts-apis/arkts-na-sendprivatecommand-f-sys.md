# sendPrivateCommand（系统接口）

## sendPrivateCommand

```TypeScript
function sendPrivateCommand(commandData: Record<string, CommandDataType>): Promise<void>
```

发送私有命令。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| commandData | Record&lt;string, CommandDataType&gt; | 是 | 将要发送的命令数据。最大大小32KB。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | 返回的Promise。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | not system application. |
| [12800026](../../apis-ime-kit/errorcode-inputmethod-framework.md#12800026-输入法系统面板错误) | input method system panel error. Possible causes:1. the system panel not connected. 2. ipc failed due to the large amount of data transferred or other reasons.3. the caller is not system panel. |

