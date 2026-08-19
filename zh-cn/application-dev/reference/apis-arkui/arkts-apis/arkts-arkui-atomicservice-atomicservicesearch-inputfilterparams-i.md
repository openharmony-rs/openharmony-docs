# InputFilterParams

搜索框过滤设置项。

**起始版本：** 18

<!--Device-unnamed-export interface InputFilterParams--><!--Device-unnamed-export interface InputFilterParams-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
import { AtomicServiceSearch, InputFilterParams, SearchButtonParams, MenuAlignParams, SearchParams, SelectParams, OperationParams, } from '@kit.ArkUI';
```

## error

```TypeScript
error?: Callback<string>
```

正则匹配失败时，返回被过滤的内容。默认值为`undefined`。

**类型：** Callback&lt;string&gt;

**起始版本：** 18

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-InputFilterParams-error?: Callback<string>--><!--Device-InputFilterParams-error?: Callback<string>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## inputFilterValue

```TypeScript
inputFilterValue: ResourceStr
```

正则表达式。仅支持单个字符匹配，不支持字符串匹配。

**类型：** ResourceStr

**起始版本：** 18

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-InputFilterParams-inputFilterValue: ResourceStr--><!--Device-InputFilterParams-inputFilterValue: ResourceStr-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

