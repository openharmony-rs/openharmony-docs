# fromSendableValues

## fromSendableValues

```TypeScript
function fromSendableValues(values: collections.Array<ValueType>): NonSendableValues
```

将可跨线程传递的数组数据，转换为不可跨线程传递的数组数据。

**起始版本：** 20

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为20。

<!--Device-sendableRelationalStore-function fromSendableValues(values: collections.Array<ValueType>): NonSendableValues--><!--Device-sendableRelationalStore-function fromSendableValues(values: collections.Array<ValueType>): NonSendableValues-End-->

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| values | collections.Array&lt;ValueType&gt; | 是 | 可跨线程传递的数组数据。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| \_\_\_MD\_LINK\_USD\_0\_\_\_ | 不可跨线程传递的数组数据。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [14800000](../../apis-basic-services-kit/errorcode-settings.md#14800000-参数检查失败) | Inner error. |

**示例：**

```TypeScript
import { sendableRelationalStore } from '@kit.ArkData';
import { collections } from '@kit.ArkTS';
const array = new collections.Array<sendableRelationalStore.ValueType>();
array.push("a");
array.push("b");
array.push(1);
array.push(2);
const values = sendableRelationalStore.fromSendableValues(array);
```

