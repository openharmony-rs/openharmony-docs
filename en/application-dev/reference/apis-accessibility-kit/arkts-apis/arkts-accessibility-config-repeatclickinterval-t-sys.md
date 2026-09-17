# RepeatClickInterval (System API)

```TypeScript
type RepeatClickInterval = 'Shortest' | 'Short' | 'Medium' | 'Long' | 'Longest'
```

Ignore repeated clicks at different time intervals.

The configuration takes effect when the ignore repeated click feature is enabled ([ignoreRepeatClick](arkts-accessibility-config-con-sys.md#ignorerepeatclick) is set to **true**). When the ignore repeated click feature is disabled ([ignoreRepeatClick](arkts-accessibility-config-con-sys.md#ignorerepeatclick) is set to **false**), the configuration does not take effect.

**Since:** 11

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

**System API:** This is a system API.

| Type | Description |
| --- | --- |
| 'Shortest' | Shortest. |
| 'Short' | Short. |
| 'Medium' | Medium. |
| 'Long' | Long. |
| 'Longest' | Longest. |
