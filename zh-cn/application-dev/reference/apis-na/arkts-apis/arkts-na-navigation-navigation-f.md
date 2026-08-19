# Navigation

## Navigation

```TypeScript
@ComponentBuilder
export declare function Navigation(
    pathInfos?: NavPathStack, 
    content_?: CustomBuilder
): NavigationAttribute
```

绑定导航控制器到Navigation组件，适用于使用[NavPathStack](arkts-na-navigation-navpathstack-c.md)配合 [navDestination](arkts-na-navigation-navigationattribute-i.md#navdestination)属性进行页面路由。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-unnamed-@ComponentBuilderexport declare function Navigation(    pathInfos?: NavPathStack,     content_?: CustomBuilder): NavigationAttribute--><!--Device-unnamed-@ComponentBuilderexport declare function Navigation(    pathInfos?: NavPathStack,     content_?: CustomBuilder): NavigationAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| pathInfos | [NavPathStack](arkts-na-navigation-navpathstack-c.md) | 否 | 导航控制器对象。 |
| content_ | CustomBuilder | 否 | 子组件。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [NavigationAttribute](arkts-na-navigation-navigationattribute-i.md) |  |


## Navigation

```TypeScript
@ComponentBuilder
export declare function Navigation(
   pathInfos?: NavPathStack, 
   homeDestination?: HomePathInfo,
   content_?: CustomBuilder
): NavigationAttribute
```

绑定导航控制器到Navigation组件，并设置自定义首页，适用于使用[NavPathStack](arkts-na-navigation-navpathstack-c.md)配合 [navDestination](arkts-na-navigation-navigationattribute-i.md#navdestination)属性进行页面路由。

**起始版本：** 24

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为24。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-unnamed-@ComponentBuilderexport declare function Navigation(   pathInfos?: NavPathStack,    homeDestination?: HomePathInfo,   content_?: CustomBuilder): NavigationAttribute--><!--Device-unnamed-@ComponentBuilderexport declare function Navigation(   pathInfos?: NavPathStack,    homeDestination?: HomePathInfo,   content_?: CustomBuilder): NavigationAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| pathInfos | [NavPathStack](arkts-na-navigation-navpathstack-c.md) | 否 | 导航控制器对象。 |
| homeDestination | [HomePathInfo](arkts-na-navigation-homepathinfo-i.md) | 否 | 自定义首页信息。 |
| content_ | CustomBuilder | 否 | 子组件。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [NavigationAttribute](arkts-na-navigation-navigationattribute-i.md) |  |


## Navigation

```TypeScript
@Builder
export declare function Navigation(
 style_: CustomBuilderT<NavigationAttribute>,
 content_?: CustomBuilder,
): NavigationAttribute
```

绑定导航控制器到Navigation组件，适用于使用[NavPathStack](arkts-na-navigation-navpathstack-c.md)配合 [navDestination](arkts-na-navigation-navigationattribute-i.md#navdestination)属性进行页面路由。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-unnamed-@Builderexport declare function Navigation( style_: CustomBuilderT<NavigationAttribute>, content_?: CustomBuilder,): NavigationAttribute--><!--Device-unnamed-@Builderexport declare function Navigation( style_: CustomBuilderT<NavigationAttribute>, content_?: CustomBuilder,): NavigationAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| style_ | CustomBuilderT&lt;[NavigationAttribute](arkts-na-navigation-navigationattribute-i.md)&gt; | 是 | 导航控制器对象。 |
| content_ | CustomBuilder | 否 | 子组件。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [NavigationAttribute](arkts-na-navigation-navigationattribute-i.md) | Returns the instance of the NavigationAttribute. |

