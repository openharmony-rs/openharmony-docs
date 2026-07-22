# MediaQueryListener

媒体查询的句柄，并包含了申请句柄时的首次查询结果。媒体查询根据设置的条件语句，比如'(width <= 600vp)'，比较系统信息，若首次查询时相关信息未初始化，matches返回false。

继承自[MediaQueryResult](arkts-arkui-mediaquery-mediaqueryresult-i.md)。

**继承/实现关系：** MediaQueryListener extends [MediaQueryResult](arkts-arkui-mediaquery-mediaqueryresult-i.md)

**起始版本：** 7

<!--Device-mediaquery-interface MediaQueryListener extends MediaQueryResult--><!--Device-mediaquery-interface MediaQueryListener extends MediaQueryResult-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
import { mediaquery } from '@kit.ArkUI';
```

## off('change')

```TypeScript
off(type: 'change', callback?: Callback<MediaQueryResult>): void
```

通过句柄向对应的查询条件取消注册回调，当媒体属性发生变更时不再触发指定的回调。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本12开始，该接口支持在ArkTS卡片中使用。

<!--Device-MediaQueryListener-off(type: 'change', callback?: Callback<MediaQueryResult>): void--><!--Device-MediaQueryListener-off(type: 'change', callback?: Callback<MediaQueryResult>): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'change' | 是 | 必须填写字符串'change'。 |
| callback | [Callback](../arkts-components/arkts-arkui-callback-i.md)&lt;MediaQueryResult&gt; | 否 | 需要取消注册的回调，如果参数缺省则注销该句柄下所有的回调。 |

**示例：**

```TypeScript
import { mediaquery } from '@kit.ArkUI';

let listener: mediaquery.MediaQueryListener = mediaquery.matchMediaSync('(orientation: landscape)'); // 监听横屏事件
function onPortrait(mediaQueryResult:mediaquery.MediaQueryResult) {
  if (mediaQueryResult.matches) {
    // do something here
  } else {
    // do something here
  }
}
listener.on('change', onPortrait) // 注册回调
listener.off('change', onPortrait) // 注销回调

```

## on('change')

```TypeScript
on(type: 'change', callback: Callback<MediaQueryResult>): void
```

通过句柄向对应的查询条件注册回调，当媒体属性发生变更时会触发该回调。
> **说明：**  
>  
> 注册的回调中不允许进一步调用on或off。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本12开始，该接口支持在ArkTS卡片中使用。

<!--Device-MediaQueryListener-on(type: 'change', callback: Callback<MediaQueryResult>): void--><!--Device-MediaQueryListener-on(type: 'change', callback: Callback<MediaQueryResult>): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'change' | 是 | 必须填写字符串'change'。 |
| callback | [Callback](../arkts-components/arkts-arkui-callback-i.md)&lt;MediaQueryResult&gt; | 是 | 向媒体查询注册的回调。 |

**示例：**

详见[off('change')](#offchange)示例。

