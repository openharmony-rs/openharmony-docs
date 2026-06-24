# NavDestination属性/事件

֧��[ͨ������](../../apis-ability-kit/arkts-apis/arkts-app-ability-common.md#common)��

��֧��[ͨ���¼�](../../apis-ability-kit/arkts-apis/arkts-app-ability-common.md#common)�⣬��֧�������¼���

**继承/实现关系：** NavDestinationAttribute extends [CommonMethod<NavDestinationAttribute>](CommonMethod<NavDestinationAttribute>)

**起始版本：** 9

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## backButtonIcon

```TypeScript
backButtonIcon(value: ResourceStr | PixelMap | SymbolGlyphModifier)
```

���ñ��������ؼ�ͼ�ꡣ

> **˵����**

> - ��API version 12��ʼ���ýӿ�֧����[attributeModifier](arkts-arkui-commonmethod-c.md#attributeModifier-1)�е��á�
>
> - ��֧��ͨ��SymbolGlyphModifier�����fontSize�����޸�ͼ���С��effectStrategy�����޸Ķ�Ч��symbolEffect�����޸Ķ�Ч���͡�

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | ResourceStr \| PixelMap \| SymbolGlyphModifier | 是 | ���������ؼ�ͼ�ꡣ [since 11 - 11] |

## backButtonIcon

```TypeScript
backButtonIcon(icon: ResourceStr | PixelMap | SymbolGlyphModifier, accessibilityText?: ResourceStr)
```

���ñ��������ؼ�ͼ������ϰ��������ݡ�

> **˵����**

> - �ýӿڲ�֧����[attributeModifier](arkts-arkui-commonmethod-c.md#attributeModifier-1)�е��á�
>
> - ��֧��ͨ��SymbolGlyphModifier�����fontSize�����޸�ͼ���С��effectStrategy�����޸Ķ�Ч��symbolEffect�����޸Ķ�Ч���͡�

**起始版本：** 19

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| icon | ResourceStr \| PixelMap \| SymbolGlyphModifier | 是 | ���������ؼ�ͼ�ꡣ |
| accessibilityText | ResourceStr | 否 | ���ؼ����ϰ��������ݡ�Ĭ��ֵ��ϵͳ����������ʱΪ�����ء���ϵͳ������Ӣ��ʱΪ��back���� |

## bindToNestedScrollable

```TypeScript
bindToNestedScrollable(scrollInfos: Array<NestedScrollInfo>)
```

��NavDestination�����Ƕ�׵Ŀɹ������������֧��[List](arkts-arkui-list.md)��[Scroll](arkts-arkui-scroll.md)��[Grid](arkts-arkui-grid.md)��
[WaterFlow](arkts-arkui-waterflow.md)����������������������ʱ���ᴥ����������󶨵�NavDestination����ı������͹���������ʾ�����ض�Ч���ϻ����أ��»���ʾ��һ��NavDestination�����
��Ƕ�׵Ŀɹ�����������󶨣�Ƕ�׵Ŀɹ����������Ҳ������NavDestination�󶨡�ʹ��ʾ���μ�
[ʾ��1](../../../../reference/apis-arkui/arkui-ts/ts-basic-components-navdestination.md#ʾ��1��������������ɹ������������)��

> **˵����**

> - ֻ��NavDestination�ı������򹤾�������Ϊ�ɼ�ʱ������Ч���Ż���Ч��
>
> - ������ɹ��������������ͬһ��NavDestination���ʱ�������κ�һ���������ᴥ���������͹���������ʾ������Ч�����ҵ��κ�һ���ɹ�����������������ײ��򶥲�λ��ʱ�������������������͹���������ʾ��Ч����ˣ�Ϊ�˻�
> ������û����飬������ͬʱ��������ɹ�����������Ĺ����¼���
>
> - ��API version 22��ʼ���ýӿ�֧����[attributeModifier](arkts-arkui-commonmethod-c.md#attributeModifier-1)�е��á�

**起始版本：** 14

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| scrollInfos | Array&lt;NestedScrollInfo&gt; | 是 | Ƕ�׵Ŀɹ�����������Ŀ������� |

## bindToScrollable

```TypeScript
bindToScrollable(scrollers: Array<Scroller>)
```

��NavDestination����Ϳɹ������������֧��[List](arkts-arkui-list.md)��[Scroll](arkts-arkui-scroll.md)��[Grid](arkts-arkui-grid.md)��
[WaterFlow](arkts-arkui-waterflow.md)�����������ɹ����������ʱ���ᴥ����������󶨵�NavDestination����ı������͹���������ʾ�����ض�Ч���ϻ����أ��»���ʾ��һ��NavDestination�����
���ɹ�����������󶨣�һ���ɹ����������Ҳ������NavDestination�󶨡�ʹ��ʾ���μ�
[ʾ��1](../../../../reference/apis-arkui/arkui-ts/ts-basic-components-navdestination.md#ʾ��1��������������ɹ������������)��

> **˵����**

> - ֻ��NavDestination�ı������򹤾�������Ϊ�ɼ�ʱ������Ч���Ż���Ч��
>
> - ������ɹ��������������ͬһ��NavDestination���ʱ�������κ�һ���������ᴥ���������͹���������ʾ������Ч�����ҵ��κ�һ���ɹ�����������������ײ��򶥲�λ��ʱ�������������������͹���������ʾ��Ч����ˣ�Ϊ�˻�
> ������û����飬������ͬʱ��������ɹ�����������Ĺ����¼���
>
> - ��API version 22��ʼ���ýӿ�֧����[attributeModifier](arkts-arkui-commonmethod-c.md#attributeModifier-1)�е��á�

**起始版本：** 14

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| scrollers | Array&lt;Scroller&gt; | 是 | �ɹ�����������Ŀ������� |

## customTransition

```TypeScript
customTransition(delegate: NavDestinationTransitionDelegate)
```

����NavDestination�Զ���ת��������

> **˵����**

> - �ýӿڲ�֧����[attributeModifier](arkts-arkui-commonmethod-c.md#attributeModifier-1)�е��á�
>
> - ��������[systemTransition](NavDestinationAttribute#systemTransition)ͬʱ����ʱ�������õ�������Ч��

**起始版本：** 15

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| delegate | NavDestinationTransitionDelegate | 是 | NavDestination�Զ��嶯���Ĵ��������� |

## enableNavigationIndicator

```TypeScript
enableNavigationIndicator(enabled: Optional<boolean>)
```

���ý����NavDestination����ʾ��������ϵͳ�ĵ�������

> **˵����**

> ��������������ȫ������ʱ����Ч��

> ����ϵͳ��������ʵ��Ч�������ھ�����豸֧�����������ο����ڵ�
> [setSpecificSystemBarEnabled](../../../../reference/apis-arkui/arkts-apis-window-Window.md#setspecificsystembarenabled11)
> �ӿڡ�

**起始版本：** 19

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| enabled | Optional&lt;boolean&gt; | 是 | �����NavDestination��ϵͳ����������ʾ/����״̬��<br/>true����ʾ��������<br/>false�����ص������� |

## enableStatusBar

```TypeScript
enableStatusBar(enabled: Optional<boolean>, animated?: boolean)
```

���ý����NavDestination����ʾ��������ϵͳ��״̬����

> **˵����**

> - ��������������ȫ������ʱ����Ч��
> > 1. NavDestination����Ӧ��������ҳ�棬����������Ϊȫ�����ڣ�
> > 2. NavDestination������Navigation�Ĵ�Сռ������ҳ�棻
> > 3. NavDestination�Ĵ�Сռ������Navigation�����
> > 4. NavDestination����Ϊ[NavDestinationMode](arkts-arkui-navdestination-navdestinationmode-e.md#NavDestinationMode).STANDARD��
>
> - ����ϵͳ״̬����ʵ��Ч�������ھ�����豸֧�����������ο����ڵ�
> [setSpecificSystemBarEnabled](../../../../reference/apis-arkui/arkts-apis-window-Window.md#setspecificsystembarenabled11)
> �ӿڡ�

**起始版本：** 19

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| enabled | Optional&lt;boolean&gt; | 是 | �����NavDestination��ϵͳ״̬������ʾ/����״̬��<br/>true����ʾ״̬����<br/>false������״̬���� |
| animated | boolean | 否 | �Ƿ�ʹ�ö����ķ�ʽ��ʾ/����ϵͳ״̬����<br/>Ĭ��ֵ��false<br/>true��ʹ�ö����ķ�ʽ��ʾ/����ϵͳ״̬����<br/>false����ʹ�ö����ķ�ʽ��ʾ<br/>/����ϵͳ״̬���� |

## fullScreenOverlay

```TypeScript
fullScreenOverlay(fullScreenOverlay: Optional<boolean>)
```

����NavDestination�Ƿ���ȫ������ģʽ��ʾ��

����������Ϊtrueʱ����Navigation����ģʽ�£���ǰҳ��Ḳ������Navigation����������NavBar���������������������ڵ�ǰNavDestination������ʵ������·��ջ������ҳ����ȫ������ģʽ��ʾʱ�������
ջ��[DIALOG](arkts-arkui-navdestination-navdestinationmode-e.md#NavDestinationMode)ҳ����δ����fullScreenOverlayΪfalse��[STANDARD](arkts-arkui-navdestination-navdestinationmode-e.md#NavDestinationMode)ҳ��Ҳ��̳�Ϊȫ��������
ʾ��δͨ���ýӿ�����ʱ��NavDestinationĬ������ͨ��ʾģʽ����ѭNavigation������ʾ����

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| fullScreenOverlay | Optional&lt;boolean&gt; | 是 | �Ƿ���ȫ������ģʽ��ʾ��<br/>true��ȫ������ģʽ����������Navigation������<br/>false����ͨ��ʾģʽ����ѭ<br/>Navigation������ʾ����ָ��Ϊfalse��STANDARD����ҳ�治��̳�ȫ����ʾ��<br/>undefined����ͨ��ʾģʽ����ѭNavigation������ʾ����ָ��Ϊundefined��ҳ���̳�ȫ����ʾ�� |

## hideBackButton

```TypeScript
hideBackButton(hide: Optional<boolean>)
```

�����Ƿ����ر������еķ��ؼ���

**起始版本：** 15

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| hide | Optional&lt;boolean&gt; | 是 | �Ƿ����ر������еķ��ؼ���<br/>Ĭ��ֵ��false<br/>true�����ط��ؼ���<br/>false����ʾ���ؼ��� |

## hideTitleBar

```TypeScript
hideTitleBar(value: boolean)
```

�����Ƿ����ر�������

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | boolean | 是 | �Ƿ����ر�������<br/>Ĭ��ֵ��false<br/>true�����ر�������<br/>false����ʾ�������� |

## hideTitleBar

```TypeScript
hideTitleBar(hide: boolean, animated: boolean)
```

�����Ƿ����ر���������[hideTitleBar](NavDestinationAttribute#hideTitleBar(value: boolean))��ȣ���������������ʱ�Ƿ�ʹ�ö�����

**起始版本：** 13

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| hide | boolean | 是 | �Ƿ����ر�������<br/>Ĭ��ֵ��false<br/>true�����ر�������<br/>false����ʾ�������� |
| animated | boolean | 是 | �����Ƿ�ʹ�ö���������������<br/>Ĭ��ֵ��false<br/>true��ʹ�ö�����ʾ���ر�������<br/>false����ʹ�ö�����ʾ���ر������� |

## hideToolBar

```TypeScript
hideToolBar(hide: boolean, animated?: boolean)
```

�����Ƿ����ع�������

**起始版本：** 13

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| hide | boolean | 是 | �Ƿ����ع�������<br/>Ĭ��ֵ��false<br/>true�����ع�������<br/>false����ʾ�������� |
| animated | boolean | 否 | �����Ƿ�ʹ�ö���������������<br/>Ĭ��ֵ��false<br/>true��ʹ�ö�����ʾ���ع�������<br/>false����ʹ�ö�����ʾ���ع������� |

## ignoreLayoutSafeArea

```TypeScript
ignoreLayoutSafeArea(types?: Array<LayoutSafeAreaType>, edges?: Array<LayoutSafeAreaEdge>)
```

��������Ĳ��֣�ʹ����չ���ǰ�ȫ����

> **˵����**

> - �������ignoreLayoutSafeArea֮����Ч������Ϊ��
> > ����LayoutSafeAreaType.SYSTEMʱ������ı߽���ǰ�ȫ�����غ�ʱ����ܹ����쵽�ǰ�ȫ�����¡�
>
> - �������չ���ǰ�ȫ�����ڣ���ʱ�ڷǰ�ȫ�����ﴥ�����¼������磺����¼����ȿ��ܻᱻϵͳ���أ�������Ӧ״̬����ϵͳ�����
>
> - �����Ҫ��չ���ǰ�ȫ�����ڣ������ػ������ñ������͹�����Ϊ[STACK](arkts-arkui-navigation-barstyle-e.md#BarStyle)ģʽ��

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| types | Array&lt;LayoutSafeAreaType&gt; | 否 | ������չ��ȫ��������͡�<br/>Ĭ��ֵ��<br/>[LayoutSafeAreaType.SYSTEM] |
| edges | Array&lt;LayoutSafeAreaEdge&gt; | 否 | ������չ��ȫ����ķ���<br/>Ĭ��ֵ��<br/><br/>[LayoutSafeAreaEdge.TOP, LayoutSafeAreaEdge.BOTTOM]�� |

## menus

```TypeScript
menus(value: Array<NavigationMenuItem> | CustomBuilder)
```

����ҳ�����Ͻǲ˵���������ʱ����ʾ�˵��ʹ��Array<[NavigationMenuItem](arkts-arkui-navigation-navigationmenuitem-i.md#NavigationMenuItem)&gt; д��ʱ���������֧����ʾ3��ͼ�꣬�������֧����ʾ5��ͼ�꣬�����ͼ��
�ᱻ�����Զ����ɵĸ���ͼ�ꡣ

> **˵����**

> - ��API version 14��ʼ���ýӿ�֧����[attributeModifier](arkts-arkui-commonmethod-c.md#attributeModifier-1)�е��á�
>
> - ��֧��ͨ��SymbolGlyphModifier�����fontSize�����޸�ͼ���С��effectStrategy�����޸Ķ�Ч��symbolEffect�����޸Ķ�Ч���͡�

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | Array&lt;NavigationMenuItem&gt; \| CustomBuilder | 是 | ҳ�����Ͻǲ˵��� |

## menus

```TypeScript
menus(items: Array<NavigationMenuItem> | CustomBuilder, options?: NavigationMenuOptions)
```

����ҳ�����Ͻǲ˵���������ʱ����ʾ�˵����
[menus](NavDestinationAttribute#menus(value: Array<NavigationMenuItem> | CustomBuilder))��ȣ������˵�ѡ�ʹ��Array<
[NavigationMenuItem](arkts-arkui-navigation-navigationmenuitem-i.md#NavigationMenuItem)&gt; д��ʱ���������֧����ʾ3��ͼ�꣬�������֧����ʾ5��ͼ�꣬�����ͼ��ᱻ�����Զ����ɵĸ���ͼ�ꡣ

> **˵����**

> - �ýӿڲ�֧����[attributeModifier](arkts-arkui-commonmethod-c.md#attributeModifier-1)�е��á�
>
> - ��֧��ͨ��SymbolGlyphModifier�����fontSize�����޸�ͼ���С��effectStrategy�����޸Ķ�Ч��symbolEffect�����޸Ķ�Ч���͡�

**起始版本：** 19

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| items | Array&lt;NavigationMenuItem&gt; \| CustomBuilder | 是 | ҳ�����Ͻǲ˵��� |
| options | NavigationMenuOptions | 否 | ҳ�����Ͻǲ˵�ѡ� |

## mode

```TypeScript
mode(value: NavDestinationMode)
```

����NavDestination���ͣ���֧�ֶ�̬�޸ġ�

> **˵����**

> ��API version 12��ʼ���ýӿ�֧����[attributeModifier](arkts-arkui-commonmethod-c.md#attributeModifier-1)�е��á�

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | NavDestinationMode | 是 | NavDestination���͡�<br/>Ĭ��ֵ��NavDestinationMode.STANDARD |

## onActive

```TypeScript
onActive(callback: Optional<Callback<NavDestinationActiveReason>>)
```

NavDestination���ڼ���̬������ջ���ɲ��������ϲ�����������ڵ���ʱ�������ûص���ʹ��ʾ���μ�
[ʾ��5](../../../../reference/apis-arkui/arkui-ts/ts-basic-components-navdestination.md#ʾ��5navdestination��onactive��oninactive��������)��

> **˵����**

> ��API version 22��ʼ���ýӿ�֧����[attributeModifier](arkts-arkui-commonmethod-c.md#attributeModifier-1)�е��á�

**起始版本：** 17

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | Optional&lt;Callback&lt;NavDestinationActiveReason&gt;&gt; | 是 | Indicates callback when destination is active. |

## onBackPressed

```TypeScript
onBackPressed(callback: () => boolean)
```

����Navigation�󶨵ĵ����������д�������ʱ���˻ص���Ч����������ؼ�ʱ�������ûص���

����ֵΪtrueʱ����ʾ��д���ؼ��߼�������ֵΪfalseʱ����ʾ���˵���һ��ҳ�档

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | () =&gt; boolean | 是 | ����Navigation�󶨵ĵ����������д�������ʱ���˻ص���Ч����������ؼ�ʱ�������ûص��� |

## onHidden

```TypeScript
onHidden(callback: Callback<VisibilityChangeReason>)
```

����NavDestinationҳ������ʱ�����˻ص�����API version 21��ʼ��֧��ͨ��VisibilityChangeReason˵��onHidden������ԭ��

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | Callback&lt;VisibilityChangeReason&gt; | 是 | ����NavDestinationҳ������ʱ�����˻ص���<br/>��API version 21֮ǰ����<br/>NavDestinationҳ������ʱ�����ص���<br/>��API version 21��ʼ���ûص����ṩ���VisibilityChangeReason��˵��onHidden������ԭ�� [since 21] |

## onInactive

```TypeScript
onInactive(callback: Optional<Callback<NavDestinationActiveReason>>)
```

NavDestination���ڷǼ���̬�����ڷ�ջ�����ɲ���������ջ��ʱ�ϲ�����������ڵ���ʱ�������ûص���ʹ��ʾ���μ�
[ʾ��5](../../../../reference/apis-arkui/arkui-ts/ts-basic-components-navdestination.md#ʾ��5navdestination��onactive��oninactive��������)��

> **˵����**

> ��API version 22��ʼ���ýӿ�֧����[attributeModifier](arkts-arkui-commonmethod-c.md#attributeModifier-1)�е��á�

**起始版本：** 17

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | Optional&lt;Callback&lt;NavDestinationActiveReason&gt;&gt; | 是 | Indicates callback when destination is<br/>inactive. |

## onNewParam

```TypeScript
onNewParam(callback: Optional<Callback<ESObject>>)
```

��֮ǰ������ջ�е�NavDestinationҳ��ͨ��[launchMode.MOVE_TO_TOP_SINGLETON](arkts-arkui-navigation-launchmode-e.md#LaunchMode)��
[launchMode.POP_TO_SINGLETON](arkts-arkui-navigation-launchmode-e.md#LaunchMode)�ƶ���ջ��ʱ�������ûص���

> **˵����**

> - [replacePath](arkts-arkui-navpathstack-c.md#replacePath-1)��
> [replaceDestination](arkts-arkui-navpathstack-c.md#replaceDestination-1)���ᴥ���ûص���
>
> - ��API version 22��ʼ���ýӿ�֧����[attributeModifier](arkts-arkui-commonmethod-c.md#attributeModifier-1)�е��á�

**起始版本：** 19

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | Optional&lt;Callback&lt;ESObject&gt;&gt; | 是 | Indicates callback when destination be pushed with singleton<br/>mode. |

## onReady

```TypeScript
onReady(callback: import('../api/@ohos.base').Callback<NavDestinationContext>)
```

��NavDestination�������������֮ǰ�ᴥ���˻ص���

> **˵����**

> ��API version 20��ʼ���ýӿ�֧����[attributeModifier](arkts-arkui-commonmethod-c.md#attributeModifier-1)�е��á�

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | import('../api/@ohos.base').Callback&lt;NavDestinationContext&gt; | 是 | ��NavDestination�������������֮ǰ�ᴥ���˻ص��� |

## onRestoreState

```TypeScript
onRestoreState(callback: Optional<RestoreStateCallback>)
```

�����Զ���ҳ��״̬�ָ��ص���

��ҳ���ع�ʱ��������onSaveState������Զ���״̬�����ݸ��˻ص���
���û�б����Զ���״̬���򴫵�Null��

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | Optional&lt;RestoreStateCallback&gt; | 是 | �Զ���״̬�ָ��ص� |

## onResult

```TypeScript
onResult(callback: Optional<Callback<ESObject>>)
```

NavDestination����ʱ�����ûص���

> **˵����**

> ��API version 22��ʼ���ýӿ�֧����[attributeModifier](arkts-arkui-commonmethod-c.md#attributeModifier-1)�е��á�

**起始版本：** 15

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | Optional&lt;Callback&lt;ESObject&gt;&gt; | 是 | Indicates callback when pop to the navDestination with result. |

## onSaveState

```TypeScript
onSaveState(callback: Optional<SaveStateCallback>)
```

�����Զ���ҳ��״̬����ص���

��ҳ�汻����ʱ�����������Զ���ҳ��״̬�Ա��ָ���
���ڴ���ҳ��ĳ�ʼ�����ɵ�������������
״̬��������ǿ����л��ġ�

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | Optional&lt;SaveStateCallback&gt; | 是 | �Զ���״̬����ص� |

## onShown

```TypeScript
onShown(callback: Callback<VisibilityChangeReason>)
```

����NavDestinationҳ����ʾʱ�����˻ص�����API version 21��ʼ��֧��ͨ��VisibilityChangeReason˵��onShown������ԭ��

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | Callback&lt;VisibilityChangeReason&gt; | 是 | ����NavDestinationҳ����ʾʱ�����˻ص���<br/>��API version 21֮ǰ����<br/>NavDestinationҳ����ʾʱ�����ص���<br/>��API version 21��ʼ���ص����ṩ���VisibilityChangeReason��˵��onShown������ԭ�� [since 21] |

## onWillAppear

```TypeScript
onWillAppear(callback: Callback<void>)
```

����NavDestination����֮ǰ�����˻ص����ڸûص��������޸�·��ջ����ǰ֡��Ч��

> **˵����**

> ��API version 20��ʼ���ýӿ�֧����[attributeModifier](arkts-arkui-commonmethod-c.md#attributeModifier-1)�е��á�

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | Callback&lt;void&gt; | 是 | ����NavDestination����֮ǰ�����˻ص����ڸûص��������޸�·��ջ����ǰ֡��Ч�� |

## onWillDisappear

```TypeScript
onWillDisappear(callback: Callback<void>)
```

����NavDestinationж��֮ǰ��������������(��ת������ʱ����ת��������ʼ֮ǰ����)��

> **˵����**

> ��API version 20��ʼ���ýӿ�֧����[attributeModifier](arkts-arkui-commonmethod-c.md#attributeModifier-1)�е��á�

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | Callback&lt;void&gt; | 是 | ����NavDestinationж��֮ǰ��������������(��ת������ʱ����ת��������ʼ֮ǰ����)�� |

## onWillHide

```TypeScript
onWillHide(callback: Callback<void>)
```

����NavDestination����֮ǰ�����˻ص���

> **˵����**

> ��API version 20��ʼ���ýӿ�֧����[attributeModifier](arkts-arkui-commonmethod-c.md#attributeModifier-1)�е��á�

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | Callback&lt;void&gt; | 是 | ����NavDestination����֮ǰ�����˻ص��� |

## onWillShow

```TypeScript
onWillShow(callback: Callback<void>)
```

����NavDestination��ʾ֮ǰ�����˻ص���

> **˵����**

> ��API version 20��ʼ���ýӿ�֧����[attributeModifier](arkts-arkui-commonmethod-c.md#attributeModifier-1)�е��á�

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | Callback&lt;void&gt; | 是 | ����NavDestination��ʾ֮ǰ�����˻ص��� |

## preferredOrientation

```TypeScript
preferredOrientation(orientation: Optional<Orientation>)
```

����NavDestination��Ӧ����ʾ����ת������NavDestination��ϵͳҲ�ὫӦ���������е�����ʾ����

> **˵����**

> - ��������������ȫ������ʱ����Ч��
> > 1. NavDestination����Ӧ��������ҳ�棬����������Ϊȫ�����ڣ�
> > 2. NavDestination������Navigation�Ĵ�Сռ������Ӧ��ҳ�棻
> > 3. NavDestination����Ϊ[NavDestinationMode](arkts-arkui-navdestination-navdestinationmode-e.md#NavDestinationMode).STANDARD��
>
> - ������ʾ�����ʵ��Ч�������ھ�����豸֧�����������ο����ڵ�
> [setPreferredOrientation](../../../../reference/apis-arkui/arkts-apis-window-Window.md#setpreferredorientation9-1)��
> �ڡ�

**起始版本：** 19

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| orientation | Optional&lt;Orientation&gt; | 是 | NavDestinationҳ���Ӧ��Orientation�� |

## recoverable

```TypeScript
recoverable(recoverable: Optional<boolean>)
```

����NavDestination�Ƿ�ɻָ���������Ϊ�ɻָ�����Ӧ�ý����쳣�˳�������������ʱ�����Զ�������NavDestination���ù�����NavDestination��Ӧ��NavigationҲ������
[�ɻָ�����](NavigationAttribute#recoverable)��

> **˵����**

> �ýӿ���Ҫ���Navigation��[recoverable](NavigationAttribute#recoverable)�ӿ�ʹ�á�

**起始版本：** 14

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| recoverable | Optional&lt;boolean&gt; | 是 | NavDestination�Ƿ�ɻָ���Ĭ��Ϊ���ɻָ���<br/>Ĭ��ֵ��false<br/>true��·��ջ�ɻָ���<br/>false��·��ջ���ɻָ��� |

## systemBarStyle

```TypeScript
systemBarStyle(style: Optional<SystemBarStyle>)
```

��Navigation����ʾ��ǰNavDestinationʱ�����ö�Ӧϵͳ״̬������ʽ��

> **˵����**

> - �������Navigationʹ�ã���Ϊ��NavigationĿ��ҳ��ĸ��ڵ�ʱ������Ч��
>
> - ����ʹ��������ο�Navigation��Ӧ��[systemBarStyle](NavigationAttribute#systemBarStyle)����˵����
>
> - ��API version 20��ʼ���ýӿ�֧����[attributeModifier](arkts-arkui-commonmethod-c.md#attributeModifier-1)�е��á�

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| style | Optional&lt;SystemBarStyle&gt; | 是 | ϵͳ״̬����ʽ�� |

## systemTransition

```TypeScript
systemTransition(type: NavigationSystemTransitionType)
```

����NavDestinationϵͳת��������֧�ֱַ�����ϵͳ���������������ݶ�����

**起始版本：** 14

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | NavigationSystemTransitionType | 是 | ϵͳת���������͡�<br/>Ĭ��ֵ��NavigationSystemTransitionType.DEFAULT |

## title

```TypeScript
title(value: string | CustomBuilder | NavDestinationCommonTitle | NavDestinationCustomTitle | Resource,
          options?: NavigationTitleOptions)
```

����ҳ����⡣�ַ�������ʱ����������ø����⣬����С�ٻ���2�к���"..."�ضϡ�������ø����⣬����С����"..."�ضϡ�

> **˵����**

> ��API version 12��ʼ���ýӿ�֧����[attributeModifier](arkts-arkui-commonmethod-c.md#attributeModifier-1)�е��á�

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | string \| CustomBuilder \| NavDestinationCommonTitle \| NavDestinationCustomTitle \| Resource | 是 | ҳ���<br/>�⡣ [since 9 - 13] |
| options | NavigationTitleOptions | 否 | Title bar options. [since 12] |

## toolbarConfiguration

```TypeScript
toolbarConfiguration(toolbarParam: Array<ToolbarItem> | CustomBuilder, options?: NavigationToolbarOptions)
```

���ù��������ݡ�δ���ñ��ӿ�ʱ����ʾ��������

> **˵����**

> - ��API version 20��ʼ���ýӿ�֧����[attributeModifier](arkts-arkui-commonmethod-c.md#attributeModifier-1)�е��á�
>
> - ��֧��ͨ��SymbolGlyphModifier�����fontSize�����޸�ͼ���С��effectStrategy�����޸Ķ�Ч��symbolEffect�����޸Ķ�Ч���͡�

**起始版本：** 13

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| toolbarParam | Array&lt;ToolbarItem&gt; \| CustomBuilder | 是 | ���������ݡ�<br/>ʹ��Arrayд��<br/>���õĹ��������������ԣ�<br/>-����������ѡ����ֵײ�����������ÿ�����������������ı���ͼ�ꡣ<br/>-����ģʽ���֧����ʾ5��ͼ�꣬�����ͼ��ᱻ�����Զ����ɵĸ���ͼ���У��������ͼ�꣬����չʾʣ�����ݡ�����ģʽ<br/>ʱ�����Ϊ[Split](arkts-arkui-navigation-navigationmode-e.md#NavigationMode)ģʽ���԰�������ģʽ��ʾ�����Ϊ[Stack](arkts-arkui-navigation-navigationmode-e.md#NavigationMode)ģʽ�����<br/>[menus](NavDestinationAttribute#menus(value: Array \| CustomBuilder))���Ե�Arrayʹ�ã��ײ����������Զ����أ�ͬʱ�ײ�����������ѡ���ƶ���ҳ�����Ͻǲ˵���<br/>ʹ��<br/>[CustomBuilder](../../../../reference/apis-arkui/arkui-ts/ts-types.md#custombuilder8)д��Ϊ�û��Զ��幤����ѡ����߱����Ϲ��ܡ� |
| options | NavigationToolbarOptions | 否 | ������ѡ�����������������ɫ������������ģ����ʽ��ģ��ѡ��������������ԡ����������ַ�ʽ���Ƿ����ع��������ı�������������ͼ��Ĳ�<br/>��ѡ� |

