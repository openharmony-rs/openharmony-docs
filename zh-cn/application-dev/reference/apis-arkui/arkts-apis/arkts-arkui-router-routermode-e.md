# RouterMode

路由跳转模式。

**起始版本：** 9

<!--Device-router-export enum RouterMode--><!--Device-router-export enum RouterMode-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## Standard

```TypeScript
Standard
```

多实例模式，也是默认情况下的跳转模式。

目标页面会被添加到页面栈顶，无论栈中是否存在相同url的页面。

**说明：**

不使用路由跳转模式时，则按照默认的多实例模式进行跳转。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-RouterMode-Standard--><!--Device-RouterMode-Standard-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## Single

```TypeScript
Single
```

单实例模式。

如果目标页面的url已经存在于页面栈中，则该url页面移动到栈顶。

如果目标页面的url在页面栈中不存在同url页面，则按照默认的多实例模式进行跳转。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-RouterMode-Single--><!--Device-RouterMode-Single-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

