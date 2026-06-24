# isKeyExist

## isKeyExist

```TypeScript
function isKeyExist(keyAlias: string, options: HuksOptions, callback: AsyncCallback<boolean>): void
```

�ж���Կ�Ƿ���ڡ�ʹ��callback�첽�ص���

> **˵����**
>
> ��API version 8��ʼ֧�֣���API version 9��ʼ����������ʹ��
> [huks.isKeyItemExist<sup>9+</sup>](arkts-universalkeystore-huks-iskeyitemexist-f.md#isKeyItemExist-1)
> �����

**起始版本：** 8

**废弃版本：** 9

**替代接口：** isKeyItemExist(keyAlias:

**系统能力：** SystemCapability.Security.Huks.Extension

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| keyAlias | string | 是 | ������ҵ���Կ�ı����� |
| options | HuksOptions | 是 | ���ڲ�ѯʱָ����Կ������TAG�� |
| callback | AsyncCallback&lt;boolean&gt; | 是 | �ص�������false������Կ�����ڣ�true������Կ���ڡ� |

**示例：**

```TypeScript
import { huks } from '@kit.UniversalKeystoreKit';

/* 此处options选择emptyOptions来传空 */
let keyAlias = 'keyAlias';
let emptyOptions: huks.HuksOptions = {
  properties: []
};
huks.isKeyExist(keyAlias, emptyOptions, (err, data) => {
});

```


## isKeyExist

```TypeScript
function isKeyExist(keyAlias: string, options: HuksOptions): Promise<boolean>
```

�ж���Կ�Ƿ���ڡ�ʹ��Promise�첽�ص���

> **˵����**
>
> ��API version 8��ʼ֧�֣���API version 9��ʼ����������ʹ��
> [huks.isKeyItemExist<sup>9+</sup>](arkts-universalkeystore-huks-iskeyitemexist-f.md#isKeyItemExist-2)�����

**起始版本：** 8

**废弃版本：** 9

**替代接口：** isKeyItemExist(keyAlias:

**系统能力：** SystemCapability.Security.Huks.Extension

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| keyAlias | string | 是 | ������ҵ���Կ�ı����� |
| options | HuksOptions | 是 | ���ڲ�ѯʱָ����Կ������TAG�� |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;boolean&gt; | Promise����false������Կ�����ڣ�true������Կ���ڡ� |

**示例：**

```TypeScript
import { huks } from '@kit.UniversalKeystoreKit';

/* 此处options选择emptyOptions来传空 */
let keyAlias = 'keyAlias';
let emptyOptions: huks.HuksOptions = {
  properties: []
};
let result = huks.isKeyExist(keyAlias, emptyOptions);

```

