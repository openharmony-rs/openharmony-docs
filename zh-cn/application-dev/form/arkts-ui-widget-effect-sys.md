# ArkTS卡片新材质适配（仅对系统应用开放）
<!--Kit: Form Kit-->
<!--Subsystem: Ability-->
<!--Owner: @cx983299475-->
<!--Designer: @xueyulong-->
<!--Tester: @yangyuecheng-->
<!--Adviser: @HelloShuo-->

从API version 22开始，Form Kit支持系统应用使用新材质，提升视觉效果，提供高端精致的用户体验。

> **说明：**
>
> - 本特性对产品功耗、性能要求较高，当前仅在部分旗舰机型上支持，不支持机型上调用后不生效。

## 开发步骤
1. [创建ArkTS卡片](arkts-ui-widget-creation.md)

2. 配置`entry/src/main/resources/base/profile/form_config.json`

   - 在form_config.json文件中的`metadata`添加`visualEffectType`配置，`lightWeightMaterialEffect`表示新材质。
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
             "value": "lightWeightMaterialEffect"
           }
         ],
         "supportDimensions": [
           "2*4"
         ]
       }
     ]
   }
   ```

3. 启用新材质能力 `HDSComponent`

   - 卡片提供方导入基础依赖包。在`entry/src/main/syscap.json`中添加以下代码:

   ``` json
   {
     "devices": {
       "general": [
         "phone"
       ]
     },
     "development": {
       "addedSysCaps": [
         "SystemCapability.UIDesign.HDSComponent.Core"
       ]
     }
   }
   ```

4. 添加背景图片到 `entry/src/main/resources/base/media/image.png`

5. 完整卡片代码实现

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
         Image($r('app.media.image'))
         Column() {
           // 使用场景枚举调用
           Button({buttonStyle: ButtonStyleMode.NORMAL})
             .width(300)
             .height(200)
             .systemMaterial(new hdsMaterial.Material({
               backgroundMaterial: {
                 type: hdsMaterial.MaterialType.IMMERSIVE,
                 scenario: hdsMaterial.ScenarioType.GENERAL,
                 level: hdsMaterial.MaterialLevel.ADAPTIVE }
             }))
             .margin({top: 10})

           // 使用传参调用
           Row()
             .width(200)
             .height(100)
             .systemMaterial(new hdsMaterial.Material({
               backgroundMaterial: {
                 params: new Map<string, Array<number>>([
                   ['blurParams', [20, 3]],
                   ['weightsEmboss', [1.0, 0.5]],
                   ['weightsEdl', [1.0, 1.0]],
                   ['bgRates', [-1.8792225, 2.7626955]],
                   ['bgKBS', [0.0073494, 0.0998859, 1.2]],
                   ['bgPos', [0.3, 0.5, 0.5]],
                   ['bgNeg', [0.5, 0.5, 1.0]],
                   ['refractParams', [0, 0.3, 0.3]],
                   ['sdParams', [-50.0, 4.0, 4.62]],
                   ['sdRates', [0.0, 0.0]],
                   ['sdKBS', [0.9, 0.0, 1.0]],
                   ['sdPos', [1.0, 1.7, 1.5]],
                   ['sdNeg', [3.0, 2.0, 1.0]],
                   ['envLightParams', [10, 2.0, 2.0]],
                   ['envLightRates', [0.0, 0.0]],
                   ['envLightKBS', [0.8, 0.27451, 2.0]],
                   ['envLightPos', [1.0, 1.7, 1.5]],
                   ['envLightNeg', [3.0, 2.0, 1.0]],
                   ['edLightParams', [2, 2]],
                   ['edLightAngles', [40, 2]],
                   ['edLightDir', [2.5, 2.5]],
                   ['edLightRates', [0.0, 0.0]],
                   ['edLightKBS', [0.6027, 0.627451, 2.0]],
                   ['edLightPos', [1.0, 1.7, 1.5]],
                   ['edLightNeg', [3.0, 2.0, 1.0]]
                 ])
               }
             }))
             .margin({top: 10})

           // 场景参数叠加部分参数调用
           Button({buttonStyle: ButtonStyleMode.NORMAL})
             .width(300)
             .height(200)
             .systemMaterial(new hdsMaterial.Material({
               backgroundMaterial: {
                 type: hdsMaterial.MaterialType.IMMERSIVE,
                 scenario: hdsMaterial.ScenarioType.GENERAL,
                 level: hdsMaterial.MaterialLevel.ADAPTIVE,
                 params: new Map<string, Array<number>>([
                   ['blurParams', [0, 4]]
                 ])
               }
             }))
             .margin({top: 10})

           // 默认效果调用
           Row({space: 5 }) {
             Row()
               .width(50)
               .height(50)
               .borderRadius(25)
               .systemMaterial(new hdsMaterial.Material({}))
             Row()
               .width(50)
               .height(50)
               .borderRadius(25)
               .systemMaterial(new hdsMaterial.Material({}))
             Row()
               .width(50)
               .height(50)
               .borderRadius(25)
               .systemMaterial(new hdsMaterial.Material({}))
           }
           .margin({top: 10})
         }
       }
     }
   }
   ```

### 运行结果
![WidgetvisualEffect](figures/WidgetVisualEffect.gif)