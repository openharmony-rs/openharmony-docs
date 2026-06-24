# getSdkVersion

## getSdkVersion

```TypeScript
function getSdkVersion(options: HuksOptions): string
```

��ȡ��ǰϵͳsdk�汾��

> **˵����**
>
> ��API version 8��ʼ֧�֣���API version 11��ʼ������

**起始版本：** 8

**废弃版本：** 11

**系统能力：** SystemCapability.Security.Huks.Extension

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | HuksOptions | 是 | �ն��󣨴˴����ռ��ɣ��� |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | ����sdk�汾�� |

**示例：**

```TypeScript
import { huks } from '@kit.UniversalKeystoreKit';

/* 此处options选择emptyOptions传空 */
let emptyOptions: huks.HuksOptions = {
  properties: []
};
let result = huks.getSdkVersion(emptyOptions);

```

