# WithTheme

## WithTheme

```TypeScript
export declare function WithTheme(
    options: WithThemeOptions | undefined, 
    content_?: CustomBuilder,
): WithThemeAttribute
```

设置应用局部页面自定义主题风格。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-unnamed-export declare function WithTheme(    options: WithThemeOptions | undefined,     content_?: CustomBuilder,): WithThemeAttribute--><!--Device-unnamed-export declare function WithTheme(    options: WithThemeOptions | undefined,     content_?: CustomBuilder,): WithThemeAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | \_\_\_MD\_LINK\_USD\_0\_\_\_ \| undefined | 是 | 设置作用域内组件配色。 |
| content\_ | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 否 | 支持单个子组件。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| \_\_\_MD\_LINK\_USD\_0\_\_\_ |  |


## WithTheme

```TypeScript
export declare function WithTheme(
    style_: CustomBuilderT<WithThemeAttribute>,
    content_?: CustomBuilder,
): WithThemeAttribute
```

用于WithTheme定义

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**装饰器类型：** @Builder

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-unnamed-export declare function WithTheme(    style_: CustomBuilderT<WithThemeAttribute>,    content_?: CustomBuilder,): WithThemeAttribute--><!--Device-unnamed-export declare function WithTheme(    style_: CustomBuilderT<WithThemeAttribute>,    content_?: CustomBuilder,): WithThemeAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| style\_ | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;\_\_\_MD\_LINK\_USD\_1\_\_\_&gt; | 是 | WithTheme属性实例 |
| content\_ | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 否 | 容器 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| \_\_\_MD\_LINK\_USD\_0\_\_\_ | WithTheme属性 |

