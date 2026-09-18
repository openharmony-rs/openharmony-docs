# getDefaultCellularDataSimId

## 导入模块

```TypeScript
import { data } from '@kit.TelephonyKit';
```

## getDefaultCellularDataSimId

```TypeScript
function getDefaultCellularDataSimId(): number
```

获取默认移动数据的SIM卡ID。

**起始版本：** 10

**系统能力：** SystemCapability.Telephony.CellularData

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 获取默认移动数据的SIM卡ID。<br>与SIM卡绑定，从1开始递增。<br>- 0：无SIM卡。<br>- 9999：esim场景下，默认移动数据的SIM卡ID为9999。<br>- 9 9999：天际通场景下，默认移动数据的SIM卡ID为99999。 |

**示例**

```TypeScript
import { data } from '@kit.TelephonyKit';

console.info("Result: "+ data.getDefaultCellularDataSimId());
```
