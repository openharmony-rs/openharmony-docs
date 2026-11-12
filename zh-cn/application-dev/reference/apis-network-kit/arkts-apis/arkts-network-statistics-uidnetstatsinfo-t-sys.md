# UidNetStatsInfo（系统接口）

```TypeScript
export type UidNetStatsInfo = {
    [uid: number]: NetStatsInfo;
  }
```

获取的所有应用历史流量信息。

**类型：** {
    [uid: number]: NetStatsInfo;
  }

**起始版本：** 12

<!--Device-statistics-export type UidNetStatsInfo = {    [uid: int]: NetStatsInfo;  }--><!--Device-statistics-export type UidNetStatsInfo = {    [uid: int]: NetStatsInfo;  }-End-->

**系统能力：** SystemCapability.Communication.NetManager.Core

**系统接口：** 此接口为系统接口。
