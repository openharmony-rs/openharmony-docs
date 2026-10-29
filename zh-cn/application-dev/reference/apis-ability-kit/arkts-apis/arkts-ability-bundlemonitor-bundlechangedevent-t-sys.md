# BundleChangedEvent（系统接口）

```TypeScript
type BundleChangedEvent = 'add' | 'update' | 'remove'
```

监听的事件类型。

取值类型为下表类型中的一个。

**起始版本：** 9

<!--Device-bundleMonitor-type BundleChangedEvent = 'add' | 'update' | 'remove'--><!--Device-bundleMonitor-type BundleChangedEvent = 'add' | 'update' | 'remove'-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

**系统接口：** 此接口为系统接口。

| 类型 | 说明 |
| --- | --- |
| 'add' | 监听应用安装事件，值固定为'add'字符串。 |
| 'update' | 监听应用更新事件，值固定为'update'字符串。 |
| 'remove' | 监听应用卸载事件，值固定为'remove'字符串。 |
