# @ohos.userIAM.pinAuth (PIN认证管理)(系统接口)

<!--Kit: User Authentication Kit-->
<!--Subsystem: UserIAM-->
<!--Owner: @WALL_EYE-->
<!--Designer: @lichangting518-->
<!--Tester: @jane_lz-->
<!--Adviser: @zengyawen-->

**pinAuth**模块是OpenHarmony用户身份认证体系（UserIAM）的组成部分，专门用于管理PIN（密码）的安全策略。该模块提供了PIN有效期、PIN删除禁用状态、PIN复杂度校验策略等策略的配置与查询接口，供系统应用按照企业的安全要求定制锁屏密码策略。

该模块主要用于以下场景：
- 系统应用需要为指定用户设置PIN有效期，当PIN过期时提示用户重置密码。
- 系统应用需要禁止用户删除PIN，保证密码凭据始终存在。
- 系统应用需要设置PIN复杂度校验策略，约束用户创建或修改锁屏密码时必须满足复杂度要求。
- 设置界面需要查询当前已生效的PIN策略并回显。

> **说明：**
>
> - 本模块同时支持ArkTS-Dyn、ArkTS-Sta。
> - 本模块首批接口从API version 26.1.0开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。
>
> - 本模块为系统接口。

## 关键Class/Interface介绍

### 核心接口类型

