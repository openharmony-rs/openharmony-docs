# display

Provides methods for setting the display effect, including the font size, screen brightness, screen rotation, animation factor, and display color.

@namespace display

**Since:** 7

**System capability:** SystemCapability.Applications.Settings.Core

## Modules to Import

```TypeScript
import { settings } from '@kit.BasicServicesKit';
```

## Summary

### Constants

| Name | Description |
| --- | --- |
| [FONT_SCALE](arkts-basicservices-display-con.md#font_scale) | Indicates the scaling factor of fonts, which is a float number. |
| [SCREEN_BRIGHTNESS_STATUS](arkts-basicservices-display-con.md#screen_brightness_status) | Indicates the screen brightness. The value ranges from 0 to 255. |
| [AUTO_SCREEN_BRIGHTNESS](arkts-basicservices-display-con.md#auto_screen_brightness) | Specifies whether automatic screen brightness adjustment is enabled. |
| [AUTO_SCREEN_BRIGHTNESS_MODE](arkts-basicservices-display-con.md#auto_screen_brightness_mode) | Indicates the value of `AUTO_SCREEN_BRIGHTNESS` when automatic screen brightness adjustment is used. |
| [MANUAL_SCREEN_BRIGHTNESS_MODE](arkts-basicservices-display-con.md#manual_screen_brightness_mode) | Indicates the value of `AUTO_SCREEN_BRIGHTNESS` when manual screen brightness adjustment is used. |
| [SCREEN_OFF_TIMEOUT](arkts-basicservices-display-con.md#screen_off_timeout) | Indicates the duration that the device waits before going to sleep after a period of inactivity, in milliseconds. |
| [DEFAULT_SCREEN_ROTATION](arkts-basicservices-display-con.md#default_screen_rotation) | Indicates the screen rotation when no other policy is available. |
| [ANIMATOR_DURATION_SCALE](arkts-basicservices-display-con.md#animator_duration_scale) | Indicates the scaling factor for the animation duration. |
| [TRANSITION_ANIMATION_SCALE](arkts-basicservices-display-con.md#transition_animation_scale) | Indicates the scaling factor for transition animations. If the value is `0`, transition animations are disabled. |
| [WINDOW_ANIMATION_SCALE](arkts-basicservices-display-con.md#window_animation_scale) | Indicates the scaling factor for normal window animations. If the value is `0`, window animations are disabled. |
| [DISPLAY_INVERSION_STATUS](arkts-basicservices-display-con.md#display_inversion_status) | Specifies whether display color inversion is enabled. |
