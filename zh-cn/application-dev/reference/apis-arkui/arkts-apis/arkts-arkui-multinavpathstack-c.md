# MultiNavPathStack

��ǰ��MultiNavigation��·��ջ��֧����ʹ�÷����д�������֧��ͨ���ص���ʽ��ȡ������ʹ��[NavDestination](arkts-arkui-navdestination.md)��
[onReady](NavDestinationAttribute#onReady)�������¼���ӿ�����ȡNavPathStack������ջ��������Ϊ����ܻᵼ�²���Ԥ֪�����⡣

**继承/实现关系：** MultiNavPathStack extends [NavPathStack](arkts-arkui-navigation-navpathstack-c.md#NavPathStack)

**起始版本：** 14

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## clear

```TypeScript
clear(animated?: boolean): void
```

���ջ������ҳ�档

> **˵����**

> ������[keepBottomPage](arkts-arkui-multinavpathstack-c.md#keepBottomPage-1)�ӿڲ�����Ϊtrueʱ���ᱣ��ջ��ҳ�档

**起始版本：** 14

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| animated | boolean | 否 | �Ƿ�֧��ת��������<br/>Ĭ��ֵ��true<br/>true��֧��ת��������<br/>false����֧��ת�������� |

## constructor

```TypeScript
constructor()
```

Creates an instance of MultiNavPathStack.

**起始版本：** 14

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## disableAnimation

```TypeScript
disableAnimation(disable: boolean): void
```

�رգ�true����򿪣�false����ǰMultiNavigation������ת��������

**起始版本：** 14

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| disable | boolean | 是 | �Ƿ�ر�ת��������<br/>Ĭ��ֵ��false<br/>true���ر�ת��������<br/>false�����ر�ת�������� |

## getAllPathName

```TypeScript
getAllPathName(): Array<string>
```

��ȡջ������NavDestinationҳ������ơ�

**起始版本：** 14

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 该接口支持在原子化服务API中使用。

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

**起始版本：** 14

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| name | string | 是 | NavDestinationҳ�����ơ� |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Array&lt;number&gt; | Indexes of all the matching navigation destination pages.<br/><br/>Value range of the number type: [0, +��). |

## getParamByIndex

```TypeScript
getParamByIndex(index: number): Object | undefined
```

��ȡindexָ����NavDestinationҳ��Ĳ�����Ϣ��

**起始版本：** 14

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| index | number | 是 | NavDestinationҳ���λ��������<br/>ȡֵ��Χ��[0, +��) |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Object | **Object**: parameter information of the matching navigation destination page.<br/><br/>**undefined**: returned when an invalid index is provided. |

## getParamByName

```TypeScript
getParamByName(name: string): Array<Object>
```

��ȡȫ����Ϊname��NavDestinationҳ��Ĳ�����Ϣ��

**起始版本：** 14

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| name | string | 是 | NavDestinationҳ�����ơ� |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Array&lt;Object&gt; | ����ȫ����Ϊname��NavDestinationҳ��Ĳ�����Ϣ�� |

## keepBottomPage

```TypeScript
keepBottomPage(keepBottom: boolean): void
```

�����ڵ���pop��clear�ӿ�ʱ�Ƿ���ջ��ҳ�档

> **˵����**

> MultiNavigation����ҳҲ������NavDestinationҳ����ջ�����Ե���pop��clear�ӿ�ʱ�Ὣջ��ҳ��Ҳ��ջ��
> > Ӧ�õ��ô˽ӿڲ�����Ϊtrueʱ��MultiNavigation���ڵ���pop��clear�ӿ�ʱ����ջ��ҳ�档

**起始版本：** 14

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| keepBottom | boolean | 是 | �Ƿ���ջ��ҳ�档<br/>Ĭ��ֵ��false<br/>true������ջ��ҳ�档<br/>false��������ջ��ҳ�档 |

## moveIndexToTop

```TypeScript
moveIndexToTop(index: number, animated?: boolean): void
```

��ָ��index��NavDestinationҳ���Ƶ�ջ����

> **˵����**

> �����ҵ��ĵ�һ����Ϊname��ҳ��Ĳ�ͬ��MultiNavigation����в�ͬ�Ĵ�����

> 1)���ҵ��������ϲ���ҳ����ȫ��ҳ����ʱ�����κδ�����

> 2)���ҵ��������ϲ���ҳ��Ӧ������ҳ����Ὣ��Ӧ������ҳ�Ƶ�ջ����

> 3)���ҵ����Ƿ����ϲ����ҳ����Ὣ��ҳ�Ͷ�Ӧ��������ҳ�Ƶ�ջ��������ҳ���ջ��ϵ���䣻

