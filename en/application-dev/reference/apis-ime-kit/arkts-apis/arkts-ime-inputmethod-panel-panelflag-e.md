# PanelFlag

```TypeScript
export enum PanelFlag
```

Enumerates the input method panel state types. Defines the display form of a panel and determines whether the panel is in fixed, floating, or candidate state. <br> <br>  
> **NOTE:** <br>
> <br>
> This enumeration applies only to **SOFT_KEYBOARD** panels. Setting **PanelFlag** for a **STATUS_BAR** panel takes <br>
> no effect. <br>
> Suggestions for the **PanelFlag** parameter: <br> <br>- Selection principles: <br>- **FLAG_FIXED** (**0**) is preferred for default scenarios. It is the most commonly‑used panel state, with visibility automatically managed by the system and no extra processing required from you. <br>- Select **FLAG_FLOATING** (**1**) for flexible‑layout scenarios (such as landscape mode or multi‑window environments). Panel position can be adjusted via **Panel.moveTo()**. <br>- Select **FLAG_CANDIDATE** (**2**) when independent candidate word display is required. You are responsible for implementing visibility management logic. <br>- Default configuration: The default value is **FLAG_FIXED** (**0**). When **flag** is not set in **PanelInfo**, the panel is in the fixed state by default. <br>- Precautions: When **FLAG_CANDIDATE** is selected, you must implement the visibility management logic of the candidate word panel; otherwise, the panel will not be shown or hidden automatically. You are advised to show the panel when the user starts input and hide it after input ends or a candidate word is selected.

**Since:** 11

<!--Device-unnamed-export enum PanelFlag--><!--Device-unnamed-export enum PanelFlag-End-->

**System capability:** SystemCapability.MiscServices.InputMethodFramework

## FLAG_CANDIDATE

```TypeScript
FLAG_CANDIDATE
```

Candidate-word state panel type. <br> <br>‑ When the input panel is in candidate-word state, it serves as a window for displaying user input candidates. <br> <br>‑ The system does not actively control showing and hiding of the candidate‑word state panel. You need to control its visibility based on app scenarios.

**Since:** 11

<!--Device-PanelFlag-FLAG_CANDIDATE--><!--Device-PanelFlag-FLAG_CANDIDATE-End-->

**System capability:** SystemCapability.MiscServices.InputMethodFramework

## FLAG_FIXED

```TypeScript
FLAG_FIXED = 0
```

Fixed-state panel type.

**Since:** 11

<!--Device-PanelFlag-FLAG_FIXED = 0--><!--Device-PanelFlag-FLAG_FIXED = 0-End-->

**System capability:** SystemCapability.MiscServices.InputMethodFramework

## FLAG_FLOATING

```TypeScript
FLAG_FLOATING
```

Floating-state panel type.

**Since:** 11

<!--Device-PanelFlag-FLAG_FLOATING--><!--Device-PanelFlag-FLAG_FLOATING-End-->

**System capability:** SystemCapability.MiscServices.InputMethodFramework
