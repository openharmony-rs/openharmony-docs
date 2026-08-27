# getDefaultCellularDataSimId

## 导入模块

```TypeScript
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
| number | 获取默认移动数据的SIM卡ID。 |

**示例**

```TypeScript
import { data } from '@kit.TelephonyKit';

console.info("Result: "+ data.getDefaultCellularDataSimId());
```
