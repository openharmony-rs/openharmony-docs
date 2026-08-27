# getActiveApnName

## 导入模块

```TypeScript
```

## getActiveApnName

```TypeScript
function getActiveApnName(): Promise<string>
```

异步获取默认移动数据SIM卡对应的处于激活状态的数据业务APN（access point name，接入点名称）name信息，若不处于激活状态，返回为空字符串。

**起始版本：** 20

**需要权限：** ohos.permission.GET_NETWORK_INFO

**系统能力：** SystemCapability.Telephony.CellularData

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise & lt;string & gt; | Promise对象，返回默认移动数据SIM卡对应的处于激活状态的数据业务APN name信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |

**示例**

```TypeScript
import { data } from '@kit.TelephonyKit';
import { BusinessError } from '@kit.BasicServicesKit';

data.getActiveApnName().then((apn: string) => {
    console.info(`getActiveApnName success, apn: ${apn}`);
}).catch((err: BusinessError) => {
    console.error(`getActiveApnName failed. code: ${err.code}, message: ${err.message}`);
});
```