- **[PinComplexityPolicy](#pincomplexitypolicy)**：PIN复杂度校验策略接口，包含复杂度校验正则表达式和策略描述。

### 核心函数类型

- **[pinAuth.setPinValidityPeriod](#pinauthsetpinvalidityperiod)**：设置指定用户的PIN有效期。
- **[pinAuth.getPinValidityPeriod](#pinauthgetpinvalidityperiod)**：查询指定用户的PIN有效期。
- **[pinAuth.setPinDeletionDisabledState](#pinauthsetpindeletiondisabledstate)**：设置指定用户的PIN删除禁用状态。
- **[pinAuth.getPinDeletionDisabledState](#pinauthgetpindeletiondisabledstate)**：查询指定用户的PIN删除禁用状态。
- **[pinAuth.setPinComplexityPolicy](#pinauthsetpincomplexitypolicy)**：设置指定用户的PIN复杂度校验策略。
- **[pinAuth.getPinComplexityPolicy](#pinauthgetpincomplexitypolicy)**：查询指定用户的PIN复杂度校验策略。

## API组合使用关系说明

使用pinAuth模块的典型流程如下：

```ts
// 以下为阐述调用逻辑的伪代码，仅提供步骤说明，不提供详细的可执行代码。
// 1. 设置PIN有效期（例如7天）。
pinAuth.setPinValidityPeriod(userId, 7 * 24 * 60 * 60 * 1000);

// 2. 设置PIN复杂度校验策略。
pinAuth.setPinComplexityPolicy(userId, {
  complexityReg: '^(?=.*[a-z])(?=.*[A-Z])(?=.*\\d)(?=.*[^\\w]).{8,}$',
  policyDescription: '密码长度至少8位，且需包含大写字母、小写字母、数字和特殊字符'
});

// 3. 禁止用户删除PIN。
pinAuth.setPinDeletionDisabledState(userId, true);

// 4. 查询当前生效的策略，供设置界面回显。
let validityPeriod = pinAuth.getPinValidityPeriod(userId);
let deletionDisabled = pinAuth.getPinDeletionDisabledState(userId);
let complexityPolicy = pinAuth.getPinComplexityPolicy(userId);
```

## 导入模块

```ts
import { pinAuth } from '@kit.UserAuthenticationKit';
```

## PinComplexityPolicy

PIN复杂度校验策略。用于定义用户创建或修改锁屏PIN时必须满足的复杂度规则，以及该规则的描述信息。

**需要权限：** ohos.permission.USE_USER_ACCESS_MANAGER

**系统能力：** SystemCapability.UserIAM.UserAuth.Core

**ArkTS-Dyn起始版本：** 26.1.0

**ArkTS-Sta起始版本：** 26.1.0

**系统接口：** 此接口为系统接口。

| 名称 | 类型 | 只读 | 可选 | 说明 |
| ---- | ---- | ---- | ---- | ---- |
| complexityReg | string | 否 | 否 | PIN复杂度校验正则表达式。策略设置成功后，用户创建或修改锁屏PIN时，输入的PIN必须匹配该正则表达式，否则校验不通过。 |
| policyDescription | string | 否 | 否 | PIN复杂度校验策略的描述信息。用于说明该复杂度规则的具体要求，便于向用户或管理员展示。 |

## pinAuth.setPinValidityPeriod

setPinValidityPeriod(userId: int, validityPeriod: long): void

设置PIN有效期。策略设置成功后，当PIN过期时，系统将弹出安全提示，要求用户重置PIN。

**需要权限：** ohos.permission.USE_USER_ACCESS_MANAGER

**系统能力：** SystemCapability.UserIAM.UserAuth.Core

**ArkTS-Dyn起始版本：** 26.1.0

**ArkTS-Sta起始版本：** 26.1.0

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| ------ | ---- | ---- | ---- |
| userId | ArkTS-Dyn: number<br>ArkTS-Sta: int | 是 | 用户ID。策略对指定用户生效。取值限定为整数。 |
| validityPeriod | ArkTS-Dyn: number<br>ArkTS-Sta: long | 是 | PIN有效期，单位为毫秒。取值必须大于等于0且小于2^50，当设置有效期为0时，表示不设置有效期。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[用户认证错误码](errorcode-useriam.md)。

| 错误码ID | 错误信息 |
| -------- | ------- |
| 201 | Permission verification failed. The application does not have the permission required to call the API. |
| 202 | Permission verification failed. A non-system application calls a system API. |
| 12500002 | General operation error. |
| 12500008 | The parameter is out of range. |

**示例：**

ArkTS-Dyn示例：

```ts
import { pinAuth } from '@kit.UserAuthenticationKit';
import { BusinessError } from '@kit.BasicServicesKit';

// 用户ID，策略对该用户生效。
let userId: number = 100;
// PIN有效期，单位为毫秒，此处设置为7天。
let validityPeriod: number = 7 * 24 * 60 * 60 * 1000;

try {
  pinAuth.setPinValidityPeriod(userId, validityPeriod);
  console.info('set pin validity period successfully.');
} catch (error) {
  const err: BusinessError = error as BusinessError;
  console.error(`Failed to set pin validity period. Code: ${err.code}, message: ${err.message}`);
}
```

ArkTS-Sta示例：

```ts
import { pinAuth } from '@kit.UserAuthenticationKit';
import { BusinessError } from '@ohos.base';

let userId: int = 100;
// PIN有效期，单位为毫秒，此处设置为7天。
let validityPeriod: long = 604800000;

try {
  pinAuth.setPinValidityPeriod(userId, validityPeriod);
  console.info('set pin validity period successfully.');
} catch (error) {
  const err: BusinessError = error as BusinessError;
  console.error(`Failed to set pin validity period. Code: ${err.code}, message: ${err.message}`);
}
```

## pinAuth.getPinValidityPeriod

getPinValidityPeriod(userId: int): long | undefined

查询PIN有效期。

**需要权限：** ohos.permission.USE_USER_ACCESS_MANAGER

**系统能力：** SystemCapability.UserIAM.UserAuth.Core

**ArkTS-Dyn起始版本：** 26.1.0

**ArkTS-Sta起始版本：** 26.1.0

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| ------ | ---- | ---- | ---- |
| userId | ArkTS-Dyn: number<br>ArkTS-Sta: int | 是 | 用户ID。查询该用户已设置的PIN有效期。取值限定为整数。 |

**返回值：**

| 类型 | 说明 |
| ---- | ---- |
| ArkTS-Dyn: number \| undefined<br>ArkTS-Sta: long \| undefined | PIN有效期，单位为毫秒。若未给指定用户设置PIN有效期或者设置PIN有效期为0时，则返回undefined。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[用户认证错误码](errorcode-useriam.md)。

| 错误码ID | 错误信息 |
| -------- | ------- |
| 201 | Permission verification failed. The application does not have the permission required to call the API. |
| 202 | Permission verification failed. A non-system application calls a system API. |
| 12500002 | General operation error. |
| 12500008 | The parameter is out of range. |

**示例：**

ArkTS-Dyn示例：

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

ArkTS-Sta示例：

```ts
import { pinAuth } from '@kit.UserAuthenticationKit';
import { BusinessError } from '@ohos.base';

let userId: int = 100;

try {
  let validityPeriod: long | undefined = pinAuth.getPinValidityPeriod(userId);
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

setPinDeletionDisabledState(userId: int, isDisabled: boolean): void

设置PIN删除功能的禁用状态。策略设置成功后，当该功能被禁用时，用户将无法删除PIN。

**需要权限：** ohos.permission.USE_USER_ACCESS_MANAGER

**系统能力：** SystemCapability.UserIAM.UserAuth.Core

**ArkTS-Dyn起始版本：** 26.1.0

**ArkTS-Sta起始版本：** 26.1.0

**系统接口：** 此接口为系统接口。

**模型约束：** 此接口仅可在Stage模型下使用。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| ------ | ---- | ---- | ---- |
| userId | ArkTS-Dyn: number<br>ArkTS-Sta: int | 是 | 用户ID。策略对指定用户生效。取值限定为整数。 |
| isDisabled | boolean | 是 | PIN删除功能是否被禁用。true表示禁用PIN删除功能，false表示允许用户删除PIN。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[用户认证错误码](errorcode-useriam.md)。

| 错误码ID | 错误信息 |
| -------- | ------- |
| 201 | Permission verification failed. The application does not have the permission required to call the API. |
| 202 | Permission verification failed. A non-system application calls a system API. |
| 12500002 | General operation error. |
| 12500008 | The parameter is out of range. |

**示例：**

ArkTS-Dyn示例：

```ts
import { pinAuth } from '@kit.UserAuthenticationKit';
import { BusinessError } from '@kit.BasicServicesKit';

let userId: number = 100;

try {
  // 禁止用户删除PIN。
  pinAuth.setPinDeletionDisabledState(userId, true);
  console.info('set pin deletion disabled state successfully.');
} catch (error) {
  const err: BusinessError = error as BusinessError;
  console.error(`Failed to set pin deletion disabled state. Code: ${err.code}, message: ${err.message}`);
}
```

ArkTS-Sta示例：

```ts
import { pinAuth } from '@kit.UserAuthenticationKit';
import { BusinessError } from '@ohos.base';

let userId: int = 100;

try {
  // 禁止用户删除PIN。
  pinAuth.setPinDeletionDisabledState(userId, true);
  console.info('set pin deletion disabled state successfully.');
} catch (error) {
  const err: BusinessError = error as BusinessError;
  console.error(`Failed to set pin deletion disabled state. Code: ${err.code}, message: ${err.message}`);
}
```

## pinAuth.getPinDeletionDisabledState

getPinDeletionDisabledState(userId: int): boolean | undefined

查询PIN删除功能的禁用状态。

**需要权限：** ohos.permission.USE_USER_ACCESS_MANAGER

**系统能力：** SystemCapability.UserIAM.UserAuth.Core

**ArkTS-Dyn起始版本：** 26.1.0

**ArkTS-Sta起始版本：** 26.1.0

**系统接口：** 此接口为系统接口。

**模型约束：** 此接口仅可在Stage模型下使用。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| ------ | ---- | ---- | ---- |
| userId | ArkTS-Dyn: number<br>ArkTS-Sta: int | 是 | 用户ID。查询该用户已设置的PIN删除禁用状态。取值限定为整数。 |

**返回值：**

| 类型 | 说明 |
| ---- | ---- |
| boolean \| undefined | PIN删除功能是否被禁用。true表示已禁用，false表示未禁用。若未给指定用户设置该状态，则返回undefined。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[用户认证错误码](errorcode-useriam.md)。

| 错误码ID | 错误信息 |
| -------- | ------- |
| 201 | Permission verification failed. The application does not have the permission required to call the API. |
| 202 | Permission verification failed. A non-system application calls a system API. |
| 12500002 | General operation error. |
| 12500008 | The parameter is out of range. |

**示例：**

ArkTS-Dyn示例：

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

ArkTS-Sta示例：

```ts
import { pinAuth } from '@kit.UserAuthenticationKit';
import { BusinessError } from '@ohos.base';

let userId: int = 100;

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

## pinAuth.setPinComplexityPolicy

setPinComplexityPolicy(userId: int, policy: PinComplexityPolicy): void

设置PIN复杂度校验策略及其描述。策略设置成功后，用户创建或修改锁屏PIN时，输入的PIN必须匹配策略中的复杂度正则表达式。

**需要权限：** ohos.permission.USE_USER_ACCESS_MANAGER

**系统能力：** SystemCapability.UserIAM.UserAuth.Core

**ArkTS-Dyn起始版本：** 26.1.0

**ArkTS-Sta起始版本：** 26.1.0

**系统接口：** 此接口为系统接口。

**模型约束：** 此接口仅可在Stage模型下使用。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| ------ | ---- | ---- | ---- |
| userId | ArkTS-Dyn: number<br>ArkTS-Sta: int | 是 | 用户ID。策略对指定用户生效。取值限定为整数。 |
| policy | [PinComplexityPolicy](#pincomplexitypolicy) | 是 | PIN复杂度校验策略及描述，包含复杂度校验正则表达式和策略描述信息。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[用户认证错误码](errorcode-useriam.md)。

| 错误码ID | 错误信息 |
| -------- | ------- |
| 201 | Permission verification failed. The application does not have the permission required to call the API. |
| 202 | Permission verification failed. A non-system application calls a system API. |
| 12500002 | General operation error. |
| 12500008 | The parameter is out of range. |

**示例：**

ArkTS-Dyn示例：

```ts
import { pinAuth } from '@kit.UserAuthenticationKit';
import { BusinessError } from '@kit.BasicServicesKit';

let userId: number = 100;
let policy: pinAuth.PinComplexityPolicy = {
  complexityReg: '^(?=.*[a-z])(?=.*[A-Z])(?=.*\\d)(?=.*[^\\w]).{8,}$',
  policyDescription: '密码长度至少8位，且需包含大写字母、小写字母、数字和特殊字符'
};

try {
  pinAuth.setPinComplexityPolicy(userId, policy);
  console.info('set pin complexity policy successfully.');
} catch (error) {
  const err: BusinessError = error as BusinessError;
  console.error(`Failed to set pin complexity policy. Code: ${err.code}, message: ${err.message}`);
}
```

ArkTS-Sta示例：

```ts
import { pinAuth } from '@kit.UserAuthenticationKit';
import { BusinessError } from '@ohos.base';

let userId: int = 100;
let policy: pinAuth.PinComplexityPolicy = {
  complexityReg: '^(?=.*[a-z])(?=.*[A-Z])(?=.*\\d)(?=.*[^\\w]).{8,}$',
  policyDescription: '密码长度至少8位，且需包含大写字母、小写字母、数字和特殊字符'
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

getPinComplexityPolicy(userId: int): PinComplexityPolicy | undefined

查询PIN复杂度校验策略及其描述。

**需要权限：** ohos.permission.USE_USER_ACCESS_MANAGER

**系统能力：** SystemCapability.UserIAM.UserAuth.Core

**ArkTS-Dyn起始版本：** 26.1.0

**ArkTS-Sta起始版本：** 26.1.0

**系统接口：** 此接口为系统接口。

**模型约束：** 此接口仅可在Stage模型下使用。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| ------ | ---- | ---- | ---- |
| userId | ArkTS-Dyn: number<br>ArkTS-Sta: int | 是 | 用户ID。查询该用户已设置的PIN复杂度校验策略。取值限定为整数。 |

**返回值：**

| 类型 | 说明 |
| ---- | ---- |
| [PinComplexityPolicy](#pincomplexitypolicy) \| undefined | PIN复杂度校验策略及描述。若未给指定用户设置复杂度策略，或者该用户的复杂度正则表达式和策略描述均为空，则返回undefined。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[用户认证错误码](errorcode-useriam.md)。

| 错误码ID | 错误信息 |
| -------- | ------- |
| 201 | Permission verification failed. The application does not have the permission required to call the API. |
| 202 | Permission verification failed. A non-system application calls a system API. |
| 12500002 | General operation error. |
| 12500008 | The parameter is out of range. |

**示例：**

ArkTS-Dyn示例：

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

ArkTS-Sta示例：

```ts
import { pinAuth } from '@kit.UserAuthenticationKit';
import { BusinessError } from '@ohos.base';

let userId: int = 100;

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
