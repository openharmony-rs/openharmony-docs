# 实现一个输入法应用

[InputMethodExtensionAbility](../reference/apis-ime-kit/js-apis-inputmethod-extension-ability.md)提供了onCreate()和onDestroy()生命周期回调，根据需要重写对应的回调方法。InputMethodExtensionAbility的生命周期如下：

- **onCreate()**

  服务被首次创建时触发该回调，开发者可以在此进行一些初始化的操作，例如注册公共事件监听等。

  > **说明：**
  >
  > 如果服务已创建，再次启动该InputMethodExtensionAbility不会触发onCreate()回调。

- **onDestroy()**

  当不再使用服务且准备将该实例销毁时，触发该回调。开发者可以在该回调中清理资源，如注销监听等。


## 开发步骤 

<!--RP1-->
开发者在实现一个输入法应用时，需要在DevEco Studio工程中新建一个InputMethodExtensionAbility，具体步骤如下：

1. 在工程Module对应的ets目录下，右键选择“New > Directory”，新建一个目录，并命名为InputMethodExtensionAbility。

2. 在InputMethodExtensionAbility目录下，右键选择“New > File”，新建四个文件，分别为KeyboardController.ts、InputMethodService.ts、Index.ets以及KeyboardKeyData.ts。目录如下：

``` 
/src/main/
├── ets/InputMethodExtensionAbility
│       └──model/KeyboardController.ts			# 显示键盘
│       └──InputMethodService.ts				# 自定义类继承InputMethodExtensionAbility并加上需要的生命周期回调
│       └──pages
│         └── Index.ets						# 绘制键盘，添加输入删除功能
│         └── KeyboardKeyData.ts			    # 键盘属性定义
├── resources/base/profile/main_pages.json  
```
<!--RP1End-->

## 文件介绍

1. InputMethodService.ts文件。

   在InputMethodService.ts文件中，增加导入InputMethodExtensionAbility的依赖包，自定义类继承InputMethodExtensionAbility并加上需要的生命周期回调。

   ```ts
   import { Want } from '@kit.AbilityKit';
   import keyboardController from './model/KeyboardController';
   import { InputMethodExtensionAbility } from '@kit.IMEKit';
   
   export default class InputDemoService extends InputMethodExtensionAbility {
   
     onCreate(want: Want): void {
       keyboardController.onCreate(this.context); // 初始化窗口并注册对输入法框架的事件监听
     }
   
     onDestroy(): void {
       console.log("onDestroy.");
       keyboardController.onDestroy(); // 销毁窗口并去注册事件监听
     }
   }
   ```

<!--RP2-->
2. KeyboardController.ts文件。

   ```ts
   import { display } from '@kit.ArkUI';
   import { inputMethodEngine, InputMethodExtensionContext } from '@kit.IMEKit';
   
   // 调用输入法框架的getInputMethodAbility方法获取实例，并由此实例调用输入法框架功能接口
   const inputMethodAbility: inputMethodEngine.InputMethodAbility = inputMethodEngine.getInputMethodAbility();
   
   export class KeyboardController {
     private mContext: InputMethodExtensionContext | undefined = undefined; // 保存InputMethodExtensionAbility中的context属性
     private panel: inputMethodEngine.Panel | undefined = undefined; 
     private textInputClient: inputMethodEngine.InputClient | undefined = undefined; 
     private keyboardController: inputMethodEngine.KeyboardController | undefined = undefined;
   
     constructor() {
     }
   
     public onCreate(context: InputMethodExtensionContext): void
     {
       this.mContext = context;
       this.initWindow(); // 初始化窗口
       this.registerListener(); // 注册对输入法框架的事件监听
     }
   
     public onDestroy(): void // 应用生命周期销毁
     {
       this.unRegisterListener(); // 去注册事件监听
       if(this.panel) { // 销毁窗口
         inputMethodAbility.destroyPanel(this.panel);
       }
       if(this.mContext) {
         this.mContext.destroy();
       }
     }
   
     public insertText(text: string): void {
       if(this.textInputClient) {
         this.textInputClient.insertText(text);
       }
     }
   
     public deleteForward(length: number): void {
       if(this.textInputClient) {
         this.textInputClient.deleteForward(length);
       }
     }
   
     private initWindow(): void // 初始化窗口
     {
       if(this.mContext === undefined) {
         return;
       }
       let dis = display.getDefaultDisplaySync();
       let dWidth = dis.width;
       let dHeight = dis.height;
       let keyHeightRate = 0.47;
       let keyHeight = dHeight * keyHeightRate;
       let nonBarPosition = dHeight - keyHeight;
       let panelInfo: inputMethodEngine.PanelInfo = {
         type: inputMethodEngine.PanelType.SOFT_KEYBOARD,
         flag: inputMethodEngine.PanelFlag.FLG_FIXED
       };
       inputMethodAbility.createPanel(this.mContext, panelInfo).then(async (inputPanel: inputMethodEngine.Panel) => {
         this.panel = inputPanel;
         if(this.panel) {
           await this.panel.resize(dWidth, keyHeight);
           await this.panel.moveTo(0, nonBarPosition);
           await this.panel.setUiContent('InputMethodExtensionAbility/pages/Index');
         }
       });
     }
   
     private registerListener(): void
     {
       this.registerInputListener(); // 注册对输入法框架服务的监听
       // 注册隐藏键盘事件监听等
     }
   
     private registerInputListener(): void { // 注册对输入法框架服务的开启及停止事件监听
       inputMethodAbility.on('inputStart', (kbController, textInputClient) => {
         this.textInputClient = textInputClient; // 此为输入法客户端实例，由此调用输入法框架提供给输入法应用的功能接口
         this.keyboardController = kbController;
       })
       inputMethodAbility.on('inputStop', () => {
         this.onDestroy(); // 销毁KeyboardController
       });
     }
   
     private unRegisterListener(): void
     {
       inputMethodAbility.off('inputStart');
       inputMethodAbility.off('inputStop', () => {});
     }
   }
   
   const keyboardController = new KeyboardController();
   
   export default keyboardController;
   ```
