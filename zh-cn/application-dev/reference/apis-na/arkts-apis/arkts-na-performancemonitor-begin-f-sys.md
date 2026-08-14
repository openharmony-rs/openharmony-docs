# begin（系统接口）

## begin

```TypeScript
function begin(scene: string, startInputType: ActionType, note?: string): void
```

用于标记用户场景开始，用户场景开始时调用此接口。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-performanceMonitor-function begin(scene: string, startInputType: ActionType, note?: string): void--><!--Device-performanceMonitor-function begin(scene: string, startInputType: ActionType, note?: string): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| scene | string | 是 | 用户场景id。字符串长度无限制，建议控制在255个字符以内，格式推荐字母大写且用下划线连接，例如LAUNCHER_APP_LAUNCH_FROM_ICON。 |
| startInputType | ActionType | 是 | 用户场景触发模式。 |
| note | string | 否 | 用户场景备注信息。字符串长度无限制，建议控制在255个字符以内，可以空缺不填，填写后性能指标上报会携带备注信息，不填无影响。 |

