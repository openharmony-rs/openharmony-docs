# NavDestinationTransitionDelegate

```TypeScript
declare type NavDestinationTransitionDelegate =
    (operation: NavigationOperation, isEnter: boolean) => Array<NavDestinationTransition> | undefined
```

NavDestination�Զ���ת�������Ĵ���������

**起始版本：** 15

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| operation | NavigationOperation | 是 | ��ǰҳ��ת���Ĳ������͡� |
| isEnter | boolean | 是 | ��ǰҳ���Ƿ�Ϊ�볡ҳ�档<br/>true����ǰҳ�����볡ҳ�棻false����ǰҳ�治���볡ҳ�档 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Array&lt;NavDestinationTransition&gt; \| undefined | Array of custom animations for the **NavDestination** page.<br/>If **undefined** is returned, the default system animation is used. |

