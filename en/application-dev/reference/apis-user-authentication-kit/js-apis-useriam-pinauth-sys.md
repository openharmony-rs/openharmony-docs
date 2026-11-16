# @ohos.userIAM.pinAuth (PIN Authentication Management) (System API)

<!--Kit: User Authentication Kit-->
<!--Subsystem: UserIAM-->
<!--Owner: @WALL_EYE-->
<!--Designer: @lichangting518-->
<!--Tester: @jane_lz-->
<!--Adviser: @zengyawen-->
<!-- md-trans-meta sourceCommit=c91ec0c72bb1741f2e139eed44d6f5f6bd33ae15 translatedAt=2026-11-12T11:37:02.106Z pushedAt=2026-11-12T12:02:31.907Z nl=1 -->

The **pinAuth** module is a component of the OpenHarmony user identity authentication system (UserIAM) and is dedicated to managing the security policies of PINs (passwords). This module provides APIs for configuring and querying policies such as the PIN validity period, the PIN deletion disabled state, the PIN historical check range, and the PIN complexity check policy, allowing system applications to customize lock screen password policies according to enterprise security requirements.

This module applies to the following scenarios:
- A system application needs to set the PIN validity period for a specified user and prompt the user to reset the password when the PIN expires.
- A system application needs to prohibit the user from deleting the PIN to ensure that the password credential always exists.
- A system application needs to set the PIN historical check range to restrict the user from repeating any of the most recent historical PINs when modifying the PIN.
- A system application needs to set the PIN complexity check policy to require that the user must meet the complexity requirements when creating or modifying the lock screen password.
- The settings screen needs to query the currently effective PIN policy and echo it.

**Since:** 26.1.0
> **NOTE**
>
> The APIs of this module are system APIs.

## Key Classes and APIs

### Key APIs

