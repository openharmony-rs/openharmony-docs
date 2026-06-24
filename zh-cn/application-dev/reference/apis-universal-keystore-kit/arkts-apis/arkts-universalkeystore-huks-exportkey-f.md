# exportKey

## exportKey

```TypeScript
function exportKey(keyAlias: string, options: HuksOptions, callback: AsyncCallback<HuksResult>): void
```

������Կ��ʹ��Callback��ʽ�ص��첽���صĽ����

> **˵����**
>
> ��API version 8��ʼ֧�֣���API version 9��ʼ����������ʹ��
> [huks.exportKeyItem<sup>9+</sup>](arkts-universalkeystore-huks-exportkeyitem-f.md#exportKeyItem-1)
> �����

**起始版本：** 8

**废弃版本：** 9

**替代接口：** exportKeyItem(keyAlias:

**系统能力：** SystemCapability.Security.Huks.Extension

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| keyAlias | string | 是 | ��Կ������Ӧ��������Կ����ʱʹ�õı�����ͬ�� |
| options | HuksOptions | 是 | �ն��󣨴˴����ռ��ɣ��� |
| callback | AsyncCallback&lt;HuksResult&gt; | 是 | �ص���������������Կ�ɹ�ʱ��errΪundefined��dataΪ��ȡ����HuksResult������Ϊ�������HuksResult��<br/>outData���ش���Կ�е����Ĺ�Կ�� |

**示例：**

```TypeScript
import { huks } from '@kit.UniversalKeystoreKit';

/* 此处options选择emptyOptions来传空 */
let keyAlias = 'keyAlias';
let emptyOptions: huks.HuksOptions = {
  properties: []
};
huks.exportKey(keyAlias, emptyOptions, (err, data) => {
});

```


## exportKey

```TypeScript
function exportKey(keyAlias: string, options: HuksOptions): Promise<HuksResult>
```

������Կ��ʹ��Promise�첽�ص���

> **˵����**
>
> ��API version 8��ʼ֧�֣���API version 9��ʼ����������ʹ��
> [huks.exportKeyItem<sup>9+</sup>](arkts-universalkeystore-huks-exportkeyitem-f.md#exportKeyItem-2)�����

**起始版本：** 8

**废弃版本：** 9

**替代接口：** exportKeyItem(keyAlias:

**系统能力：** SystemCapability.Security.Huks.Extension

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| keyAlias | string | 是 | ��Կ������Ӧ��������Կ����ʱʹ�õı�����ͬ�� |
| options | HuksOptions | 是 | �ն��󣨴˴����ռ��ɣ��� |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;HuksResult&gt; | Promise���󣬷���HuksResult��HuksResult��outData���ش�HUKS�е����Ĺ�Կ�� |

**示例：**

```TypeScript
import { huks } from '@kit.UniversalKeystoreKit';

/* 此处options选择emptyOptions来传空 */
let keyAlias = 'keyAlias';
let emptyOptions: huks.HuksOptions = {
  properties: []
};
let result = huks.exportKey(keyAlias, emptyOptions);

```

