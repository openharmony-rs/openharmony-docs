# DeviceTypes

设备类型枚举值，可用于校验deviceType的返回值。

**起始版本：** 20

**系统能力：** SystemCapability.Startup.SystemInfo

## TYPE_DEFAULT

```TypeScript
TYPE_DEFAULT = 'default'
```

默认设备。

**起始版本：** 20

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Startup.SystemInfo

## TYPE_PHONE

```TypeScript
TYPE_PHONE = 'phone'
```

手机。

**起始版本：** 20

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Startup.SystemInfo

## TYPE_TABLET

```TypeScript
TYPE_TABLET = 'tablet'
```

平板。

**起始版本：** 20

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Startup.SystemInfo

## TYPE_2IN1

```TypeScript
TYPE_2IN1 = '2in1'
```

PC/2in1。

**起始版本：** 20

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Startup.SystemInfo

## TYPE_TV

```TypeScript
TYPE_TV = 'tv'
```

智慧屏。

**起始版本：** 20

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Startup.SystemInfo

## TYPE_WEARABLE

```TypeScript
TYPE_WEARABLE = 'wearable'
```

智能手表。

**起始版本：** 20

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Startup.SystemInfo

## TYPE_CAR

```TypeScript
TYPE_CAR = 'car'
```

车机。

**起始版本：** 20

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Startup.SystemInfo

**示例**

```TypeScript
let deviceTypesInfoDefault: string = deviceInfo.DeviceTypes.TYPE_DEFAULT;
// 输出结果：the value of the DeviceTypes is :default
console.info('the value of the DeviceTypes is :' + deviceTypesInfoDefault);

let deviceTypesInfoPhone: string = deviceInfo.DeviceTypes.TYPE_PHONE;
// 输出结果：the value of the DeviceTypes is :phone
console.info('the value of the DeviceTypes is :' + deviceTypesInfoPhone);

let deviceTypesInfoTablet: string = deviceInfo.DeviceTypes.TYPE_TABLET;
// 输出结果：the value of the DeviceTypes is :tablet
console.info('the value of the DeviceTypes is :' + deviceTypesInfoTablet);

let deviceTypesInfo2IN1: string = deviceInfo.DeviceTypes.TYPE_2IN1;
// 输出结果：the value of the DeviceTypes is :2in1
console.info('the value of the DeviceTypes is :' + deviceTypesInfo2IN1);

let deviceTypesInfoTV: string = deviceInfo.DeviceTypes.TYPE_TV;
// 输出结果：the value of the DeviceTypes is :tv
console.info('the value of the DeviceTypes is :' + deviceTypesInfoTV);

let deviceTypesInfoWearable: string = deviceInfo.DeviceTypes.TYPE_WEARABLE;
// 输出结果：the value of the DeviceTypes is :wearable
console.info('the value of the DeviceTypes is :' + deviceTypesInfoWearable);

let deviceTypesInfoCar: string = deviceInfo.DeviceTypes.TYPE_CAR;
// 输出结果：the value of the DeviceTypes is :car
console.info('the value of the DeviceTypes is :' + deviceTypesInfoCar);
```
