# replaceUrl

## replaceUrl

```TypeScript
function replaceUrl(options: RouterOptions, callback: AsyncCallback<void>): void
```

��Ӧ���ڵ�ĳ��ҳ���滻��ǰҳ�棬�����ٱ��滻��ҳ�档

> **˵����**
>
> - ��API version 9��ʼ֧�֣���Lite Wearable�⣬��API version 18��ʼ����������ʹ��
> [replaceUrl](arkts-arkui-router-c.md#replaceUrl-1)
> �����replaceUrl����ͨ��[UIContext](arkts-arkui-uicontext.md)�е�
> [getRouter](../../../../reference/apis-arkui/arkts-apis-uicontext-uicontext.md#getrouter)��ȡ
> [Router](arkts-arkui-uicontext.md)ʵ����Ȼ��ͨ����ʵ�����е��á�
>
> - ��API version 10��ʼ������ͨ��ʹ��[UIContext](arkts-arkui-uicontext.md)�е�
> [getRouter](../../../../reference/apis-arkui/arkts-apis-uicontext-uicontext.md#getrouter)������ȡ��ǰUI�����Ĺ�����
> [Router](arkts-arkui-uicontext.md)����

**起始版本：** 9

**废弃版本：** 18

**替代接口：** replaceUrl(options:

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Lite

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | RouterOptions | 是 | �滻ҳ��������Ϣ�� |
| callback | AsyncCallback&lt;void&gt; | 是 | �쳣��Ӧ�ص��� |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-Parameter) | Parameter error. Possible causes:<br/><br/>1. Mandatory parameters are left unspecified.<br/><br/>2. Incorrect parameters types.<br/><br/>3. Parameter verification failed. |
| [100001](../../errorcode-universal.md#100001-The) | The UI execution context is not found. This error code is thrown only in the<br/>standard system. |
| [200002](../../errorcode-universal.md#200002-Uri) | Uri error. The URI of the page to be used for replacement is incorrect or does<br/>not exist. |

**示例：**

```TypeScript
class RouterParams {
  data1: string;

  constructor(str: string) {
    this.data1 = str;
  }
}

router.replaceUrl({
  url: 'pages/detail',
  params: new RouterParams('message')
}, (err) => {
  if (err) {
    console.error(`replaceUrl failed, code is ${err.code}, message is ${err.message}`);
    return;
  }
  console.info('replaceUrl success');
})

```


## replaceUrl

```TypeScript
function replaceUrl(options: RouterOptions): Promise<void>
```

��Ӧ���ڵ�ĳ��ҳ���滻��ǰҳ�棬�����ٱ��滻��ҳ�档��֧������ҳ��ת����Ч���������ã��Ƽ�ʹ��[Navigation���](../../../../ui/arkts-navigation-architecture.md)��

> **˵����**
>
> - ��API version 9��ʼ֧�֣���Lite Wearable�⣬��API version 18��ʼ����������ʹ��
> [replaceUrl](arkts-arkui-router-c.md#replaceUrl-2)�����replaceUrl����ͨ��
> [UIContext](arkts-arkui-uicontext.md)�е�
> [getRouter](../../../../reference/apis-arkui/arkts-apis-uicontext-uicontext.md#getrouter)��ȡ
> [Router](arkts-arkui-uicontext.md)ʵ����Ȼ��ͨ����ʵ�����е��á�
>
> - ��API version 10��ʼ������ͨ��ʹ��[UIContext](arkts-arkui-uicontext.md)�е�
> [getRouter](../../../../reference/apis-arkui/arkts-apis-uicontext-uicontext.md#getrouter)������ȡ��ǰUI�����Ĺ�����
> [Router](arkts-arkui-uicontext.md)����

**起始版本：** 9

**废弃版本：** 18

**替代接口：** replaceUrl(options:

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Lite

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | RouterOptions | 是 | �滻ҳ��������Ϣ�� |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | �쳣���ؽ���� |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-Parameter) | Parameter error. Possible causes:<br/><br/>1. Mandatory parameters are left unspecified.<br/><br/>2. Incorrect parameters types.<br/><br/>3. Parameter verification failed. |
| [100001](../../errorcode-universal.md#100001-The) | The UI execution context is not found. This error code is thrown only in the<br/>standard system. |
| [200002](../../errorcode-universal.md#200002-Uri) | Uri error. The URI of the page to be used for replacement is incorrect or does<br/>not exist. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

class RouterParams {
  data1: string;

  constructor(str: string) {
    this.data1 = str;
  }
}

router.replaceUrl({
  url: 'pages/detail',
  params: new RouterParams('message')
})
  .then(() => {
    console.error(`replaceUrl finish`);
  })
  .catch((err: ESObject) => {
    console.error(`replaceUrl failed, code is ${(err as BusinessError).code}, message is ${(err as BusinessError).message}`);
  })

```


## replaceUrl

```TypeScript
function replaceUrl(options: RouterOptions, mode: RouterMode, callback: AsyncCallback<void>): void
```

��Ӧ���ڵ�ĳ��ҳ���滻��ǰҳ�棬�����ٱ��滻��ҳ�档

> **˵����**
>
> - ��API version 9��ʼ֧�֣���Lite Wearable�⣬��API version 18��ʼ����������ʹ��
> [replaceUrl](arkts-arkui-router-c.md#replaceUrl-3)
> �����replaceUrl����ͨ��[UIContext](arkts-arkui-uicontext.md)�е�
> [getRouter](../../../../reference/apis-arkui/arkts-apis-uicontext-uicontext.md#getrouter)��ȡ
> [Router](arkts-arkui-uicontext.md)ʵ����Ȼ��ͨ����ʵ�����е��á�
>
> - ��API version 10��ʼ������ͨ��ʹ��[UIContext](arkts-arkui-uicontext.md)�е�
> [getRouter](../../../../reference/apis-arkui/arkts-apis-uicontext-uicontext.md#getrouter)������ȡ��ǰUI�����Ĺ�����
> [Router](arkts-arkui-uicontext.md)����

**起始版本：** 9

**废弃版本：** 18

**替代接口：** replaceUrl(options:

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Lite

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | RouterOptions | 是 | �滻ҳ��������Ϣ�� |
| mode | RouterMode | 是 | ��תҳ��ʹ�õ�ģʽ�� |
| callback | AsyncCallback&lt;void&gt; | 是 | �쳣��Ӧ�ص��� |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-Parameter) | Parameter error. Possible causes:<br/><br/>1. Mandatory parameters are left unspecified.<br/><br/>2. Incorrect parameters types.<br/><br/>3. Parameter verification failed. |
| [100001](../../errorcode-universal.md#100001-The) | The UI execution context is not found. This error code is thrown only in the<br/>standard system. |
| [200002](../../errorcode-universal.md#200002-Uri) | Uri error. The URI of the page to be used for replacement is incorrect or does<br/>not exist. |

**示例：**

```TypeScript
class RouterParams {
  data1: string;

  constructor(str: string) {
    this.data1 = str;
  }
}

router.replaceUrl({
  url: 'pages/detail',
  params: new RouterParams('message')
}, router.RouterMode.Standard, (err) => {
  if (err) {
    console.error(`replaceUrl failed, code is ${err.code}, message is ${err.message}`);
    return;
  }
  console.info('replaceUrl success');
});

```


## replaceUrl

```TypeScript
function replaceUrl(options: RouterOptions, mode: RouterMode): Promise<void>
```

��Ӧ���ڵ�ĳ��ҳ���滻��ǰҳ�棬�����ٱ��滻��ҳ�档

> **˵����**
>
> - ��API version 9��ʼ֧�֣���Lite Wearable�⣬��API version 18��ʼ����������ʹ��
> [replaceUrl](arkts-arkui-router-c.md#replaceUrl-4)
> �����replaceUrl����ͨ��[UIContext](arkts-arkui-uicontext.md)�е�
> [getRouter](../../../../reference/apis-arkui/arkts-apis-uicontext-uicontext.md#getrouter)��ȡ
> [Router](arkts-arkui-uicontext.md)ʵ����Ȼ��ͨ����ʵ�����е��á�
>
> - ��API version 10��ʼ������ͨ��ʹ��[UIContext](arkts-arkui-uicontext.md)�е�
> [getRouter](../../../../reference/apis-arkui/arkts-apis-uicontext-uicontext.md#getrouter)������ȡ��ǰUI�����Ĺ�����
> [Router](arkts-arkui-uicontext.md)����

**起始版本：** 9

**废弃版本：** 18

**替代接口：** replaceUrl(options:

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Lite

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | RouterOptions | 是 | �滻ҳ��������Ϣ�� |
| mode | RouterMode | 是 | ��תҳ��ʹ�õ�ģʽ�� |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | �쳣���ؽ���� |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-Parameter) | Parameter error. Possible causes:<br/><br/>1. Mandatory parameters are left unspecified.<br/><br/>2. Incorrect parameters types.<br/><br/>3. Parameter verification failed. |
| [100001](../../errorcode-universal.md#100001-Failed) | Failed to get the delegate. This error code is thrown only in the standard<br/>system. |
| [200002](../../errorcode-universal.md#200002-Uri) | Uri error. The URI of the page to be used for replacement is incorrect or does<br/>not exist. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

class RouterParams {
  data1:string;

  constructor(str:string) {
    this.data1 = str;
  }
}

router.replaceUrl({
  url: 'pages/detail',
  params: new RouterParams('message')
}, router.RouterMode.Standard)
  .then(() => {
    console.error(`replaceUrl finish`);
  })
  .catch((err: ESObject) => {
    console.error(`replaceUrl failed, code is ${(err as BusinessError).code}, message is ${(err as BusinessError).message}`);
  })

```

