# BusinessError

错误参数。

**继承/实现关系：** BusinessError extends [Error](../../apis-arkweb/arkts-components/arkts-arkweb-messagelevel-e.md#Error)

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-unnamed-export declare class BusinessError--><!--Device-unnamed-export declare class BusinessError-End-->

**系统能力：** SystemCapability.Base

## constructor

```TypeScript
constructor()
```

BusinessError的构造函数。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-BusinessError-constructor()--><!--Device-BusinessError-constructor()-End-->

**系统能力：** SystemCapability.Base

## constructor

```TypeScript
constructor(code: int, error: Error)
```

BusinessError的构造函数。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-BusinessError-constructor(code: int, error: Error)--><!--Device-BusinessError-constructor(code: int, error: Error)-End-->

**系统能力：** SystemCapability.Base

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| code | int | 是 | 接口调用失败返回的错误码信息。 |
| error | Error | 是 | 错误参数。 |

## constructor

```TypeScript
constructor(code: int, data: T, error: Error)
```

BusinessError的构造函数。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-BusinessError-constructor(code: int, data: T, error: Error)--><!--Device-BusinessError-constructor(code: int, data: T, error: Error)-End-->

**系统能力：** SystemCapability.Base

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| code | int | 是 | 接口调用失败返回的错误码信息。 |
| data | T | 是 | 接口调用时的公共回调信息。 |
| error | Error | 是 | 错误参数。 |

## constructor

```TypeScript
constructor(code: int, message: string, data?: T)
```

BusinessError的构造函数。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-BusinessError-constructor(code: int, message: string, data?: T)--><!--Device-BusinessError-constructor(code: int, message: string, data?: T)-End-->

**系统能力：** SystemCapability.Base

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| code | int | 是 | 接口调用失败返回的错误码信息。 |
| message | string | 是 | 接口调用失败返回描述信息。 |
| data | T | 否 | 接口调用时的公共回调信息。 |

## data

```TypeScript
public data?: T
```

接口调用时的公共回调信息。如果不填，则回调不返回相关信息。

**类型：** T

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-BusinessError-public data?: T--><!--Device-BusinessError-public data?: T-End-->

**系统能力：** SystemCapability.Base