> 4)���ҵ����Ƿ����ϲ������ҳ����Ὣ��ҳ�Ͷ�Ӧ��������ҳ�Ƶ�ջ�����ҽ�Ŀ������ҳ�ƶ�����Ӧ��������ҳ��ջ����

> 5)���ҵ����Ƿ����ϲ��ȫ��ҳ����Ὣȫ��ҳ�ƶ���ջ����

**起始版本：** 14

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| index | number | 是 | NavDestinationҳ���λ��������<br/>ȡֵ��Χ��[0, +��) |
| animated | boolean | 否 | �Ƿ�֧��ת��������<br/>Ĭ��ֵ��true<br/>true��֧��ת��������<br/>false����֧��ת�������� |

## moveToTop

```TypeScript
moveToTop(name: string, animated?: boolean): number
```

����ջ�׿�ʼ��һ����Ϊname��NavDestinationҳ���Ƶ�ջ����

> **˵����**

> �����ҵ��ĵ�һ����Ϊname��ҳ��Ĳ�ͬ��MultiNavigation����в�ͬ�Ĵ�����

> 1)���ҵ��������ϲ���ҳ����ȫ��ҳ����ʱ�����κδ�����

> 2)���ҵ��������ϲ���ҳ��Ӧ������ҳ����Ὣ��Ӧ������ҳ�Ƶ�ջ����

> 3)���ҵ����Ƿ����ϲ����ҳ����Ὣ��ҳ�Ͷ�Ӧ��������ҳ�Ƶ�ջ��������ҳ���ջ��ϵ���䣻

> 4)���ҵ����Ƿ����ϲ������ҳ����Ὣ��ҳ�Ͷ�Ӧ��������ҳ�Ƶ�ջ�����ҽ�Ŀ������ҳ�ƶ�����Ӧ��������ҳ��ջ����

> 5)���ҵ����Ƿ����ϲ��ȫ��ҳ����Ὣȫ��ҳ�ƶ���ջ����

**起始版本：** 14

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| name | string | 是 | NavDestinationҳ�����ơ� |
| animated | boolean | 否 | �Ƿ�֧��ת��������<br/>Ĭ��ֵ��true<br/>true��֧��ת��������<br/>false����֧��ת�������� |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | ���ջ�д�����Ϊname��NavDestinationҳ�棬�򷵻���ջ�׿�ʼ��һ����Ϊname��NavDestinationҳ������������򷵻�-1�� |

## pop

```TypeScript
pop(animated?: boolean): NavPathInfo | undefined
```

����·��ջջ��Ԫ�ء�

> **˵����**

