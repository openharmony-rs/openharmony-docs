# getIntelligentVoiceManager (System API)

## Modules to Import

```TypeScript
import { intelligentVoice } from '@kit.BasicServicesKit';
```

## getIntelligentVoiceManager

```TypeScript
function getIntelligentVoiceManager(): IntelligentVoiceManager
```

Obtains an [IntelligentVoiceManager](arkts-basicservices-intelligentvoice-intelligentvoicemanager-i-sys.md) instance.

**Since:** 10

**Required permissions:** ohos.permission.MANAGE_INTELLIGENT_VOICE

**System capability:** SystemCapability.AI.IntelligentVoice.Core

**System API:** This is a system API.

**Return value:**

| Type | Description |
| --- | --- |
| [IntelligentVoiceManager](arkts-basicservices-intelligentvoice-intelligentvoicemanager-i-sys.md) | this [IntelligentVoiceManager](arkts-basicservices-intelligentvoice-intelligentvoicemanager-i-sys.md) object. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Not system application. |
| [22700101](../errorcode-intelligentVoice.md#22700101-insufficient-memory) | No memory. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let intelligentVoiceManager: intelligentVoice.IntelligentVoiceManager | null = null;
try {
  intelligentVoiceManager = intelligentVoice.getIntelligentVoiceManager();
} catch (err) {
  let error = err as BusinessError;
  console.error(`Get IntelligentVoiceManager failed. Code:${error.code}, message:${error.message}`);
}
```
