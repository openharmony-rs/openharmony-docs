# @ohos.app.ability.continueManager

continueManager提供了应用跨端迁移的管理能力，如获取应用跨端迁移过程中快速拉起目标应用的结果。跨端迁移是指当用户在一个设备上操作某个应用时，可以在另一个设备的同一个应用中快速切换，无缝衔接上一个设备的应用体验。

> 本模块接口仅可在Stage模型下使用。

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Mission

## 导入模块

```TypeScript
import { continueManager } from '@kit.AbilityKit';
```

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| [off](arkts-ability-continuemanager-off-f.md#offpreparecontinue) | 在应用快速拉起时，注销回调函数，不再获取快速拉起结果。使用callback异步回调。适用于跨设备应用迁移完成或取消迁移后的回调清理场景，如应用迁移成功后清理监听、用户取消迁移操作时释放资源等。 |
| [on](arkts-ability-continuemanager-on-f.md#onpreparecontinue) | 在应用快速拉起时，注册回调函数以获取快速拉起结果。使用callback异步回调。适用于跨设备应用迁移场景，如游戏进度从手机迁移到平板、视频播放跨端同步、文档编辑协作等需要保持应用状态连续的场景。 |

### 接口

| 名称 | 说明 |
| --- | --- |
| [ContinueResultInfo](arkts-ability-continuemanager-continueresultinfo-i.md) | 注册或注销回调函数返回的快速拉起结果，包含操作状态码和结果说明信息，用于应用获取跨端迁移快速拉起的执行结果。 |

### 枚举

| 名称 | 说明 |
| --- | --- |
| [ContinueStateCode](arkts-ability-continuemanager-continuestatecode-e.md) | 快速拉起的结果状态码的枚举值。模型约束：此接口仅可在Stage模型下使用。 |
