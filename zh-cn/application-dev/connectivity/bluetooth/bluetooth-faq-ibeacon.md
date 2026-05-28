# iBeacon数据包解析过滤

## iBeacon概述
BLE的通信包括两个主要部分：advertising和connecting，iBeacon依赖于advertising实现。
iBeacon是苹果公司于2013年推出的基于蓝牙低功耗（BLE）的微定位协议。它通过周期性广播包含唯一标识符（UUID、Major、Minor）的数据包，使智能设备（如手机）在接受信号后，结合信号强度（RSSI）估算距离、实现室内定位、场景触发等功能。其优势在于低功耗、低成本，广泛应用于零售导购、博物馆导览、仓储物流等场景，成为物联网中“近场交互”的重要技术。

## 使用nrf connect调试助手模拟一个iBeacon设备
**1、添加模拟广播设备**<br>
如下图所示，点击右下角加号添加一个模拟广播设备。

**2、填写广播设备名称和数据内容**<br>
添加【Manufacturer Data】数据内容如下：
1. 16bit Company Identifier 填写苹果公司 0x004C
2. Data 填写 0x 02 15 00 11 22 33 44 55 66 77 88 99 AA BB CC DD EE FF 11 22 33 44 55 其中 00 11 ~ EE FF 总共16字节，代表模拟Beacon设备的唯一标识符（用16字节UUID表示，和蓝牙service uuid格式一样，但标识的对象不同，这里标识的是设备，蓝牙service uuid标识的是蓝牙服务）

**3、勾选可扫描和可连接选项**<br>
添加完数据后，勾选设备可扫描和可连接选项，打开广播即可。最后完成效果如下图中mybeacon设备所示，00 11 ~ EE FF共16字节会被自动识别为Beacon设备的UUID标识符。

**4、广播包内容**<br>
实际广播包内容如下图所示，中间16字节为Beacon的UUID

## Beacon设备扫描过滤器配置
```ts
let manufactureId = 0x004C; //16位id
let manufactureData: Uint8Array = new Uint8Array([0xFF, 0xFF, 0x00, 0x11, 0x22, 0x33, 0x44, 0x55, 0x66, 0x77,
    0x88, 0x99, 0xAA, 0xBB, 0xCC, 0xDD, 0xEE, 0xFF]);
let manufactureDataMask: Uint8Array = new Uint8Array([0x00, 0x00, 0xFF, 0xFF, 0xFF, 0xFF, 0xFF, 0xFF, 0xFF,
    0xFF, 0xFF, 0xFF, 0xFF, 0xFF, 0xFF, 0xFF, 0xFF, 0xFF]);

let filter1: ble.ScanFilter = {
    manufactureId: manufactureId,
    manufactureData: manufactureData,
    manufactureDataMask: manufactureDataMask.buffer
};
let filterArry: Array<ble.ScanFilter> = new Array();
filterArry.push(filter1);
let scanOption: ble.ScanOptions = {
    "dutyMode": 2,
    "interval": 0,
    "matchMode": 1
};
try {
    ble.startBLEScan(filterArry, scanOption);
} catch (err) {
    console.error(`errCode: ${err.code}, errMessage: ${err.message}`);
}
```