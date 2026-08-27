# IsolatedComponentInterface（系统接口）

```TypeScript
declare type IsolatedComponentInterface = (options: IsolatedOptions) => IsolatedComponentAttribute
```

创建IsolatedComponent组件，用于显示受限Worker运行的Abc。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [IsolatedOptions](arkts-arkui-isolatedoptions-i-sys.md) | 是 | 需要传递的构造参数，仅首次传入有效，不支持构造参数更新。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [IsolatedComponentAttribute](arkts-arkui-isolatedcomponentattribute-c-sys.md) | IsolatedComponent的属性 |
