# MediaQueryList

定义MediaQuery列表信息。

**起始版本：** 3

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
import { SystemMediaQuery, MediaQueryEvent, MediaQueryList } from '@kit.ArkUI';
```

## addListener

```TypeScript
addListener(callback: (event: MediaQueryEvent) => void): void
```

给MediaQueryList添加回调函数，回调函数应在onShow生命周期之前添加，即需要在onInit或onReady生命周期里添加。

**起始版本：** 3

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | (event: MediaQueryEvent) = & gt; void | 是 | 匹配条件发生变化时触发的回调。 |

**示例**

```TypeScript
import mediaquery, { MediaQueryEvent } from '@system.mediaquery';
let mMediaQueryList = mediaquery.matchMedia('(max-width: 466)');

function maxWidthMatch(e: MediaQueryEvent): void {
  if(e.matches){
    // do something
  }
}
mMediaQueryList.addListener(maxWidthMatch);
```

## onchange

```TypeScript
onchange?: (matches: boolean) => void
```

匹配结果发生变化时的执行函数。matches表示是否匹配媒体查询条件，true满足查询条件，false不满足查询条件。 该参数为只读。

**起始版本：** 3

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| matches | boolean | 是 |  |

## removeListener

```TypeScript
removeListener(callback: (event: MediaQueryEvent) => void): void
```

移除MediaQueryList中的回调函数。

**起始版本：** 3

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | (event: MediaQueryEvent) = & gt; void | 是 | 匹配条件发生变化时触发的回调。 |

**示例**

```TypeScript
import mediaquery, { MediaQueryEvent } from '@system.mediaquery';
let mMediaQueryList = mediaquery.matchMedia('(max-width: 466)');

function maxWidthMatch(e: MediaQueryEvent): void {
  if(e.matches){
    // do something
  }
}
mMediaQueryList.removeListener(maxWidthMatch);
```

## matches

```TypeScript
matches?: boolean
```

匹配结果。 true表示满足查询条件，false表示不满足查询条件。 该参数为只读。

**类型：** boolean

**起始版本：** 3

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## media

```TypeScript
media?: string
```

序列化媒体查询条件。 该参数为只读。

**类型：** string

**起始版本：** 3

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full
