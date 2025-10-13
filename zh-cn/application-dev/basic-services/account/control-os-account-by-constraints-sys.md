# 使用约束管控系统账号（仅对系统应用开放）

<!--Kit: Basic Services Kit-->
<!--Subsystem: Account-->
<!--Owner: @steven-q-->
<!--Designer: @JiDong-CS1-->
<!--Tester: @zhaimengchao-->
<!--Adviser: @zengyawen-->

账号管理模块提供了基于角色的访问控制机制，用户可以为系统账号设置约束，以限制目标账号的行为。

## 约束列表

预定义的账号约束条件，可以参考：[系统账号约束列表](../../reference/apis-basic-services-kit/js-apis-osAccount.md#系统账号约束列表)。

## 开发准备

1. 申请权限：ohos.permission.MANAGE_LOCAL_ACCOUNTS。申请流程请参考：[申请应用权限](../../security/AccessToken/determine-application-mode.md#system_basic等级应用申请权限的方式)。

2. 导入系统账号模块。

   ```ts
   import { osAccount, BusinessError } from '@kit.BasicServicesKit';
   ```
   <!-- [import_system_account_module](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Account/SystemAccount/entry/src/main/ets/pages/SystemAccount/UseConstraintManagementSystemAccount.ets) -->

3. 获取系统账号的单实例对象。

   ```ts
   let accountManager = osAccount.getAccountManager();
   ```
   <!-- [obtain_account_single_instance_object](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Account/SystemAccount/entry/src/main/ets/pages/SystemAccount/UseConstraintManagementSystemAccount.ets) -->

## 设置指定系统账号的约束列表

设备所有者可以给指定系统账号设置约束，以限制该账号的行为。例如在家长模式下，家长可以禁止儿童打开WIFI、安装应用等。

具体开发实例如下：

1. 指定系统账号标识和待使能的约束集合。

   ```ts
   let localId: number = 100;
   let constraint: string[] = [ 'constraint.wifi.set' ];
   ```
   <!-- [constraint_collections](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Account/SystemAccount/entry/src/main/ets/pages/SystemAccount/UseConstraintManagementSystemAccount.ets) -->

2. 调用[setOsAccountConstraints](../../reference/apis-basic-services-kit/js-apis-osAccount-sys.md#setosaccountconstraints)接口，使能系统账号100的约束。

   ```ts
   try {
     accountManager.setOsAccountConstraints(localId, constraint, true);
     console.info('setOsAccountConstraints successfully');
   } catch (e) {
     const err = e as BusinessError;
     console.error(`setOsAccountConstraints failed, error: code is ${err.code}, message is ${err.message}`);
   }
   ```
   <!-- [system_account_constraint](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Account/SystemAccount/entry/src/main/ets/pages/SystemAccount/UseConstraintManagementSystemAccount.ets) -->

## 判断目标系统账号的指定约束是否使能

业务应用需要判断目标系统账号的指定约束是否使能，以此来决策是否对目标系统账号的行为做管控。开发者可以使用[isOsAccountConstraintEnabled](../../reference/apis-basic-services-kit/js-apis-osAccount-sys.md#isosaccountconstraintenabled11)接口完成此操作。

具体开发实例如下：

1. 指定系统账号标识和约束名称。

   ```ts
   let localId: number = 100;
   let constraint: string = 'constraint.wifi.set';
   ```
   <!-- [specify_the_system_account_id_and_constraint_name](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Account/SystemAccount/entry/src/main/ets/pages/SystemAccount/UseConstraintManagementSystemAccount.ets) -->

2. 调用[isOsAccountConstraintEnabled](../../reference/apis-basic-services-kit/js-apis-osAccount-sys.md#isosaccountconstraintenabled11)接口，判断指定约束是否使能。

   ```ts
   accountManager.isOsAccountConstraintEnabled(localId, constraint).then((isEnabled: boolean) => {
     if (isEnabled) {
        // your business logic
     }
   });
   ```
   <!-- [check_whether_the_specified_constraint_is_enabled](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Account/SystemAccount/entry/src/main/ets/pages/SystemAccount/UseConstraintManagementSystemAccount.ets) -->
