# ChipGroup

以下接口在ArkTS1.1中已标记为废弃，并在ArkTS1.2中不再支持。

## ChipGroupItemOptions.suffixIcon

ArkTS1.1接口声明：[ChipGroupItemOptions.suffixIcon](../reference/apis-arkui/arkui-ts/ohos-arkui-advanced-ChipGroup.md#chipgroupitemoptions)

替代的ArkTS1.2接口声明：[ChipGroupItemOptions.suffixImageIcon](../reference/apis-arkui/arkui-ts/ohos-arkui-advanced-ChipGroup.md#chipgroupitemoptions)

ArkTS1.1

```ts
ChipGroup({
  items: [{
    label: { text: '选项1' },
    suffixIcon: { src: $r('sys.media.ohos_ic_public_cut') }
  }]
})
```

ArkTS1.2

```ts
ChipGroup({
  items: [{
    label: { text: '选项1' },
    suffixImageIcon: { src: $r('sys.media.ohos_ic_public_cut') }
  }]
})
```