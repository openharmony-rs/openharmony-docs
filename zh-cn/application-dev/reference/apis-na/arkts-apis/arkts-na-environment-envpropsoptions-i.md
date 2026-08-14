# EnvPropsOptions

Defining the EnvPropsOptions interface

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-unnamed-export declare interface EnvPropsOptions--><!--Device-unnamed-export declare interface EnvPropsOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## defaultValue

```TypeScript
defaultValue: int | long | double | string | boolean
```

查询不到环境变量key，则使用defaultValue作为默认值存入AppStorage中。

**类型：** int \| long \| double \| string \| boolean

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-EnvPropsOptions-defaultValue: int | long | double | string | boolean--><!--Device-EnvPropsOptions-defaultValue: int | long | double | string | boolean-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## key

```TypeScript
key: string
```

环境变量名称，支持的范围详见内置环境变量说明。

**类型：** string

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-EnvPropsOptions-key: string--><!--Device-EnvPropsOptions-key: string-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

