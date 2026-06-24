# abort

## abort

```TypeScript
function abort(handle: number, options: HuksOptions, callback: AsyncCallback<HuksResult>): void
```

abort��ֹ��Կ������ʹ��callback�첽�ص���

> **˵����**
>
> ��API version 8��ʼ֧�֣���API version 9��ʼ����������ʹ��
> [huks.abortSession<sup>9+</sup>](arkts-universalkeystore-huks-abortsession-f.md#abortSession-1)
> �����

**起始版本：** 8

**废弃版本：** 9

**替代接口：** abortSession(handle:

**系统能力：** SystemCapability.Security.Huks.Extension

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| handle | number | 是 | Abort������uint64���͵�handleֵ�� |
| options | HuksOptions | 是 | Abort�����Ĳ������ϡ� |
| callback | AsyncCallback&lt;HuksResult&gt; | 是 | �ص�����������Կ����abort�ɹ�ʱ��errΪundefined��dataΪ��ȡ����HuksResult������Ϊ������� |

**示例：**

```TypeScript
import { huks } from '@kit.UniversalKeystoreKit';

/* huks.init、huks.update、huks.finish为三段式接口，需要一起使用，
 * 当这三个操作中的任一阶段发生错误时，都需要调用huks.abort来终止密钥的使用
 *
 * 以下以RSA2048密钥的callback操作使用为例
 */

let keyAlias = "HuksDemoRSA";
let properties: Array<huks.HuksParam> = [];
let options: huks.HuksOptions = {
  properties: properties,
  inData: new Uint8Array(0)
};
let handle: number = 0;
let resultMessage = "";

async function generateKey() {
  properties = [{
    tag: huks.HuksTag.HUKS_TAG_ALGORITHM,
    value: huks.HuksKeyAlg.HUKS_ALG_RSA
  }, {
    tag: huks.HuksTag.HUKS_TAG_KEY_SIZE,
    value: huks.HuksKeySize.HUKS_RSA_KEY_SIZE_2048
  }, {
    tag: huks.HuksTag.HUKS_TAG_PURPOSE,
    value: huks.HuksKeyPurpose.HUKS_KEY_PURPOSE_ENCRYPT
  }, {
    tag: huks.HuksTag.HUKS_TAG_PADDING,
    value: huks.HuksKeyPadding.HUKS_PADDING_OAEP
  }, {
    tag: huks.HuksTag.HUKS_TAG_DIGEST,
    value: huks.HuksKeyDigest.HUKS_DIGEST_SHA256
  }];
  huks.generateKey(keyAlias, options);
}

function stringToUint8Array(str: string) {
  let arr: number[] = [];
  for (let i = 0, j = str.length; i < j; ++i) {
    arr.push(str.charCodeAt(i));
  }
  let tmpUint8Array = new Uint8Array(arr);
  return tmpUint8Array;
}

async function huksInit() {
  await huks.init(keyAlias, options).then((data) => {
    console.info(`test init data: ${JSON.stringify(data)}`);
    handle = data.handle;
  });
}

async function huksUpdate() {
  options.inData = stringToUint8Array("huksHmacTest");
  await huks.update(handle, options.inData, options).then((data) => {
    if (data.errorCode === 0) {
      resultMessage += "update success!";
    } else {
      resultMessage += "update fail!";
    }
  });
  console.info(resultMessage);
}

function huksFinish() {
  options.inData = stringToUint8Array("HuksDemoHMAC");
  huks.finish(handle, options).then((data) => {
    if (data.errorCode === 0) {
      resultMessage = "finish success!";
      console.info(resultMessage);
    } else {
      resultMessage = "finish fail errorCode: " + data.errorCode;
      console.error(resultMessage);
    }
  });
}

async function huksAbort() {
  new Promise<huks.HuksResult>((resolve, reject) => {
    huks.abort(handle, options, (err, data) => {
      console.info(`huksAbort data ${JSON.stringify(data)}`);
      console.error(`huksAbort err ${JSON.stringify(err)}`);
    });
  });
}

```


## abort

```TypeScript
function abort(handle: number, options: HuksOptions): Promise<HuksResult>
```

abort��ֹ��Կ������ʹ��Promise�첽�ص���

> **˵����**
>
> ��API version 8��ʼ֧�֣���API version 9��ʼ����������ʹ��
> [huks.abortSession<sup>9+</sup>](arkts-universalkeystore-huks-abortsession-f.md#abortSession-2)�����

**起始版本：** 8

**废弃版本：** 9

**替代接口：** abortSession(handle:

**系统能力：** SystemCapability.Security.Huks.Extension

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| handle | number | 是 | Abort������uint64���͵�handleֵ�� |
| options | HuksOptions | 是 | Abort�����Ĳ������ϡ� |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;HuksResult&gt; | Promise���󣬷���HuksResult�� |

**示例：**

```TypeScript
import { huks } from '@kit.UniversalKeystoreKit';

/* huks.init、huks.update、huks.finish为三段式接口，需要一起使用，
 * 当这三个操作中的任一阶段发生错误时，都需要调用huks.abort来终止密钥的使用
 *
 * 以下以RSA2048密钥的promise操作使用为例
 */
let keyAlias = "HuksDemoRSA";
let properties: Array<huks.HuksParam> = [];
let options: huks.HuksOptions = {
  properties: properties,
  inData: new Uint8Array(0)
};
let handle: number = 0;
let resultMessage = "";

function stringToUint8Array(str: string) {
  let arr: number[] = [];
  for (let i = 0, j = str.length; i < j; ++i) {
    arr.push(str.charCodeAt(i));
  }
  let tmpUint8Array = new Uint8Array(arr);
  return tmpUint8Array;
}

async function generateKey() {
  properties = [{
    tag: huks.HuksTag.HUKS_TAG_ALGORITHM,
    value: huks.HuksKeyAlg.HUKS_ALG_RSA
  }, {
    tag: huks.HuksTag.HUKS_TAG_KEY_SIZE,
    value: huks.HuksKeySize.HUKS_RSA_KEY_SIZE_2048
  }, {
    tag: huks.HuksTag.HUKS_TAG_PURPOSE,
    value: huks.HuksKeyPurpose.HUKS_KEY_PURPOSE_ENCRYPT
  }, {
    tag: huks.HuksTag.HUKS_TAG_PADDING,
    value: huks.HuksKeyPadding.HUKS_PADDING_OAEP
  }, {
    tag: huks.HuksTag.HUKS_TAG_DIGEST,
    value: huks.HuksKeyDigest.HUKS_DIGEST_SHA256
  }];
  huks.generateKey(keyAlias, options, (err, data) => {
    if (data.errorCode === 0) {
      resultMessage = "generate success!";
    } else {
      resultMessage = "generate fail errorCode: " + data.errorCode;
    }
  });
}

async function huksInit() {
  return new Promise<huks.HuksHandle>((resolve, reject) => {
    huks.init(keyAlias, options, async (err, data) => {
      if (data.errorCode === 0) {
        resultMessage = "init success!";
        handle = data.handle;
      } else {
        resultMessage = "init fail errorCode: " + data.errorCode;
      }
    });
  });
}

async function huksUpdate() {
  options.inData = stringToUint8Array("huksHmacTest");
  new Promise<huks.HuksResult>((resolve, reject) => {
    huks.update(handle, options.inData, options, (err, data) => {
      if (data.errorCode === 0) {
        resultMessage += "update success!";
        console.info(resultMessage);
      } else {
        resultMessage += "update fail!";
        console.error(resultMessage);
      }
    });
  });
}

async function huksFinish() {
  options.inData = stringToUint8Array("0");
  new Promise<huks.HuksResult>((resolve, reject) => {
    huks.finish(handle, options, (err, data) => {
      if (data.errorCode === 0) {
        resultMessage = "finish success!";
      } else {
        resultMessage = "finish fail errorCode: " + data.errorCode;
      }
    });
  });
}

function huksAbort() {
  huks.abort(handle, options).then((data) => {
    if (data.errorCode === 0) {
      console.info("abort success!");
    } else {
      console.error("abort fail errorCode: " + data.errorCode);
    }
  });
}

```

