# ErrorCallback

通用回调函数，携带错误参数，用于在接口调用失败时回传错误信息。具体错误码值由各接口定义，请参考对应接口的错误码说明。 回调返回的信息为[BusinessError]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_类型的错误参数。

**起始版本：** 6

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为6。

<!--Device-unnamed-export interface ErrorCallback<T extends Error = BusinessError>--><!--Device-unnamed-export interface ErrorCallback<T extends Error = BusinessError>-End-->

**系统能力：** SystemCapability.Base

## constructor

```TypeScript
(err: T): void
```

**起始版本：** 6

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为6。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-ErrorCallback-(err: T): void--><!--Device-ErrorCallback-(err: T): void-End-->

**系统能力：** SystemCapability.Base

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| err | T | 是 | 接口调用失败的公共错误信息，类型默认为[BusinessError]\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_JSDOC\_\_\_ESCAPED\_UNDERSCORE\_\_\_LINK\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_，包含错误码（code）和可选附加数据（data）。 |

