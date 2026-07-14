# allocUninitialized

## allocUninitialized

```TypeScript
function allocUninitialized(size: number): FastBuffer
```

创建指定大小未初始化的FastBuffer对象，需要使用fill函数来初始化FastBuffer对象。

**起始版本：** 20

**元服务API：** 从API版本20开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| size | number | 是 | 指定的FastBuffer对象长度，单位：字节。取值范围：0 &lt;= size &lt;= UINT32_MAX。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| FastBuffer | 未初始化的FastBuffer实例。 |

**示例：**

```TypeScript
import { fastbuffer } from '@kit.ArkTS';

let buf = fastbuffer.allocUninitialized(10);
buf.fill(0);
// "buf":[0, 0, 0, 0, 0, 0, 0, 0, 0, 0]

```

