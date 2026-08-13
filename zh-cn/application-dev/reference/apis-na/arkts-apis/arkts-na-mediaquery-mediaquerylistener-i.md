# MediaQueryListener

媒体查询的句柄，并包含了申请句柄时的首次查询结果。媒体查询根据设置的条件语句， 比如'(width <= 600vp)'，比较系统信息，若首次查询时相关信息未初始化，matches返回false。 继承自[MediaQueryResult](arkts-na-mediaquery-mediaqueryresult-i.md#MediaQueryResult)。

**继承/实现关系：** MediaQueryListener extends [MediaQueryResult](arkts-na-mediaquery-mediaqueryresult-i.md#MediaQueryResult)

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-mediaquery-export interface MediaQueryListener--><!--Device-mediaquery-export interface MediaQueryListener-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## offChange

```TypeScript
offChange(callback?: Callback<MediaQueryResult>): void
```

通过句柄向对应的查询条件取消注册回调，当媒体属性发生变更时不再触发指定的回调。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-MediaQueryListener-offChange(callback?: Callback<MediaQueryResult>): void--><!--Device-MediaQueryListener-offChange(callback?: Callback<MediaQueryResult>): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;[MediaQueryResult](arkts-na-mediaquery-mediaqueryresult-i.md)&gt; | 否 |  |

## onChange

```TypeScript
onChange(callback: Callback<MediaQueryResult>): void
```

通过句柄向对应的查询条件注册回调，当媒体属性发生变更时会触发该回调。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-MediaQueryListener-onChange(callback: Callback<MediaQueryResult>): void--><!--Device-MediaQueryListener-onChange(callback: Callback<MediaQueryResult>): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;[MediaQueryResult](arkts-na-mediaquery-mediaqueryresult-i.md)&gt; | 是 |  |

