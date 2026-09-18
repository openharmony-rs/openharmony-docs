# AVCastPickerOptions

An option to make different picker usage

**Since:** 14

**System capability:** SystemCapability.Multimedia.AVSession.AVCast

## Modules to Import

```TypeScript
import { avSession } from '@kit.AVSessionKit';
```

## menuPosition

```TypeScript
menuPosition?: MenuPosition
```

Set the popup menu position if pickerstyple is set to STYLE_MENU.

**Type:** [MenuPosition](arkts-avsession-avsession-menuposition-i.md)

**Since:** 22

**System capability:** SystemCapability.Multimedia.AVSession.AVCast

## pickerStyle

```TypeScript
pickerStyle?: AVCastPickerStyle
```

Set the picker style.

**Type:** [AVCastPickerStyle](arkts-avsession-multimedia-avcastpickerparam-avcastpickerstyle-e.md)

**Since:** 22

**System capability:** SystemCapability.Multimedia.AVSession.AVCast

## sessionType

```TypeScript
sessionType?: AVSessionType
```

Indicates current session type to show different picker ui. If not set, default value is 'audio'.

**Type:** [AVSessionType](arkts-avsession-avsession-avsessiontype-t.md)

**Since:** 14

**Atomic service API:** This API can be used in atomic services since API version 14.

**System capability:** SystemCapability.Multimedia.AVSession.AVCast
