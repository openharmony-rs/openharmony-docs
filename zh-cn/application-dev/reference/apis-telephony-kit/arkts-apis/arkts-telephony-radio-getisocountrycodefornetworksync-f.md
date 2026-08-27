# getISOCountryCodeForNetworkSync

## 导入模块

```TypeScript
```

## getISOCountryCodeForNetworkSync

```TypeScript
function getISOCountryCodeForNetworkSync(slotId: number): string
```

获取注册网络所在国家的ISO国家码。

**起始版本：** 10

**系统能力：** SystemCapability.Telephony.CoreService

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| slotId | number | 是 | 卡槽ID。   - 0：卡槽1。   - 1：卡槽2。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | 返回注册网络所在国家的ISO国家码，例如CN(中国)。如果设备没有注册任何网络，接口返回空字符串。 |

**示例**

```TypeScript
let slotId: number = 0;
let countryISO: string = radio.getISOCountryCodeForNetworkSync(slotId);
console.info(`the country ISO is:` + countryISO);
```
