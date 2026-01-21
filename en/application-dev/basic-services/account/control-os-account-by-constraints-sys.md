# Applying Constraints for System Accounts (for System Applications Only)

<!--Kit: Basic Services Kit-->
<!--Subsystem: Account-->
<!--Owner: @steven-q-->
<!--Designer: @JiDong-CS1-->
<!--Tester: @zhaimengchao-->
<!--Adviser: @zengyawen-->

The **account** module provides a role-based access control mechanism. You can set constraints for system accounts to restrict their behaviors.

## Constraints

For details about the predefined account constraints, see [Constraints](../../reference/apis-basic-services-kit/js-apis-osAccount.md#constraints).

## Getting Started

1. Request the ohos.permission.MANAGE_LOCAL_ACCOUNTS permission. For details, see [Requesting Permissions for system_basic Applications](../../security/AccessToken/determine-application-mode.md#requesting-permissions-for-system_basic-applications).

2. Import the **osAccount** module.

   <!-- @[import_system_account_module](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Account/SystemAccount/entry/src/main/ets/pages/SystemAccount/UseConstraintManagementSystemAccount.ets) -->

``` TypeScript
import { osAccount, BusinessError } from '@kit.BasicServicesKit';
```


3. Obtain an **AccountManager** instance.

   <!-- @[obtain_account_single_instance_object](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Account/SystemAccount/entry/src/main/ets/pages/SystemAccount/UseConstraintManagementSystemAccount.ets) -->

``` TypeScript
let accountManager = osAccount.getAccountManager();
```


## Setting Constraints for a System Account

The user can set constraints to restrict the system account behaviors. For example, the user can enable mobile guardian for children to prevent the kids to use Wi-Fi or install applications.

**Procedure**

1. Specify the system account ID and the constraints.

   <!-- @[constraint_collections](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Account/SystemAccount/entry/src/main/ets/pages/SystemAccount/UseConstraintManagementSystemAccount.ets) -->

``` TypeScript
    let localId: number = 100;
    let constraint: string[] = [ 'constraint.wifi.set' ];
```


2. Use [setOsAccountConstraints](../../reference/apis-basic-services-kit/js-apis-osAccount-sys.md#setosaccountconstraints) to enable the constraints for the system account.

   <!-- @[system_account_constraint](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Account/SystemAccount/entry/src/main/ets/pages/SystemAccount/UseConstraintManagementSystemAccount.ets) -->

``` TypeScript
    try {
      accountManager.setOsAccountConstraints(localId, constraint, true);
      console.info('setOsAccountConstraints successfully');
	// ···
    } catch (e) {
      const err = e as BusinessError;
      console.error(`setOsAccountConstraints failed, error: code is ${err.code}, message is ${err.message}`);
	// ···
    }
```


## Checking Whether a Constraint Can be Enabled for a System Account

Before a constraint is enabled for a system account, the application needs to check whether the constraint can be enabled. You can use [isOsAccountConstraintEnabled](../../reference/apis-basic-services-kit/js-apis-osAccount-sys.md#isosaccountconstraintenabled11) to implement this operation.

**Procedure**

1. Set the system account ID and constraint.

   <!-- @[specify_the_system_account_id_and_constraint_name](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Account/SystemAccount/entry/src/main/ets/pages/SystemAccount/UseConstraintManagementSystemAccount.ets) -->

``` TypeScript
    let localId: number = 100;
    let constraint: string = 'constraint.wifi.set';
```


2. Use [isOsAccountConstraintEnabled](../../reference/apis-basic-services-kit/js-apis-osAccount-sys.md#isosaccountconstraintenabled11) to check whether the constraint can be enabled for the system account.

   <!-- @[check_whether_the_specified_constraint_is_enabled](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Account/SystemAccount/entry/src/main/ets/pages/SystemAccount/UseConstraintManagementSystemAccount.ets) -->

``` TypeScript
    accountManager.isOsAccountConstraintEnabled(localId, constraint).then((isEnabled: boolean) => {
      if (isEnabled) {
        // your business logic
		// ···
      }
    });
```
