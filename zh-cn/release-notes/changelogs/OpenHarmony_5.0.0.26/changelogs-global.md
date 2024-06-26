# 全球化变更说明

## cl.global.1 深色模式默认行为变更

**访问级别**

其他

**变更原因**

未适配深色模式的应用较多，为了保证用户在深色模式下的应用使用体验，系统新增判断规则，如果应用完全没有深色资源且没有调用setColorMode接口指定深浅色，那么系统内置组件也不会进行反色。

**变更影响**

该变更为非兼容性变更。会影响完全没有深色资源且未调用setColorMode接口指定深浅色的应用，这些应用在深色模式下系统内置组件也不会进行反色。

**起始 API Level**

9

**变更发生版本**

从OpenHarmony SDK 5.0.0.26 版本开始。

**变更的接口/组件**

变更前： 系统内置组件都跟随设置应用内的深色模式开关自动切换深浅色。

变更后： 系统内置组件仅在应用内含有深色资源的情况下或者使用setColorMode接口指定跟随系统的条件下切换深浅色。

**适配指导**

默认效果变更：如果您的应用全部都是由系统控件/系统颜色开发完成，且想要跟随系统切换深浅色模式，请参考下例修改您的代码来保证应用体验。

```typescript
onCreate(): void {
  this.context.getApplicationContext().setColorMode(ConfigurationConstant.ColorMode.COLOR_MODE_NOT_SET);
}
```

