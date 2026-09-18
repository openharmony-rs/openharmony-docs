# convertUuid

## 导入模块

```TypeScript
import { access } from '@kit.ConnectivityKit';
```

## convertUuid

```TypeScript
function convertUuid(uuid: string): string
```

将指定格式的的UUID转换为128bit的UUID。

常用的UUID格式主要包括16bit、32bit和128bit三种格式。蓝牙协议定义的128bit格式的基准UUID为：00000000-0000-1000-8000-00805f9b34fb。若输入16bit或者32bit的UUID，将基于蓝牙基准UUID进行转换。若输入128bit的UUID，将不做转换直接输出该UUID。

若输入16bit的UUID，例如“1801”，将输出“00001801-0000-1000-8000-00805f9b34fb”。若输入32bit的UUID，例如“12341801”，将输出“12341801-0000-1000-8000-00805f9b34fb”。若输入128bit的UUID，例如“11112222-3333-4444-5555-666677778888”，将直接输出该UUID。若输入不符合以上格式的UUID或包含非16进制范围内的字符，将返回401错误码。

**起始版本：** 22

**系统能力：** SystemCapability.Communication.Bluetooth.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| uuid | string | 是 | 16bit、32bit、128bit的UUID。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | 转换后的128bit的UUID。 |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

try {
    let inputUuid: string = '1801';
    let convertedUuid: string = access.convertUuid(inputUuid);
    console.info("convertedUuid: " + convertedUuid);
} catch (err) {
    console.error('errCode: ' + (err as BusinessError).code + ', errMessage: ' + (err as BusinessError).message);
}
```
