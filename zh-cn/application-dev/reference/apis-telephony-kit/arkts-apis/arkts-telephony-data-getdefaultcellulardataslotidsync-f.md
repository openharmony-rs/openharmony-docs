# getDefaultCellularDataSlotIdSync

## 导入模块

```TypeScript
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
| number | 获取默认移动数据的SIM卡。 |

**示例**

```TypeScript
import { data } from '@kit.TelephonyKit';

console.info("Result: "+ data.getDefaultCellularDataSlotIdSync())
```
