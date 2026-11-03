# DriverExtensionContext(定义驱动扩展的上下文)

## 使用说明

在使用DriverExtensionContext的功能前，需要通过DriverExtensionAbility子类实例获取。

```ts
 let context: DriverExtensionContext | undefined;
 class EntryAbility extends DriverExtensionAbility {
 onInit() {
 context = this.context; // 获取DriverExtensionContext
 }
 }
 ```

## 汇总

### 类

| 名称 | 说明 |
| --- | --- |
| [DriverExtensionContext](arkts-driverdevelopment-driverextensioncontext-c.md) | DriverExtensionContext模块是DriverExtensionAbility的上下文环境，继承自ExtensionContext。 |
