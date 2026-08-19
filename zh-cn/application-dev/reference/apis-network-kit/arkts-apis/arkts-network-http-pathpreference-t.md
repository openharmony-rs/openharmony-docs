# PathPreference

```TypeScript
export type PathPreference = 'auto' | 'primaryCellular' | 'secondaryCellular'
```

HTTP请求指定特定网络的类型枚举。 > **说明：** > > 推荐在网络并发等场景下使用。 > 当指定的网络没有激活时，系统按照指定默认网络处理。

**起始版本：** 23

<!--Device-http-export type PathPreference = 'auto' | 'primaryCellular' | 'secondaryCellular'--><!--Device-http-export type PathPreference = 'auto' | 'primaryCellular' | 'secondaryCellular'-End-->

**系统能力：** SystemCapability.Communication.NetStack

| 类型 | 说明 |
| --- | --- |
| 'auto' | 表示HTTP请求指定默认的网络连接。 |
| 'primaryCellular' | 表示在蜂窝网络激活的场景下，HTTP请求指定默认的蜂窝网络连接。 |
| 'secondaryCellular' | 表示在双蜂窝网络激活的场景下，HTTP请求指定副卡的蜂窝网络连接。 |

