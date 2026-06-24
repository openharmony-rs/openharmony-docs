# deleteKey

## deleteKey

```TypeScript
function deleteKey(keyAlias: string, options: HuksOptions, callback: AsyncCallback<HuksResult>): void
```

ɾ����Կ��ʹ��callback�첽�ص���

> **˵����**
>
> ��API version 8��ʼ֧�֣���API version 9��ʼ����������ʹ��
> [huks.deleteKeyItem<sup>9+</sup>](arkts-universalkeystore-huks-deletekeyitem-f.md#deleteKeyItem-1)
> �����

**起始版本：** 8

**废弃版本：** 9

**替代接口：** deleteKeyItem(keyAlias:

**系统能力：** SystemCapability.Security.Huks.Extension

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| keyAlias | string | 是 | ��Կ������ӦΪ����keyʱ����ı����� |
| options | HuksOptions | 是 | ����ɾ��ʱָ����Կ������TAG�� |
| callback | AsyncCallback&lt;HuksResult&gt; | 是 | �ص���������ɾ����Կ�ɹ�ʱ��errΪundefined��dataΪ��ȡ����HuksResult������Ϊ������� |

**示例：**

```TypeScript
import { huks } from '@kit.UniversalKeystoreKit';

/* 此处options选择emptyOptions传空 */
let keyAlias = 'keyAlias';
let emptyOptions: huks.HuksOptions = {
  properties: []
};
huks.deleteKey(keyAlias, emptyOptions, (err, data) => {
});

```


## deleteKey

```TypeScript
function deleteKey(keyAlias: string, options: HuksOptions): Promise<HuksResult>
```

ɾ����Կ��ʹ��Promise�첽�ص���

> **˵����**
>
> ��API version 8��ʼ֧�֣���API version 9��ʼ����������ʹ��
> [huks.deleteKeyItem<sup>9+</sup>](arkts-universalkeystore-huks-deletekeyitem-f.md#deleteKeyItem-2)�����

**起始版本：** 8

**废弃版本：** 9

**替代接口：** deleteKeyItem(keyAlias:

**系统能力：** SystemCapability.Security.Huks.Extension

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| keyAlias | string | 是 | ��Կ������ӦΪ����keyʱ����ı����� |
| options | HuksOptions | 是 | ����ɾ��ʱָ����Կ������TAG�� |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;HuksResult&gt; | Promise���󣬷���HuksResult�� |

**示例：**

```TypeScript
import { huks } from '@kit.UniversalKeystoreKit';
import { BusinessError } from "@kit.BasicServicesKit"

/* 此处options选择emptyOptions传空 */
let keyAlias = 'keyAlias';
let emptyOptions: huks.HuksOptions = {
  properties: []
};
let result = huks.deleteKey(keyAlias, emptyOptions).then((data) => {
  console.info('delete key success');
}).catch((err: BusinessError) => {
  console.error("密钥删除失败，错误码是： " + err.code + " 错误码信息： " + err.message);
});

```

