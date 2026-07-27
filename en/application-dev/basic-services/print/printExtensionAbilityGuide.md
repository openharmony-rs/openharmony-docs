# PrintExtensionAbility

<!--Kit: Basic Services Kit-->
<!--Subsystem: Print-->
<!--Owner: @guoshengbang-->
<!--Designer: @gcw_4D6e0BBd-->
<!--Tester: @guoshengbang-->
<!--Adviser: @fang-jinxu-->

## Overview
**PrintExtensionAbility** is supported since API version 14. It extends the system printing functionality, allowing software to simulate printer behavior and implement printing interaction with upper-layer applications. With this extension ability, you can implement custom printing logic in special scenarios and flexibly develop differentiated functionalities under a unified framework, improving the adaptability and maintainability of solutions.

## Callback Description
| Name| Description|
| ------- | ------- |
| [onCreate(want: Want): void](../../reference/apis-basic-services-kit/js-apis-app-ability-PrintExtensionAbility.md#oncreate) | Initializes the printer capability.|
| [onDestroy(): void](../../reference/apis-basic-services-kit/js-apis-app-ability-PrintExtensionAbility.md#ondestroy) | Destroys **PrintExtensionAbility**.|
| [onStartDiscoverPrinter(): void](../../reference/apis-basic-services-kit/js-apis-app-ability-PrintExtensionAbility.md#onstartdiscoverprinter) | Starts printer discovery.|
| [onStopDiscoverPrinter(): void](../../reference/apis-basic-services-kit/js-apis-app-ability-PrintExtensionAbility.md#onstopdiscoverprinter) | Stops printer discovery.|
| [onConnectPrinter(printerId: number): void](../../reference/apis-basic-services-kit/js-apis-app-ability-PrintExtensionAbility.md#onconnectprinter) | Connects to a printer.|
| [onDisconnectPrinter(printerId: number): void](../../reference/apis-basic-services-kit/js-apis-app-ability-PrintExtensionAbility.md#ondisconnectprinter) | Disconnects from a printer.|

## How to Develop

### Implementing PrintExtensionAbility
1. Create a project directory.

   In the .**/entry/src/main/ets** directory of the **entry** module, create a directory and an ArkTS file. For example, create a directory named **PrintExtensionAbility** and an ArkTS file named **MyPrintExtension.ets** in it to implement the print extension ability.

2. Open the **MyPrintExtension.ets** file and import the following module.
   ```ts
   import { PrintExtensionAbility } from '@kit.BasicServicesKit';
   ```

3. Implement the APIs provided by **PrintExtensionAbility**.
   ```ts
   import { PrintExtensionAbility } from '@kit.BasicServicesKit';
   import { Want } from '@kit.AbilityKit';
   
   // Create a class that extends PrintExtensionAbility and implements the print extension ability.
   export default class MyPrintExtension extends PrintExtensionAbility {
       // Called when the system connects to the print extension for the first time.
       onCreate(want: Want): void {
           console.info('onCreate');
           // Initialize the extension ability. You can register events using this API.
       }
   
       // Called when the print extension ability is destroyed.
       onDestroy(): void {
           console.info('onDestroy');
           // Unregister the event.
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
   
       // Called when a printer is connected.
       onConnectPrinter(printerId: number): void {
           console.info('onConnectPrinter enter');
           // Implement the logic for connecting to a printer. You can connect to a specified printer or query the printer capabilities based on the printer ID.
       }
   
       // Called when a printer is disconnected.
       onDisconnectPrinter(printerId: number): void {
           console.info('onDisconnectPrinter enter');
           // Implement the logic for disconnecting from a printer. You can disconnect from a specified printer based on the printer ID.
       }
   }
   ```

4. In the **module.json5** configuration file under the **./entry/src/main/** directory, register the **PrintExtensionAbility** and set the following tags:
   * Set **type** to **print**.
   * Set **srcEntry** to the code path of the **PrintExtensionAbility** component.
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
Check whether the callback in **PrintExtensionAbility** is correctly implemented and whether the callback can be successfully executed. After the HAP package is successfully pushed to the device, go to **Settings** > **Printers & scanners** > **Add printer/scanner** to start **PrintExtensionAbility**. After a callback is triggered by a specific action, you can check the logs in the corresponding API (determined by the implemented service logic) to see whether the callback is successfully executed.
