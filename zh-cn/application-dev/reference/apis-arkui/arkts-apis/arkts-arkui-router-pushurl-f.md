# pushUrl

## pushUrl

```TypeScript
function pushUrl(options: RouterOptions, callback: AsyncCallback<void>): void
```

��ת��Ӧ���ڵ�ָ��ҳ�档

> **˵����**
>
> - ��API version 9��ʼ֧�֣���API version 18��ʼ����������ʹ��
> [pushUrl](arkts-arkui-router-c.md#pushUrl-1)
> �����pushUrl����ͨ��[UIContext](arkts-arkui-uicontext.md)�е�
> [getRouter](../../../../reference/apis-arkui/arkts-apis-uicontext-uicontext.md#getrouter)��ȡ
> [Router](arkts-arkui-uicontext.md)ʵ����Ȼ��ͨ����ʵ�����е��á�
>
> - ��API version 10��ʼ������ͨ��ʹ��[UIContext](arkts-arkui-uicontext.md)�е�
> [getRouter](../../../../reference/apis-arkui/arkts-apis-uicontext-uicontext.md#getrouter)������ȡ��ǰUI�����Ĺ�����
> [Router](arkts-arkui-uicontext.md)����

**起始版本：** 9

**废弃版本：** 18

**替代接口：** pushUrl(options:

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | RouterOptions | 是 | ��תҳ��������Ϣ�� |
| callback | AsyncCallback&lt;void&gt; | 是 | �쳣��Ӧ�ص��� |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-Parameter) | Parameter error. Possible causes:<br/><br/>1. Mandatory parameters are left unspecified.<br/><br/>2. Incorrect parameters types.<br/><br/>3. Parameter verification failed. |
| [100001](../../errorcode-universal.md#100001-Internal) | Internal error. |
| [100002](../../errorcode-universal.md#100002-Uri) | Uri error. The URI of the page to redirect is incorrect or does not exist |
| [100003](../../errorcode-universal.md#100003-Page) | Page stack error. Too many pages are pushed. |

**示例：**

```TypeScript
class innerParams {
  data3: number[];

  constructor(tuple: number[]) {
    this.data3 = tuple;
  }
}

class RouterParams {
  data1: string;
  data2: innerParams;

  constructor(str: string, tuple: number[]) {
    this.data1 = str;
    this.data2 = new innerParams(tuple);
  }
}

router.pushUrl({
  url: 'pages/routerpage2',
  params: new RouterParams('message', [123, 456, 789])
}, (err) => {
  if (err) {
    console.error(`pushUrl failed, code is ${err.code}, message is ${err.message}`);
    return;
  }
  console.info('pushUrl success');
})

```


## pushUrl

```TypeScript
function pushUrl(options: RouterOptions): Promise<void>
```

��ת��Ӧ���ڵ�ָ��ҳ�档

> **˵����**
>
> - ��API version 9��ʼ֧�֣���API version 18��ʼ����������ʹ��
> [pushUrl](arkts-arkui-router-c.md#pushUrl-2)�����pushUrl����ͨ��
> [UIContext](arkts-arkui-uicontext.md)�е�
> [getRouter](../../../../reference/apis-arkui/arkts-apis-uicontext-uicontext.md#getrouter)��ȡ
> [Router](arkts-arkui-uicontext.md)ʵ����Ȼ��ͨ����ʵ�����е��á�
>
> - ��API version 10��ʼ������ͨ��ʹ��[UIContext](arkts-arkui-uicontext.md)�е�
> [getRouter](../../../../reference/apis-arkui/arkts-apis-uicontext-uicontext.md#getrouter)������ȡ��ǰUI�����Ĺ�����
> [Router](arkts-arkui-uicontext.md)����

**起始版本：** 9

**废弃版本：** 18

**替代接口：** pushUrl(options:

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | RouterOptions | 是 | ��תҳ��������Ϣ�� |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | �쳣���ؽ���� |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-Parameter) | Parameter error. Possible causes:<br/><br/>1. Mandatory parameters are left unspecified.<br/><br/>2. Incorrect parameters types.<br/><br/>3. Parameter verification failed. |
| [100001](../../errorcode-universal.md#100001-Internal) | Internal error. |
| [100002](../../errorcode-universal.md#100002-Uri) | Uri error. The URI of the page to redirect is incorrect or does not exist |
| [100003](../../errorcode-universal.md#100003-Page) | Page stack error. Too many pages are pushed. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

class innerParams {
  data3: number[];

  constructor(tuple: number[]) {
    this.data3 = tuple;
  }
}

class RouterParams {
  data1: string;
  data2: innerParams;

  constructor(str: string, tuple: number[]) {
    this.data1 = str;
    this.data2 = new innerParams(tuple);
  }
}

router.pushUrl({
  url: 'pages/routerpage2',
  params: new RouterParams('message', [123, 456, 789])
})
  .then(() => {
    console.error(`pushUrl finish`);
  })
  .catch((err: ESObject) => {
    console.error(`pushUrl failed, code is ${(err as BusinessError).code}, message is ${(err as BusinessError).message}`);
  })

```


## pushUrl

```TypeScript
function pushUrl(options: RouterOptions, mode: RouterMode, callback: AsyncCallback<void>): void
```

��ת��Ӧ���ڵ�ָ��ҳ�档

> **˵����**
>
> - ��API version 9��ʼ֧�֣���API version 18��ʼ����������ʹ��
> [pushUrl](arkts-arkui-router-c.md#pushUrl-3)
> �����pushUrl����ͨ��[UIContext](arkts-arkui-uicontext.md)�е�
> [getRouter](../../../../reference/apis-arkui/arkts-apis-uicontext-uicontext.md#getrouter)��ȡ
> [Router](arkts-arkui-uicontext.md)ʵ����Ȼ��ͨ����ʵ�����е��á�
>
> - ��API version 10��ʼ������ͨ��ʹ��[UIContext](arkts-arkui-uicontext.md)�е�
> [getRouter](../../../../reference/apis-arkui/arkts-apis-uicontext-uicontext.md#getrouter)������ȡ��ǰUI�����Ĺ�����
> [Router](arkts-arkui-uicontext.md)����

**起始版本：** 9

**废弃版本：** 18

**替代接口：** pushUrl(options:

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | RouterOptions | 是 | ��תҳ��������Ϣ�� |
| mode | RouterMode | 是 | ��תҳ��ʹ�õ�ģʽ�� |
| callback | AsyncCallback&lt;void&gt; | 是 | �쳣��Ӧ�ص��� |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-Parameter) | Parameter error. Possible causes:<br/><br/>1. Mandatory parameters are left unspecified.<br/><br/>2. Incorrect parameters types.<br/><br/>3. Parameter verification failed. |
| [100001](../../errorcode-universal.md#100001-Internal) | Internal error. |
| [100002](../../errorcode-universal.md#100002-Uri) | Uri error. The URI of the page to redirect is incorrect or does not exist |
| [100003](../../errorcode-universal.md#100003-Page) | Page stack error. Too many pages are pushed. |

**示例：**

```TypeScript
class innerParams {
  data3: number[];

  constructor(tuple: number[]) {
    this.data3 = tuple;
  }
}

class RouterParams {
  data1: string;
  data2: innerParams;

  constructor(str: string, tuple: number[]) {
    this.data1 = str;
    this.data2 = new innerParams(tuple);
  }
}

router.pushUrl({
  url: 'pages/routerpage2',
  params: new RouterParams('message', [123, 456, 789])
}, router.RouterMode.Standard, (err) => {
  if (err) {
    console.error(`pushUrl failed, code is ${err.code}, message is ${err.message}`);
    return;
  }
  console.info('pushUrl success');
})

```


## pushUrl

```TypeScript
function pushUrl(options: RouterOptions, mode: RouterMode): Promise<void>
```

��ת��Ӧ���ڵ�ָ��ҳ�档

> **˵����**
>
> - ��API version 9��ʼ֧�֣���API version 18��ʼ����������ʹ��
> [pushUrl](arkts-arkui-router-c.md#pushUrl-4)�����
> pushUrl����ͨ��[UIContext](arkts-arkui-uicontext.md)�е�
> [getRouter](../../../../reference/apis-arkui/arkts-apis-uicontext-uicontext.md#getrouter)��ȡ
> [Router](arkts-arkui-uicontext.md)ʵ����Ȼ��ͨ����ʵ�����е��á�
>
> - ��API version 10��ʼ������ͨ��ʹ��[UIContext](arkts-arkui-uicontext.md)�е�
> [getRouter](../../../../reference/apis-arkui/arkts-apis-uicontext-uicontext.md#getrouter)������ȡ��ǰUI�����Ĺ�����
> [Router](arkts-arkui-uicontext.md)����

**起始版本：** 9

**废弃版本：** 18

**替代接口：** pushUrl(options:

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | RouterOptions | 是 | ��תҳ��������Ϣ�� |
| mode | RouterMode | 是 | ��תҳ��ʹ�õ�ģʽ�� |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | �쳣���ؽ���� |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-Parameter) | Parameter error. Possible causes:<br/><br/>1. Mandatory parameters are left unspecified.<br/><br/>2. Incorrect parameters types.<br/><br/>3. Parameter verification failed. |
| [100001](../../errorcode-universal.md#100001-Internal) | Internal error. |
| [100002](../../errorcode-universal.md#100002-Uri) | Uri error. The URI of the page to redirect is incorrect or does not exist |
| [100003](../../errorcode-universal.md#100003-Page) | Page stack error. Too many pages are pushed. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

class innerParams {
  data3: number[];

  constructor(tuple: number[]) {
    this.data3 = tuple;
  }
}

class RouterParams {
  data1: string;
  data2: innerParams;

  constructor(str: string, tuple: number[]) {
    this.data1 = str;
    this.data2 = new innerParams(tuple);
  }
}

router.pushUrl({
  url: 'pages/routerpage2',
  params: new RouterParams('message', [123, 456, 789])
}, router.RouterMode.Standard)
  .then(() => {
    console.error(`pushUrl finish`);
  })
  .catch((err: ESObject) => {
    console.error(`pushUrl failed, code is ${(err as BusinessError).code}, message is ${(err as BusinessError).message}`);
  })

```

