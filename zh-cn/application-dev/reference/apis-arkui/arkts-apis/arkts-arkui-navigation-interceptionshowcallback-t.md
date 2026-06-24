# InterceptionShowCallback

```TypeScript
declare type InterceptionShowCallback = (from: NavDestinationContext|NavBar, to: NavDestinationContext|NavBar, operation: NavigationOperation, isAnimated: boolean) => void
```

Navigationҳ����תǰ��ҳ����ת������ػص���

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| from | NavDestinationContext \| NavBar | 是 | ҳ����ת֮ǰ��ջ��ҳ����Ϣ������ֵΪnavBar�����ʾ��תǰ��ҳ��ΪNavigation��ҳ�� |
| to | NavDestinationContext \| NavBar | 是 | ҳ����ת֮ǰ��ջ��ҳ����Ϣ������ֵΪnavBar�����ʾ��תǰ��ҳ��ΪNavigation��ҳ�� |
| operation | NavigationOperation | 是 | ��ǰҳ����ת���͡� |
| isAnimated | boolean | 是 | ҳ����ת�Ƿ��ж�����<br/>true��ҳ����ת�ж�����<br/>false��ҳ����תû�ж����� |

