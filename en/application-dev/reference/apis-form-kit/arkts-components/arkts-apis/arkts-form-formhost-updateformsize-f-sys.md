# updateFormSize (System API)

## Modules to Import

```TypeScript
import { formHost } from '@kit.FormKit';
```

## updateFormSize

```TypeScript
function updateFormSize(formId: string, newDimension: formInfo.FormDimension, newRect: formInfo.Rect): void
```

Updates the size of the widget.

**Since:** 20

**Required permissions:** ohos.permission.REQUIRE_FORM

**System capability:** SystemCapability.Ability.Form

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| formId | string | Yes | Widget ID. |
| newDimension | [formInfo.FormDimension](arkts-form-forminfo-formdimension-e.md) | Yes | Widget dimension. For example, **Dimension_1_2** indicates a 1 x 2 widget. |
| newRect | [formInfo.Rect](arkts-form-forminfo-rect-i.md) | Yes | Widget position information, including the X and Y coordinates of the widget's top-left corner, as well as its width and height. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permissions denied. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | caller is not system app. |
| [16501000](../errorcode-form.md#16501000-internal-function-error) | An internal functional error occurred. |
| [16501001](../errorcode-form.md#16501001-widget-id-not-exist) | The ID of the form to be operated does not exist. |
| [16501012](../errorcode-form.md#16501012-incorrect-widget-dimension) | The dimension parameter is incorrect |

**Examples**

```TypeScript
import { formHost, formInfo } from '@kit.FormKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let formId: string = '12400633174999288';
  let newDimension = formInfo.FormDimension.Dimension_1_2;
  let newRect: formInfo.Rect = {
    left: 1,
    top: 2,
    width: 100,
    height: 100
  };
  formHost.updateFormSize(formId, newDimension, newRect);
} catch (error) {
  console.error(`catch error, code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}`);
}
```
