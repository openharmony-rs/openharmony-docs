# 应用深浅色适配
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @lushi871202-->
<!--Designer: @lushi871202-->
<!--Tester: @sally__-->
<!--Adviser: @HelloCrease-->

## 概述

当前系统存在深浅色两种显示模式，为了给用户更好的使用体验，应用应适配深浅色模式。从应用与系统配置关联的角度来看，适配深浅色模式可以分为下面两种情况：

[应用跟随系统的深浅色模式](#应用跟随系统的深浅色模式)

[应用主动设置深浅色模式](#应用主动设置深浅色模式)

## 应用跟随系统的深浅色模式

1. 颜色适配

   - 自定义资源实现

     resources目录下增加深色模式限定词目录（命名为dark）并新建color.json文件，可显示深色模式颜色资源的配置。详细请参考[资源分类与访问](../quick-start/resource-categories-and-access.md)。

     图1 resources目录结构示意

     ![colorJsonDir](figures/colorJsonDir.png)
    
     例如，开发者可在这两个color.json中定义同名配色定义并赋予不同的色值。
    
     base/element/color.json文件：
    
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
    
     dark/element/color.json文件：
    
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

   - 通过系统资源实现

     开发者可直接使用的[系统预置资源](../quick-start/resource-categories-and-access.md#系统资源)，即分层参数，同一资源ID在设备类型、深浅色等不同配置下有不同的取值。通过使用系统资源，不同的开发者可以开发出具有相同视觉风格的应用，不需要自定义两份颜色资源，在深浅色模式下也会自动切换成不同的颜色值。例如，开发者可调用系统资源中的文本主要配色来定义应用内文本颜色。

     ```ts
     Text('使用系统定义配色')
       .fontColor($r('sys.color.ohos_id_color_text_primary'))
     ```

2. 图片资源适配

    采用资源限定词目录的方式。参照颜色适配的方法，需要将深色模式下对应的同名图片放到 dark/media 目录下，再通过$r的方式加载图片资源的key值，系统做深浅色模式切换时，会自动加载对应资源文件中的value值。

    对于 SVG 格式的一些简单图标，可以使用[fillColor](arkts-graphics-display.md#显示矢量图)属性配合系统资源改变图片的绘制颜色。不通过两套图片资源的方式，也可以实现深浅色模式适配。

    ```ts
    Image($r('app.media.pic_svg'))
      .width(50)
      .fillColor($r('sys.color.ohos_id_color_text_primary'))
    ```

3. Web组件适配

    Web组件支持对前端页面进行深色模式配置，可参考[Web组件深色模式](../web/web-set-dark-mode.md)进行相关配置。

4. "自定义节点"适配

    自定义节点BuilderNode和ComponentContent需手动传递系统环境变化事件，触发节点的全量更新，详细请参考[builderNode系统环境变化更新](../reference/apis-arkui/js-apis-arkui-builderNode.md#updateconfiguration12)

    ```ts
    // 记录创建的自定义节点对象
    const builderNodeMap: Array<BuilderNode<[Params]>> = new Array();

    class MyFrameCallback extends FrameCallback {
      onFrame() {
        updateColorMode();
      }
    }

    function updateColorMode() {
      builderNodeMap.forEach((value, index) => {
        // 通知BuilderNode环境变量改变，触发深浅色切换
        value.updateConfiguration();
      })
    }
    // ... other code ...
    aboutToAppear() {
    // ... other code ...
      this.getUIContext()?.postFrameCallback(new MyFrameCallback());
    // ... other code ...
    }
    ```

5. 应用监听深浅色模式切换事件

    应用可以主动监听系统深浅色模式变化，进行其他类型的资源初始化等自定义逻辑。无论应用是否跟随系统深浅色模式变化，该监听方式均可生效。

    a. 在 AbilityStage 的 onCreate() 生命周期中获取APP当前的颜色模式并保存到 AppStorage。

    ```ts
    onCreate(): void {
      hilog.info(0x0000, 'testTag', '%{public}s', 'Ability onCreate');
      AppStorage.setOrCreate('currentColorMode', this.context.config.colorMode);
    }
    ```

    b. 在 AbilityStage 的 onConfigurationUpdate() 生命周期中获取最新变更的颜色模式并刷新到 AppStorage。

    ```ts
    onConfigurationUpdate(newConfig: Configuration): void {
      AppStorage.setOrCreate('currentColorMode', newConfig.colorMode);
      hilog.info(0x0000, 'testTag', 'the newConfig.colorMode is %{public}s', JSON.stringify(AppStorage.get('currentColorMode')) ?? '');
    }
    ```

    c. 在Page中通过 @StorageProp + @Watch 方式获取当前最新颜色并监听设备深色模式变化。

    ```ts
    @StorageProp('currentColorMode') @Watch('onColorModeChange') currentMode: number = ConfigurationConstant.ColorMode.COLOR_MODE_LIGHT;
    ```

    d. 在 aboutToAppear 初始化函数中根据当前最新颜色模式刷新状态变量。

    ```ts
    aboutToAppear(): void {
      if (this.currentMode == ConfigurationConstant.ColorMode.COLOR_MODE_LIGHT) {
        //当前为浅色模式，资源初始化逻辑
      }else {
        //当前为深色模式，资源初始化逻辑
      }
    }
    ```

    e. 在 @Watch 回调函数中执行同样的适配逻辑。

    ```ts
    onColorModeChange(): void {
      if (this.currentMode == ConfigurationConstant.ColorMode.COLOR_MODE_LIGHT) {
        //当前为浅色模式，资源初始化逻辑
      } else {
        //当前为深色模式，资源初始化逻辑
      }
    }
    ```

6. 局部深浅色适配

    通过[WithTheme](../reference/apis-arkui/arkui-ts/ts-container-with-theme.md)可以设置三种颜色模式，分别为：跟随系统模式、浅色模式和深色模式。

    在WithTheme作用范围内，组件的样式资源值将依据指定模式，读取对应的深浅色模式系统和应用资源值。这表明，在WithTheme作用范围内，组件的配色将根据指定的深浅模式进行调整。详情请参阅[设置应用页面局部深浅色](./theme_skinning.md#设置应用页面局部深浅色)。

## 应用主动设置深浅色模式

应用默认配置为跟随系统切换深浅色模式，如不希望应用跟随系统深浅色模式变化，可主动设置应用的深浅色风格。设置后，应用的深浅色模式固定，不会随系统改变。

> **说明：**
> 
> 应用未适配深色模式时，如遇到显示异常，可考虑使用该方法禁用深色模式。

```ts
onCreate(): void {
  hilog.info(0x0000, 'testTag', '%{public}s', 'Ability onCreate');
  this.context.getApplicationContext().setColorMode(ConfigurationConstant.ColorMode.COLOR_MODE_DARK);
}
```

## 系统默认判断规则

1. 如果应用调用上述setColorMode接口主动设置了深浅色，则以接口效果优先。

2. 应用没有调用setColorMode接口时：

   - 如果应用工程dark目录下有深色资源，则系统组件在深色模式下会自动切换成为深色。

   - 如果应用工程dark目录下没有任何深色资源，则系统组件在深色模式下仍会保持浅色体验。

     ![darkDir](figures/darkDir.png)

如果应用全部都是由系统组件/系统颜色开发，且想要跟随系统切换深浅色模式时，请参考以下示例修改代码来保证应用体验。

```ts
onCreate(): void {
  this.context.getApplicationContext().setColorMode(ConfigurationConstant.ColorMode.COLOR_MODE_NOT_SET);
}
```

## 使用建议与限制

- 建议方法

  当应用跟随系统深色或浅色模式时，建议采用[AbilityStage的监听回调](../reference/apis-ability-kit/js-apis-app-ability-abilityStage.md#onconfigurationupdate)或[Ability的监听回调](../reference/apis-ability-kit/js-apis-app-ability-ability.md#abilityonconfigurationupdate)方式，主动监听系统深浅色模式变化。一旦颜色模式发生变化，应通过绑定状态变量等方法，执行特定的业务逻辑。

- 不推荐方法

  开发者在使用资源时，未采用监听系统深浅色模式变化的方式，而是在属性设置中通过函数适配深浅色变更。例如，参考以下代码写法：

  ```ts
  getResource() : string {
    // 获取系统颜色模式
    if (colorMode == "dark") {
      return "#FF000000"
    } else {
      return "#FFFFFFFF"
    }
  // ... other code ...
  build() {
    // ... other code ...
    Button.backgroundColor(this.getResource())
    // ... other code ...
  }
  }
  ```
  这种方式依赖于切换流程中重新执行属性设置代码，随着系统的发展和性能优化，并不能确保所有属性代码均被重新执行。因为在大部分热更新场景中，重新执行全部页面构建和属性设置代码显然是冗余的。