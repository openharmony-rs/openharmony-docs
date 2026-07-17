# generateRandomUUID

## 导入模块

```TypeScript
import { util } from '@kit.ArkTS';
```

## generateRandomUUID

```TypeScript
function generateRandomUUID(entropyCache?: boolean): string
```

使用安全随机数生成器生成 RFC 4122 版本 4 的随机通用唯一识别码（UUID，字符串类型）。为了提升性能，本接口默认使用缓存的 uuid，其中 **entropyCache** 设置为 **true**。最多可缓存 128 个随机 uuid。当缓存的 128 个 uuid 全部用完后，会再生成一组新的 uuid 以保持随机分布。如果不需要使用缓存的 uuid，可将 **entropyCache** 设置为 **false**。

**起始版本：** 9

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-util-function generateRandomUUID(entropyCache?: boolean): string--><!--Device-util-function generateRandomUUID(entropyCache?: boolean): string-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| entropyCache | boolean | 否 | 是否使用缓存的 uuid。值为 **true** 表示使用缓存的 uuid，值为 **false** 表示相反的情况。默认值为 **true**。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | 表示所生成 uuid 的字符串。 |

**示例：**

```TypeScript
let uuid = util.generateRandomUUID(true);
console.info("RFC 4122 Version 4 UUID:" + uuid);
// 输出随机生成的UUID

```

