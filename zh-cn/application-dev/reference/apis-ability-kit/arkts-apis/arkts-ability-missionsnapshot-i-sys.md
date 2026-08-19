# MissionSnapshot（系统接口）

一个任务的任务快照对象，可以通过 [missionManager.getMissionSnapShot](arkts-ability-missionmanager-getmissionsnapshot-f-sys.md) 获取。

**起始版本：** 23

<!--Device-unnamed-export interface MissionSnapshot--><!--Device-unnamed-export interface MissionSnapshot-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Mission

**系统接口：** 此接口为系统接口。

## ability

```TypeScript
ability: ElementName
```

表示该任务的组件信息。

**类型：** [ElementName](arkts-ability-elementname-i.md)

**起始版本：** 23

<!--Device-MissionSnapshot-ability: ElementName--><!--Device-MissionSnapshot-ability: ElementName-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Mission

**系统接口：** 此接口为系统接口。

## snapshot

```TypeScript
snapshot: image.PixelMap
```

表示任务快照。

**类型：** image.PixelMap

**起始版本：** 23

<!--Device-MissionSnapshot-snapshot: image.PixelMap--><!--Device-MissionSnapshot-snapshot: image.PixelMap-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Mission

**系统接口：** 此接口为系统接口。

