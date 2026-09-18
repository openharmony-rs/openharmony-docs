# getDefaultCellularDataSlotIdSync

## 导入模块

```TypeScript
import { data } from '@kit.TelephonyKit';
```

## getDefaultCellularDataSlotIdSync

```TypeScript
function getDefaultCellularDataSlotIdSync(): number
```

获取默认移动数据的SIM卡。

**起始版本：** 9

**系统能力：** SystemCapability.Telephony.CellularData

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 获取默认移动数据的SIM卡。<br>- 0：卡槽1。 <br>- 1：卡槽2。<br>- 2：esim和天际通场景下，默认移动数据的slotId为2。 |

**示例**

```TypeScript
import { data } from '@kit.TelephonyKit';

console.info("Result: "+ data.getDefaultCellularDataSlotIdSync())
```
