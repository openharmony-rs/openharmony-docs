# 打印扩展能力

<!--Kit: Basic Services Kit-->
<!--Subsystem: Print-->
<!--Owner: @guoshengbang-->
<!--Designer: @gcw_4D6e0BBd-->
<!--Tester: @guoshengbang-->
<!--Adviser: @fang-jinxu-->

## 概述
打印扩展能力从API version 14开始支持。打印扩展能力是对系统打印功能的扩展，允许开发者以软件的方式模拟打印机行为，实现与上层应用的打印交互。通过该扩展能力，开发者可以实现特殊场景下的定制化打印逻辑，在统一框架下灵活开发差异化功能，提升解决方案的适应性与可维护性。

## 回调说明
| 回调名称 | 回调描述 |
| ------- | ------- |
| [onCreate(want: Want): void](../../reference/apis-basic-services-kit/js-apis-app-ability-PrintExtensionAbility.md#oncreate) | 初始化打印机能力 |
| [onDestroy(): void](../../reference/apis-basic-services-kit/js-apis-app-ability-PrintExtensionAbility.md#ondestroy) | 结束打印扩展 |
| [onStartDiscoverPrinter(): void](../../reference/apis-basic-services-kit/js-apis-app-ability-PrintExtensionAbility.md#onstartdiscoverprinter) | 开始发现打印机 |
| [onStopDiscoverPrinter(): void](../../reference/apis-basic-services-kit/js-apis-app-ability-PrintExtensionAbility.md#onstopdiscoverprinter) | 停止发现打印机 |
| [onConnectPrinter(printerId: number): void](../../reference/apis-basic-services-kit/js-apis-app-ability-PrintExtensionAbility.md#onconnectprinter) | 连接打印机 |
| [onDisconnectPrinter(printerId: number): void](../../reference/apis-basic-services-kit/js-apis-app-ability-PrintExtensionAbility.md#ondisconnectprinter) | 断开与打印机的连接 |

## 开发步骤

### 实现打印扩展能力
1. 新建工程目录

   在工程entry Module对应的ets目录 (./entry/src/main/ets)下，新建目录及ArkTs文件。例如新建一个目录并命名为PrintExtensionAbility，在PrintExtensionAbility目录下，新建一个ArkTs文件并命名为MyPrintExtension.ets，用以实现打印扩展能力接口。

2. 打开MyPrintExtension.ets文件，导入模块。
   ```ts
   import { PrintExtensionAbility } from '@kit.BasicServicesKit';
   ```

3. 实现PrintExtensionAbility提供的接口。
   ```ts
   import { PrintExtensionAbility } from '@kit.BasicServicesKit';
   import { Want } from '@kit.AbilityKit';
   
   // 创建打印扩展能力类，继承PrintExtensionAbility，并实现打印扩展功能。
   export default class MyPrintExtension extends PrintExtensionAbility {
       // 系统首次连接打印扩展时调用。
       onCreate(want: Want): void {
           console.info('onCreate');
           // 初始化扩展能力，可以在此注册事件。
       }
   
       // 结束打印扩展时调用。
       onDestroy(): void {
           console.info('onDestroy');
           // 注销事件。
       }
   
       // 开始发现打印机时调用。
       onStartDiscoverPrinter(): void {
           console.info('onStartDiscoverPrinter enter');
           // 实现发现打印机的逻辑。
       }
   
       // 停止发现打印机时调用。
       onStopDiscoverPrinter(): void {
           console.info('onStopDiscoverPrinter enter');
           // 实现停止发现打印机的逻辑。
       }
   
       // 连接某台打印机时调用。
       onConnectPrinter(printerId: number): void {
           console.info('onConnectPrinter enter');
           // 实现连接打印机逻辑。可以通过打印机ID连接指定的打印机、查询打印机能力等。
       }
   
       // 断开与某台打印机的连接时调用。
       onDisconnectPrinter(printerId: number): void {
           console.info('onDisconnectPrinter enter');
           // 实现断开打印机连接逻辑。可以通过打印机ID断开与指定打印机的连接。
       }
   }
   ```

4. 在工程entry Module目录下的module.json5配置文件中(./entry/src/main/module.json5)注册PrintExtensionAbility并设置如下标签：
   * type标签设置为"print"；
   * srcEntry标签设置为当前ExtensionAbility组件所对应的代码路径。
   示例如下：
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

### 功能验证
确认打印扩展能力PrintExtensionAbility中的回调方法实现是否正确、是否可以成功回调。在成功推送HAP包到设备后，可以在设置-打印机和扫描仪-添加打印机和扫描仪，拉起打印扩展能力，执行相应的动作触发回调时机后，通过查找对应接口实现中的日志(由开发者实现的业务逻辑决定)来判断是否成功回调。