# PanelFlag

```TypeScript
export enum PanelFlag
```

Enumerates the state types of the input method panel.<br> <br>

| Name | Value| Description |  
| ------------ | -- | ------------------ |  
| [FLG_FIXED](arkts-ime-inputmethodengine-panelflag-e.md) | 0 | Fixed state type.|
| [FLG_FLOATING](arkts-ime-inputmethodengine-panelflag-e.md) | 1 | Floating state type.|
| FLAG_CANDIDATE&lt;sup&gt;15+&lt;/sup&gt; | 2 | Candidate state type.|

**Since:** 10

**System capability:** SystemCapability.MiscServices.InputMethodFramework

## FLG_FIXED

```TypeScript
FLG_FIXED = 0
```

Fixed style. <br> <br><p>It's provided for the panel with type of SOFT_KEYBOARD. When the flag is set, the soft keyboard is fixed at the bottom of the screen.</p>

**Since:** 10

**System capability:** SystemCapability.MiscServices.InputMethodFramework

## FLG_FLOATING

```TypeScript
FLG_FLOATING
```

Floating style. <br> <br><p>It's provided for the panel with type of SOFT_KEYBOARD. When the flag is set, the soft keyboard is floating.</p>

**Since:** 10

**System capability:** SystemCapability.MiscServices.InputMethodFramework

## FLAG_CANDIDATE

```TypeScript
FLAG_CANDIDATE
```

Candidate style. <br> <br><p>It's provided for the panel with type of SOFT_KEYBOARD. When the flag is set, the soft keyboard is a candidate window which will show the possible characters when user types a input code. Panel with candidate style will not be automatically shown or hidden by input method service. Input method application developers are supposed to control the panel status on their own.</p>

**Since:** 15

**System capability:** SystemCapability.MiscServices.InputMethodFramework
