# NavPathInfo

Provides the navigation page information.

**Since:** 10

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## constructor

```TypeScript
constructor(name: string, param: unknown, onPop?: import('../api/@ohos.base').Callback<PopInfo>, isEntry?: boolean)
```

Creates a **NavPathInfo** object.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| name | string | Yes | Name of the navigation destination page. The name matches the name in the following route tables:<br>1. Custom route table, which is passed via the [navDestination](arkts-arkui-navigation-comp-attribute.md#navdestination) method.<br>2. System route table, which is set by **name** in **routerMap**. For details, please refer to [Example 2: Using NavPathStack APIs](../../../reference/apis-arkui/arkui-ts/ts-basic-components-navigation.md#example-2-using-navpathstack-apis). |
| param | unknown | Yes | Detailed parameters for the custom **NavDestination** page. The **unknown** type can be replaced with a user-defined type. |
| onPop | import('../api/@ohos.base').Callback&lt;[PopInfo](arkts-arkui-popinfo-i.md)&gt; | No | Callback returned when [pop](arkts-arkui-navpathstack-c.md#pop), [popToName](arkts-arkui-navpathstack-c.md#poptoname), or [popToIndex](arkts-arkui-navpathstack-c.md#poptoindex) is called on the navigation destination page. It is triggered only when the **result** parameter is set in [pop](arkts-arkui-navpathstack-c.md#pop), [popToName](arkts-arkui-navpathstack-c.md#poptoname), or [popToIndex](arkts-arkui-navpathstack-c.md#poptoindex).<br>**Since:** 11 |
| isEntry | boolean | No | Whether the navigation destination page is the entry page.<br>**true**: yes; **false**: no<br>Default value: **false**<br>The value of this parameter is reviewed or reset under the following conditions:<br>1. A global return event is triggered on the current navigation destination page.<br> 2. The application is switched to the background.<br>**NOTE:** <br>The navigation destination page serving as an entry does not respond to the in-app global back events; instead, it directly triggers the global back event between applications.<br>**Since:** 12 |

## isEntry

```TypeScript
isEntry?: boolean
```

Whether the navigation destination page is the entry page.

**true**: yes; **false**: no

Default value: **false**

The value of this parameter is reviewed or reset under the following conditions:

1. A global back event is triggered on the current navigation destination page.
2. The application is switched to the background.

**NOTE:** 

The navigation destination page serving as an entry does not respond to the in-app global back events; instead, it directly triggers the global back event between applications.

**Type:** boolean

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## name

```TypeScript
name: string
```

Name of the navigation destination page. The name matches the name in the following route tables:

1. Custom route table, which is passed via the [navDestination](arkts-arkui-navigation-comp-attribute.md#navdestination) method.
2. System route table, which is set by **name** in **routerMap**. For details, please refer to [Example 2: Using NavPathStack APIs](../../../reference/apis-arkui/arkui-ts/ts-basic-components-navigation.md#example-2-using-navpathstack-apis).

**Type:** string

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## navDestinationId

```TypeScript
navDestinationId?: string
```

Unique ID of the navigation destination page. This ID is system-generated and globally unique. It can be obtained using the [getPathStack](arkts-arkui-navpathstack-c.md#getpathstack) API and should not be manually reassigned.

**Type:** string

**Since:** 19

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 19.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## onPop

```TypeScript
onPop?: import('../api/@ohos.base').Callback<PopInfo>
```

Callback returned when [pop](arkts-arkui-navpathstack-c.md#pop), [popToName](arkts-arkui-navpathstack-c.md#poptoname), or [popToIndex](arkts-arkui-navpathstack-c.md#poptoindex) is called on the navigation destination page. It is triggered only when the **result** parameter is set in [pop](arkts-arkui-navpathstack-c.md#pop), [popToName](arkts-arkui-navpathstack-c.md#poptoname), or [popToIndex](arkts-arkui-navpathstack-c.md#poptoindex).

**Type:** import('../api/@ohos.base').Callback&lt;[PopInfo](arkts-arkui-popinfo-i.md)&gt;

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## param

```TypeScript
param?: unknown
```

Detailed parameters for the custom **NavDestination** page. The **unknown** type can be replaced with a user- defined type.

**Type:** unknown

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
