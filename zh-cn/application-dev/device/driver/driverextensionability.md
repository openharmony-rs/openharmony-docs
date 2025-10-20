# 开发无UI界面基础驱动
<!--Kit: Driver Development Kit-->
<!--Subsystem: Driver-->
<!--Owner: @lixinsheng2-->
<!--Designer: @w00373942-->
<!--Tester: @dong-dongzhen-->
<!--Adviser: @w_Machine_cc-->

## 场景介绍

无UI界面的基础驱动，适用于不需要通过UI界面设置驱动能力的简单设备，例如鼠标，键盘等，保证设备的即插即用功能即可。开发者可以通过DriverExtensionAbility实现此类应用的开发。

## 基本概念

 - DriverExtensionAbility

    [DriverExtensionAbility](../../reference/apis-driverdevelopment-kit/js-apis-app-ability-driverExtensionAbility.md)是Driver类型的ExtensionAbility组件，提供驱动相关扩展框架能力。对于部分设备，支持插入外接的硬件模块来扩展设备能力， 此时可以以应用方式安装该硬件模块的驱动程序。[DriverExtensionAbility](../../reference/apis-driverdevelopment-kit/js-apis-app-ability-driverExtensionAbility.md)可以通过DriverExtensionManager被应用绑定，并根据应用的请求信息在后台处理相关事务。
    每个类型的ExtensionAbility都有自己的Context，DriverExtensionAbility通过[DriverExtensionContext](../../reference/apis-driverdevelopment-kit/js-apis-inner-application-driverExtensionContext.md)提供相关能力。

## 环境搭建

请参考[环境准备](environmental-preparation.md)完成开发前的准备工作。

## 开发步骤

开发者在实现一个驱动时，需要在DevEco Studio工程中手动新建一个DriverExtensionAbility，具体步骤如下：

1. 创建新工程，请参考[创建一个新的工程](https://developer.huawei.com/consumer/cn/doc/harmonyos-guides/ide-create-new-project)，创建一个OpenHarmony工程。（如果在[开发带UI界面基础驱动](externaldevice-guidelines.md)已经创建，则此处不需要创建。）

2. 在新创建的工程对应的ets目录下，右键选择“New &gt; Directory”，新建一个目录并命名为driverextability。

3. 在driverextability目录，右键选择“New &gt; ArkTS File”，新建一个文件并命名为DriverExtAbility.ets。

4. 在文件中导入相关Kit，并定义请求Code。

    <!-- @[driver_service_step4](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/DriverDevelopmentKit/DriverDemo/entry/src/main/ets/driverextability/DriverExtAbility.ets) -->

5. 打开DriverExtAbility.ets文件，导入[RPC通信模块](../../reference/apis-ipc-kit/js-apis-rpc.md)，重载onRemoteMessageRequest()方法，接收应用传递过来的消息，并将处理的结果返回给应用。REQUEST_CODE用于校验应用发送的服务请求码。

    <!-- @[driver_service_step5](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/DriverDevelopmentKit/DriverDemo/entry/src/main/ets/driverextability/DriverExtAbility.ets) -->

6. 在DriverExtAbility.ets文件中，增加导入[DriverExtensionAbility](../../reference/apis-driverdevelopment-kit/js-apis-app-ability-driverExtensionAbility.md)的依赖包，该包提供了onInit()、onRelease()、onConnect()和onDisconnect()生命周期回调，自定义类继承[DriverExtensionAbility](../../reference/apis-driverdevelopment-kit/js-apis-app-ability-driverExtensionAbility.md)并根据需要重写需要的生命周期回调。

    <!-- @[driver_service_step6](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/DriverDevelopmentKit/DriverDemo/entry/src/main/ets/driverextability/DriverExtAbility.ets) -->

7. 在工程Module对应的[module.json5配置文件](../../quick-start/module-configuration-file.md)中注册DriverExtensionAbility，type标签需要设置为“driver”，srcEntry标签表示当前ExtensionAbility组件所对应的代码路径。

    <!-- @[driver_service_step7](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/DriverDevelopmentKit/DriverDemo/entry/src/main/module.json5) -->

8. 完成客户端和驱动示例代码开发后，请参考[使用本地真机运行应用/元服务](https://developer.huawei.com/consumer/cn/doc/harmonyos-guides/ide-run-device)，将Hap导入设备中，并点击hap中的Hello，查看是否会转变为Hello world，即实现ipc通信功能。

## 扩展设备能力

扩展外设管理目前提供了HID DDK、USB DDK、USB Serical DDK和SCSI Peripheral DDK四种能力，用于扩展外设专项驱动的开发。具体使用方法，请参考：

* [开发适用HID协议的设备驱动](hid-ddk-guidelines.md)
* [开发适用USB协议的设备驱动](usb-ddk-guidelines.md)
* [开发适用串口协议的设备驱动](usb-serial-ddk-guidelines.md)
* [开发使用SCSI协议的设备驱动](scsi-peripheral-ddk-guidelines.md)

<!--RP1-->
## 应用签名

**注意：** 先配置权限，再自动签名。

应用需要配置签名文件才能在设备上运行，并且扩展外设管理客户端开发，需要配置扩展外设的权限：ohos.permission.ACCESS_EXTENSIONAL_DEVICE_DRIVER及ohos.permission.ACCESS_DDK_DRIVERS。
- ohos.permission.ACCESS_EXTENSIONAL_DEVICE_DRIVER（API version 10及以上版本，需要申请此权限。）

  在module.json5配置文件的requestPermissions标签中[声明权限](../../security/AccessToken/declare-permissions.md)后，即可获得授权。

- ohos.permission.ACCESS_DDK_DRIVERS（API version 18及以上版本，需要申请此权限。）

  1. 在module.json5配置文件的requestPermissions标签中[声明权限](../../security/AccessToken/declare-permissions.md)。
  2. HarmonyAppProvision配置文件中，修改acls字段，跨级别申请权限，可参考[申请使用受限权限](../../security/AccessToken/declare-permissions-in-acl.md)。
  3. 在HarmonyAppProvision配置文件（即SDK目录下的“Sdk/openharmony/_{Version} _/toolchains /lib/UnsgnedReleasedProfileTemplate.json”文件）中，配置当前客户需要连接的驱动服务端的bundleName，如果存在多个服务端，多个服务端的bundleName以逗号分隔。

      具体配置方法如下：

      在文件的根节点加上app-services-capabilities节点，并采用以下格式进行配置。
      ```json
      "app-services-capabilities": {
        "ohos.permission.ACCESS_DDK_DRIVERS": {"bundleNames": "bundleName0,bundleName1,bundleName2"}
      }
      ```

自动签名方法： 请参考[自动签名](https://developer.huawei.com/consumer/cn/doc/harmonyos-guides/ide-signing#section18815157237)。
<!--RP1End-->