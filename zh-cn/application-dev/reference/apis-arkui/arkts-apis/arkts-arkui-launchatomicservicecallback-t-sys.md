# LaunchAtomicServiceCallback（系统接口）

```TypeScript
export declare type LaunchAtomicServiceCallback = (appId: string, options?: AtomicServiceOptions) => void
```

拉起原子化服务触发的回调。

**起始版本：** 12

<!--Device-unnamed-export declare type LaunchAtomicServiceCallback = (appId: string, options?: AtomicServiceOptions) => void--><!--Device-unnamed-export declare type LaunchAtomicServiceCallback = (appId: string, options?: AtomicServiceOptions) => void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| appId | string | 是 | 原子化服务的appId。 |
| options | [AtomicServiceOptions](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-atomicserviceoptions-atomicserviceoptions-c.md) | 否 | 拉起原子化服务的参数。不填时使用默认参数拉起原子化服务。 |

