# @ohos.ai.intelligentVoice

@namespace intelligentVoice

**Since:** 10

**System capability:** SystemCapability.AI.IntelligentVoice.Core

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { intelligentVoice } from '@kit.BasicServicesKit';
```

## Summary

<!--Del-->
### Functions(System API)

| Name | Description |
| --- | --- |
| [createEnrollIntelligentVoiceEngine](arkts-basicservices-intelligentvoice-createenrollintelligentvoiceengine-f-sys.md) | Obtains an [EnrollIntelligentVoiceEngine](arkts-basicservices-intelligentvoice-enrollintelligentvoiceengine-i-sys.md) instance. This method uses an asynchronous callback to return the EnrollIntelligentVoiceEngine instance. |
| [createEnrollIntelligentVoiceEngine](arkts-basicservices-intelligentvoice-createenrollintelligentvoiceengine-f-sys.md) | Obtains an [EnrollIntelligentVoiceEngine](arkts-basicservices-intelligentvoice-enrollintelligentvoiceengine-i-sys.md) instance. This method uses a promise to return the EnrollIntelligentVoiceEngine instance. |
| [createWakeupIntelligentVoiceEngine](arkts-basicservices-intelligentvoice-createwakeupintelligentvoiceengine-f-sys.md) | Obtains an [WakeupIntelligentVoiceEngine](arkts-basicservices-intelligentvoice-wakeupintelligentvoiceengine-i-sys.md) instance. This method uses an asynchronous callback to return the WakeupIntelligentVoiceEngine instance. |
| [createWakeupIntelligentVoiceEngine](arkts-basicservices-intelligentvoice-createwakeupintelligentvoiceengine-f-sys.md) | Obtains an [WakeupIntelligentVoiceEngine](arkts-basicservices-intelligentvoice-wakeupintelligentvoiceengine-i-sys.md) instance. This method uses a promise to return the WakeupIntelligentVoiceEngine instance. |
| [getIntelligentVoiceManager](arkts-basicservices-intelligentvoice-getintelligentvoicemanager-f-sys.md) | Obtains an [IntelligentVoiceManager](arkts-basicservices-intelligentvoice-intelligentvoicemanager-i-sys.md) instance. |
| [getWakeupManager](arkts-basicservices-intelligentvoice-getwakeupmanager-f-sys.md) | Obtains an [WakeupManager](arkts-basicservices-intelligentvoice-wakeupmanager-i-sys.md) instance. |
<!--DelEnd-->

<!--Del-->
### Interfaces(System API)

| Name | Description |
| --- | --- |
| [EnrollCallbackInfo](arkts-basicservices-intelligentvoice-enrollcallbackinfo-i-sys.md) | Describes enroll callback information. @typedef EnrollCallbackInfo |
| [EnrollEngineConfig](arkts-basicservices-intelligentvoice-enrollengineconfig-i-sys.md) | Describes enroll engine config. @typedef EnrollEngineConfig |
| [EnrollIntelligentVoiceEngine](arkts-basicservices-intelligentvoice-enrollintelligentvoiceengine-i-sys.md) | Implements enroll intelligent voice engine. @typedef EnrollIntelligentVoiceEngine |
| [EnrollIntelligentVoiceEngineDescriptor](arkts-basicservices-intelligentvoice-enrollintelligentvoiceenginedescriptor-i-sys.md) | Describes enroll intelligent voice engine. @typedef EnrollIntelligentVoiceEngineDescriptor |
| [EvaluationResult](arkts-basicservices-intelligentvoice-evaluationresult-i-sys.md) | Describes evaluation result. @typedef EvaluationResult |
| [IntelligentVoiceManager](arkts-basicservices-intelligentvoice-intelligentvoicemanager-i-sys.md) | Implements intelligent voice management. @typedef IntelligentVoiceManager |
| [UploadFile](arkts-basicservices-intelligentvoice-uploadfile-i-sys.md) | Describes upload file information. @typedef UploadFile |
| [WakeupHapInfo](arkts-basicservices-intelligentvoice-wakeuphapinfo-i-sys.md) | Describes wakeup hap information. @typedef WakeupHapInfo |
| [WakeupIntelligentVoiceEngine](arkts-basicservices-intelligentvoice-wakeupintelligentvoiceengine-i-sys.md) | Implements wakeup intelligent voice engine. @typedef WakeupIntelligentVoiceEngine |
| [WakeupIntelligentVoiceEngineCallbackInfo](arkts-basicservices-intelligentvoice-wakeupintelligentvoiceenginecallbackinfo-i-sys.md) | Describes wakeup intelligent voice engine callback information. @typedef WakeupIntelligentVoiceEngineCallbackInfo |
| [WakeupIntelligentVoiceEngineDescriptor](arkts-basicservices-intelligentvoice-wakeupintelligentvoiceenginedescriptor-i-sys.md) | Describes wakeup intelligent voice engine. @typedef WakeupIntelligentVoiceEngineDescriptor |
| [WakeupManager](arkts-basicservices-intelligentvoice-wakeupmanager-i-sys.md) | Implements wakeup management. @typedef WakeupManager |
| [WakeupSourceFile](arkts-basicservices-intelligentvoice-wakeupsourcefile-i-sys.md) | Describes wakeup source file information. @typedef WakeupSourceFile |
<!--DelEnd-->

<!--Del-->
### Enums(System API)

| Name | Description |
| --- | --- |
| [CapturerChannel](arkts-basicservices-intelligentvoice-capturerchannel-e-sys.md) | Enumerates capturer channel. @enum {number} |
| [EnrollResult](arkts-basicservices-intelligentvoice-enrollresult-e-sys.md) | Enumerates enroll result. @enum {number} |
| [EvaluationResultCode](arkts-basicservices-intelligentvoice-evaluationresultcode-e-sys.md) | Enumerates evaluation result code. @enum {number} |
| [IntelligentVoiceEngineType](arkts-basicservices-intelligentvoice-intelligentvoiceenginetype-e-sys.md) | Enumerates intelligent voice engine type. @enum {number} |
| [IntelligentVoiceErrorCode](arkts-basicservices-intelligentvoice-intelligentvoiceerrorcode-e-sys.md) | Enumerates intelligent voice error code. @enum {number} |
| [SensibilityType](arkts-basicservices-intelligentvoice-sensibilitytype-e-sys.md) | Enumerates sensibility type. @enum {number} |
| [ServiceChangeType](arkts-basicservices-intelligentvoice-servicechangetype-e-sys.md) | Enumerates service change type. @enum {number} |
| [UploadFileType](arkts-basicservices-intelligentvoice-uploadfiletype-e-sys.md) | Enumerates upload file type. @enum {number} |
| [WakeupIntelligentVoiceEventType](arkts-basicservices-intelligentvoice-wakeupintelligentvoiceeventtype-e-sys.md) | Enumerates wakeup intelligent voice event type. @enum {number} |
<!--DelEnd-->
