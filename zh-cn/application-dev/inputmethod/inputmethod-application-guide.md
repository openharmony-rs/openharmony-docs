# 实现一个输入法应用
<!--Kit: IME Kit-->
<!--Subsystem: MiscServices-->
<!--Owner: @illybyy-->
<!--Designer: @andeszhang-->
<!--Tester: @murphy84-->
<!--Adviser: @zhang_yixin13-->

[InputMethodExtensionAbility](../reference/apis-ime-kit/js-apis-inputmethod-extension-ability.md)提供了onCreate()和onDestroy()生命周期回调，根据需要重写对应的回调方法。InputMethodExtensionAbility的生命周期如下：

- **onCreate()**

  服务被首次创建时触发该回调，开发者可以在此进行一些初始化的操作，例如注册公共事件监听等。

  > **说明：**
  >
  > 如果服务已创建，再次启动该InputMethodExtensionAbility不会触发onCreate()回调。

- **onDestroy()**

  当不再使用服务且准备将该实例销毁时，触发该回调。开发者可以在该回调中清理资源，如注销监听等。


## 开发步骤 

开发者在实现一个输入法应用时，需要在DevEco Studio工程中新建一个InputMethodExtensionAbility，具体步骤如下：

1. 在工程Module对应的ets目录下，右键选择“New > Directory”，新建一个目录，并命名为InputMethodExtensionAbility。

2. 在InputMethodExtensionAbility目录下，右键选择“New > File”，新建四个文件，分别为KeyboardController.ts、InputMethodService.ts、Index.ets以及KeyboardKeyData.ts。目录如下：

   ``` TypeScript
   /src/main/
   ├── ets/InputMethodExtensionAbility
   │       └──model/KeyboardController.ts      # 显示键盘
   │       └──InputMethodService.ts        # 自定义类继承InputMethodExtensionAbility并加上需要的生命周期回调
   │       └──pages
   │         └── Index.ets            # 绘制键盘，添加输入删除功能
   │         └── KeyboardKeyData.ts          # 键盘属性定义
   ├── resources/base/profile/main_pages.json  
   ```

## 文件介绍

1. InputMethodService.ts文件。

   在InputMethodService.ts文件中，增加导入InputMethodExtensionAbility的依赖包，自定义类继承InputMethodExtensionAbility并加上需要的生命周期回调。

   <!-- @[input_case_module_import_InputMethodExtensionAbility](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/Solutions/InputMethod/KikaInputMethod/entry/src/main/ets/InputMethodExtensionAbility/InputMethodService.ets) -->
   
   ``` TypeScript
   
   import { InputMethodExtensionAbility } from '@kit.IMEKit';
   import Log from '../model/Log';
   import { keyboardController } from '../InputMethodExtensionAbility/model/KeyboardController';
   import { Want } from '@kit.AbilityKit';
   
   const TAG: string = 'ServiceExtAbility->';
   
   export default class ServiceExtAbility extends InputMethodExtensionAbility {
     onCreate(want: Want): void {
       this.addLog(`onCreate want: ${want.abilityName}`);
       keyboardController.onCreate(this.context);
     }
   
     onDestroy(): void {
       this.addLog('onDestroy');
       keyboardController.onDestroy();
     }
   
     addLog(message: string): void {
       Log.showInfo(TAG, `kikaInput-new: ${message}`);
     }
   }
   ```


