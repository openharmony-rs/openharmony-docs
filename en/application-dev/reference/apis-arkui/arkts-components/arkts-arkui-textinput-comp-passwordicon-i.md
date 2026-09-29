# PasswordIcon

```TypeScript
interface PasswordIcon
```

PasswordIcon object.

**Since:** 10

<!--Device-unnamed-interface PasswordIcon--><!--Device-unnamed-interface PasswordIcon-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## offIconSrc

```TypeScript
offIconSrc?: string | Resource
```

Icon displayed when the password visibility cannot be toggled in password input mode. The system-provided password icon is used by default.

The string format can be used to load network images and local images.

Network images support URLs in HTTP or HTTPS format; local images support the application resource path format.

**Type:** string &#124; [Resource](../arkts-apis/arkts-arkui-resource-t.md)

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-PasswordIcon-offIconSrc?: string | Resource--><!--Device-PasswordIcon-offIconSrc?: string | Resource-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## onIconSrc

```TypeScript
onIconSrc?: string | Resource
```

Icon displayed when the password visibility can be toggled in password input mode. The system-provided password icon is used by default.

The string format can be used to load network images and local images.

Network images support URLs in HTTP or HTTPS format; local images support the application resource path format.

**Type:** string &#124; [Resource](../arkts-apis/arkts-arkui-resource-t.md)

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-PasswordIcon-onIconSrc?: string | Resource--><!--Device-PasswordIcon-onIconSrc?: string | Resource-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
