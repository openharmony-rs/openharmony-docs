# replaceNamedRoute

## replaceNamedRoute

```TypeScript
function replaceNamedRoute(options: NamedRouterOptions, callback: AsyncCallback<void>): void
```

��ָ��������·��ҳ���滻��ǰҳ�棬�����ٱ��滻��ҳ�档

> **˵����**
>
> - ��API version 10��ʼ֧�֣���API version 18��ʼ����������ʹ��
> [replaceNamedRoute](arkts-arkui-router-c.md#replaceNamedRoute-1)
> �����replaceNamedRoute����ͨ��[UIContext](arkts-arkui-uicontext.md)�е�
> [getRouter](../../../../reference/apis-arkui/arkts-apis-uicontext-uicontext.md#getrouter)��ȡ
> [Router](arkts-arkui-uicontext.md)ʵ����Ȼ��ͨ����ʵ�����е��á�
>
> - ��API version 10��ʼ������ͨ��ʹ��[UIContext](arkts-arkui-uicontext.md)�е�
> [getRouter](../../../../reference/apis-arkui/arkts-apis-uicontext-uicontext.md#getrouter)������ȡ��ǰUI�����Ĺ�����
> [Router](arkts-arkui-uicontext.md)����

**起始版本：** 10

**废弃版本：** 18

**替代接口：** replaceNamedRoute(options:

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | NamedRouterOptions | 是 | �滻ҳ��������Ϣ�� |
| callback | AsyncCallback&lt;void&gt; | 是 | �쳣��Ӧ�ص��� |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-Parameter) | Parameter error. Possible causes:<br/><br/>1. Mandatory parameters are left unspecified.<br/><br/>2. Incorrect parameters types.<br/><br/>3. Parameter verification failed. |
| [100001](../../errorcode-universal.md#100001-The) | The UI execution context is not found. This error code is thrown only in the<br/>standard system. |
| [100004](../../errorcode-universal.md#100004-Named) | Named route error. The named route does not exist. |

**示例：**

```TypeScript
class RouterParams {
  data1: string;

  constructor(str: string) {
    this.data1 = str;
  }
}

router.replaceNamedRoute({
  name: 'myPage',
  params: new RouterParams('message')
}, (err) => {
  if (err) {
    console.error(`replaceNamedRoute failed, code is ${err.code}, message is ${err.message}`);
    return;
  }
  console.info('replaceNamedRoute success');
})

```


## replaceNamedRoute

```TypeScript
function replaceNamedRoute(options: NamedRouterOptions): Promise<void>
```

��ָ��������·��ҳ���滻��ǰҳ�棬�����ٱ��滻��ҳ�档

> **˵����**
>
> - ��API version 10��ʼ֧�֣���API version 18��ʼ����������ʹ��
> [replaceNamedRoute](arkts-arkui-router-c.md#replaceNamedRoute-2)�����
> replaceNamedRoute����ͨ��[UIContext](arkts-arkui-uicontext.md)�е�
> [getRouter](../../../../reference/apis-arkui/arkts-apis-uicontext-uicontext.md#getrouter)��ȡ
> [Router](arkts-arkui-uicontext.md)ʵ����Ȼ��ͨ����ʵ�����е��á�
>
> - ��API version 10��ʼ������ͨ��ʹ��[UIContext](arkts-arkui-uicontext.md)�е�
> [getRouter](../../../../reference/apis-arkui/arkts-apis-uicontext-uicontext.md#getrouter)������ȡ��ǰUI�����Ĺ�����
> [Router](arkts-arkui-uicontext.md)����

**起始版本：** 10

**废弃版本：** 18

**替代接口：** replaceNamedRoute(options:

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | NamedRouterOptions | 是 | �滻ҳ��������Ϣ�� |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | �쳣���ؽ���� |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-Parameter) | Parameter error. Possible causes:<br/><br/>1. Mandatory parameters are left unspecified.<br/><br/>2. Incorrect parameters types.<br/><br/>3. Parameter verification failed. |
| [100001](../../errorcode-universal.md#100001-The) | The UI execution context is not found. This error code is thrown only in the<br/>standard system. |
| [100004](../../errorcode-universal.md#100004-Named) | Named route error. The named route does not exist. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

class RouterParams {
  data1: string;

  constructor(str: string) {
    this.data1 = str;
  }
}

router.replaceNamedRoute({
  name: 'myPage',
  params: new RouterParams('message')
})
  .then(() => {
    console.error(`replaceNamedRoute finish`);
  })
  .catch((err: ESObject) => {
    console.error(`replaceNamedRoute failed, code is ${(err as BusinessError).code}, message is ${(err as BusinessError).message}`);
  })

```


## replaceNamedRoute

```TypeScript
function replaceNamedRoute(options: NamedRouterOptions, mode: RouterMode, callback: AsyncCallback<void>): void
```

��ָ��������·��ҳ���滻��ǰҳ�棬�����ٱ��滻��ҳ�档

> **˵����**
>
> - ��API version 10��ʼ֧�֣���API version 18��ʼ����������ʹ��
> [replaceNamedRoute](arkts-arkui-router-c.md#replaceNamedRoute-3)
> �����replaceNamedRoute����ͨ��[UIContext](arkts-arkui-uicontext.md)�е�
> [getRouter](../../../../reference/apis-arkui/arkts-apis-uicontext-uicontext.md#getrouter)��ȡ
> [Router](arkts-arkui-uicontext.md)ʵ����Ȼ��ͨ����ʵ�����е��á�
>
> - ��API version 10��ʼ������ͨ��ʹ��[UIContext](arkts-arkui-uicontext.md)�е�
> [getRouter](../../../../reference/apis-arkui/arkts-apis-uicontext-uicontext.md#getrouter)������ȡ��ǰUI�����Ĺ�����
> [Router](arkts-arkui-uicontext.md)����

**起始版本：** 10

**废弃版本：** 18

**替代接口：** replaceNamedRoute(options:

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | NamedRouterOptions | 是 | �滻ҳ��������Ϣ�� |
| mode | RouterMode | 是 | ��תҳ��ʹ�õ�ģʽ�� |
| callback | AsyncCallback&lt;void&gt; | 是 | �쳣��Ӧ�ص��� |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-Parameter) | Parameter error. Possible causes:<br/><br/>1. Mandatory parameters are left unspecified.<br/><br/>2. Incorrect parameters types.<br/><br/>3. Parameter verification failed. |
| [100001](../../errorcode-universal.md#100001-The) | The UI execution context is not found. This error code is thrown only in the<br/>standard system. |
| [100004](../../errorcode-universal.md#100004-Named) | Named route error. The named route does not exist. |

**示例：**

```TypeScript
class RouterParams {
  data1: string;

  constructor(str: string) {
    this.data1 = str;
  }
}

router.replaceNamedRoute({
  name: 'myPage',
  params: new RouterParams('message')
}, router.RouterMode.Standard, (err) => {
  if (err) {
    console.error(`replaceNamedRoute failed, code is ${err.code}, message is ${err.message}`);
    return;
  }
  console.info('replaceNamedRoute success');
});

```


## replaceNamedRoute

```TypeScript
function replaceNamedRoute(options: NamedRouterOptions, mode: RouterMode): Promise<void>
```

��ָ��������·��ҳ���滻��ǰҳ�棬�����ٱ��滻��ҳ�档

> **˵����**
>
> - ��API version 10��ʼ֧�֣���API version 18��ʼ����������ʹ��
> [replaceNamedRoute](arkts-arkui-router-c.md#replaceNamedRoute-4)
> �����replaceNamedRoute����ͨ��[UIContext](arkts-arkui-uicontext.md)�е�
> [getRouter](../../../../reference/apis-arkui/arkts-apis-uicontext-uicontext.md#getrouter)��ȡ
> [Router](arkts-arkui-uicontext.md)ʵ����Ȼ��ͨ����ʵ�����е��á�
>
> - ��API version 10��ʼ������ͨ��ʹ��[UIContext](arkts-arkui-uicontext.md)�е�
> [getRouter](../../../../reference/apis-arkui/arkts-apis-uicontext-uicontext.md#getrouter)������ȡ��ǰUI�����Ĺ�����
> [Router](arkts-arkui-uicontext.md)����

**起始版本：** 10

**废弃版本：** 18

**替代接口：** replaceNamedRoute(options:

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | NamedRouterOptions | 是 | �滻ҳ��������Ϣ�� |
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
| [100004](../../errorcode-universal.md#100004-Named) | Named route error. The named route does not exist. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

class RouterParams {
  data1: string;

  constructor(str: string) {
    this.data1 = str;
  }
}

router.replaceNamedRoute({
  name: 'myPage',
  params: new RouterParams('message')
}, router.RouterMode.Standard)
  .then(() => {
    console.error(`replaceNamedRoute finish`);
  })
  .catch((err: ESObject) => {
    console.error(`replaceNamedRoute failed, code is ${(err as BusinessError).code}, message is ${(err as BusinessError).message}`);
  })

```

