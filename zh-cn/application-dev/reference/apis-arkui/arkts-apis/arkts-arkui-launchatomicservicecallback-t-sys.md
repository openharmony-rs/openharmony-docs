# LaunchAtomicServiceCallback（系统接口）

```TypeScript
export declare type LaunchAtomicServiceCallback = (appId: string, options?: AtomicServiceOptions) => void
```

拉起原子化服务触发的回调。

**起始版本：** 12

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为12。

<!--Device-unnamed-export declare type LaunchAtomicServiceCallback = (appId: string, options?: AtomicServiceOptions) => void--><!--Device-unnamed-export declare type LaunchAtomicServiceCallback = (appId: string, options?: AtomicServiceOptions) => void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| appId | string | 是 | 原子化服务的appId。  |
| options | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 否 | 拉起原子化服务参数。  |

