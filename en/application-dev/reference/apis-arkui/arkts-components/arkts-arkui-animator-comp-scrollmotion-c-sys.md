# ScrollMotion (System API)

```TypeScript
declare class ScrollMotion
```

Rolling animation model: You can build rolling animation based on the initial position, initial speed, boundary position, and spring attributes.

**Since:** 7

**Deprecated since:** 22

<!--Device-unnamed-declare class ScrollMotion--><!--Device-unnamed-declare class ScrollMotion-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.

## constructor

```TypeScript
constructor(position: number, velocity: number, min: number, max: number, prop: SpringProp)
```

Constructor parameters

**Since:** 7

**Deprecated since:** 22

<!--Device-ScrollMotion-constructor(position: number, velocity: number, min: number, max: number, prop: SpringProp)--><!--Device-ScrollMotion-constructor(position: number, velocity: number, min: number, max: number, prop: SpringProp)-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| position | number | Yes |  |
| velocity | number | Yes |  |
| min | number | Yes |  |
| max | number | Yes |  |
| prop | [SpringProp](arkts-arkui-animator-comp-springprop-c-sys.md) | Yes |  |
