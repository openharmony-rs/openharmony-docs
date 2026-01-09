# ArkTS卡片新材质适配（仅对系统应用开放）
<!--Kit: Form Kit-->
<!--Subsystem: Ability-->
<!--Owner: @cx983299475-->
<!--Designer: @xueyulong-->
<!--Tester: @yangyuecheng-->
<!--Adviser: @HelloShuo-->

从API version 23开始，Form Kit支持系统应用使用新材质，提供炫彩透光视觉效果，提供高端精致的用户体验。

> **说明：**
>
> - 本特性对产品功耗、性能要求较高，当前仅在部分旗舰机型上支持，不支持机型上调用后不生效。

## 开发步骤
1. [创建ArkTS卡片](arkts-ui-widget-creation.md)

2. 配置`entry/src/main/resources/base/profile/form_config.json`

   - 在form_config.json文件中的`metadata`添加`visualEffectType`配置，`immersiveMaterial`表示新材质。
   - 为了达到最佳显示效果，建议开启透明卡片配置。需在form_config.json文件中添加`"transparencyEnabled": true`配置。

   ``` json
   {
     "forms": [
       {
         "name": "widget",
         "displayName": "$string:widget_display_name",
         "description": "$string:widget_desc",
         "src": "./ets/widget/pages/WidgetCard.ets",
         "uiSyntax": "arkts",
         "window": {
           "designWidth": 720,
           "autoDesignWidth": true
         },
         "colorMode": "auto",
         "isDynamic": true,
         "isDefault": true,
         "updateEnabled": false,
         "scheduledUpdateTime": "10:30",
         "updateDuration": 1,
         "defaultDimension": "2*4",
         "transparencyEnabled": true,
         "metadata": [
           {
             "name": "visualEffectType",
             "value": "immersiveMaterial"
           }
         ],
         "supportDimensions": [
           "2*4"
         ]
       }
     ]
   }
   ```

3. 完整卡片代码实现

   > **说明：**
   >
   > - 这里需要注意使用系统应用证书进行签名打包。

   `entry/src/main/ets/widget/pages/WidgetCard.ets`完整代码。

   ``` TypeScript
   import  {hdsMaterial}  from '@hms.hds.hdsMaterial';

   @Entry
   @ComponentV2
   struct WidgetCard {
     build() {
       Stack() {
         Column() {
           // 使用场景枚举调用
           Button('hdsMaterial button', {buttonStyle: ButtonStyleMode.NORMAL})
             .width(300)
             .height(80)
             .systemMaterial(new hdsMaterial.Material({
               backgroundMaterial: {
                 type: hdsMaterial.MaterialType.IMMERSIVE,   // 材质类型:沉浸式材质
                 scenario: hdsMaterial.ScenarioType.GENERAL, // 场景:通用
                 level: hdsMaterial.MaterialLevel.ADAPTIVE   // 材质分档:自适应 
               }
             }))
             .margin({top: 10})
         }
         .height('100%')
         .width('100%')
       }
     }
   }
   ```

### 运行结果
![WidgetMaterialVisualEffect](figures/WidgetMaterialVisualEffect.gif)