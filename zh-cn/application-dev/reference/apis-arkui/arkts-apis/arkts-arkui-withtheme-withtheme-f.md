# WithTheme

## WithTheme

```TypeScript
@ComponentBuilder
export declare function WithTheme(
    options: WithThemeOptions | undefined, 
    content_?: CustomBuilder,
): WithThemeAttribute
```

设置应用局部页面自定义主题风格。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-unnamed-@ComponentBuilderexport declare function WithTheme(    options: WithThemeOptions | undefined,     content_?: CustomBuilder,): WithThemeAttribute--><!--Device-unnamed-@ComponentBuilderexport declare function WithTheme(    options: WithThemeOptions | undefined,     content_?: CustomBuilder,): WithThemeAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [WithThemeOptions](arkts-arkui-withtheme-withthemeoptions-i.md) \| undefined | 是 | 设置作用域内组件配色。 |
| content_ | CustomBuilder | 否 | 支持单个子组件。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [WithThemeAttribute](arkts-arkui-withtheme-withthemeattribute-i.md) |  |


## WithTheme

```TypeScript
@Builder
export declare function WithTheme(
    style_: CustomBuilderT<WithThemeAttribute>,
    content_?: CustomBuilder,
): WithThemeAttribute
```

用于WithTheme定义

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-unnamed-@Builderexport declare function WithTheme(    style_: CustomBuilderT<WithThemeAttribute>,    content_?: CustomBuilder,): WithThemeAttribute--><!--Device-unnamed-@Builderexport declare function WithTheme(    style_: CustomBuilderT<WithThemeAttribute>,    content_?: CustomBuilder,): WithThemeAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| style_ | CustomBuilderT&lt;[WithThemeAttribute](arkts-arkui-withtheme-withthemeattribute-i.md)&gt; | 是 | WithTheme属性实例 |
| content_ | CustomBuilder | 否 | 容器 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [WithThemeAttribute](arkts-arkui-withtheme-withthemeattribute-i.md) | WithTheme属性 |

