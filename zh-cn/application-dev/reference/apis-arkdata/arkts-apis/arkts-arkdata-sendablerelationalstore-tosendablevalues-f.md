# toSendableValues

## toSendableValues

```TypeScript
function toSendableValues(values: NonSendableValues): collections.Array<ValueType>
```

将不可跨线程传递的数组数据，转换为可跨线程传递的数组数据。

**起始版本：** 20

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为20。

<!--Device-sendableRelationalStore-function toSendableValues(values: NonSendableValues): collections.Array<ValueType>--><!--Device-sendableRelationalStore-function toSendableValues(values: NonSendableValues): collections.Array<ValueType>-End-->

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| values | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 不可跨线程传递的数组数据。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| collections.Array&lt;ValueType&gt; | 可跨线程传递的数组数据。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [14800000](../../apis-basic-services-kit/errorcode-settings.md#14800000-参数检查失败) | Inner error. |

**示例：**

```TypeScript
import { relationalStore, sendableRelationalStore } from '@kit.ArkData';
const array: relationalStore.ValueType[] = [];
array.push(1);
array.push(2);
array.push("aaaaaa")
const values = sendableRelationalStore.toSendableValues(array);
```

