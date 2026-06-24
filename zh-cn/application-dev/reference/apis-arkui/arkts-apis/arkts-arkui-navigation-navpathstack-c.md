# NavPathStack

Navigation��������������ջ�����ݽṹ����Navigation�����е���ҳ�棬���ṩջ�����ķ������ڿ���Navigation����ҳ����л���

��API version 12��ʼ��NavPathStack�������̳У��������������������NavPathStack����ʹ�á�ʹ��ʾ���μ�
[ʾ��10](../../../../reference/apis-arkui/arkui-ts/ts-basic-components-navigation.md#ʾ��10���嵼��������������)��

> **˵����**
>
> 1.�������ö��������������������ʱ���м���̻ᱻ���ԣ���ʾ���յ�ջ���������

> ���磺��Page1ҳ����pop��pushһ��Page1��ϵͳ����Ϊ����ǰ�Ͳ�����Ľ��һ�¶��������κβ����������Ҫǿ��pushһ��Page1ʵ������������
> [NavigationOption](arkts-arkui-navigation-navigationoptions-i.md#NavigationOptions)�е�launchMode����ֵΪLaunchMode.NEW_INSTANCEģʽ��
>
> 2.�����鿪����ͨ������ҳ���������ڵķ�ʽ�����Լ��ĵ�����������
>
> 3.��Ӧ�ô��ں�̨״̬�£�����NavPathStack��ջ��������������Ӧ���ٴλص�ǰ̨״̬ʱ����ˢ�¡�

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## clear

```TypeScript
clear(animated?: boolean): void
```

���ջ������ҳ�档

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| animated | boolean | 否 | �Ƿ�֧��ת��������<br/>true��֧��ת��������false����֧��ת��������<br/>Ĭ��ֵ��true [since 11] |

## constructor

```TypeScript
constructor()
```

����NavPathStack����

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## disableAnimation

```TypeScript
disableAnimation(value: boolean): void
```

�رգ�true����򿪣�false����ǰNavigation������ת��������

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | boolean | 是 | �Ƿ�ر�ת��������<br/>Ĭ��ֵ��false<br/>true���ر�ת��������<br/>false�����ر�ת�������� |

## getAllPathName

```TypeScript
getAllPathName(): Array<string>
```

��ȡջ������NavDestinationҳ������ơ�

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Array&lt;string&gt; | ����ջ������NavDestinationҳ������ơ� |

## getIndexByName

```TypeScript
getIndexByName(name: string): Array<number>
```

��ȡȫ����Ϊname��NavDestinationҳ���λ��������

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| name | string | 是 | NavDestinationҳ�����ơ� |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Array&lt;number&gt; | ����ȫ����Ϊname��NavDestinationҳ���λ�������� ��·��ջ�в����ڴ�name�����ؿ����顣����ȡֵ��ΧΪ[0, ·��ջ��С-1] |

## getParamByIndex

```TypeScript
getParamByIndex(index: number): unknown | undefined
```

��ȡindexָ����NavDestinationҳ��Ĳ�����Ϣ��

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| index | number | 是 | NavDestinationҳ���λ�������� ����ֵ��0��ʼ�� |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| unknown | **unknown**: parameter information of the corresponding navigation destination<br/>page. **unknown** can represent a user-defined type.<br/><br/>**undefined**: an invalid index is provided. |

## getParamByName

```TypeScript
getParamByName(name: string): Array<unknown>
```

��ȡ������Ϊname��NavDestinationҳ��Ĳ�����Ϣ����ҳ��������С��������

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| name | string | 是 | NavDestinationҳ�����ơ� |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Array&lt;unknown&gt; | ����ȫ����Ϊname��NavDestinationҳ��Ĳ�����Ϣ��unknown�������û��Զ�������͡� |

## getParent

```TypeScript
getParent(): NavPathStack | null
```

��ȡ��NavPathStack��

������NavigationǶ��Navigation�����ʱ��������ֱ��Ƕ�ף�Ҳ�����Ǽ��Ƕ�ף����ڲ�Navigation��NavPathStack�ܹ���ȡ�����Navigation��NavPathStack��

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| NavPathStack | Navigation path stack of the outer **Navigation** component in which the current<br/>**Navigation** component is nested. If there is no outer **Navigation** component., **null** is returned. |

## getPathStack

```TypeScript
getPathStack(): Array<NavPathInfo>
```

��ȡ��ǰ·��ջ�е�·��ҳ����Ϣ���顣

**起始版本：** 19

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Array&lt;NavPathInfo&gt; | ��ǰ·��ջ�е�·��ҳ����Ϣ���顣 |

## moveIndexToTop

```TypeScript
moveIndexToTop(index: number, animated?: boolean): void
```

��indexָ����NavDestinationҳ���Ƶ�ջ����

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| index | number | 是 | NavDestinationҳ���λ������������ֵ��0��ʼ�� |
| animated | boolean | 否 | �Ƿ�֧��ת��������<br/>true��֧��ת��������false����֧��ת��������<br/>Ĭ��ֵ��true [since 11] |

## moveToTop

```TypeScript
moveToTop(name: string, animated?: boolean): number
```

����ջ�׿�ʼ��һ����Ϊname��NavDestinationҳ���Ƶ�ջ����

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| name | string | 是 | NavDestinationҳ�����ơ� |
| animated | boolean | 否 | �Ƿ�֧��ת��������<br/>true��֧��ת��������false����֧��ת��������<br/>Ĭ��ֵ��true [since 11] |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | ���ջ�д�����Ϊname��NavDestinationҳ�棬�򷵻���ջ�׿�ʼ��һ����Ϊname��NavDestinationҳ��ĵ�ǰ���������򷵻�-1�� |

## pop

```TypeScript
pop(animated?: boolean): NavPathInfo | undefined
```

����·��ջջ��Ԫ�ء�

> **˵����**
>
> �������ö����������������ʱ���м䱻pop��ҳ��ᱻ���棬����pushͬ��ҳ��ʱ�����ȸ��ø�ҳ�棬�������µ�ҳ�洴�����̡�

> ���磺

> pathStack: NavPathStack = new NavPathStack()

> // ��ʼҳ��ջΪ��[A]

> pathStack.pop()

> pathStack.pushPath(A)

> pathStack.pushPath(B)

> // ������ҳ��ջΪ��[A B]

> ��ʱAҳ��ᱻ���ã��������µĴ������̡�

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| animated | boolean | 否 | �Ƿ�֧��ת��������<br/>true��֧��ת��������false����֧��ת��������<br/>Ĭ��ֵ��true [since 11] |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| NavPathInfo | **NavPathInfo**: information about the navigation destination page at the top<br/>of the stack.<br/><br/>**undefined**: the routing stack is empty. |

## pop

```TypeScript
pop(result: Object, animated?: boolean): NavPathInfo | undefined
```

����·��ջջ��Ԫ�أ�������onPop�ص�����ҳ�洦�������

> **˵����**
>
> �������ö����������������ʱ���м䱻pop��ҳ��ᱻ���棬����pushͬ��ҳ��ʱ�����ȸ��ø�ҳ�棬�������µ�ҳ�洴�����̡�

> ���磺

> pathStack: NavPathStack = new NavPathStack()

> // ��ʼҳ��ջΪ��[A]

> pathStack.pop()

> pathStack.pushPath(A)

> pathStack.pushPath(B)

> // ������ҳ��ջΪ��[A B]

> ��ʱAҳ��ᱻ���ã��������µĴ������̡�

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| result | Object | 是 | ҳ���Զ��崦���������֧��boolean���͡� |
| animated | boolean | 否 | �Ƿ�֧��ת��������<br/>true��֧��ת��������false����֧��ת��������<br/>Ĭ��ֵ��true |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| NavPathInfo | **NavPathInfo**: information about the navigation destination page at the top<br/>of the stack.<br/><br/>**undefined**: the routing stack is empty. |

## popToIndex

```TypeScript
popToIndex(index: number, animated?: boolean): void
```

����·��ջ��indexָ����NavDestinationҳ�档

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| index | number | 是 | NavDestinationҳ���λ������������ֵ��0��ʼ�� |
| animated | boolean | 否 | �Ƿ�֧��ת��������<br/>true��֧��ת��������false����֧��ת��������<br/>Ĭ��ֵ��true [since 11] |

## popToIndex

```TypeScript
popToIndex(index: number, result: Object, animated?: boolean): void
```

����·��ջ��indexָ����NavDestinationҳ�棬������onPop�ص�����ҳ�洦�������

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| index | number | 是 | NavDestinationҳ���λ������������ֵ��0��ʼ�� |
| result | Object | 是 | ҳ���Զ��崦���������֧��boolean���͡� |
| animated | boolean | 否 | �Ƿ�֧��ת��������<br/>true��֧��ת��������false����֧��ת��������<br/>Ĭ��ֵ��true |

## popToName

```TypeScript
popToName(name: string, animated?: boolean): number
```

����·��ջ����ջ�׿�ʼ��һ����Ϊname��NavDestinationҳ�档

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| name | string | 是 | NavDestinationҳ�����ơ� |
| animated | boolean | 否 | �Ƿ�֧��ת��������<br/>true��֧��ת��������false����֧��ת��������<br/>Ĭ��ֵ��true [since 11] |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | ���ջ�д�����Ϊname��NavDestinationҳ�棬�򷵻���ջ�׿�ʼ��һ����Ϊname��NavDestinationҳ������������򷵻�-1�� |

## popToName

```TypeScript
popToName(name: string, result: Object, animated?: boolean): number
```

����·��ջ����ջ�׿�ʼ��һ����Ϊname��NavDestinationҳ�棬������onPop�ص�����ҳ�洦�������

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| name | string | 是 | NavDestinationҳ�����ơ� |
| result | Object | 是 | ҳ���Զ��崦���������֧��boolean���͡� |
| animated | boolean | 否 | �Ƿ�֧��ת��������<br/>true��֧��ת��������false����֧��ת��������<br/>Ĭ��ֵ��true |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | ���ջ�д�����Ϊname��NavDestinationҳ�棬�򷵻���ջ�׿�ʼ��һ����Ϊname��NavDestinationҳ������������򷵻�-1�� |

## pushDestination

```TypeScript
pushDestination(info: NavPathInfo, animated?: boolean): Promise<void>
```

��infoָ����NavDestinationҳ����Ϣ��ջ��ʹ��Promise�첽�ص����ؽӿڵ��ý����

> **˵����**
>
> ��������[aboutToAppear](arkts-arkui-basecustomcomponent-c.md#aboutToAppear-1)��ʹ��ջ��������ʱ��ҳ�滹δ������ɣ��ᵼ�°�������תʧ�ܵ����⡣

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| info | NavPathInfo | 是 | NavDestinationҳ�����Ϣ�� |
| animated | boolean | 否 | �Ƿ�֧��ת��������<br/>true��֧��ת��������false����֧��ת��������<br/>Ĭ��ֵ��true |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | �첽���ؽ���� |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-Parameter) | Parameter error. Possible causes:<br/>1. Mandatory parameters are left unspecified.<br/>2. Incorrect parameters types.<br/>3. Parameter verification failed. |
| [100001](../../errorcode-universal.md#100001-Internal) | Internal error. |
| [100005](../../errorcode-universal.md#100005-Builder) | Builder function not registered. |
| [100006](../../errorcode-universal.md#100006-NavDestination) | NavDestination not found. |

## pushDestination

```TypeScript
pushDestination(info: NavPathInfo, options?: NavigationOptions): Promise<void>
```

��infoָ����NavDestinationҳ����Ϣ��ջ��ʹ��Promise�첽�ص����ؽӿڵ��ý�����������options��ָ����ͬ��[LaunchMode](arkts-arkui-navigation-launchmode-e.md#LaunchMode)����ʵ�ֲ�ͬ����Ϊ��

> **˵����**
>
> ��������[aboutToAppear](arkts-arkui-basecustomcomponent-c.md#aboutToAppear-1)��ʹ��ջ��������ʱ��ҳ�滹δ������ɣ��ᵼ�°�������תʧ�ܵ����⡣

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| info | NavPathInfo | 是 | NavDestinationҳ�����Ϣ�� |
| options | NavigationOptions | 否 | ·��ջ����ѡ� |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | �쳣���ؽ���� |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-Parameter) | Parameter error. Possible causes:<br/>1. Mandatory parameters are left unspecified.<br/>2. Incorrect parameters types.<br/>3. Parameter verification failed. |
| [100001](../../errorcode-universal.md#100001-Internal) | Internal error. |
| [100005](../../errorcode-universal.md#100005-Builder) | Builder function not registered. |
| [100006](../../errorcode-universal.md#100006-NavDestination) | NavDestination not found. |

## pushDestinationByName

```TypeScript
pushDestinationByName(name: string, param: Object, animated?: boolean): Promise<void>
```

��nameָ����NavDestinationҳ����Ϣ��ջ�����ݵ�����Ϊparam��ʹ��Promise�첽�ص����ؽӿڵ��ý����

> **˵����**
>
> ��������[aboutToAppear](arkts-arkui-basecustomcomponent-c.md#aboutToAppear-1)��ʹ��ջ��������ʱ��ҳ�滹δ������ɣ��ᵼ�°�������תʧ�ܵ����⡣

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| name | string | 是 | NavDestinationҳ�����ơ� |
| param | Object | 是 | ���������õ�NavDestinationҳ����ϸ������ |
| animated | boolean | 否 | �Ƿ�֧��ת��������<br/>true��֧��ת��������false����֧��ת��������<br/>Ĭ��ֵ��true |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | �쳣���ؽ���� |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-Parameter) | Parameter error. Possible causes:<br/>1. Mandatory parameters are left unspecified.<br/>2. Incorrect parameters types.<br/>3. Parameter verification failed. |
| [100001](../../errorcode-universal.md#100001-Internal) | Internal error. |
| [100005](../../errorcode-universal.md#100005-Builder) | Builder function not registered. |
| [100006](../../errorcode-universal.md#100006-NavDestination) | NavDestination not found. |

## pushDestinationByName

```TypeScript
pushDestinationByName(name: string, param: Object, onPop: import('../api/@ohos.base').Callback<PopInfo>, animated?: boolean): Promise<void>
```

��nameָ����NavDestinationҳ����Ϣ��ջ�����ݵ�����Ϊparam��������������ҳ���ջʱ�������ؽ����onPop�ص���ʹ��Promise�첽�ص����ؽӿڵ��ý����

> **˵����**
>
> ��������[aboutToAppear](arkts-arkui-basecustomcomponent-c.md#aboutToAppear-1)��ʹ��ջ��������ʱ��ҳ�滹δ������ɣ��ᵼ�°�������תʧ�ܵ����⡣

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| name | string | 是 | NavDestinationҳ�����ơ� |
| param | Object | 是 | ���������õ�NavDestinationҳ����ϸ������ |
| onPop | import('../api/@ohos.base').Callback&lt;PopInfo&gt; | 是 | Callback�ص�������ҳ���ջʱ�������ؽ������<br/>[pop](NavPathStack#pop(result: Object, animated?: boolean))��<br/>[popToName](arkts-arkui-navpathstack-c.md#popToName-2)��<br/>[popToIndex](arkts-arkui-navpathstack-c.md#popToIndex-2)������result�����󴥷��� |
| animated | boolean | 否 | �Ƿ�֧��ת��������<br/>true��֧��ת��������false����֧��ת��������<br/>Ĭ��ֵ��true |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | �쳣���ؽ���� |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-Parameter) | Parameter error. Possible causes:<br/>1. Mandatory parameters are left unspecified.<br/>2. Incorrect parameters types.<br/>3. Parameter verification failed. |
| [100001](../../errorcode-universal.md#100001-Internal) | Internal error. |
| [100005](../../errorcode-universal.md#100005-Builder) | Builder function not registered. |
| [100006](../../errorcode-universal.md#100006-NavDestination) | NavDestination not found. |

## pushPath

```TypeScript
pushPath(info: NavPathInfo, animated?: boolean): void
```

��infoָ����NavDestinationҳ����Ϣ��ջ��

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| info | NavPathInfo | 是 | NavDestinationҳ�����Ϣ�� |
| animated | boolean | 否 | �Ƿ�֧��ת��������<br/>true��֧��ת��������false����֧��ת��������<br/>��������Ƿ�ʱ����true������ [since 11] |

## pushPath

```TypeScript
pushPath(info: NavPathInfo, options?: NavigationOptions): void
```

��infoָ����NavDestinationҳ����Ϣ��ջ���������options��ָ����ͬ��[LaunchMode](arkts-arkui-navigation-launchmode-e.md#LaunchMode)����ʵ�ֲ�ͬ����Ϊ��

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| info | NavPathInfo | 是 | NavDestinationҳ�����Ϣ�� |
| options | NavigationOptions | 否 | ·��ջ����ѡ� |

## pushPathByName

```TypeScript
pushPathByName(name: string, param: unknown, animated?: boolean): void
```

��nameָ����NavDestinationҳ����Ϣ��ջ�����ݵ�����Ϊparam��

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| name | string | 是 | NavDestinationҳ�����ơ� |
| param | unknown | 是 | ���������õ�NavDestinationҳ����ϸ������unknown�������û��Զ�������͡� |
| animated | boolean | 否 | �Ƿ�֧��ת��������<br/>true��֧��ת��������false����֧��ת��������<br/>Ĭ��ֵ��true [since 11] |

## pushPathByName

```TypeScript
pushPathByName(name: string, param: Object, onPop: import('../api/@ohos.base').Callback<PopInfo>, animated?: boolean): void
```

��nameָ����NavDestinationҳ����Ϣ��ջ�����ݵ�����Ϊparam������onPop�ص�������ջҳ���ջʱ�ķ��ؽ���������д�����

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| name | string | 是 | NavDestinationҳ�����ơ� |
| param | Object | 是 | ���������õ�NavDestinationҳ����ϸ������ |
| onPop | import('../api/@ohos.base').Callback&lt;PopInfo&gt; | 是 | Callback�ص�������ҳ���ջʱ�����ûص��������ؽ������<br/>[pop](NavPathStack#pop(result: Object, animated?: boolean))��<br/>[popToName](arkts-arkui-navpathstack-c.md#popToName-2)��<br/>[popToIndex](arkts-arkui-navpathstack-c.md#popToIndex-2)������result�����󴥷��� |
| animated | boolean | 否 | �Ƿ�֧��ת��������<br/>true��֧��ת��������false����֧��ת��������<br/>Ĭ��ֵ��true |

## removeByIndexes

```TypeScript
removeByIndexes(indexes: Array<number>): number
```

��·��ջ������ֵ��indexes�е�NavDestinationҳ��ɾ����

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| indexes | Array&lt;number&gt; | 是 | ��ɾ��NavDestinationҳ�������ֵ���顣����ֵ��0��ʼ�� |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | ����ɾ����NavDestinationҳ�������� |

## removeByName

```TypeScript
removeByName(name: string): number
```

��·��ջ��ָ��name��NavDestinationҳ��ɾ����

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| name | string | 是 | ɾ����NavDestinationҳ������֡� |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | ����ɾ����NavDestinationҳ�������� |

## removeByNavDestinationId

```TypeScript
removeByNavDestinationId(navDestinationId: string): boolean
```

��·��ջ��ָ��navDestinationId��NavDestinationҳ��ɾ����navDestinationId������NavDestination��
[onReady](NavDestinationAttribute#onReady)�ص��л�ȡ��Ҳ������
[NavDestinationInfo](arkts-arkui-uiobserver-navdestinationinfo-i.md#NavDestinationInfo)�л�ȡ��

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| navDestinationId | string | 是 | ɾ����NavDestinationҳ���Ψһ��ʶ��navDestinationId�� |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | �����Ƿ�ɹ�ɾ����ҳ�棬<br/>true��ɾ���ɹ���<br/>false��ɾ��ʧ�ܡ� |

## replaceDestination

```TypeScript
replaceDestination(info: NavPathInfo, options?: NavigationOptions): Promise<void>
```

�滻·��ջ������ʹ��Promise�첽�ص����ؽӿڵ��ý�����������options��ָ����ͬ��[LaunchMode](arkts-arkui-navigation-launchmode-e.md#LaunchMode)����ʵ�ֲ�ͬ����Ϊ��

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| info | NavPathInfo | 是 | NavDestinationҳ�����Ϣ�� |
| options | NavigationOptions | 否 | ·��ջ����ѡ� |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | �쳣���ؽ���� |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-Parameter) | Parameter error. Possible causes:<br/>1. Mandatory parameters are left unspecified.<br/>2. Incorrect parameters types.<br/>3. Parameter verification failed. |
| [100001](../../errorcode-universal.md#100001-Internal) | Internal error. |
| [100005](../../errorcode-universal.md#100005-Builder) | Builder function not registered. |
| [100006](../../errorcode-universal.md#100006-NavDestination) | NavDestination not found. |

## replacePath

```TypeScript
replacePath(info: NavPathInfo, animated?: boolean): void
```

����ǰ·��ջջ���˳�����infoָ����NavDestinationҳ����Ϣ��ջ��

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| info | NavPathInfo | 是 | ��ջ��ҳ�������Ϣ�� |
| animated | boolean | 否 | �Ƿ�֧��ת��������<br/>true��֧��ת��������false����֧��ת��������<br/>Ĭ��ֵ��true |

## replacePath

```TypeScript
replacePath(info: NavPathInfo, options?: NavigationOptions): void
```

�滻·��ջ�������������options��ָ����ͬ��[LaunchMode](arkts-arkui-navigation-launchmode-e.md#LaunchMode)����ʵ�ֲ�ͬ����Ϊ��

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| info | NavPathInfo | 是 | ��ջ��ҳ�������Ϣ�� |
| options | NavigationOptions | 否 | ·��ջ����ѡ� |

## replacePathByName

```TypeScript
replacePathByName(name: string, param: Object, animated?: boolean): void
```

����ǰ·��ջջ���˳�����nameָ����ҳ����ջ��

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| name | string | 是 | NavDestinationҳ�����ơ� |
| param | Object | 是 | ���������õ�NavDestinationҳ����ϸ������ |
| animated | boolean | 否 | �Ƿ�֧��ת��������<br/>true��֧��ת��������false����֧��ת��������<br/>Ĭ��ֵ��true |

## setInterception

```TypeScript
setInterception(interception: NavigationInterception): void
```

����Navigationҳ����ת���ػص���

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| interception | NavigationInterception | 是 | ����Navigation��ת���ض��� |

## setPathStack

```TypeScript
setPathStack(pathStack: Array<NavPathInfo>, animated?: boolean): void
```

����ǰ·��ջ�е�·��ҳ����Ϣ�������Ϊָ�����ݣ���ʵ��·��ת����

> **˵����**
>
> 1. �����߿�����ԭ��ջ�Ļ������������ӻ�ɾ��ҳ�档������ջ��ҳ���У�ֻ�пɼ���ҳ��ᴥ������������ҳ��������ջ��������������������Щҳ���Ϊ�ɼ�ʱ���Żᴥ��������
>
> 2. ͨ��������ջ���ܸ��µ�·��ջ����ҳ������������¼�����˳��Ϊ��ջ�����ײ����δ���������������ջ�ӿڴ�ջ�׵������Ĵ���˳��ͬ��
>
> 3. �����߿���ͨ��[NavPathInfo](arkts-arkui-navigation-navpathinfo-c.md#NavPathInfo)�е�ҳ��Ψһ��ʶ��navDestinationId����������ҳ�棬��id��ϵͳĬ��������ȫ��Ψһ������ͨ��
> [getPathStack](arkts-arkui-navpathstack-c.md#getPathStack-1)�ӿڻ�ȡ��������������ֵ��������id�ڵ�ǰ·��ջ�в����ڣ����ʾ����ҳ�棬���ڵ�ǰ·��ջ�д��ڣ�ͬʱ��Ӧ��name��ͬ�����ʾ������
> ��ҳ�档

**起始版本：** 19

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| pathStack | Array&lt;NavPathInfo&gt; | 是 | ���õ�ǰ·��ջ�е�·��ҳ����Ϣ���顣<br/>**˵����**<br/>���鳤�������ơ� |
| animated | boolean | 否 | �Ƿ���ת��������<br/>true������ת��������false��������ת��������<br/>Ĭ��ֵ��true |

## size

```TypeScript
size(): number
```

��ȡջ��С��

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | Stack size.<br/><br/>Value range: [0, +��) |