> ������[keepBottomPage](arkts-arkui-multinavpathstack-c.md#keepBottomPage-1)�ӿڲ�����Ϊtrueʱ���ᱣ��ջ��ҳ�档

**起始版本：** 14

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| animated | boolean | 否 | �Ƿ�֧��ת��������<br/>Ĭ��ֵ��true<br/>true��֧��ת��������<br/>false����֧��ת�������� |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| NavPathInfo | Information about the navigation destination page at the top of the stack. |

## pop

```TypeScript
pop(result?: Object, animated?: boolean): NavPathInfo | undefined
```

����·��ջջ��Ԫ�أ�������onPop�ص�����ҳ�洦�������

> **˵����**

> ������[keepBottomPage](arkts-arkui-multinavpathstack-c.md#keepBottomPage-1)�ӿڲ�����Ϊtrueʱ���ᱣ��ջ��ҳ�档

**起始版本：** 14

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| result | Object | 否 | ҳ���Զ��崦������� |
| animated | boolean | 否 | �Ƿ�֧��ת��������<br/>Ĭ��ֵ��true<br/>true��֧��ת��������<br/>false����֧��ת�������� |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| NavPathInfo | Information about the navigation destination page at the top of the stack. |

## popToIndex

```TypeScript
popToIndex(index: number, animated?: boolean): void
```

����·��ջ��indexָ����NavDestinationҳ�档

**起始版本：** 14

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| index | number | 是 | NavDestinationҳ���λ��������<br/>ȡֵ��Χ��[0, +��) |
| animated | boolean | 否 | �Ƿ�֧��ת��������<br/>Ĭ��ֵ��true<br/>true��֧��ת��������<br/>false����֧��ת�������� |

## popToIndex

```TypeScript
popToIndex(index: number, result: Object, animated?: boolean): void
```

����·��ջ��indexָ����NavDestinationҳ�棬������onPop�ص�����ҳ�洦�������

**起始版本：** 14

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| index | number | 是 | NavDestinationҳ���λ��������<br/>ȡֵ��Χ��[0, +��) |
| result | Object | 是 | ҳ���Զ��崦������� |
| animated | boolean | 否 | �Ƿ�֧��ת��������<br/>Ĭ��ֵ��true<br/>true��֧��ת��������<br/>false����֧��ת�������� |

## popToName

```TypeScript
popToName(name: string, animated?: boolean): number
```

����·��ջ����ջ�׿�ʼ��һ����Ϊname��NavDestinationҳ�档

**起始版本：** 14

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| name | string | 是 | NavDestinationҳ�����ơ� |
| animated | boolean | 否 | �Ƿ�֧��ת��������<br/>Ĭ��ֵ��true<br/>true��֧��ת��������<br/>false����֧��ת�������� |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | Returns the index of the first navigation destination page that matches **name** from the<br/>bottom of the navigation stack; returns **-1** if no such a page is found.<br/><br/>Value range: [-1, +��). |

## popToName

```TypeScript
popToName(name: string, result: Object, animated?: boolean): number
```

����·��ջ����ջ�׿�ʼ��һ����Ϊname��NavDestinationҳ�棬������onPop�ص�����ҳ�洦�������

**起始版本：** 14

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| name | string | 是 | NavDestinationҳ�����ơ� |
| result | Object | 是 | ҳ���Զ��崦������� |
| animated | boolean | 否 | �Ƿ�֧��ת��������<br/>Ĭ��ֵ��true<br/>true��֧��ת��������<br/>false����֧��ת�������� |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | Returns the index of the first navigation destination page that matches **name** from the<br/>bottom of the navigation stack; returns **-1** if no such a page is found.<br/><br/>Value range: [-1, +��). |

## pushPath

```TypeScript
pushPath(info: NavPathInfo, animated?: boolean, policy?: SplitPolicy): void
```

��ָ����NavDestinationҳ����Ϣ��ջ��

**起始版本：** 14

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| info | NavPathInfo | 是 | NavDestinationҳ�����Ϣ�� |
| animated | boolean | 否 | �Ƿ�֧��ת��������<br/>Ĭ��ֵ��true<br/>true��֧��ת��������<br/>false����֧��ת�������� |
| policy | SplitPolicy | 否 | ��ǰ��ջҳ��Ĳ��ԡ�Ĭ��ֵ��DETAIL_PAGE |

## pushPath

```TypeScript
pushPath(info: NavPathInfo, options?: NavigationOptions, policy?: SplitPolicy): void
```

��ָ����NavDestinationҳ����Ϣ��ջ��ͨ��NavigationOptions����ҳ��ջ����ѡ�

**起始版本：** 14

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| info | NavPathInfo | 是 | NavDestinationҳ�����Ϣ�� |
| options | NavigationOptions | 否 | ҳ��ջ����ѡ���֧�����е�animated�ֶΡ� |
| policy | SplitPolicy | 否 | ��ǰ��ջҳ��Ĳ��ԡ�Ĭ��ֵ��DETAIL_PAGE |

## pushPathByName

```TypeScript
pushPathByName(name: string, param: Object, animated?: boolean, policy?: SplitPolicy): void
```

��nameָ����NavDestinationҳ����Ϣ��ջ�����ݵ�����Ϊparam��

**起始版本：** 14

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| name | string | 是 | NavDestinationҳ�����ơ� |
| param | Object | 是 | NavDestinationҳ����ϸ������ |
| animated | boolean | 否 | �Ƿ�֧��ת��������<br/>Ĭ��ֵ��true<br/>true��֧��ת��������<br/>false����֧��ת�������� |
| policy | SplitPolicy | 否 | ��ǰ��ջҳ��Ĳ��ԡ�Ĭ��ֵ��DETAIL_PAGE |

## pushPathByName

```TypeScript
pushPathByName(
    name: string, param: Object, onPop?: base.Callback<PopInfo>, animated?: boolean, policy?: SplitPolicy): void
```

��nameָ����NavDestinationҳ����Ϣ��ջ�����ݵ�����Ϊparam������onPop�ص�������ջҳ���ջʱ�ķ��ؽ���������д�����

**起始版本：** 14

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| name | string | 是 | NavDestinationҳ�����ơ� |
| param | Object | 是 | NavDestinationҳ����ϸ������ |
| onPop | base.Callback&lt;PopInfo&gt; | 否 | Callback�ص�������ҳ���ջʱ�����ûص��������ؽ���� |
| animated | boolean | 否 | �Ƿ�֧��ת��������<br/>Ĭ��ֵ��true<br/>true��֧��ת��������<br/>false����֧��ת�������� |
| policy | SplitPolicy | 否 | ��ǰ��ջҳ��Ĳ��ԡ�Ĭ��ֵ��DETAIL_PAGE |

## removeByIndexes

```TypeScript
removeByIndexes(indexes: Array<number>): number
```

��ҳ��ջ������ֵ��indexes�е�NavDestinationҳ��ɾ����

**起始版本：** 14

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| indexes | Array&lt;number&gt; | 是 | ��ɾ��NavDestinationҳ�������ֵ���顣<br/>number���͵�ȡֵ��Χ��[0, +��) |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | ����ɾ����NavDestinationҳ�������� |

## removeByName

```TypeScript
removeByName(name: string): number
```

��ҳ��ջ��ָ��name��NavDestinationҳ��ɾ����

**起始版本：** 14

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| name | string | 是 | ��ɾ��NavDestinationҳ������֡� |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | ����ɾ����NavDestinationҳ�������� |

## replacePath

```TypeScript
replacePath(info: NavPathInfo, animated?: boolean): void
```

����ǰҳ��ջջ���˳�����ָ����NavDestinationҳ����Ϣ��ջ����ҳ��ķ������Լ̳�ԭջ��ҳ��Ĳ��ԡ�

**起始版本：** 14

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| info | NavPathInfo | 是 | NavDestinationҳ�����Ϣ�� |
| animated | boolean | 否 | �Ƿ�֧��ת��������<br/>Ĭ��ֵ��true<br/>true��֧��ת��������<br/>false����֧��ת�������� |

## replacePath

```TypeScript
replacePath(info: NavPathInfo, options?: NavigationOptions): void
```

����ǰҳ��ջջ���˳�����ָ����NavDestinationҳ����Ϣ��ջ����ҳ��ķ������Լ̳�ԭջ��ҳ��Ĳ��ԣ�ͨ��NavigationOptions����ҳ��ջ����ѡ�

**起始版本：** 14

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| info | NavPathInfo | 是 | NavDestinationҳ�����Ϣ�� |
| options | NavigationOptions | 否 | ҳ��ջ����ѡ���֧�����е�animated�ֶΡ� |

## replacePathByName

```TypeScript
replacePathByName(name: string, param: Object, animated?: boolean): void
```

����ǰҳ��ջջ���˳�����nameָ����ҳ����ջ����ҳ��ķ������Լ̳�ԭջ��ҳ��Ĳ��ԡ�

**起始版本：** 14

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| name | string | 是 | NavDestinationҳ�����ơ� |
| param | Object | 是 | NavDestinationҳ����ϸ������ |
| animated | boolean | 否 | �Ƿ�֧��ת��������<br/>Ĭ��ֵ��true<br/>true��֧��ת��������<br/>false����֧��ת�������� |

## setHomeWidthRange

```TypeScript
setHomeWidthRange(minPercent: number, maxPercent: number): void
```

������ҳ���ȿ��϶���Χ��Ӧ�ò����õ�����¿���Ϊ50%���Ҳ����϶���

**起始版本：** 14

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| minPercent | number | 是 | ��С��ҳ���Ȱٷֱȡ�<br/>ȡֵ��Χ��[0, 100] |
| maxPercent | number | 是 | �����ҳ���Ȱٷֱȡ�<br/>ȡֵ��Χ��[0, 100] |

## setPlaceholderPage

```TypeScript
setPlaceholderPage(info: NavPathInfo): void
```

����ռλҳ�档

> **˵��**

> ռλҳ��Ϊ����ҳ�����ͣ���Ӧ�����ú���һЩ�����豸�ϻ����ҳĬ���γ����ҷ�����Ч�����������ҳ���ұ�ռλҳ��

> ��Ӧ�ÿɻ�������С��600vp���۵�����չ��̬�л�Ϊ�۵�̬��ƽ�����ת�����ȳ���ʱ�����Զ���ռλҳ��ջ��ֻ��ʾ��ҳ��
> > ����Ӧ�ÿɻ���������ڵ���600vp���۵������۵�̬�л�Ϊչ��̬��ƽ������ת�����ȳ���ʱ�����Զ�����ռλҳ���γɷ�����

**起始版本：** 14

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| info | NavPathInfo | 是 | ռλҳҳ����Ϣ�� |

## size

```TypeScript
size(): number
```

��ȡջ��С��

**起始版本：** 14

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | Stack size.<br/><br/>Value range: [0, +��). |

## switchFullScreenState

```TypeScript
switchFullScreenState(isFullScreen?: boolean): boolean
```

�л���ǰ��ջ����ҳ�����ʾģʽ��

**起始版本：** 14

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| isFullScreen | boolean | 否 | �Ƿ��л�Ϊȫ����Ĭ��ֵΪfalse��true��ʾȫ��ģʽ��false��ʾ����ģʽ�� |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | �л��ɹ���ʧ�ܡ�<br/>true���л��ɹ���<br/>false���л�ʧ�ܡ� |

