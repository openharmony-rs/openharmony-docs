# getKeyProperties

## getKeyProperties

```TypeScript
function getKeyProperties(keyAlias: string, options: HuksOptions, callback: AsyncCallback<HuksResult>): void
```

��ȡ��Կ���ԡ�ʹ��callback�첽�ص���

> **˵����**
>
> ��API version 8��ʼ֧�֣���API version 9��ʼ����������ʹ��
> [huks.getKeyItemProperties<sup>9+</sup>](arkts-universalkeystore-huks-getkeyitemproperties-f.md#getKeyItemProperties-1)
> �����

**起始版本：** 8

**废弃版本：** 9

**替代接口：** getKeyItemProperties(

**系统能力：** SystemCapability.Security.Huks.Extension

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| keyAlias | string | 是 | ��Կ������Ӧ��������Կ����ʱʹ�õı�����ͬ�� |
| options | HuksOptions | 是 | �ն��󣨴˴����ռ��ɣ��� |
| callback | AsyncCallback&lt;HuksResult&gt; | 是 | �ص�����������ȡ��Կ���Գɹ�ʱ��errΪundefined��dataΪ��ȡ����HuksResult������Ϊ������� |

**示例：**

```TypeScript
import { huks } from '@kit.UniversalKeystoreKit';

/* 此处options选择emptyOptions来传空 */
let keyAlias = 'keyAlias';
let emptyOptions: huks.HuksOptions = {
  properties: []
};
huks.getKeyProperties(keyAlias, emptyOptions, (err, data) => {
});

```


## getKeyProperties

```TypeScript
function getKeyProperties(keyAlias: string, options: HuksOptions): Promise<HuksResult>
```

��ȡ��Կ���ԡ�ʹ��Promise�첽�ص���

> **˵����**
>
> ��API version 8��ʼ֧�֣���API version 9��ʼ����������ʹ��
> [huks.getKeyItemProperties<sup>9+</sup>](arkts-universalkeystore-huks-getkeyitemproperties-f.md#getKeyItemProperties-2)
> �����

**起始版本：** 8

**废弃版本：** 9

**替代接口：** getKeyItemProperties(keyAlias:

**系统能力：** SystemCapability.Security.Huks.Extension

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| keyAlias | string | 是 | ��Կ������Ӧ��������Կ����ʱʹ�õı�����ͬ�� |
| options | HuksOptions | 是 | �ն��󣨴˴����ռ��ɣ��� |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;HuksResult&gt; | Promise���󣬷���HuksResult��HuksResult��properties������Կ������ |

**示例：**

```TypeScript
import { huks } from '@kit.UniversalKeystoreKit';

/* 此处options选择emptyOptions来传空 */
let keyAlias = 'keyAlias';
let emptyOptions: huks.HuksOptions = {
  properties: []
};
let result = huks.getKeyProperties(keyAlias, emptyOptions);

```