<!--RP2End-->
3. KeyboardKeyData.ts文件。

   定义软键盘的按键显示内容。

   ```ts
   export interface sourceListType {
     content: string,
   }
   
   export let numberSourceListData: sourceListType[] = [
     {
       content: '1'
     },
     {
       content: '2'
     },
     {
       content: '3'
     },
     {
       content: '4'
     },
     {
       content: '5'
     },
     {
       content: '6'
     },
     {
       content: '7'
     },
     {
       content: '8'
     },
     {
       content: '9'
     },
     {
       content: '0'
     }
   ]
   ```

4. Index.ets文件。

   主要描绘了具体按键功能。如按下数字键，就会将数字内容在输入框中打印出来，按下删除键，就会将内容删除。

   同时在resources/base/profile/main_pages.json文件的src字段中添加此文件路径。

   ```ets
   import { numberSourceListData, sourceListType } from './KeyboardKeyData';
   import keyboardController from '../model/KeyboardController';
   
   @Component
   struct keyItem {
     private keyValue: sourceListType = numberSourceListData[0];
     @State keyBgc: string = "#fff"
     @State keyFontColor: string = "#000"
   
     build() {
       Column() {
         Flex({ direction: FlexDirection.Column,
           alignItems: ItemAlign.Center, justifyContent: FlexAlign.Center }) {
           Text(this.keyValue.content).fontSize(20).fontColor(this.keyFontColor)
         }
       }
       .backgroundColor(this.keyBgc)
       .borderRadius(6)
       .width("8%")
       .height("65%")
       .onClick(() => {
         keyboardController.insertText(this.keyValue.content);
       })
     }
   }
   
   // 删除组件
   @Component
   export struct deleteItem {
     @State keyBgc: string = "#fff"
     @State keyFontColor: string = "#000"
   
     build() {
       Column() {
         Flex({ direction: FlexDirection.Column,
           alignItems: ItemAlign.Center, justifyContent: FlexAlign.Center }) {
           Text("删除").fontSize(20).fontColor(this.keyFontColor)
         }
       }
       .backgroundColor(this.keyBgc)
       .width("13%")
       .borderRadius(6)
       .onClick(() => {
         keyboardController.deleteForward(1);
       })
     }
   }
   
   // 数字键盘
   @Component
   struct numberMenu {
     private numberList: sourceListType[] = numberSourceListData;
   
     build() {
       Flex({ direction: FlexDirection.Column, alignItems: ItemAlign.Center, justifyContent: FlexAlign.SpaceEvenly }) {
         Flex({ justifyContent: FlexAlign.SpaceBetween }) {
           ForEach(this.numberList, (item: sourceListType) => { // 数字键盘第一行
             keyItem({ keyValue: item })
           }, (item: sourceListType) => item.content);
         }
         .padding({ top: "2%" })
         .width("96%")
         .height("25%")
   
         Flex({ justifyContent: FlexAlign.SpaceBetween }) {
           deleteItem()
         }
         .width("96%")
         .height("25%")
       }
     }
   }
   
   @Entry
   @Component
   struct Index {
     private numberList: sourceListType[] = numberSourceListData
   
     build() {
       Stack() {
         Flex({
           direction: FlexDirection.Column,
           alignItems: ItemAlign.Center,
           justifyContent: FlexAlign.End
         }) {
               Flex({
                 direction: FlexDirection.Column,
                 alignItems: ItemAlign.Center,
                 justifyContent: FlexAlign.SpaceBetween
               }) {
                 numberMenu({
                   numberList: this.numberList
                 })
               }
               .align(Alignment.End)
               .width("100%")
               .height("75%")
             }
         .height("100%").align(Alignment.End).backgroundColor("#cdd0d7")
       }
       .position({ x: 0, y: 0 }).zIndex(99999)
     }
   }
   ```

<!--Del-->
5. 在工程Module对应的[module.json5配置文件](../quick-start/module-configuration-file.md)中注册InputMethodExtensionAbility，type标签需要设置为“inputMethod”，srcEntry标签表示当前InputMethodExtensionAbility组件所对应的代码路径。

   ```json
   {
     "module": {
       ...
       "extensionAbilities": [
         {
           "description": "inputMethod",
           "name": "InputMethodExtensionAbility",       
           "icon": "$media:app_icon",
           "srcEntry": "./ets/InputMethodExtensionAbility/InputMethodService.ts",
           "type": "inputMethod",
           "exported": true
         }
       ]
     }
   }
   ```
<!--DelEnd-->


<!--RP3-->

<!--RP3End-->

## 约束与限制

为了降低InputMethodExtensionAbility能力被三方应用滥用的风险，现通过基础访问模式的功能约束对输入法应用进行安全管控。

> **说明：**
>
> 严格遵从基础访问模式的功能约束。在此模式下，开发者应仅提供基础打字功能，不应提供任何形式与网络交互相关的功能。系统会逐步增加基础访问模式的安全管控能力，包括但不限于：以独立进程和沙箱的方式运行Extension进程；禁止Extension进程创建子进程；进程间通信与网络访问等。因此未遵从此约定可能会导致功能异常。

## 相关实例

针对InputMethodExtensionAbility开发，有以下相关实例可供参考：

- [轻量级输入法](https://gitcode.com/openharmony/applications_app_samples/tree/master/code/Solutions/InputMethod/KikaInput)
