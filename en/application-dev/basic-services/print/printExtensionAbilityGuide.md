# PrintExtensionAbility

<!--Kit: Basic Services Kit-->
<!--Subsystem: Print-->
<!--Owner: @Zouhaifeng1-->
<!--Designer: @baozewei-->
<!--Tester: @baozewei-->
<!--Adviser: @fang-jinxu-->
<!-- md-trans-meta sourceCommit=d9ce0c4979b7c4bdc149b31fa03dbef79e9b182c translatedAt=2026-11-06T12:05:40.572Z pushedAt=2026-11-09T12:29:58.666Z nl=1 -->

## Overview
**PrintExtensionAbility** is supported since API version 14. It extends the system printing functionality, allowing software to simulate printer behavior and implement printing interaction with upper-layer applications. With this extension ability, you can implement custom printing logic in special scenarios and flexibly develop differentiated functionalities under a unified framework, improving the adaptability and maintainability of solutions.

## Callback Description
| Name| Description|
| ------- | ------- |
| [onCreate(want: Want): void](../../reference/apis-basic-services-kit/js-apis-app-ability-PrintExtensionAbility.md#oncreate) | Initializes the Print Extension Ability |
| [onDestroy(): void](../../reference/apis-basic-services-kit/js-apis-app-ability-PrintExtensionAbility.md#ondestroy) | Ends the Print Extension Ability |
| [onStartDiscoverPrinter(): void](../../reference/apis-basic-services-kit/js-apis-app-ability-PrintExtensionAbility.md#onstartdiscoverprinter) | Starts printer discovery.|
| [onStopDiscoverPrinter(): void](../../reference/apis-basic-services-kit/js-apis-app-ability-PrintExtensionAbility.md#onstopdiscoverprinter) | Stops printer discovery.|
| [onConnectPrinter(printerId: number): void](../../reference/apis-basic-services-kit/js-apis-app-ability-PrintExtensionAbility.md#onconnectprinter) | Connects to a printer.|
| [onDisconnectPrinter(printerId: number): void](../../reference/apis-basic-services-kit/js-apis-app-ability-PrintExtensionAbility.md#ondisconnectprinter) | Disconnects from a printer.|

## How to Develop

### Implementing PrintExtensionAbility
1. Create a project directory.

    Under the **ets** directory (./entry/src/main/ets) corresponding to the entry Module of the project, create a directory and an ArkTS file. For example, create a directory named **PrintExtensionAbility**, and in the **PrintExtensionAbility** directory, create an ArkTS file named **MyPrintExtension.ets** to implement the Print Extension Ability APIs.

2. Open the **MyPrintExtension.ets** file and import the following module.
    <!-- @[print_extension_import](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/print/PrintExtensionAbilityGuide/entry/src/main/ets/PrintExtensionAbility/MyPrintExtension.ets) -->

    ``` TypeScript
    import { PrintExtensionAbility } from '@kit.BasicServicesKit';
    ```

3. Implement the APIs provided by **PrintExtensionAbility**.
    <!-- @[print_extension_impl](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/print/PrintExtensionAbilityGuide/entry/src/main/ets/PrintExtensionAbility/MyPrintExtension.ets) -->

    ``` TypeScript
    import { PrintExtensionAbility } from '@kit.BasicServicesKit';
    import { Want } from '@kit.AbilityKit';
    // Create a print extension ability class that inherits PrintExtensionAbility and implements the print extension functions.
    export default class MyPrintExtension extends PrintExtensionAbility {
        // Called when the system first connects to the print extension.
        onCreate(want: Want): void {
            console.info('onCreate');
            // Initialize the extension ability. You can register events here.
        }
        // Called when the print extension ends.
        onDestroy(): void {
            console.info('onDestroy');
            // Unregister events.
        }
        // Called when printer discovery starts.
        onStartDiscoverPrinter(): void {
            console.info('onStartDiscoverPrinter enter');
            // Implement the logic for discovering printers.
        }
        // Called when printer discovery stops.
        onStopDiscoverPrinter(): void {
            console.info('onStopDiscoverPrinter enter');
            // Implement the logic for stopping printer discovery.
        }
        // Called when connecting to a printer.
        onConnectPrinter(printerId: number): void {
            console.info('onConnectPrinter enter');
            // Implement the logic for connecting to a printer. You can connect to a specified printer by printer ID, query printer capabilities, and so on.
        }
        // Called when disconnecting from a printer.
        onDisconnectPrinter(printerId: number): void {
            console.info('onDisconnectPrinter enter');
            // Implement the logic for disconnecting from a printer. You can disconnect from a specified printer by printer ID.
        }
    }
    ```

4. In the **module.json5** configuration file under the entry Module directory of the project (./entry/src/main/module.json5), register the **PrintExtensionAbility** and set the following tags:
    * Set the **type** tag to **"print"**.
    * Set the **srcEntry** tag to the code path corresponding to the current ExtensionAbility component.

    Example:
    ```ts
    {
        "module": {
            "extensionAbilities": [
                {
                    "name": "MyPrintExtension",
                    "srcEntry": "./ets/PrintExtensionAbility/MyPrintExtension.ets",
                    "type": "print"
                }
            ]
        }
    }
    ```

### Verifying Functionality
Verify that the callback methods in the Print Extension Ability **PrintExtensionAbility** are implemented correctly and can be invoked successfully. After the HAP package is successfully pushed to the device, go to **Settings > Printers & scanners > Add printer and scanner** to launch the Print Extension Ability. After performing the corresponding action to trigger the callback, check the logs in the corresponding API implementation (determined by the business logic implemented by the developer) to determine whether the callback is successful.