2. KeyboardController.ts文件。KeyboardController中除创建输入法窗口，设置输入法事件监听，实现文本插入、删除之外，还可以获取[输入法键盘与系统面板的偏移区域](../reference/apis-ime-kit/js-apis-inputmethodengine.md#getsystempanelcurrentinsets21)，输入法系统面板在不同设备上存在差异，当设备有系统面板时，输入法软键盘相对系统面板的偏移区域如图所示：

   ![偏移区域示意图](./figures/系统面板与软键盘偏移区域示意图.png)

   <!-- @[input_case_input_KeyboardController358](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/Solutions/InputMethod/KikaInputMethod/entry/src/main/ets/InputMethodExtensionAbility/model/KeyboardController.ets) -->
   
 
   <!-- @[input_case_input_KeyboardController507](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/Solutions/InputMethod/KikaInputMethod/entry/src/main/ets/InputMethodExtensionAbility/model/KeyboardController.ets) -->
 

   <!-- @[input_case_input_KeyboardController587](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/Solutions/InputMethod/KikaInputMethod/entry/src/main/ets/InputMethodExtensionAbility/model/KeyboardController.ets) -->


 
3. KeyboardKeyData.ts文件。

   定义软键盘的按键显示内容。


   <!-- @[input_case_input_KeyboardKeyData016](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/Solutions/InputMethod/KikaInputMethod/entry/src/main/ets/model/KeyboardKeyData.ets) -->
   
   ``` TypeScript
   export interface keySourceListType {
     title: string,
     content: string,
     upperContent: string
   }
   
   export interface sourceListType {
     content: string
   }
   
   export enum MenuKey {
     NUMBER_KEY = '?123',
     NORMAL_KEY = 'ABC',
     SPECIAL_KEY = '=/\<'
   }
   
   export enum SubMenuType {
     NORMAL = 0,
     MENU = 1,
     EDIT = 2
   }
   
   export enum MenuType {
     NORMAL = 0,
     NUMBER = 1,
     SPECIAL = 2
   }
   
   export enum KeyState {
     LOWER_CASE = 0,
     ONCE_UPPER_CASE = 1,
     UPPER_CASE = 2
   }
   
   export let keySourceListData: keySourceListType[] = [
     {
       title: '1',
       content: 'q',
       upperContent: 'Q'
     },
     {
       title: '2',
       content: 'w',
       upperContent: 'W'
     },
     {
       title: '3',
       content: 'e',
       upperContent: 'E'
     },
     {
       title: '4',
       content: 'r',
       upperContent: 'R'
     },
     {
       title: '5',
       content: 't',
       upperContent: 'T'
     },
     {
       title: '6',
       content: 'y',
       upperContent: 'Y'
     },
     {
       title: '7',
       content: 'u',
       upperContent: 'U'
     },
     {
       title: '8',
       content: 'i',
       upperContent: 'I'
     },
     {
       title: '9',
       content: 'o',
       upperContent: 'O'
     },
     {
       title: '0',
       content: 'p',
       upperContent: 'P'
     },
     {
       title: String.fromCharCode(126),
       content: 'a',
       upperContent: 'A'
     },
     {
       title: String.fromCharCode(33),
       content: 's',
       upperContent: 'S'
     },
     {
       title: '@',
       content: 'd',
       upperContent: 'D'
     },
     {
       title: String.fromCharCode(35),
       content: 'f',
       upperContent: 'F'
     },
     {
       title: '%',
       content: 'g',
       upperContent: 'G'
     },
     {
       title: String.fromCharCode(39),
       content: 'h',
       upperContent: 'H'
     },
     {
       title: '&',
       content: 'j',
       upperContent: 'J'
     },
     {
       title: '*',
       content: 'k',
       upperContent: 'K'
     },
     {
       title: '?',
       content: 'l',
       upperContent: 'L'
     },
     {
       title: String.fromCharCode(72),
       content: 'z',
       upperContent: 'Z'
     },
     {
       title: String.fromCharCode(73),
       content: 'x',
       upperContent: 'X'
     },
     {
       title: String.fromCharCode(175),
       content: 'c',
       upperContent: 'C'
     },
     {
       title: String.fromCharCode(95),
       content: 'v',
       upperContent: 'V'
     },
     {
       title: String.fromCharCode(58),
       content: 'b',
       upperContent: 'B'
     },
     {
       title: String.fromCharCode(59),
       content: 'n',
       upperContent: 'N'
     },
     {
       title: String.fromCharCode(47),
       content: 'm',
       upperContent: 'M'
     }
   ]
   ```


   <!-- @[input_case_input_KeyboardKeyData186](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/Solutions/InputMethod/KikaInputMethod/entry/src/main/ets/model/KeyboardKeyData.ets) -->
   
   ``` TypeScript
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
     },
     {
       content: '@'
     },
     {
       content: '#'
     },
     {
       content: '$'
     },
     {
       content: '%'
     },
     {
       content: '&'
     },
     {
       content: '-'
     },
     {
       content: '+'
     },
     {
       content: '('
     },
     {
       content: ')'
     },
     {
       content: '/'
     },
     {
       content: '*'
     },
     {
       content: '"'
     },
     {
       content: "'"
     },
     {
       content: ':'
     },
     {
       content: ';'
     },
     {
       content: '!'
     },
     {
       content: '?'
     },
   
   ]
   
   export let symbolSourceListData: sourceListType[] = [
     {
       content: '~'
     },
     {
       content: '`'
     },
     {
       content: '|'
     },
     {
       content: '\u2022'
     },
     {
       content: '\u221A'
     },
     {
       content: '\u03A0'
     },
     {
       content: '\u00F7'
     },
     {
       content: '\u00D7'
     },
     {
       content: String.fromCharCode(182)
     },
     {
       content: '\u2206'
     },
     {
       content: String.fromCharCode(163)
     },
     {
       content: '\u20ac'
     },
     {
       content: String.fromCharCode(165)
     },
     {
       content: String.fromCharCode(162)
     },
     {
       content: String.fromCharCode(94)
     },
     {
       content: '\u00B0'
     },
     {
       content: '='
     },
     {
       content: String.fromCharCode(123)
     },
     {
       content: String.fromCharCode(125)
     },
     {
       content: String.fromCharCode(44)
     },
     {
       content: String.fromCharCode(92)
     },
     {
       content: String.fromCharCode(169)
     },
     {
       content: String.fromCharCode(174)
     },
     {
       content: '\u2122'
     },
     {
       content: '\u2105'
     },
     {
       content: '['
     },
     {
       content: ']'
     }
   ]
   ```
 
4. Index.ets文件。

   主要描绘了具体按键功能。如按下数字键，就会将数字内容在输入框中打印出来，按下删除键，就会将内容删除。

   <!--Del-->同时在resources/base/profile/main_pages.json文件的src字段中添加此文件路径。<!--DelEnd-->

   <!-- @[input_case_input_index](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/Solutions/InputMethod/KikaInputMethod/entry/src/main/ets/InputMethodExtensionAbility/pages/Index.ets) -->
   
   ``` TypeScript
   import deviceInfo from '@ohos.deviceInfo';
   import Log from '../../model/Log';
   import { EditView } from '../../components/EditView';
   import { InputHandler } from '../model/KeyboardController';
   import {
     MenuType,
     SubMenuType,
     keySourceListData,
     numberSourceListData,
     symbolSourceListData,
     keySourceListType,
     sourceListType
   } from '../../model/KeyboardKeyData';
   import { KeyMenu } from '../../components/KeyMenu';
   import { NumberMenu } from '../../components/NumberMenu';
   import { StyleConfiguration, KeyStyle } from '../../common/StyleConfiguration';
   import { SymbolMenu } from '../../components/SymbolMenu';
   import { Submenu } from '../../components/Submenu';
   import { TopMenu } from '../../components/TopMenu';
   import { inputMethodEngine } from '@kit.IMEKit';
   
   
   const DEVICE_TYPE: string = deviceInfo.deviceType;
   const TAG: string = 'index->';
   
   @Entry
   @Component
   struct Index {
     @Provide menuType: number = MenuType.NORMAL;
     @StorageLink('inputPattern') @Watch('inputPatternChange') inputPattern: InputType = InputType.Normal
     @StorageLink('submenuType') submenuType: number = SubMenuType.NORMAL;
     @StorageLink('isLandscape') @Watch('change') isLandscape: boolean = false;
     @StorageLink('isRkDevice') isRkDevice: boolean = true;
     @StorageLink('inputStyle') inputStyle: KeyStyle = StyleConfiguration.getInputStyle(this.isLandscape, this.isRkDevice, DEVICE_TYPE);
     private panel: inputMethodEngine.Panel | undefined;
     @StorageLink('subtypeChange') subtypeChange: number = 0;
   
   
     aboutToAppear(): void {
       // 感知是否设置沉浸模式，如果是沉浸模式选择沉浸模式类型
       inputMethodEngine.getKeyboardDelegate().on("editorAttributeChanged", (attr : inputMethodEngine.EditorAttribute) => {
         console.info('recv editorAttributeChanged, immersiveMode: ', attr.immersiveMode);
         if (attr.immersiveMode == 1) {
           this.panel?.setImmersiveMode(inputMethodEngine.ImmersiveMode.DARK_IMMERSIVE);
           console.info('recv editorAttributeChanged, panel:', this.panel?.getImmersiveMode());
         }
       })
     }
   
     onBackPress(): boolean {
       Log.showInfo(TAG, 'kikaInput onBackPress');
       this.submenuType = SubMenuType.NORMAL;
       InputHandler.getInstance().hideKeyboardSelf();
       return true;
     }
   
     inputPatternChange(): void {
       if (this.inputPattern === InputType.Number || this.inputPattern === InputType.PhoneNumber) {
         this.menuType = MenuType.NUMBER;
       } else {
         this.menuType = MenuType.NORMAL;
       }
     }
   
     change(): void {
       AppStorage.set('inputStyle', StyleConfiguration.getInputStyle(this.isLandscape, this.isRkDevice, DEVICE_TYPE));
     }
   
   
   
     build() {
       Stack() {
         Column() {
           TopMenu()
           Column() {
             if (this.submenuType > SubMenuType.NORMAL) {
               if (this.submenuType === SubMenuType.MENU) {
                 Submenu()
               } else {
                 EditView();
               }
             } else {
               if (this.menuType === MenuType.NORMAL) {
                 if (this.subtypeChange == 0) {
                   KeyMenu()
                 } else {
                   NumberMenu()
                 }
               } else if (this.menuType === MenuType.NUMBER) {
                 NumberMenu()
               } else {
                 SymbolMenu()
               }
             }
           }
           .width('100%')
           .layoutWeight(1)
           .justifyContent(FlexAlign.Center)
           .backgroundColor('#D5D8DD')
         }
         .height('100%')
       }
       .height('100%')
       .backgroundColor(Color.White)
     }
   }
   ```

5. main_pages.json文件。对应ets/InputMethodExtensionAbility/pages/路径下键盘的绘制页面。

   ``` JSON
   {
     "src": [
       "InputMethodExtensionAbility/pages/Index"
     ]
   }
   ```

6. 在工程Module对应的[module.json5配置文件](../quick-start/module-configuration-file.md)中注册InputMethodExtensionAbility，type标签需要设置为“inputMethod”，srcEntry标签表示当前InputMethodExtensionAbility组件所对应的代码路径。


   <!-- @[input_case_entry_module_extensionAbilities](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/Solutions/InputMethod/KikaInputMethod/entry/src/main/module.json5) -->
   
   ``` JSON5
   "extensionAbilities": [
     {
       "srcEntry": "./ets/InputMethodExtensionAbility/InputMethodService.ets",
       "name": "InputMethodService",
       "label": "$string:MainAbility_label",
       "description": "$string:extension_ability_descripter",
       "type": "inputMethod",
       "exported": true,
       "metadata": [
         {
           "name": "ohos.extension.input_method",
           "resource": "$profile:input_method_config"
         }
       ]
     }
   ],
   ```




## 约束与限制

为了降低InputMethodExtensionAbility能力被三方应用滥用的风险，现通过基础访问模式的功能约束对输入法应用进行安全管控。

> **说明：**
>
> 严格遵从基础访问模式的功能约束。在此模式下，开发者应仅提供基础打字功能，不应提供任何形式与网络交互相关的功能。系统会逐步增加基础访问模式的安全管控能力，包括但不限于：以独立进程和沙箱的方式运行Extension进程；禁止Extension进程创建子进程；进程间通信与网络访问等。因此未遵从此约定可能会导致功能异常。

## 相关实例

针对InputMethodExtensionAbility开发，有以下相关实例可供参考：

- [轻量级输入法](https://gitcode.com/openharmony/applications_app_samples/tree/master/code/Solutions/InputMethod/KikaInput)

## 示例效果图
![示例效果图](./figures/实现一个输入法应用示例效果图.png)