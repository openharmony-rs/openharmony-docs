# isKeyItemExist

## isKeyItemExist

```TypeScript
function isKeyItemExist(keyAlias: string, options: HuksOptions, callback: AsyncCallback<boolean>): void
```

�ж���Կ�Ƿ���ڡ�ʹ��callback�첽�ص���

����Կ�����ڣ����׳�������Ϊ12000011���쳣��

**起始版本：** 9

**系统能力：** SystemCapability.Security.Huks.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| keyAlias | string | 是 | ������ҵ���Կ�ı����� |
| options | HuksOptions | 是 | ���ڲ�ѯʱָ����Կ������TAG����ʹ��[HuksAuthStorageLevel](arkts-universalkeystore-huks-huksauthstoragelevel-e.md#HuksAuthStorageLevel)ָ�����ѯ��Կ��<br/>��ȫ����<br/>�ɴ��գ���API version �� 12ʱ������Ĭ��ΪCE����API version �� 12ʱ������Ĭ��ΪDE�� |
| callback | AsyncCallback&lt;boolean&gt; | 是 | �ص���������Կ����ʱ��dataΪtrue����Կ������ʱ��dataΪundefined��err�еĴ�����Ϊ12000011����������Ӧ��������<br/>�� |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-Parameter) | Parameter error. Possible causes:<br/>1. Mandatory parameters are left unspecified.<br/>2. Incorrect parameter types.<br/>3. Parameter verification failed. |
| [801](../../errorcode-universal.md#801-api) | api is not supported |
| [12000004](../../errorcode-universal.md#12000004-operating) | operating file failed |
| [12000005](../../errorcode-universal.md#12000005-IPC) | IPC communication failed |
| [12000006](../../errorcode-universal.md#12000006-error) | error occurred in crypto engine |
| [12000011](../../errorcode-universal.md#12000011-queried) | queried entity does not exist |
| [12000012](../../errorcode-universal.md#12000012-Device) | Device environment or input parameter abnormal |
| [12000014](../../errorcode-universal.md#12000014-memory) | memory is insufficient |
| [12000018](../../errorcode-universal.md#12000018-the) | the group id specified by the access group tag is invalid&lt;br&gt;**适用版本：** 23+ |

**示例：**

ArkTS示例：

```TypeScript
import { huks } from '@kit.UniversalKeystoreKit';

/* 此处options选择emptyOptions来传空 */
let keyAlias = 'keyAlias';
let emptyOptions: huks.HuksOptions = {
  properties: []
};

huks.isKeyItemExist(keyAlias, emptyOptions, (error, data) => {
  if (error) {
    console.error(`callback: isKeyItemExist failed`);
  } else {
    if (data) {
      console.info(`keyAlias:${keyAlias} is existed!`);
    } else {
      console.error(`find key failed`);
    }
  }
});

```

JS示例代码仅供轻量级设备使用。

```TypeScript
<stack class="container">
    <input type="button" class="existBtn" @click="existKey">查询密钥</input>
    <text class="result">{{result}}</text>
</stack>

```

```TypeScript
.container {
  width: 454px;
  height: 800px;
  background-color: #ffffffff;
}

.existBtn {
  left: 77px;
  top: 100px;
  width: 300px;
  height: 80px;
  text-align: center;
  color: white;
  background-color: orange;
  font-size: 25px;
}

.result {
  left: 30px;
  top: 190px;
  width: 390px;
  height: 80px;
  text-align: center;
  color: #ff000000;
  background-color: #ffffffff;
  font-size: 25px;
}

```

```TypeScript
import huks from '@ohos.security.huks';

function testKeyExist() {
    let huksInfo;
    let keyAlias = 'keyAlias';
    let emptyOptions = {
        properties: []
    };

    huks.isKeyItemExist(keyAlias, emptyOptions, (err, data) => {
        if (err) {
            huksInfo = 'isKeyItemExist failed, code: ' + err.code + ', message: ' + err.message;
            console.error(huksInfo);
        } else {
            if (data) {
                huksInfo = `key: ${keyAlias} exists`;
                console.info(huksInfo);
            } else {
                huksInfo = 'key does not exist';
                console.error(huksInfo);
            }
        }
    });
    return huksInfo;
}

export default {
    data: {
        result: ''
    },

    existKey() {
        this.result = testKeyExist();
    },
};


```


## isKeyItemExist

```TypeScript
function isKeyItemExist(keyAlias: string, options: HuksOptions): Promise<boolean>
```

�ж���Կ�Ƿ���ڡ�ʹ��Promise�첽�ص���

����Կ�����ڣ����׳�������Ϊ12000011���쳣��

**起始版本：** 9

**系统能力：** SystemCapability.Security.Huks.Extension

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| keyAlias | string | 是 | ������ҵ���Կ�ı����� |
| options | HuksOptions | 是 | ���ڲ�ѯʱָ����Կ������TAG����ʹ��[HuksAuthStorageLevel](arkts-universalkeystore-huks-huksauthstoragelevel-e.md#HuksAuthStorageLevel)ָ�����ѯ��Կ��<br/>��ȫ����<br/>�ɴ��գ���API version �� 12ʱ������Ĭ��ΪCE����API version �� 12ʱ������Ĭ��ΪDE�� |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;boolean&gt; | Promise������Կ����ʱ��dataΪtrue����Կ������ʱ��err�еĴ�����Ϊ12000011����������Ӧ���������� |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-Parameter) | Parameter error. Possible causes:<br/>1. Mandatory parameters are left unspecified.<br/>2. Incorrect parameter types.<br/>3. Parameter verification failed. |
| [801](../../errorcode-universal.md#801-api) | api is not supported |
| [12000004](../../errorcode-universal.md#12000004-operating) | operating file failed |
| [12000005](../../errorcode-universal.md#12000005-IPC) | IPC communication failed |
| [12000006](../../errorcode-universal.md#12000006-error) | error occurred in crypto engine |
| [12000011](../../errorcode-universal.md#12000011-queried) | queried entity does not exist |
| [12000012](../../errorcode-universal.md#12000012-Device) | Device environment or input parameter abnormal |
| [12000014](../../errorcode-universal.md#12000014-memory) | memory is insufficient |
| [12000018](../../errorcode-universal.md#12000018-the) | the group id specified by the access group tag is invalid&lt;br&gt;**适用版本：** 23+ |

**示例：**

```TypeScript
import { huks } from '@kit.UniversalKeystoreKit';

/* 此处options选择emptyOptions来传空 */
let keyAlias = 'keyAlias';
let emptyOptions: huks.HuksOptions = {
  properties: []
};

huks.isKeyItemExist(keyAlias, emptyOptions).then(() => {
  console.info(`keyAlias:${keyAlias} is existed!`);
});

```

