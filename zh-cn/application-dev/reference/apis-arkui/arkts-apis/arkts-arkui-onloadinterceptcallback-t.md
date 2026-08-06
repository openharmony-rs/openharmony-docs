# OnLoadInterceptCallback

```TypeScript
export type OnLoadInterceptCallback = (event: OnLoadInterceptEvent) => boolean
```

资源加载被拦截时触发该回调。

**起始版本：** 12

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为12。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-unnamed-export type OnLoadInterceptCallback = (event: OnLoadInterceptEvent) => boolean--><!--Device-unnamed-export type OnLoadInterceptCallback = (event: OnLoadInterceptEvent) => boolean-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| event | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 当资源加载被拦截时，加载拦截事件。  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 返回资源是否被拦截，true表示被拦截。 |

