# parseSendable

## 导入模块

```TypeScript
import { JSON } from '@kit.ArkTS';
```

## parseSendable

```TypeScript
function parseSendable(text: string, reviver?: SendableTransformer, options?: ParseOptions): ISendable | null
```

解析JSON字符串，生成可直接跨并发实例（Worker或TaskPool）传递、无需拷贝的Sendable对象图。当解析后的JSON数据需要跨线程共享时，使用本接口替代[parse](arkts-arkts-json-parse-f.md)：解析结果直接创建于共享堆，调用返回后即可被各并发实例访问。

使用说明：&lt;ul&gt; &lt;li&gt;取值范围在"0"到"4294967294"之间的数字字符串键会作为元素下标存储；任意属性数量下所有键值均可完整访问与枚举。&lt;/li&gt; &lt;li&gt;重复键以后值为准，且枚举位置保持在首次出现的位置。&lt;/li&gt; &lt;li&gt;当options.parseReturnType为[MAP](arkts-arkts-json-parsereturntype-e.md#map)时，返回支持任意条数增删的Sendable Map；为[OBJECT](arkts-arkts-json-parsereturntype-e.md#object)（默认）时，返回不可扩展的Sendable对象，其已有属性可更新、不可新增或删除。&lt;/li&gt; &lt;/ul&gt;

**起始版本：** 26.0.1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.1开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| text | string | 是 | 有效的JSON字符串，需符合JSON语法规范。 |
| reviver | [SendableTransformer](arkts-arkts-json-sendabletransformer-t.md) | 否 | 用于转换结果的函数。当前仅接受undefined；传入函数将抛出TypeError（与ASON.parse一致）。默认值是undefined。 |
| options | [ParseOptions](arkts-arkts-json-parseoptions-i.md) | 否 | 解析的配置选项。也可传入仅含bigIntMode的既有ParseOptions对象（此时parseReturnType默认为OBJECT）。默认值是undefined。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [ISendable](arkts-arkts-json-isendable-t.md) &#124; null | 返回与JSON文本对应的Sendable对象图；当JSON文本为'null'时返回null；当options.parseReturnType为[MAP](arkts-arkts-json-parsereturntype-e.md#map)时返回Sendable Map。 |
