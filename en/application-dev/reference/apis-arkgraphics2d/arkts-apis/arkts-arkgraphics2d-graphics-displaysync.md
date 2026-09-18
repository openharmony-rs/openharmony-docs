# @ohos.graphics.displaySync(Variable Frame Rate)

The displaySync module allows your application to draw its custom UI content at a specified frame rate.

**Since:** 11

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Modules to Import

```TypeScript
import { displaySync } from '@kit.ArkGraphics2D';
```

## Summary

### Functions

| Name | Description |
| --- | --- |
| [create](arkts-arkgraphics2d-displaysync-create-f.md) | Creates a **DisplaySync** object, through which you can set the frame rate of the custom UI content. |

### Interfaces

| Name | Description |
| --- | --- |
| [DisplaySync](arkts-arkgraphics2d-displaysync-displaysync-i.md) | An object that implements the setting of the frame rate and callback. It provides APIs for you to set the frame rate, register a callback, and start/stop the callback. Before calling any of the following APIs, you must use [displaySync.create()](arkts-arkgraphics2d-displaysync-create-f.md) to create a **DisplaySync** instance. |
| [IntervalInfo](arkts-arkgraphics2d-displaysync-intervalinfo-i.md) | You can obtain the timestamp information from the event callback, including the timestamp when the current frame arrives and the timestamp when the next frame is expected to arrive. |
