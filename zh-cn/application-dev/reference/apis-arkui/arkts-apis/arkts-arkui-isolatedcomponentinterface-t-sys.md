# IsolatedComponentInterface（系统接口）

```TypeScript
declare type IsolatedComponentInterface = (options: IsolatedOptions) => IsolatedComponentAttribute
```

提供IsolatedComponent的接口，用于渲染其他ABC的UI。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-unnamed-declare type IsolatedComponentInterface = (options: IsolatedOptions) => IsolatedComponentAttribute--><!--Device-unnamed-declare type IsolatedComponentInterface = (options: IsolatedOptions) => IsolatedComponentAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [IsolatedOptions](arkts-arkui-isolatedoptions-i-sys.md) | 是 | IsolatedComponentAttribute的构造配置  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [IsolatedComponentAttribute](arkts-arkui-isolatedcomponentattribute-c-sys.md) | IsolatedComponent的属性  |

