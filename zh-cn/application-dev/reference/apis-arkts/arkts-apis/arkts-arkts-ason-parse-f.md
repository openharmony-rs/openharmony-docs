# parse

## 导入模块

```TypeScript
import { ArkTSUtils } from '@kit.ArkTS';
```

## parse

```TypeScript
function parse(text: string, reviver?: Transformer, options?: ParseOptions): ISendable | null
```

用于解析JSON字符串生成ISendable数据或null。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| text | string | 是 | 有效的JSON字符串。 |
| reviver | Transformer | 否 | 转换函数，传入该参数，可以用来修改解析生成的原始值。默认值是undefined。该参数目前仅支持传入undefined值，其他值会被忽略或视为无效。 |
| options | ParseOptions | 否 | 解析的配置，传入该参数，可以用来控制解析生成的结果类型。默认值是undefined。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| ISendable \| null | 返回ISendable数据或null。入参为null时，返回null。 |
