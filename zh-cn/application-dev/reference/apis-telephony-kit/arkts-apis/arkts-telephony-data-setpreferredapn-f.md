# setPreferredApn

## 导入模块

```TypeScript
import { data } from '@kit.TelephonyKit';
```

## setPreferredApn

```TypeScript
function setPreferredApn(apnId: int): Promise<boolean>
```

异步设置apnId对应的APN为首选APN。 > 注意: > > 如果传入的apnId为无效的apnId，切回运营商默认配置的优选Apn。

**起始版本：** 23

**需要权限：** ohos.permission.MANAGE_APN_SETTING

<!--Device-data-function setPreferredApn(apnId: int): Promise<boolean>--><!--Device-data-function setPreferredApn(apnId: int): Promise<boolean>-End-->

**系统能力：** SystemCapability.Telephony.CellularData

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| apnId | int | 是 | 要设置的apnId，可以通过[queryApnIds](arkts-telephony-data-queryapnids-f.md)查询。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;boolean&gt; | Promise对象，返回设置的结果，在未插卡时会返回false。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |

**示例**

```TypeScript
import { data } from '@kit.TelephonyKit';
import { BusinessError } from '@kit.BasicServicesKit';

let apnId: number = 0; // apnId为通过queryApnIds返回的有效值，setPreferredApn传入无效的apnId会切回运营商默认配置的优选APN。
data.setPreferredApn(apnId).then((result: boolean) => {
    console.info(`setPreferredApn result: ${result}`);
}).catch((err: BusinessError) => {
    console.error(`setPreferredApn failed. code: ${err.code}, message: ${err.message}`);
});
```

