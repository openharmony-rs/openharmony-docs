# MediaQueryListener

媒体查询的句柄，并包含了申请句柄时的首次查询结果。媒体查询根据设置的条件语句， 比如'(width <= 600vp)'，比较系统信息，若首次查询时相关信息未初始化，matches返回false。 继承自[MediaQueryResult]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_。

**继承/实现关系：** MediaQueryListener extends [MediaQueryResult](arkts-arkui-mediaquery-mediaqueryresult-i.md)

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-mediaquery-export interface MediaQueryListener extends MediaQueryResult--><!--Device-mediaquery-export interface MediaQueryListener extends MediaQueryResult-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## offChange

```TypeScript
offChange(callback?: Callback<MediaQueryResult>): void
```

通过句柄向对应的查询条件取消注册回调，当媒体属性发生变更时不再触发指定的回调。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-MediaQueryListener-offChange(callback?: Callback<MediaQueryResult>): void--><!--Device-MediaQueryListener-offChange(callback?: Callback<MediaQueryResult>): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;MediaQueryResult&gt; | 否 |  |

## onChange

```TypeScript
onChange(callback: Callback<MediaQueryResult>): void
```

通过句柄向对应的查询条件注册回调，当媒体属性发生变更时会触发该回调。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-MediaQueryListener-onChange(callback: Callback<MediaQueryResult>): void--><!--Device-MediaQueryListener-onChange(callback: Callback<MediaQueryResult>): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;MediaQueryResult&gt; | 是 |  |