- **[PinComplexityPolicy](#pincomplexitypolicy)**: PIN complexity check policy API, which contains the complexity check regular expression and the policy description.

### Key Functions

- **[pinAuth.setPinValidityPeriod](#pinauthsetpinvalidityperiod)**: Sets the PIN validity period for a specified user.
- **[pinAuth.getPinValidityPeriod](#pinauthgetpinvalidityperiod)**: Queries the PIN validity period of a specified user.
- **[pinAuth.setPinDeletionDisabledState](#pinauthsetpindeletiondisabledstate)**: Sets the PIN deletion disabled state for a specified user.
- **[pinAuth.getPinDeletionDisabledState](#pinauthgetpindeletiondisabledstate)**: Queries the PIN deletion disabled state of a specified user.
- **[pinAuth.setPinHistoryCheckRange](#pinauthsetpinhistorycheckrange)**: Sets the PIN historical check range of the specified user.
- **[pinAuth.getPinHistoryCheckRange](#pinauthgetpinhistorycheckrange)**: Queries the PIN historical check range of the specified user.
- **[pinAuth.clearPinHistoryCheckRange](#pinauthclearpinhistorycheckrange)**: Clears the PIN historical check range policy of the specified user.
- **[pinAuth.setPinComplexityPolicy](#pinauthsetpincomplexitypolicy)**: Sets the PIN complexity check policy for a specified user.
- **[pinAuth.getPinComplexityPolicy](#pinauthgetpincomplexitypolicy)**: Queries the PIN complexity check policy of a specified user.

## APIs Used in Combination

The typical process of using the **pinAuth** module is as follows:

```ts
// The following is pseudocode for illustrating the call logic. It provides only step descriptions, not detailed executable code.
// 1. Set the PIN validity period (for example, 7 days).
pinAuth.setPinValidityPeriod(userId, 7 * 24 * 60 * 60 * 1000);

// 2. Set the PIN complexity check policy.
pinAuth.setPinComplexityPolicy(userId, {
  complexityReg: '^(?=.*[a-z])(?=.*[A-Z])(?=.*\\d)(?=.*[^\\w]).{8,}$',
  policyDescription: 'The password length must be at least 8 characters, and it must contain uppercase letters, lowercase letters, digits, and special characters'
});

// 3. Prohibit the user from deleting the PIN.
pinAuth.setPinDeletionDisabledState(userId, true);

// 4. Set the PIN historical check range (for example, the most recent 5 times).
pinAuth.setPinHistoryCheckRange(userId, 5);

// 5. Clear the PIN historical check range policy.
pinAuth.clearPinHistoryCheckRange(userId);

// 6. Query the currently effective policy to display it in the settings interface.
let validityPeriod = pinAuth.getPinValidityPeriod(userId);
let deletionDisabled = pinAuth.getPinDeletionDisabledState(userId);
let historyRange = pinAuth.getPinHistoryCheckRange(userId);
let complexityPolicy = pinAuth.getPinComplexityPolicy(userId);
```

## Modules to Import

```ts
import { pinAuth } from '@kit.UserAuthenticationKit';
```

## PinComplexityPolicy

Defines the PIN complexity check policy. It is used to define the complexity rules that must be met when a user creates or modifies the lock screen PIN, as well as the description of the rules.

**Since:** 26.1.0

**System capability**: SystemCapability.UserIAM.UserAuth.Core

**System API**: This is a system API.

**Model restriction**: This API can be used only in the stage model.

| Name | Type | Read-Only | Optional | Description |
| ---- | ---- | ---- | ---- | ---- |
| complexityReg | string | No | No | PIN complexity check regular expression. After the policy is set successfully, when a user creates or modifies the lock screen PIN, the input PIN must match this regular expression; otherwise, the check fails. |
| policyDescription | string | No | No | Description information of the PIN complexity check policy. It is used to describe the specific requirements of the complexity rules for display to users or administrators. |

## pinAuth.setPinValidityPeriod

setPinValidityPeriod(userId: number, validityPeriod: number): void

Sets the PIN validity period. After the policy is set successfully, when the PIN expires, the system displays a security prompt requiring the user to reset the PIN.

**Since:** 26.1.0

**Required permissions**: ohos.permission.USE_USER_ACCESS_MANAGER

**System capability**: SystemCapability.UserIAM.UserAuth.Core

**System API**: This is a system API.

**Model restriction**: This API can be used only in the stage model.

**Parameters**

| Name | Type | Mandatory | Description |
| ------ | ---- | ---- | ---- |
| userId | number | Yes | User ID. If the value is **0**, it takes effect for all users; otherwise, it takes effect for the specified user. The value must be an integer. |
| validityPeriod | number | Yes | PIN validity period. The unit is milliseconds. The valid value is an integer greater than or equal to 0 and less than 2 to the power of 50. When the validity period is set to **0**, it indicates that no validity period is set. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [User Authentication Error Codes](errorcode-useriam.md).

| ID | Error Message |
| -------- | ------- |
| 201 | Permission verification failed. The application does not have the permission required to call the API. |
| 202 | Permission verification failed. A non-system application calls a system API. |
| 12500002 | General operation error. |
| 12500008 | The parameter is out of range. |

**Example**

```ts
import { pinAuth } from '@kit.UserAuthenticationKit';
import { BusinessError } from '@kit.BasicServicesKit';

// User ID. The policy takes effect for this user.
let userId: number = 100;
// PIN validity period, in milliseconds. It is set to 7 days here.
let validityPeriod: number = 7 * 24 * 60 * 60 * 1000;

try {
  pinAuth.setPinValidityPeriod(userId, validityPeriod);
  console.info('set pin validity period successfully.');
} catch (error) {
  const err: BusinessError = error as BusinessError;
  console.error(`Failed to set pin validity period. Code: ${err.code}, message: ${err.message}`);
}
```

## pinAuth.getPinValidityPeriod

getPinValidityPeriod(userId: number): number | undefined

Queries the PIN validity period.

**Since:** 26.1.0

**Required permissions**: ohos.permission.USE_USER_ACCESS_MANAGER

**System capability**: SystemCapability.UserIAM.UserAuth.Core

**System API**: This is a system API.

**Model restriction**: This API can be used only in the stage model.

**Parameters**

| Name | Type | Mandatory | Description |
| ------ | ---- | ---- | ---- |
| userId | number | Yes | User ID. It is used to query the PIN validity period that the user has set. The value must be an integer. |

**Return value**

| Type | Description |
| ---- | ---- |
| number \| undefined | PIN validity period, in milliseconds. If no PIN validity period is set for the specified user or the PIN validity period is set to **0**, **undefined** is returned. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [User Authentication Error Codes](errorcode-useriam.md).

| ID | Error Message |
| -------- | ------- |
| 201 | Permission verification failed. The application does not have the permission required to call the API. |
| 202 | Permission verification failed. A non-system application calls a system API. |
| 12500002 | General operation error. |
| 12500008 | The parameter is out of range. |

**Example**

```ts
import { pinAuth } from '@kit.UserAuthenticationKit';
import { BusinessError } from '@kit.BasicServicesKit';

let userId: number = 100;

try {
  let validityPeriod: number | undefined = pinAuth.getPinValidityPeriod(userId);
  if (validityPeriod === undefined) {
    console.info('pin validity period is not set.');
  } else {
    console.info(`pin validity period is ${validityPeriod} ms.`);
  }
} catch (error) {
  const err: BusinessError = error as BusinessError;
  console.error(`Failed to get pin validity period. Code: ${err.code}, message: ${err.message}`);
}
```

## pinAuth.setPinDeletionDisabledState

setPinDeletionDisabledState(userId: number, isDisabled: boolean): void

Sets the disabled state of the PIN delete function. After the policy is set successfully, when the function is disabled, the user cannot delete the PIN.

**Since:** 26.1.0

**Required permissions**: ohos.permission.USE_USER_ACCESS_MANAGER

**System capability**: SystemCapability.UserIAM.UserAuth.Core

**System API**: This is a system API.

**Model restriction**: This API can be used only in the stage model.

**Parameters**

| Name | Type | Mandatory | Description |
| ------ | ---- | ---- | ---- |
| userId | number | Yes | User ID. If the value is **0**, it takes effect for all users; otherwise, it takes effect for the specified user. The value must be an integer. |
| isDisabled | boolean | Yes | Whether the PIN delete function is disabled. **true** indicates that the PIN delete function is disabled, and **false** indicates that the user is allowed to delete the PIN. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [User Authentication Error Codes](errorcode-useriam.md).

| ID | Error Message |
| -------- | ------- |
| 201 | Permission verification failed. The application does not have the permission required to call the API. |
| 202 | Permission verification failed. A non-system application calls a system API. |
| 12500002 | General operation error. |
| 12500008 | The parameter is out of range. |

**Example**

```ts
import { pinAuth } from '@kit.UserAuthenticationKit';
import { BusinessError } from '@kit.BasicServicesKit';

let userId: number = 100;

try {
  // Prohibit the user from deleting the PIN.
  pinAuth.setPinDeletionDisabledState(userId, true);
  console.info('set pin deletion disabled state successfully.');
} catch (error) {
  const err: BusinessError = error as BusinessError;
  console.error(`Failed to set pin deletion disabled state. Code: ${err.code}, message: ${err.message}`);
}
```

## pinAuth.getPinDeletionDisabledState

getPinDeletionDisabledState(userId: number): boolean | undefined

Queries the disabled state of the PIN delete function.

**Since:** 26.1.0

**Required permissions**: ohos.permission.USE_USER_ACCESS_MANAGER

**System capability**: SystemCapability.UserIAM.UserAuth.Core

**System API**: This is a system API.

**Model restriction**: This API can be used only in the stage model.

**Parameters**

| Name | Type | Mandatory | Description |
| ------ | ---- | ---- | ---- |
| userId | number | Yes | User ID. Queries the PIN deletion disabled state that the user has set. The value must be an integer. |

**Return value**

| Type | Description |
| ---- | ---- |
| boolean \| undefined | Whether the PIN delete function is disabled. true indicates that it is disabled, and false indicates that it is not disabled. If the state is not set for the specified user, undefined is returned. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [User Authentication Error Codes](errorcode-useriam.md).

| ID | Error Message |
| -------- | ------- |
| 201 | Permission verification failed. The application does not have the permission required to call the API. |
| 202 | Permission verification failed. A non-system application calls a system API. |
| 12500002 | General operation error. |
| 12500008 | The parameter is out of range. |

**Example**

```ts
import { pinAuth } from '@kit.UserAuthenticationKit';
import { BusinessError } from '@kit.BasicServicesKit';

let userId: number = 100;

try {
  let isDisabled: boolean | undefined = pinAuth.getPinDeletionDisabledState(userId);
  if (isDisabled === undefined) {
    console.info('pin deletion disabled state is not set.');
  } else {
    console.info(`pin deletion disabled state is ${isDisabled}.`);
  }
} catch (error) {
  const err: BusinessError = error as BusinessError;
  console.error(`Failed to get pin deletion disabled state. Code: ${err.code}, message: ${err.message}`);
}
```

## pinAuth.setPinHistoryCheckRange

setPinHistoryCheckRange(userId: number, historyRange: number): void

Sets the historical check range for PIN modification. After the policy is set successfully, the most recent PINs of the specified quantity cannot be reused when the user modifies the PIN.

**Since:** 26.1.0

**Required permissions**: ohos.permission.USE_USER_ACCESS_MANAGER

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.UserIAM.UserAuth.Core

**System API**: This is a system API.

**Parameters**

| Name | Type | Mandatory | Description |
| ------ | ---- | ---- | ---- |
| userId | number | Yes | User ID. The policy takes effect for the specified user. When the value is 0, the policy takes effect for all users. The value must be an integer. |
| historyRange | number | Yes | PIN historical check range, which indicates the number of the most recent historical PINs that cannot be reused when the PIN is modified. The value range is an integer from 1 to 5. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [User Authentication Error Codes](errorcode-useriam.md).

| ID | Error Message |
| -------- | ------- |
| 201 | Permission verification failed. The application does not have the permission required to call the API. |
| 202 | Permission verification failed. A non-system application calls a system API. |
| 12500002 | General operation error. |
| 12500008 | The parameter is out of range. |

**Example**

```ts
import { pinAuth } from '@kit.UserAuthenticationKit';
import { BusinessError } from '@kit.BasicServicesKit';

let userId: number = 100;
// PIN historical check range. The value 5 indicates that the user cannot reuse the most recent 5 historical PINs when modifying the PIN.
let historyRange: number = 5;

try {
  pinAuth.setPinHistoryCheckRange(userId, historyRange);
  console.info('set pin history check range successfully.');
} catch (error) {
  const err: BusinessError = error as BusinessError;
  console.error(`Failed to set pin history check range. Code: ${err.code}, message: ${err.message}`);
}
```

## pinAuth.getPinHistoryCheckRange

getPinHistoryCheckRange(userId: number): number | undefined

Queries the historical check range for PIN modification.

**Since:** 26.1.0

**Required permissions**: ohos.permission.USE_USER_ACCESS_MANAGER

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.UserIAM.UserAuth.Core

**System API**: This is a system API.

**Parameters**

| Name | Type | Mandatory | Description |
| ------ | ---- | ---- | ---- |
| userId | number | Yes | User ID. It is used to query the PIN historical check range that the user has set. The value must be an integer. |

**Return value**

| Type | Description |
| ---- | ---- |
| number \| undefined | PIN historical check range, which indicates the number of most recent historical PINs that cannot be reused when modifying the PIN. The value range is an integer from 1 to 5. If no range is configured for the specified user, **undefined** is returned. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [User Authentication Error Codes](errorcode-useriam.md).

| ID | Error Message |
| -------- | ------- |
| 201 | Permission verification failed. The application does not have the permission required to call the API. |
| 202 | Permission verification failed. A non-system application calls a system API. |
| 12500002 | General operation error. |
| 12500008 | The parameter is out of range. |

**Example**

```ts
import { pinAuth } from '@kit.UserAuthenticationKit';
import { BusinessError } from '@kit.BasicServicesKit';

let userId: number = 100;

try {
  let historyRange: number | undefined = pinAuth.getPinHistoryCheckRange(userId);
  if (historyRange === undefined) {
    console.info('pin history check range is not set.');
  } else {
    console.info(`pin history check range is ${historyRange}.`);
  }
} catch (error) {
  const err: BusinessError = error as BusinessError;
  console.error(`Failed to get pin history check range. Code: ${err.code}, message: ${err.message}`);
}
```

## pinAuth.clearPinHistoryCheckRange

clearPinHistoryCheckRange(userId: number): void

Clears the PIN historical check range policy. After the policy is cleared, the user can reuse any historical PIN when modifying the PIN.

**Since:** 26.1.0

**Required permissions**: ohos.permission.USE_USER_ACCESS_MANAGER

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.UserIAM.UserAuth.Core

**System API**: This is a system API.

**Parameters**

| Name | Type | Mandatory | Description |
| ------ | ---- | ---- | ---- |
| userId | number | Yes | User ID. The policy is cleared for the specified user. When the value is 0, the PIN historical check range policy is cleared for all users. The value must be an integer. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [User Authentication Error Codes](errorcode-useriam.md).

| ID | Error Message |
| -------- | ------- |
| 201 | Permission verification failed. The application does not have the permission required to call the API. |
| 202 | Permission verification failed. A non-system application calls a system API. |
| 12500002 | General operation error. |
| 12500008 | The parameter is out of range. |

**Example**

```ts
import { pinAuth } from '@kit.UserAuthenticationKit';
import { BusinessError } from '@kit.BasicServicesKit';

let userId: number = 100;

try {
  pinAuth.clearPinHistoryCheckRange(userId);
  console.info('clear pin history check range successfully.');
} catch (error) {
  const err: BusinessError = error as BusinessError;
  console.error(`Failed to clear pin history check range. Code: ${err.code}, message: ${err.message}`);
}
```

## pinAuth.setPinComplexityPolicy

setPinComplexityPolicy(userId: number, policy: PinComplexityPolicy): void

Sets the PIN complexity check policy and its description. After the policy is set successfully, when a user creates or modifies the lock screen PIN, the input PIN must match the complexity regular expression in the policy.

**Since:** 26.1.0

**Required permissions**: ohos.permission.USE_USER_ACCESS_MANAGER

**System capability**: SystemCapability.UserIAM.UserAuth.Core

**System API**: This is a system API.

**Model restriction**: This API can be used only in the stage model.

**Parameters**

| Name | Type | Mandatory | Description |
| ------ | ---- | ---- | ---- |
| userId | number | Yes | User ID. If the value is 0, it takes effect for all users; otherwise, it takes effect for the specified user. The value must be an integer. |
| policy | [PinComplexityPolicy](#pincomplexitypolicy) | Yes | PIN complexity check policy and description, which contains the complexity check regular expression and the policy description information. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [User Authentication Error Codes](errorcode-useriam.md).

| ID | Error Message |
| -------- | ------- |
| 201 | Permission verification failed. The application does not have the permission required to call the API. |
| 202 | Permission verification failed. A non-system application calls a system API. |
| 12500002 | General operation error. |
| 12500008 | The parameter is out of range. |

**Example**

```ts
import { pinAuth } from '@kit.UserAuthenticationKit';
import { BusinessError } from '@kit.BasicServicesKit';

let userId: number = 100;
let policy: pinAuth.PinComplexityPolicy = {
  complexityReg: '^(?=.*[a-z])(?=.*[A-Z])(?=.*\\d)(?=.*[^\\w]).{8,}$',
  policyDescription: 'The password length must be at least 8 characters, and it must contain uppercase letters, lowercase letters, digits, and special characters'
};

try {
  pinAuth.setPinComplexityPolicy(userId, policy);
  console.info('set pin complexity policy successfully.');
} catch (error) {
  const err: BusinessError = error as BusinessError;
  console.error(`Failed to set pin complexity policy. Code: ${err.code}, message: ${err.message}`);
}
```

## pinAuth.getPinComplexityPolicy

getPinComplexityPolicy(userId: number): PinComplexityPolicy | undefined

Queries the PIN complexity check policy and its description.

**Since:** 26.1.0

**Required permissions**: ohos.permission.USE_USER_ACCESS_MANAGER

**System capability**: SystemCapability.UserIAM.UserAuth.Core

**System API**: This is a system API.

**Model restriction**: This API can be used only in the stage model.

**Parameters**

| Name | Type | Mandatory | Description |
| ------ | ---- | ---- | ---- |
| userId | number | Yes | User ID. It is used to query the PIN complexity check policy that the user has set. The value must be an integer. |

**Return value**

| Type | Description |
| ---- | ---- |
| [PinComplexityPolicy](#pincomplexitypolicy) \| undefined | PIN complexity check policy and description. If no complexity policy is set for the specified user, or both the complexity regular expression and the policy description configured for the specified user are empty, **undefined** is returned. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [User Authentication Error Codes](errorcode-useriam.md).

| ID | Error Message |
| -------- | ------- |
| 201 | Permission verification failed. The application does not have the permission required to call the API. |
| 202 | Permission verification failed. A non-system application calls a system API. |
| 12500002 | General operation error. |
| 12500008 | The parameter is out of range. |

**Example**

```ts
import { pinAuth } from '@kit.UserAuthenticationKit';
import { BusinessError } from '@kit.BasicServicesKit';

let userId: number = 100;

try {
  let policy: pinAuth.PinComplexityPolicy | undefined = pinAuth.getPinComplexityPolicy(userId);
  if (policy === undefined) {
    console.info('pin complexity policy is not set.');
  } else {
    console.info(`pin complexity policy is ${policy.complexityReg}, description: ${policy.policyDescription}.`);
  }
} catch (error) {
  const err: BusinessError = error as BusinessError;
  console.error(`Failed to get pin complexity policy. Code: ${err.code}, message: ${err.message}`);
}
```
