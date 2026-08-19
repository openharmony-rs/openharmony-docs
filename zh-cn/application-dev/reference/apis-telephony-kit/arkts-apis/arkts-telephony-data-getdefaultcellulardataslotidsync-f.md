# getDefaultCellularDataSlotIdSync

## 导入模块

```TypeScript
import { data } from '@kit.TelephonyKit';
```

## getDefaultCellularDataSlotIdSync

```TypeScript
function getDefaultCellularDataSlotIdSync(): int
```

获取默认移动数据的SIM卡。

**起始版本：** 23

<!--Device-data-function getDefaultCellularDataSlotIdSync(): int--><!--Device-data-function getDefaultCellularDataSlotIdSync(): int-End-->

**系统能力：** SystemCapability.Telephony.CellularData

**返回值：**

| 类型 | 说明 |
| --- | --- |
| int | 获取默认移动数据的SIM卡。&lt;br /&gt;- 0：卡槽1。 &lt;br /&gt;- 1：卡槽2。&lt;br /&gt;- 2：esim和天际通场景下，默认移动数据的slotId为2。 |

**示例**

```TypeScript
import { data } from '@kit.TelephonyKit';

console.info("Result: "+ data.getDefaultCellularDataSlotIdSync())
```

