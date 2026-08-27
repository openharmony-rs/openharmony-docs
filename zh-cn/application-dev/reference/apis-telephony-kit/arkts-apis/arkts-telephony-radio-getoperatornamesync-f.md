# getOperatorNameSync

## 导入模块

```TypeScript
```

## getOperatorNameSync

```TypeScript
function getOperatorNameSync(slotId: number): string
```

获取运营商名称。

**起始版本：** 10

**系统能力：** SystemCapability.Telephony.CoreService

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| slotId | number | 是 | 卡槽ID。   - 0：卡槽1。   - 1：卡槽2。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | 返回运营商名称。例如：中国移动。 |

**示例**

```TypeScript
let slotId: number = 0;
let operatorName: string = radio.getOperatorNameSync(slotId);
console.info(`operator name is:` + operatorName);
```
