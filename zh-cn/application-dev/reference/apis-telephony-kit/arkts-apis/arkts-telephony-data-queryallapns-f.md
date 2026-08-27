# queryAllApns

## 导入模块

```TypeScript
```

## queryAllApns

```TypeScript
function queryAllApns(): Promise<Array<ApnInfo>>
```

异步获取默认移动数据的SIM卡的APN（access point name，接入点名称）信息。

**起始版本：** 16

**需要权限：** ohos.permission.MANAGE_APN_SETTING

**系统能力：** SystemCapability.Telephony.CellularData

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Array&lt;[ApnInfo](arkts-telephony-data-apninfo-i.md)&gt;&gt; | Promise对象，返回默认移动数据的SIM卡的APN信息列表。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |

**示例**

```TypeScript
import { data } from '@kit.TelephonyKit';
import { BusinessError } from '@kit.BasicServicesKit';

data.queryAllApns().then((apnInfos: Array<data.ApnInfo>) => {
    console.info(`queryAllApns success, promise: apnInfos->${JSON.stringify(apnInfos)}`);
}).catch((err: BusinessError) => {
    console.error(`queryAllApns failed. code: ${err.code}, message: ${err.message}`);
});
```
