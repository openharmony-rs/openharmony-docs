# allocUninitializedFromPool

## allocUninitializedFromPool

```TypeScript
function allocUninitializedFromPool(size: number): FastBuffer
```

从缓冲池中创建指定大小未初始化的FastBuffer对象。调用[fill]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_函数初始化该对象。

**起始版本：** 20

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为20。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-fastbuffer-function allocUninitializedFromPool(size: number): FastBuffer--><!--Device-fastbuffer-function allocUninitializedFromPool(size: number): FastBuffer-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| size | number | 是 | 指定的FastBuffer对象长度，单位：字节。取值范围：0 <= size <= UINT32\_\_\_ESCAPED\_UNDERSCORE\_\_\_MAX。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| \_\_\_MD\_LINK\_USD\_0\_\_\_ | 未初始化的FastBuffer实例。 |

**示例：**

```TypeScript
import { fastbuffer } from '@kit.ArkTS';

let buf = fastbuffer.allocUninitializedFromPool(10);
buf.fill(0);
// "buf":[0, 0, 0, 0, 0, 0, 0, 0, 0, 0]
```

