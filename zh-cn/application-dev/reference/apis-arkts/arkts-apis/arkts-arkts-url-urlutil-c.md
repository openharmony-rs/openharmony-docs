# URLUtil

```TypeScript
class URLUtil
```

URL相关工具类，提供URL相关的工具方法。

**起始版本：** 26.2.0

<!--Device-url-class URLUtil--><!--Device-url-class URLUtil-End-->

**系统能力：** SystemCapability.Utils.Lang

## 导入模块

```TypeScript
import { url } from '@kit.ArkTS';
```

## toString

```TypeScript
static toString(urlParams: URLParams): string
```

将指定的URLParams对象序列化为字符串，其中空格被百分比编码为%20（而非'+'）。

**起始版本：** 26.2.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.2.0开始，该接口支持在原子化服务中使用。

<!--Device-URLUtil-static toString(urlParams: URLParams): string--><!--Device-URLUtil-static toString(urlParams: URLParams): string-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| urlParams | [URLParams](arkts-arkts-url-urlparams-c.md) | 是 | 待序列化的URLParams对象。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | 返回序列化后的字符串，其中空格被编码为%20。 |
