# ExtInfoChangeCallback（系统接口）

```TypeScript
type ExtInfoChangeCallback = (extensionId: string, info: string) => void
```

Defines the callback type used in registering to listen for extension change. The value of extensionId indicates the print extension id. The value of info indicates the connect info.

**起始版本：** 23

<!--Device-print-type ExtInfoChangeCallback = (extensionId: string, info: string) => void--><!--Device-print-type ExtInfoChangeCallback = (extensionId: string, info: string) => void-End-->

**系统能力：** SystemCapability.Print.PrintFramework

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| extensionId | string | 是 | the printer extension id |
| info | string | 是 | the information of printer |

