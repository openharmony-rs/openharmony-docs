# Navigator属性/事件

Navigator的属性。

**继承/实现关系：** NavigatorAttribute extends [CommonMethod<NavigatorAttribute>]

**起始版本：** 7

**废弃版本：** 13

**替代接口：** Navigation

<!--Device-unnamed-declare class NavigatorAttribute extends CommonMethod<NavigatorAttribute>--><!--Device-unnamed-declare class NavigatorAttribute extends CommonMethod<NavigatorAttribute>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## active

```TypeScript
active(value: boolean)
```

设置当前路由组件是否处于激活状态，处于激活状态时，会生效相应的路由操作。

**起始版本：** 7

**废弃版本：** 13

**替代接口：** Navigation

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-NavigatorAttribute-active(value: boolean): NavigatorAttribute--><!--Device-NavigatorAttribute-active(value: boolean): NavigatorAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | boolean | 是 | 路由组件是否处于激活状态。设置为true时，组件处于激活态。设置为false时，组件不处于激活态。 |

## params

```TypeScript
params(value: object)
```

设置跳转时传递到目标页面的数据。
> **说明：**

**起始版本：** 7

**废弃版本：** 13

**替代接口：** [param](arkts-arkui-navpathinfo-c.md#param)

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-NavigatorAttribute-params(value: object): NavigatorAttribute--><!--Device-NavigatorAttribute-params(value: object): NavigatorAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | object | 是 | 跳转时要同时传递到目标页面的数据，可在目标页面使用[router.getParams()](../arkts-apis/arkts-arkui-router-getparams-f.md#getparams)获得。 |

## target

```TypeScript
target(value: string)
```

设置跳转目标页面的路径。目标页面需加入main_pages.json文件中。

**起始版本：** 7

**废弃版本：** 13

**替代接口：** Navigation

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-NavigatorAttribute-target(value: string): NavigatorAttribute--><!--Device-NavigatorAttribute-target(value: string): NavigatorAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | string | 是 | 跳转目标页面的路径。 |

## type

```TypeScript
type(value: NavigationType)
```

设置路由跳转方式。
> **说明：**

**起始版本：** 7

**废弃版本：** 13

**替代接口：** Navigation

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-NavigatorAttribute-type(value: NavigationType): NavigatorAttribute--><!--Device-NavigatorAttribute-type(value: NavigationType): NavigatorAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [NavigationType](arkts-arkui-navigationtype-e.md) | 是 | 路由跳转方式。<br/>默认值：NavigationType.Push |

