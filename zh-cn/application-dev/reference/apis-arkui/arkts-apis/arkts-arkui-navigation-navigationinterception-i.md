# NavigationInterception

Navigation��ת���ض���

###### InterceptionShowCallback<sup>12+</sup>

type InterceptionShowCallback = (from: NavDestinationContext | NavBar, to: NavDestinationContext | NavBar, operation:
NavigationOperation, isAnimated: boolean) => void

Navigationҳ����תǰ��ҳ����ת������ػص���

**ԭ�ӻ�����API��** ��API version 12��ʼ���ýӿ�֧����ԭ�ӻ�������ʹ�á�

**ϵͳ������** SystemCapability.ArkUI.ArkUI.Full

**������**

| ������ | ���� | ���� | ˵�� |
| ------ | ------ | ---- | ---------------- |
| from | [NavDestinationContext](arkts-arkui-navdestination-navdestinationcontext-i.md#NavDestinationContext) \| [NavBar](arkts-arkui-navigation-navbar-t.md#NavBar) | �� | ҳ����ת֮ǰ��ջ��ҳ����Ϣ������ֵΪnavBar�����ʾ��תǰ��ҳ��ΪNavigation��ҳ�� |
| to | [NavDestinationContext](arkts-arkui-navdestination-navdestinationcontext-i.md#NavDestinationContext) \| [NavBar](arkts-arkui-navigation-navbar-t.md#NavBar) | �� | ҳ����ת֮���ջ��ҳ����Ϣ������ֵΪnavBar�����ʾ��ת��Ŀ��ҳ��ΪNavigation��ҳ�� |
| operation | [NavigationOperation](arkts-arkui-navigation-navigationoperation-e.md#NavigationOperation) | �� | ��ǰҳ����ת���͡� |
| isAnimated | boolean | �� | ҳ����ת�Ƿ��ж�����<br/>true��ҳ����ת�ж�����<br/>false��ҳ����תû�ж����� |

###### InterceptionModeCallback<sup>12+</sup>

type InterceptionModeCallback = (mode: NavigationMode) => void

Navigation��˫����ʾ״̬�������ʱ�����ػص���

**ԭ�ӻ�����API��** ��API version 12��ʼ���ýӿ�֧����ԭ�ӻ�������ʹ�á�

**ϵͳ������** SystemCapability.ArkUI.ArkUI.Full

**������**

| ������ | ���� | ���� | ˵�� |
| ------ | ------ | ---- | ---------------- |
| mode | [NavigationMode](arkts-arkui-navigation-navigationmode-e.md#NavigationMode) | �� | ����ҳ����ʾģʽ�� |

###### InterceptionCallback<sup>22+</sup>

type InterceptionCallback = (from: NavPathInfo | NavBar, to: NavPathInfo | NavBar, pathStack: NavPathStack,
operation: NavigationOperation, isAnimated: boolean) => void

Navigationҳ����תǰ�����ػص���

**ԭ�ӻ�����API��** ��API version 22��ʼ���ýӿ�֧����ԭ�ӻ�������ʹ�á�

**ϵͳ������** SystemCapability.ArkUI.ArkUI.Full

**������**

| ������ | ���� | ���� | ˵�� |
| ------ | ------ | ---- | ---------------- |
| from | [NavPathInfo](arkts-arkui-navigation-navpathinfo-c.md#NavPathInfo) \|[NavBar](arkts-arkui-navigation-navbar-t.md#NavBar) | �� | �˳�ҳ����Ϣ������ֵΪnavBar�����ʾ��תǰ��ҳ��ΪNavigation��ҳ�� |
| to | [NavPathInfo](arkts-arkui-navigation-navpathinfo-c.md#NavPathInfo) \|[NavBar](arkts-arkui-navigation-navbar-t.md#NavBar) | �� | ����ҳ����Ϣ������ֵΪnavBar�����ʾ��ת��Ŀ��ҳ��ΪNavigation��ҳ�� |
| pathStack | [NavPathStack](arkts-arkui-navigation-navpathstack-c.md#NavPathStack) | �� | ҳ��ջ�� |
| operation | [NavigationOperation](arkts-arkui-navigation-navigationoperation-e.md#NavigationOperation) | �� | ��ǰҳ����ת���͡� |
| isAnimated | boolean | �� | ҳ����ת�Ƿ��ж�����<br/>true��ҳ����ת�ж�����<br/>false��ҳ����תû�ж����� |

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## didShow

```TypeScript
didShow?: InterceptionShowCallback
```

ҳ����ת��ص����ڸûص��в���ջ����һ����ת��ˢ�¡�

**类型：** InterceptionShowCallback

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## interception

```TypeScript
interception?: InterceptionCallback
```

ҳ����תǰ�Ļص�����������ջ���ڵ�ǰ��ת����Ч�����ص�ҳ�治�ᱻ������

**类型：** InterceptionCallback

**起始版本：** 22

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## modeChange

```TypeScript
modeChange?: InterceptionModeCallback
```

Navigation��˫����ʾ״̬�������ʱ�����ûص���

**类型：** InterceptionModeCallback

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## willShow

```TypeScript
willShow?: InterceptionShowCallback
```

ҳ����תǰ�Ļص�����������ջ���ڵ�ǰ��ת����Ч�����ص�ҳ��ᱻ������

**类型：** InterceptionShowCallback

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

