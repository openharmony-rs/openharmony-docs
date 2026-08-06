# PageTransitionCallback

```TypeScript
export type PageTransitionCallback = (type: RouteType, progress: double) => void
```

页面转场事件回调。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-unnamed-export type PageTransitionCallback = (type: RouteType, progress: double) => void--><!--Device-unnamed-export type PageTransitionCallback = (type: RouteType, progress: double) => void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | transition route type  |
| progress | double | 是 | transition progess  |

