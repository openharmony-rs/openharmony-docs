# DepthComponent (系统接口)
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @CCFFWW-->
<!--Designer: @CCFFWW-->
<!--Tester: @lxl007-->
<!--Adviser: @Brilliantry_Rui-->

景深组件利用背景与深度图，生成具有景深空间效果的内容。

> **说明：**
>
> 当前页面仅包含本模块的系统接口，其他公开接口参见[DepthComponent](./ts-basic-components-depthcomponent.md)。

**起始版本：** 26.0.0

## DepthSpaceType

景深空间类型枚举。

> **说明：**
>
> 全局模式下，其余进程复用壁纸进程的背景、深度图及相机和光照参数，且不可自定义。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

| 名称 | 值 | 说明 |
| -------- | -------- | -------- |
| GLOBAL | 1 | 全局模式。使用全局的背景、深度图、相机参数及光照参数。|

## 示例
以下两段代码需要配合使用，分别运行于壁纸进程和其他系统应用进程中。

```ts
// 以下代码运行于壁纸进程中。
// 壁纸进程需要设置背景、深度图、相机参数及光照参数。
@Entry
@Component
struct DepthComponentGlobalExample {
  build() {
    Column() {
      // 请开发者替换为实际的资源文件
      DepthComponent($r('app.media.background'), {depthSpace: DepthSpaceType.GLOBAL})
        .width('100%')
        .height('100%')
        .depthMap($r('app.media.depth_map')) // 请开发者替换为实际的资源文件
        .camera({
          position: { x: 0, y: 0, z: 0 },
          quaternion: { x: 0, y: 0, z: 0, w: 1 },
          yFov: 1.05,
          zNear: 0.1,
          zFar: 100
        })
        .light({
          direction: { x: 0, y: 0, z: -1 },
          color: { red: 255, green: 255, blue: 255 },
          intensity: 1
        })
        .backgroundOffset({ x: 0, y: 0 })
        .backgroundScale({ x: 1, y: 1, z: 1, centerX: '50%', centerY: '50%' })
    }
    .width('100%')
    .height('100%')
  }
}
```

```ts
// 以下代码运行于其他系统应用进程中。
// 其他进程中不需要设置背景、深度图、相机参数及光照参数。
@Entry
@Component
struct DepthComponentGlobalOthersExample {
  build() {
    Column() {
      DepthComponent('', {depthSpace: DepthSpaceType.GLOBAL}) {
        Text('Hello World')
          .spatialEffect({
            position: {
              leftTop: { x: -0.355, y: 0.915, z: -1.941 },
              rightTop: { x: 0.483, y: 1.259, z: -2.295 },
              leftBottom: { x: -0.355, y: -0.281, z: -1.941 },
              rightBottom: { x: 0.483, y: 0.063, z: -2.295 }
            },
            occlusionWeight: 0.5
          })
      }
      .width('100%')
      .height('100%')
    }
    .width('100%')
    .height('100%')
  }
}
```
