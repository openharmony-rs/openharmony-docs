# isDesktopLyricSupported

## Modules to Import

```TypeScript
import { avSession } from '@kit.AVSessionKit';
```

## isDesktopLyricSupported

```TypeScript
function isDesktopLyricSupported(): Promise<boolean>
```

Whether desktop lyric feature is supported.

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.AVSession.Core

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;boolean&gt; | result returned to indicate desktop lyric is supported. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [6600101](../errorcode-avsession.md#6600101-session-service-exception) | Session service exception. |

**Examples**

```TypeScript
import { avSession } from '@kit.AVSessionKit';

avSession.isDesktopLyricSupported().then((isSupported: boolean) => {
  console.info(`Succeeded in checking desktop lyric supported: ${isSupported}`);
});
```
