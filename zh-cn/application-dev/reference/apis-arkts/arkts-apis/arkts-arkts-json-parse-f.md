# parse

## parse

```TypeScript
function parse(text: string, reviver?: Transformer, options?: ParseOptions): Object | null
```

解析JSON字符串生成ArkTS对象或null。解析过程中，每个键值对按从最内层到最外层的顺序依次经过reviver函数处理，返回值替换原始值； 当传入ParseOptions指定BigIntMode时，符合条件的整数将被解析为BigInt；当入参字符串为'null'时返回null。

**起始版本：** 12

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为12。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-json-function parse(text: string, reviver?: Transformer, options?: ParseOptions): Object | null--><!--Device-json-function parse(text: string, reviver?: Transformer, options?: ParseOptions): Object | null-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| text | string | 是 | 有效的JSON字符串，需符合JSON语法规范。 |
| reviver | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 否 | 转换函数，用于修改解析生成的原始值；当需要对解析结果进行自定义转换时使用。默认值是undefined。 |
| options | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 否 | 解析的配置选项，用于控制解析生成的类型。默认值是undefined。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Object | 当传入的字符串为'null'时，返回null。 |

