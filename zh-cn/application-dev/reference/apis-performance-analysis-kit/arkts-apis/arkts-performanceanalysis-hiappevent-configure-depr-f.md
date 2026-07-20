# configure

<a id="configure"></a>
## configure

```TypeScript
function configure(config: ConfigOption): boolean
```

应用事件打点配置方法，可用于配置打点开关、文件目录存储限额大小等功能。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** configure

<!--Device-hiAppEvent-function configure(config: ConfigOption): boolean--><!--Device-hiAppEvent-function configure(config: ConfigOption): boolean-End-->

**系统能力：** SystemCapability.HiviewDFX.HiAppEvent

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| config | [ConfigOption](arkts-performanceanalysis-hiappevent-configoption-i.md) | 是 | 应用事件打点配置项对象。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 配置结果，true 表示配置成功，false 表示配置失败。 |

**示例：**

```TypeScript
// 配置应用事件打点功能开关
let config1: hiAppEvent.ConfigOption = {
  disable: true,
};
hiAppEvent.configure(config1);

// 配置事件文件目录存储限额大小
let config2: hiAppEvent.ConfigOption = {
  maxStorage: '100MB',
};
hiAppEvent.configure(config2);

```

