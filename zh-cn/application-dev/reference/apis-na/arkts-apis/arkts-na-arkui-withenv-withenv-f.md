# WithEnv

## WithEnv

```TypeScript
@ComponentBuilder
export declare function WithEnv(
    content_?: CustomBuilder,
): WithEnvAttribute
```

WithEnv组件用于为子组件树设置局部环境变量作用域。开发者可以通过该组件为后代组件提供自定义环境变量，或设置系统环境变量。

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-unnamed-@ComponentBuilderexport declare function WithEnv(    content_?: CustomBuilder,): WithEnvAttribute--><!--Device-unnamed-@ComponentBuilderexport declare function WithEnv(    content_?: CustomBuilder,): WithEnvAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| content_ | CustomBuilder | 否 | 组件的内容。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [WithEnvAttribute](../../apis-arkui/arkts-apis/arkts-arkui-arkui-withenv-withenvattribute-c.md) |  |

