# UIServiceHostProxy（系统接口）

UIServiceHostProxy提供代理能力，可以将数据从
[UIServiceExtension](arkts-ability-uiserviceextensionability-c-sys.md)服务端发送到客户端。

> **说明：**
>
> - 本模块接口需要在主线程中使用，不要在Worker、TaskPool等子线程中使用。

**起始版本：** 14

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

## sendData

```TypeScript
sendData(data: Record<string, Object>): void
```

从[UIServiceExtension](arkts-ability-uiserviceextensionability-c-sys.md)服务端给客户端发送数据。

**起始版本：** 14

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| data | Record&lt;string, Object&gt; | 是 | 待发送到[UIServiceExtension](arkts-ability-uiserviceextensionability-c-sys.md)客户端的数据。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not System App. Interface caller is not a system app. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;2. Incorrect parameter types; 3. Parameter verification failed. |
| [16000050](../errorcode-ability.md#16000050-内部错误) | Internal error. |

