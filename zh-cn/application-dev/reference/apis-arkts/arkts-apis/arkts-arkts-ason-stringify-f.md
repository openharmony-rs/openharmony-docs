# stringify

## 导入模块

```TypeScript
import { ArkTSUtils } from '@kit.ArkTS';
```

## stringify

```TypeScript
function stringify(value: Object | null | undefined): string
```

将ArkTS值转换为JavaScript对象表示法（JSON）字符串。额外支持Map和Set。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-ASON-function stringify(value: Object | null | undefined): string--><!--Device-ASON-function stringify(value: Object | null | undefined): string-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | Object \| null \| undefined | 是 | 要转换的值。<br>**起始版本：** 18 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | 该值的JSON字符串表示。 |

