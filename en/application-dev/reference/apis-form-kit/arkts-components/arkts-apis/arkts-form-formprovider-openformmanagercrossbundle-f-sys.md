# openFormManagerCrossBundle (System API)

## Modules to Import

```TypeScript
import { formProvider } from '@kit.FormKit';
```

## openFormManagerCrossBundle

```TypeScript
function openFormManagerCrossBundle(want: Want): void
```

Open the view of forms belonging to the specified bundle. Client to communication with FormManagerService.

**Since:** 20

**Required permissions:** ohos.permission.PUBLISH_FORM_CROSS_BUNDLE

**System capability:** SystemCapability.Ability.Form

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| want | [Want](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-want-want-c.md) | Yes | The want of the form to open. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permissions denied. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | The application is not a system application. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. |
| [16500050](../errorcode-form.md#16500050-ipc-failure) | IPC connection error. |
