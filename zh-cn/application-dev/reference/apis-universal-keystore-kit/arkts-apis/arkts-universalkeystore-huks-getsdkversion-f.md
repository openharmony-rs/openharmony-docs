# getSdkVersion

## 导入模块

```TypeScript
import { huks } from '@kit.UniversalKeystoreKit';
```

## getSdkVersion

```TypeScript
function getSdkVersion(options: HuksOptions): string
```

获取当前系统sdk版本。

> **说明：**  
>  
> 从API version 8开始支持，从API version 11开始废弃。

**起始版本：** 8

**废弃版本：** 11

<!--Device-huks-function getSdkVersion(options: HuksOptions): string--><!--Device-huks-function getSdkVersion(options: HuksOptions): string-End-->

**系统能力：** SystemCapability.Security.Huks.Extension

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [HuksOptions](arkts-universalkeystore-huks-huksoptions-i.md) | 是 | 空对象（此处传空即可）。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | 返回sdk版本。 |

**示例：**

```TypeScript
import { huks } from '@kit.UniversalKeystoreKit';

/* 此处options选择emptyOptions传空 */
let emptyOptions: huks.HuksOptions = {
  properties: []
};
let result = huks.getSdkVersion(emptyOptions);

```

