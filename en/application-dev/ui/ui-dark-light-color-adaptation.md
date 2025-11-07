# Application Dark and Light Mode Adaptation
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @lushi871202-->
<!--Designer: @lushi871202-->
<!--Tester: @sally__-->
<!--Adviser: @Brilliantry_Rui-->

## Overview

To enhance user experience, applications should adapt to the system's dark and light modes. There are two primary scenarios for implementing this adaptation:

[Following the system's color mode](#following-the-systems-color-mode)

[Setting the color mode independently](#setting-the-color-mode-independently)

## Following the System's Color Mode

1. Color Adaptation

   - Custom Resource Implementation

     Create a **dark** folder under the **resources** directory and add a **color.json** file to define dark mode color resources. For details, see [Resource Categories and Access](../quick-start/resource-categories-and-access.md).

     Figure 1 Structure of the resources directory

     ![colorJsonDir](figures/colorJsonDir.png)
    
     The following is the example configuration:
    
     **base/element/color.json** file:
    
     ```json
     {
       "color": [
         {
           "name": "app_title_color",
           "value": "#000000"
         }
       ]
     }
     ```
    
     **dark/element/color.json** file:
    
     ```json
     {
       "color": [
         {
           "name": "app_title_color",
           "value": "#FFFFFF"
         }
       ]
     }
     ```

   - System Resource Implementation

     You can use [system-provided resources](../quick-start/resource-categories-and-access.md#system-resources), which automatically adapt to different configurations including the device type and dark or light mode. The same resource ID can have different values under these configurations. This means you don't need to create separate color resources for dark and light modes. Instead, you can reference system resources to maintain a consistent look. For example, to set your application's text color, simply use:

     ```ts
     Text('Use system-defined colors')
       .fontColor($r('sys.color.ohos_id_color_text_primary'))
     ```

2. Image Resource Adaptation

    To adapt images to dark and light modes, use resource qualifier directories. Specifically, place images with the same name in the **dark/media** directory. Reference these images using the **$r** syntax based on their **key** values. The system will automatically load the appropriate image based on the current mode.

    For SVG icons, use the [fillColor](arkts-graphics-display.md#displaying-vector-images) attribute with system resources to dynamically adjust their appearance for dark and light modes, eliminating the need for separate image sets.

    ```ts
    Image($r('app.media.pic_svg'))
      .width(50)
      .fillColor($r('sys.color.ohos_id_color_text_primary'))
    ```

3. Web Component Adaptation

    The **Web** component supports dark color mode configuration. For details, see [Setting the Dark Mode](../web/web-set-dark-mode.md).

4. Custom Node Adaptation

    Custom nodes **BuilderNode** and **ComponentContent** require manual propagation of system environment change events to trigger complete node updates. For implementation details, see the [BuilderNode system environment change](../reference/apis-arkui/js-apis-arkui-builderNode.md#updateconfiguration12) section.

    <!-- @[custom_node](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/ColorAdaptionSys/entry/src/main/ets/pages/BuilderNodeAdaptation.ets) -->
    
    ``` TypeScript
    // Record the created custom node object.
    const builderNodeMap: BuilderNode<[Params]>[] = [];
    
    class MyFrameCallback extends FrameCallback {
      onFrame() {
        updateColorMode();
      }
    }
    
    function updateColorMode() {
      builderNodeMap.forEach((value, index) => {
        // Notify the BuilderNode of the environment changes to trigger switching between light and dark modes.
        value.updateConfiguration();
      })
    }
    // ···
      aboutToAppear(): void {
        // ···
            this.getUIContext()?.postFrameCallback(new MyFrameCallback());
        // ···
      }
    ```

5. Listening for Color Mode Switching Events

    Applications can listen for system color mode changes and perform custom logic, such as initializing resources of other types. This approach works regardless of whether the application is set to follow the system's dark or light mode.

    a. Save the current color mode to the AppStorage in the **onCreate()** lifecycle of the AbilityStage.

    <!-- @[create_sys](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/ColorAdaptionSys/entry/src/main/ets/entryability/EntryAbility.ets) -->
    
    ``` TypeScript
    onCreate(): void {
      this.context.getApplicationContext().setColorMode(ConfigurationConstant.ColorMode.COLOR_MODE_NOT_SET);
      AppStorage.setOrCreate('currentColorMode', this.context.config.colorMode);
    }
    ```

    b. Update the color mode to the AppStorage in the **onConfigurationUpdate()** lifecycle callback of the AbilityStage..

    <!-- @[update_app](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/ColorAdaptionApp/entry/src/main/ets/entryability/EntryAbility.ets) -->
    
    ``` TypeScript
    onConfigurationUpdate(newConfig: Configuration): void {
      AppStorage.setOrCreate('currentColorMode', newConfig.colorMode);
      hilog.info(0x0000, 'testTag', 'the newConfig.colorMode is %{public}s', JSON.stringify(AppStorage.get('currentColorMode')) ?? '');
    }
    ```

    c. Use @StorageProp and @Watch to listen for color mode changes and refresh the state variable.

    <!-- @[prop](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/ColorAdaptionApp/entry/src/main/ets/pages/BuilderNodeAdaptation.ets) -->
    
    ``` TypeScript
    @StorageProp('currentColorMode') @Watch('onColorModeChange') currentMode: number = ConfigurationConstant.ColorMode.COLOR_MODE_LIGHT;
    ```

    d. Refresh the state variable based on the latest color mode in the **aboutToAppear()** API.

    <!-- @[color_mode_change_appear](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/ColorAdaptionApp/entry/src/main/ets/pages/BuilderNodeAdaptation.ets) -->
    
    ``` TypeScript
    aboutToAppear(): void {
      // ···
      if (this.currentMode == ConfigurationConstant.ColorMode.COLOR_MODE_LIGHT) {
        // Resource initialization logic for light mode
      // ···
      } else {
        // Resource initialization logic for dark mode
      // ···
      }
    }
    ```

    e. Implement the same logic in the @Watch callback function.

    <!-- @[color_mode_change](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/ColorAdaptionApp/entry/src/main/ets/pages/BuilderNodeAdaptation.ets) -->
    
    ``` TypeScript
    onColorModeChange(): void {
      if (this.currentMode == ConfigurationConstant.ColorMode.COLOR_MODE_LIGHT) {
        // Resource initialization logic for light mode
        this.colorText == 'light';
      } else {
        // Resource initialization logic for dark mode
        this.colorText == 'dark';
      }
    }
    ```

6. Partial Adaptation

    Using [WithTheme](../reference/apis-arkui/arkui-ts/ts-container-with-theme.md), you can set three color modes: follow the system, light mode, and dark mode.

    Within the scope of **WithTheme**, component styles adapt to the specified color mode by accessing the corresponding system and application resource values, ensuring components adjust their appearance based on the configured mode. For details, see [Setting a Custom Theme Style for Specific Application Pages](./theme_skinning.md#setting-a-custom-theme-style-for-specific-application-pages).

## Setting the Color Mode Independently

By default, applications follow the system's color mode. When configured this way, the application's color mode becomes fixed and no longer follows system changes.

> **NOTE**
> 
> If your application does not support dark mode properly and displays abnormalities, you can use this approach to lock the UI in light mode.

<!-- @[create_app](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/ColorAdaptionApp/entry/src/main/ets/entryability/EntryAbility.ets) -->

``` TypeScript
onCreate(want: Want, launchParam: AbilityConstant.LaunchParam): void {
  try {
    hilog.info(0x0000, 'testTag', '%{public}s', 'Ability onCreate');
    this.context.getApplicationContext().setColorMode(ConfigurationConstant.ColorMode.COLOR_MODE_LIGHT);
  } catch (err) {
    hilog.error(DOMAIN, 'testTag', 'Failed to set colorMode. Cause: %{public}s', JSON.stringify(err));
  }
  hilog.info(DOMAIN, 'testTag', '%{public}s', 'Ability onCreate');
}
```

## System Rules for Determining the Application Color Mode

1. If the application calls the **setColorMode** API, its effect takes precedence.

2. If the application does not call the **setColorMode** API:

   - If there are dark resources in the **dark** directory of the application project, system components automatically switch to dark mode.

   - If no dark resources are available, system components maintain light color appearances in dark mode.

     ![darkDir](figures/darkDir.png)

If your application is built using system components or colors and needs to synchronize with the system's color mode, refer to the following example to modify your code and ensure proper application behavior.

<!-- @[create_sys](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/ColorAdaptionSys/entry/src/main/ets/entryability/EntryAbility.ets) -->

``` TypeScript
onCreate(): void {
  this.context.getApplicationContext().setColorMode(ConfigurationConstant.ColorMode.COLOR_MODE_NOT_SET);
  AppStorage.setOrCreate('currentColorMode', this.context.config.colorMode);
}
```

## Recommendations and Precautions

- Recommended Approach

  Use the [AbilityStage listener callback](../reference/apis-ability-kit/js-apis-app-ability-abilityStage.md#onconfigurationupdate) or [Ability listener callback](../reference/apis-ability-kit/js-apis-app-ability-ability.md#abilityonconfigurationupdate) to proactively listen for system code mode changes. Execute specific service logic by binding state variables when color mode changes.

- Not Recommended Approach

  Avoid adapting to color mode changes through functions in attribute settings that rely on re-executing attribute setting code during the color mode switching process. Incorrect usage:

  ```ts
  getResource() : string {
    // Obtain the system color mode.
    if (colorMode == "dark") {
      return "#FF000000"
    } else {
      return "#FFFFFFFF"
    }
  }
  // ... other code ...
  build() {
    // ... other code ...
    Button.backgroundColor(this.getResource())
    // ... other code ...
  }
  ```
  The approach described in the preceding example relies on re-executing attribute setting code during the mode switching process. As the system evolves and performance optimizations are implemented, there is no guarantee that all attribute code will be re-executed. In most hot update scenarios, re-executing all page construction and attribute setting code is clearly redundant and inefficient.

## Optimizing Color Mode Switching Overhead
  
By default, color mode switching requires a full redraw, including resetting attributes for all components. The performance overhead increases linearly with application UI complexity.

Starting from API version 20, the system provides an optimized color mode switching mechanism. You can enable this capability by adding the [metadata](../quick-start/module-configuration-file.md#metadata) configuration item to reduce overhead during mode transitions.

> **NOTE**
>
> When configuring **metadata**, ensure that any custom adaptation logic implemented through attribute setting functions properly handles color mode changes.
> <!--RP1--><!--RP1End-->

1. Enable color mode switching optimization through **metadata**.

   To reduce color mode switching overhead, add the **metadata** field to the **module.json5** file and ensure proper adaptation of component attributes:

    ```ts
    "metadata": [
      {
        "name": "configColorModeChangePerformanceInArkUI",
        "value": "true"
      }
    ]
    ```

2. Ensure proper adaptation of your application's custom behavior.

   After enabling color mode switching optimization, frontend code and attribute settings are not re-executed during mode switching. Only essential attributes are updated and redrawn. If your application relies on function-based attribute settings to handle mode changes, this adaptation approach will no longer work. You must implement proper adaptation before enabling the optimization. For detailed guidance, see [Recommendations and Precautions](#recommendations-and-precautions).

## Using Color Inversion for Quick Dark Mode Adaptation

Starting from API version 20, applications with substantial existing codebases can leverage the system's color inversion capability to rapidly implement dark mode support. This approach serves as an alternative to the [resource configuration approach](#following-the-systems-color-mode) and [theme-based adaptation](../reference/apis-arkui/arkui-ts/ts-container-with-theme.md).

While offering less granular control compared to resource configuration and theme modes, color inversion significantly reduces adaptation effort and prevents application package size growth from extensive resource definitions. This method provides visually acceptable results in most scenarios.

> **NOTE**
>
> The color inversion capability requires [enabled color mode switching overhead optimization](#optimizing-color-mode-switching-overhead).

1. Implement color inversion.

   The ArkUI framework introduces the [OH_ArkUI_SetForceDarkConfig](../reference/apis-arkui/capi-native-node-h.md#oh_arkui_setforcedarkconfig) API in API version 20. This feature automatically applies color inversion based on your custom algorithms during color mode switching. The inversion only affects color attributes set with non-resource values; when colors are defined via $r references, resource file configurations take precedence.

   This capability proves particularly useful when applications require multiple color attribute configurations but lack comprehensive dark mode resource definitions.

    > **NOTE**
    >
    > 1. Before calling **OH_ArkUI_SetForceDarkConfig**, ensure that [OH_ArkUI_QueryModuleInterfaceByName(ARKUI_NATIVE_NODE, "ArkUI_NativeNodeAPI_1")](../reference/apis-arkui/capi-native-interface-h.md#oh_arkui_querymoduleinterfacebyname) is loaded.
    >
    > 2. The **OH_ArkUI_SetForceDarkConfig** API must be called in the UI thread before node creation.
    >
    > 3. The **OH_ArkUI_SetForceDarkConfig** API takes effect only at the process level. Different instances cannot use different color inversion algorithms.
    >
    > 4. The **OH_ArkUI_SetForceDarkConfig** API supports only C API implementation. This design avoids significant cross-language call overhead during frequent color mode transitions.

    This example demonstrates the fundamental usage of the **OH_ArkUI_SetForceDarkConfig** API. Configure a custom color inversion algorithm based on actual scenarios to display appropriate color values during color mode transitions.

      ```c++
      OH_ArkUI_SetForceDarkConfig(nullptr, true, ArkUI_NodeType::ARKUI_NODE_UNDEFINED, nullptr); // Apply the default system color inversion algorithm to all components.
      ```

      ```ts
      // Use the color inversion capability when creating components on the ArkTS side.
      // By default, the default color inversion algorithm is applied to all components. Text colors invert during theme switching.
      build() {
        // ... other code ...
        Text("Test color inversion algorithm")
          .fontColor(Color.Black)
        // ... other code ...
      }
      ```

    The **OH_ArkUI_SetForceDarkConfig** API supports various configuration modes.
      ```c++
      // Custom color inversion algorithm function.
      uint32_t colorInvertFunc(uint32_t color) {
        return ~color;
      }
      OH_ArkUI_SetForceDarkConfig(nullptr, true, ArkUI_NodeType::ARKUI_NODE_UNDEFINED, colorInvertFunc); // Apply the custom inversion algorithm to all components.
      ```
      ```c++
      OH_ArkUI_SetForceDarkConfig(nullptr, false, ArkUI_NodeType::ARKUI_NODE_UNDEFINED, nullptr); // Disable color inversion for all components. The original system logic is used.
      ```
      ```c++
      OH_ArkUI_SetForceDarkConfig(nullptr, true, ArkUI_NodeType::ARKUI_NODE_TEXT, nullptr); // Apply the default inversion algorithm only to text components.
      ```
      ```c++
      // Custom color inversion algorithm function.
      uint32_t colorInvertFunc(uint32_t color) {
        return ~color;
      }
      OH_ArkUI_SetForceDarkConfig(nullptr, true, ArkUI_NodeType::ARKUI_NODE_TEXT, colorInvertFunc); // Apply the custom inversion algorithm only to text components.
      ```

    > **NOTE**
    >
    > - Component-specific inversion requires global capability enablement.
    >
    > - The color inversion algorithm cannot be disabled only for a certain type of components when the global color inversion capability is enabled.

2. Understand the following color inversion priority order that the system follows when applying color treatments:

   a. Dark mode color resources
   
   b. Component-specific inversion algorithms
   
   c. Global inversion algorithms

3. Implement inversion capability control.

   Use the [allowForceDark](../reference/apis-arkui/arkui-ts/ts-allow-force-dark.md#allowforcedark) attribute as an escape mechanism to disable automatic color inversion for specific components, preserving their original appearance during theme transitions.
