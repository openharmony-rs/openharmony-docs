# UIServiceProxy

UIServiceProxy提供代理能力，可以从UIServiceExtension客户端发送数据到服务端。

> **说明：**  
>  
> - 本模块接口需要在主线程中使用，不要在Worker、TaskPool等子线程中使用。

**起始版本：** 14

<!--Device-unnamed-export default interface UIServiceProxy--><!--Device-unnamed-export default interface UIServiceProxy-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

<a id="senddata"></a>
## sendData

```TypeScript
sendData(data: Record<string, Object>): void
```

给UIServiceExtension服务端发送数据。

> **说明：**  
>  
> 组件启动规则详见：[组件启动规则（Stage模型）](docroot://application-models/component-startup-rules.md)。

**起始版本：** 14

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本14开始，该接口支持在原子化服务API中使用。

<!--Device-UIServiceProxy-sendData(data: Record<string, Object>): void--><!--Device-UIServiceProxy-sendData(data: Record<string, Object>): void-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| data | Record&lt;string, Object&gt; | 是 | 待发送给UIServiceExtension服务端的数据。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;2. Incorrect parameter types; 3. Parameter verification failed. |
| [16000050](../errorcode-ability.md#16000050-内部错误) | Internal error. |

