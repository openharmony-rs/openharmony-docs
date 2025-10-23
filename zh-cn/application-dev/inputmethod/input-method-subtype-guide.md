# 输入法子类型开发指南
<!--Kit: IME Kit-->
<!--Subsystem: MiscServices-->
<!--Owner: @illybyy-->
<!--Designer: @andeszhang-->
<!--Tester: @murphy1984-->
<!--Adviser: @zhang_yixin13-->

输入法子类型允许输入法展现不同的输入模式或语言，用户可以根据需要在不同模式和语言中切换。如：输入法的中文键盘、英文键盘等都属于输入法的子类型。

## 输入法子类型的配置与实现

1. 输入法应用开发者只需要注册实现一个InputMethodExtensionAbility，所有的输入法子类型共用该InputMethodExtensionAbility，在[module.json5配置文件](../quick-start/module-configuration-file.md)中添加metadata，name为ohos_extension.input_method，用于配置所有子类型的资源信息。

``` JSON5
    "extensionAbilities": [
      {
        "srcEntry": "./ets/ServiceExtAbility/ServiceExtAbility.ets",
        "name": "ServiceExtAbility",
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
   
2. 子类型配置文件格式如下，字段释义参照[InputMethodSubtype](../reference/apis-ime-kit/js-apis-inputmethod-subtype.md#inputmethodsubtype)，开发者需要严格按照配置文件格式及字段进行子类型信息配置，locale字段的配置参照[i18n-locale-culture](.././internationalization/i18n-locale-culture.md#实现原理)。
   ```
   {
     "subtypes": [
       {
         "icon": "$media:icon",
         "id": "InputMethodExtAbility",
         "label": "$string:english",
         "locale": "en-US",
         "mode": "lower"
       },
       {
         "icon": "$media:icon",
         "id": "InputMethodExtAbility1",
         "label": "$string:chinese",
         "locale": "zh-CN",
         "mode": "lower"
       }
     ]
   }
   ```
   
3. 输入法应用中监听子类型事件，根据不同的子类型，可以加载不同的软键盘界面，或者使用状态变量控制界面中的软键盘显示。

<!-- @[input_case_input_KeyboardControllersetSubtype](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/Solutions/InputMethod/KikaInputMethod/entry/src/main/ets/model/KeyboardController.ets) -->

``` TypeScript
    // 设置监听子类型事件，改变输入法应用界面
    InputMethodEngine.on('setSubtype', (inputMethodSubtype: InputMethodSubtype) => {
      this.inputHandle.addLog('GJ setSubtype inputMethodSubtype:' + inputMethodSubtype.id);
      if(inputMethodSubtype.id == 'InputMethodExtAbility') {
        AppStorage.setOrCreate('subtypeChange', 0);
        this.inputHandle.addLog('GJ setSubtype subtypeChange:' + AppStorage.get('subtypeChange'));
      }
      if(inputMethodSubtype.id == 'InputMethodExtAbility1') {
        AppStorage.setOrCreate('subtypeChange', 1);
        this.inputHandle.addLog('GJ setSubtype subtypeChange:' + AppStorage.get('subtypeChange'));
      }
    });
```


## 输入法子类型相关信息的获取

1. 开发者可以通过调用[getCurrentInputMethodSubtype](../reference/apis-ime-kit/js-apis-inputmethod.md#inputmethodgetcurrentinputmethodsubtype9)获取当前输入法应用的当前子类型。

2. 开发者可以通过调用[listCurrentInputMethodSubtype](../reference/apis-ime-kit/js-apis-inputmethod.md#listcurrentinputmethodsubtype9)获取当前输入法应用的所有子类型。

3. 开发者可以通过调用[listInputMethodSubtype](../reference/apis-ime-kit/js-apis-inputmethod.md#listinputmethodsubtype9)获取指定输入法应用的所有子类型。


## 输入法子类型的切换

1. 开发者可以通过调用[switchCurrentInputMethodSubtype](../reference/apis-ime-kit/js-apis-inputmethod.md#inputmethodswitchcurrentinputmethodsubtype9)切换当前输入法应用的子类型。

2. 开发者可以通过调用[switchCurrentInputMethodAndSubtype](../reference/apis-ime-kit/js-apis-inputmethod.md#inputmethodswitchcurrentinputmethodandsubtype9)切换至指定输入法应用的指定子类型。
