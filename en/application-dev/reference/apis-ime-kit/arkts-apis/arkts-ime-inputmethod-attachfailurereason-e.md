# AttachFailureReason

```TypeScript
export enum AttachFailureReason
```

Enumerates the reasons for attachment failure.

**Since:** 22

<!--Device-inputMethod-export enum AttachFailureReason--><!--Device-inputMethod-export enum AttachFailureReason-End-->

**System capability:** SystemCapability.MiscServices.InputMethodFramework

## CALLER_NOT_FOCUSED

```TypeScript
CALLER_NOT_FOCUSED = 0
```

Indicates a failure caused because the caller is not the application that owns the focused window. <br> <br>Usage scenarios: When **attach** is called while the application window is not focused, this failure reason is returned. <br> <br>Note: Ensure that the application window is focused before calling attach.

**Since:** 22

<!--Device-AttachFailureReason-CALLER_NOT_FOCUSED = 0--><!--Device-AttachFailureReason-CALLER_NOT_FOCUSED = 0-End-->

**System capability:** SystemCapability.MiscServices.InputMethodFramework

## IME_ABNORMAL

```TypeScript
IME_ABNORMAL
```

Indicates a failure caused by an input method application exception. <br> <br>Usage scenarios: When the input method application process crashes or is not running normally, **attach** returns this failure reason.

**Since:** 22

<!--Device-AttachFailureReason-IME_ABNORMAL--><!--Device-AttachFailureReason-IME_ABNORMAL-End-->

**System capability:** SystemCapability.MiscServices.InputMethodFramework

## SERVICE_ABNORMAL

```TypeScript
SERVICE_ABNORMAL
```

Indicates a failure caused by an input method framework service exception. <br> <br>Usage scenarios: When the input method framework service process is abnormal, **attach** returns this failure reason.

**Since:** 22

<!--Device-AttachFailureReason-SERVICE_ABNORMAL--><!--Device-AttachFailureReason-SERVICE_ABNORMAL-End-->

**System capability:** SystemCapability.MiscServices.InputMethodFramework
