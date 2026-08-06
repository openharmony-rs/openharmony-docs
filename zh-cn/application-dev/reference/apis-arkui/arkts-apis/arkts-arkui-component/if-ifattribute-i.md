# IfAttribute

支持\_\_\_MD\_LINK\_DESC\_USD\_0\_\_\_、 \_\_\_MD\_LINK\_DESC\_USD\_1\_\_\_和 \_\_\_MD\_LINK\_DESC\_USD\_2\_\_\_属性。

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

<!--Device-unnamed-export declare interface IfAttribute--><!--Device-unnamed-export declare interface IfAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## Else

```TypeScript
Else(
        content_: CustomBuilder
    ): void
```

定义Else分支。

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-IfAttribute-Else(        content_: CustomBuilder    ): void--><!--Device-IfAttribute-Else(        content_: CustomBuilder    ): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| content\_ | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | ElseIf分支代码 |

## ElseIf

```TypeScript
ElseIf(
        condition: boolean,
        content_: CustomBuilder
    ): this
```

定义ElseIf分支。

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-IfAttribute-ElseIf(        condition: boolean,        content_: CustomBuilder    ): this--><!--Device-IfAttribute-ElseIf(        condition: boolean,        content_: CustomBuilder    ): this-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| condition | boolean | 是 | 分支判断条件。\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_true: 执行该分支的UI描述。\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_1\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_false: 不执行该分支的UI描述。 |
| content\_ | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | ElseIf分支代码 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## applyAttributesFinish

```TypeScript
applyAttributesFinish(): void
```

如果已完成设置其属性，则通知。

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-IfAttribute-applyAttributesFinish(): void--><!--Device-IfAttribute-applyAttributesFinish(): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## debugLine

```TypeScript
debugLine(sourceLine: string, moduleName?: string): this
```

设置组件源码重定向信息。

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-IfAttribute-debugLine(sourceLine: string, moduleName?: string): this--><!--Device-IfAttribute-debugLine(sourceLine: string, moduleName?: string): this-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| sourceLine | string | 是 | 源码行号。 |
| moduleName | string | 否 | 组件所属模块名。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## setIfOptions

```TypeScript
setIfOptions(condition: boolean): this
```

设置If选项

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-IfAttribute-setIfOptions(condition: boolean): this--><!--Device-IfAttribute-setIfOptions(condition: boolean): this-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| condition | boolean | 是 | 条件分支。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this | IfAttribute实例 |

