# CustomValueType

```TypeScript
export type CustomValueType = number | string | boolean
```

表示扩展信息值的类型，接口参数具体类型根据其功能而定。开发者可根据配置项的含义选择合适的值类型：数值型配置（如字号大小、权重系数等）使用number；文本型配置（如输入模式名称、主题标识等）使用string；开关型配置（如是否启用某功能、是否展示某面板等）使用boolean。

**起始版本：** 22

<!--Device-unnamed-export type CustomValueType = int | string | boolean--><!--Device-unnamed-export type CustomValueType = int | string | boolean-End-->

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

| 类型 | 说明 |
| --- | --- |
| int | 表示值类型为数字。 |
| string | 表示值类型为字符串。 |
| boolean | 表示值类型为布尔值。 |

