# Navigator

路由容器组件，提供路由跳转能力。

> **说明：**

## 子组件

可以包含子组件。

## Navigator

```TypeScript
Navigator(value?: { target: string; type?: NavigationType })
```

在路由跳转时调用。

**起始版本：** 7

**废弃版本：** 13

**替代接口：** <!--SUBSTITUTE_API-->NavPathInfo<!--/SUBSTITUTE_API-->

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-NavigatorInterface-(value?: { target: string; type?: NavigationType }): NavigatorAttribute--><!--Device-NavigatorInterface-(value?: { target: string; type?: NavigationType }): NavigatorAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数:**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | { target: string; type?: NavigationType } | 否 | 跳转页面的信息。<br/>target：指定跳转目标页面的路径。<br/>type：指定路由方式。<br/>默认值：NavigationType.Push |

## Navigator

```TypeScript
Navigator()
```

在使用Navigator时调用。

NavigationAttribute为Navigation组件的属性。

**起始版本：** 7

**废弃版本：** 13

**替代接口：** <!--SUBSTITUTE_API-->NavigationAttribute<!--/SUBSTITUTE_API-->

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-NavigatorInterface-(): NavigatorAttribute--><!--Device-NavigatorInterface-(): NavigatorAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 汇总

- [NavigationType](arkts-arkui-navigator-navigationtype-e.md)
