# HID DDK Development
<!--Kit: Driver Development Kit-->
<!--Subsystem: Driver-->
<!--Owner: @lixinsheng2-->
<!--Designer: @w00373942-->
<!--Tester: @dong-dongzhen-->
<!--Adviser: @w_Machine_cc-->

## Overview

The Human Interface Device (HID) Driver Development Kit (HidDdk) is a toolset that helps you develop HID drivers at the application layer based on the user mode. It provides APIs for accessing HID devices on a host, including creating a HID device, sending events to a device, destroying a device, opening or closing a device, reading and writing a report, and obtaining device information.

The HidDdk can be used to develop drivers for devices that use HID protocol to transfer data over a USB bus, or for devices that use peripheral drivers to create virtual devices to exchange information with non-standard devices.

### Basic Concepts

Before you get started, understand the following concepts:

- **HID**

  HID is a type of hardware device that implements interaction between a person and a computer or another electronic device. The primary function of HID is to convert user input (such as a key, a click, or a movement) into a data signal, and send the signal to a host device (such as a computer, tablet, or game console), so that the user can control and operate the device.

- **DDK**

  A toolkit provided by OpenHarmony for developing drivers for non-standard USB serial port devices based on the peripheral framework.

### Implementation Principles

A non-standard peripheral application obtains the HID device ID by using the peripheral management service, and delivers the ID and the action to the HID device driver application through RPC. The driver application calls the HidDdk API to create and destroy a HID device, send events to a HID device, or obtain and parse packets sent from a HID device. The DDK API uses the HDI service to deliver instructions to the kernel driver, and the kernel driver uses instructions to communicate with the device.

**Figure 1** Principles of invoking the HidDdk

![HID_DDK schematic diagram](figures/ddk-schematic-diagram.png)

## Constraints

- The open APIs of the HidDdk can be used to develop drivers of non-standard HID peripherals.

- The open APIs of the HidDdk can be used only within the lifecycle of **DriverExtensionAbility**.

- To use the open APIs of the HidDdk, you need to declare the matching ACL permissions in **module.json5**, for example, **ohos.permission.ACCESS_DDK_HID**.

## Available APIs

| Name| Description|
| -------- | -------- |
| OH_Hid_CreateDevice(Hid_Device *hidDevice, Hid_EventProperties *hidEventProperties) | Creates a HID device. When the device is no longer required, call **OH_Hid_DestroyDevice** to destroy it.|
| OH_Hid_EmitEvent(int32_t deviceId, const Hid_EmitItem items[], uint16_t length) | Sends an event to a HID device.|
| OH_Hid_DestroyDevice(int32_t deviceId) | Destroys a HID device.|
| int32_t OH_Hid_Init(void) | Initializes the HidDdk.|
| int32_t OH_Hid_Release(void) | Releases the HidDdk.|
| int32_t OH_Hid_Open(uint64_t deviceId, uint8_t interfaceIndex, Hid_DeviceHandle **dev) | Opens the device specified by **deviceId** and **interfaceIndex**.|
| int32_t OH_Hid_Close(Hid_DeviceHandle **dev) | Closes a HID device.|
| int32_t OH_Hid_Write(Hid_DeviceHandle *dev, uint8_t *data, uint32_t length, uint32_t *bytesWritten) | Writes a report to a HID device.|
| int32_t OH_Hid_ReadTimeout(Hid_DeviceHandle *dev, uint8_t *data, uint32_t buffSize, int timeout, uint32_t *bytesRead) | Reads a report from a HID device within the specified time.|
| int32_t OH_Hid_Read(Hid_DeviceHandle *dev, uint8_t *data, uint32_t buffSize, uint32_t *bytesRead) | Reads a report from a HID device in the specified mode. The blocking mode (that is, blocking remains active until data can be read) is used by default. You can call **OH_Hid_SetNonBlocking** to change the mode.|
| int32_t OH_Hid_SetNonBlocking(Hid_DeviceHandle *dev, int nonblock) | Sets the device read mode to non-blocking mode.|
| int32_t OH_Hid_GetRawInfo(Hid_DeviceHandle *dev, Hid_RawDevInfo *rawDevInfo) | Obtains the raw information of a HID device.|
| int32_t OH_Hid_GetRawName(Hid_DeviceHandle *dev, char *data, uint32_t buffSize) | Obtains the raw name of a HID device.|
| int32_t OH_Hid_GetPhysicalAddress(Hid_DeviceHandle *dev, char *data, uint32_t buffSize) | Obtains the physical address of a HID device.|
| int32_t OH_Hid_GetRawUniqueId(Hid_DeviceHandle *dev, uint8_t *data, uint32_t buffSize) | Obtains the raw unique identifier of a HID device.|
| int32_t OH_Hid_SendReport(Hid_DeviceHandle *dev, Hid_ReportType reportType, const uint8_t *data, uint32_t length) | Sends a report to a HID device.|
| int32_t OH_Hid_GetReport(Hid_DeviceHandle *dev, Hid_ReportType reportType, uint8_t *data, uint32_t buffSize) | Obtains a report from a HID device.|
| int32_t OH_Hid_GetReportDescriptor(Hid_DeviceHandle *dev, uint8_t *buf, uint32_t buffSize, uint32_t *bytesRead) | Obtains the report descriptor of a HID device.|

For details about the APIs, see [HidDdk](../../reference/apis-driverdevelopment-kit/capi-hidddk.md).

## How to Develop

### Developing a Basic HID Driver

The following steps you through on how to develop a HID device driver using the HidDdk:

**Adding Dynamic Link Libraries**

Add the following libraries to **CMakeLists.txt**.
```txt
libhid.z.so
```

**Including Header Files**
```c++
#include <hid/hid_ddk_api.h>
#include <hid/hid_ddk_types.h>
```

1. Create a HID device.

   Use **OH_Hid_CreateDevice** in **hid_ddk_api.h** to create a HID device. If the operation is successful, a device ID is returned. If the operation fails, an [HidDdk error code](../../reference/apis-driverdevelopment-kit/capi-hid-ddk-types-h.md#hid_ddkerrcode) is returned.

   <!-- @[driver_hid1_step1](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/DriverDevelopmentKit/UsbDriverDemo/entry/src/main/cpp/inject_thread.cpp) --> 
   
   ``` C++
   Hid_Device hidDevice = {
       .deviceName = deviceName.c_str(),
       .vendorId = 0x6006,
       .productId = 0x6008,
       .version = 1,
       .bustype = BUS_USB
   };
   std::vector<Hid_EventType> eventType = {HID_EV_KEY};
   Hid_EventTypeArray eventTypeArray = {.hidEventType = eventType.data(), .length = (uint16_t)eventType.size()};
   std::vector<Hid_KeyCode> keyCode = {
       HID_KEY_1,          HID_KEY_SPACE,       HID_KEY_BACKSPACE,   HID_KEY_ENTER,     HID_KEY_ESC, HID_KEY_SYSRQ,
       HID_KEY_LEFT_SHIFT, HID_KEY_RIGHT_SHIFT, HID_KEY_VOLUME_DOWN, HID_KEY_VOLUME_UP, HID_KEY_0,   HID_KEY_2,
       HID_KEY_3,          HID_KEY_4,           HID_KEY_5,           HID_KEY_6,         HID_KEY_7,   HID_KEY_8,
       HID_KEY_9,          HID_KEY_A,           HID_KEY_B,           HID_KEY_C,         HID_KEY_D,   HID_KEY_E,
       HID_KEY_F,          HID_KEY_G,           HID_KEY_H,           HID_KEY_I,         HID_KEY_J,   HID_KEY_K,
       HID_KEY_L,          HID_KEY_M,           HID_KEY_N,           HID_KEY_O,         HID_KEY_P,   HID_KEY_Q,
       HID_KEY_R,          HID_KEY_S,           HID_KEY_T,           HID_KEY_U,         HID_KEY_V,   HID_KEY_W,
       HID_KEY_X,          HID_KEY_Y,           HID_KEY_Z,           HID_KEY_DELETE};
   Hid_KeyCodeArray keyCodeArray = {.hidKeyCode = keyCode.data(), .length = (uint16_t)keyCode.size()};
   Hid_EventProperties hidEventProp = {.hidEventTypes = eventTypeArray, .hidKeys = keyCodeArray};
   int deviceId = OH_Hid_CreateDevice(&hidDevice, &hidEventProp);
   ```

2. Send an event to the HID device.

   Call **OH_Hid_EmitEvent** in **hid_ddk_api.h** to send an event to the device with the specified **deviceId**.

   <!-- @[driver_hid1_step2](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/DriverDevelopmentKit/UsbDriverDemo/entry/src/main/cpp/inject_thread.cpp) --> 
   
   ``` C++
   // Send an event to the device identified by the specified deviceId. The event is injected by the physical peripheral through InjectEvent.
   int32_t ret = OH_Hid_EmitEvent(item.first, item.second.data(), (uint16_t)item.second.size());
   if (ret != HID_DDK_SUCCESS) {
       OH_LOG_ERROR(LOG_APP, "OH_Hid_EmitEvent failed, deviceId:%{public}d", item.first);
   }
   ```

3. Release resources.

   Call **OH_Hid_DestroyDevice** in **hid_ddk_api.h** to destroy the device after all requests are processed and before the application exits.

   <!-- @[driver_hid1_step3](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/DriverDevelopmentKit/UsbDriverDemo/entry/src/main/cpp/inject_thread.cpp) --> 
   
   ``` C++
   // Destroy a HID device.
   int32_t res = OH_Hid_DestroyDevice(deviceId);
   ```


### Developing a HID Packet Communication Driver

The following steps you through on how to develop a HID packet communication driver using the HidDdk:

**Adding Dynamic Link Libraries**

Add the following libraries to **CMakeLists.txt**.
```txt
libhid.z.so
```

**Including Header Files**
```c++
#include <hid/hid_ddk_api.h>
#include <hid/hid_ddk_types.h>
```

1. Initialize the HidDdk.

   Call **OH_Hid_Init** in **hid_ddk_api.h** to initialize the HidDdk.

   <!-- @[driver_hid_report_step1](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/DriverDevelopmentKit/HidDriverDemo/entry/src/main/cpp/data_parser.cpp) --> 
   
   ``` C++
   // Initialize the HidDdk.
   int32_t ret = OH_Hid_Init();
   if (ret != HID_DDK_SUCCESS) {
       OH_LOG_ERROR(LOG_APP, "OH_Hid_Init() return failed: %{public}d", ret);
       return ret;
   }
   ```

2. Open the device.

   Call **OH_Hid_Open** in **hid_ddk_api.h** to open the HID device.

   <!-- @[driver_hid_report_step2](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/DriverDevelopmentKit/HidDriverDemo/entry/src/main/cpp/data_parser.cpp) --> 
   
   ``` C++
   uint32_t bInterfaceNum1 = 0x00;
   // Open the HID device specified by deviceId and interfaceIndex1. Generally, it is a /dev/hidraw0 file.
   ret = OH_Hid_Open(deviceID_, bInterfaceNum1, &hid_);
   if (ret != 0) {
       OH_LOG_ERROR(LOG_APP, "Failed to open hid device, interface number:%{public}u ret:%{public}d",
           bInterfaceNum1, ret);
       return ret;
   }
   uint32_t bInterfaceNum2 = 0x01;
   // Open the HID device specified by deviceId and interfaceIndex2. Generally, it is a /dev/hidraw1 file.
   ret = OH_Hid_Open(deviceID_, bInterfaceNum2, &hid2_);
   if (ret != 0) {
       OH_LOG_ERROR(LOG_APP, "Failed to open hid device, interface number:%{public}u ret:%{public}d",
           bInterfaceNum2, ret);
       return ret;
   }
   ```

3. (Optional) Write or send reports from the host to the HID device as data packets.
   - If the report type is **HID_OUTPUT_REPORT** (output report), you can write/send the report in any of the following ways:
     - Call **OH_Hid_Write** in **hid_ddk_api.h** to write an output report to the HID device.

       <!-- @[driver_hid_report_step3_1](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/DriverDevelopmentKit/HidDriverDemo/entry/src/main/cpp/hello.cpp) --> 
       
       ``` C++
       uint32_t bytesWritten;
       // Write a report.
       int32_t ret = OH_Hid_Write(DataParser::GetInstance().getHidObject(), dataBuff, sizeof(dataBuff), &bytesWritten);
       if (ret != HID_DDK_SUCCESS) {
           OH_LOG_ERROR(LOG_APP, "OH_Hid_Write failed. ret: %{public}u", ret);
       }
       ```


     - Call **OH_Hid_SendReport** in **hid_ddk_api.h** to send an output report to the HID device.

       <!-- @[driver_hid_report_step3_2](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/DriverDevelopmentKit/HidDriverDemo/entry/src/main/cpp/hello.cpp) --> 
       
       ``` C++
       // Send an output report.
       int32_t ret = OH_Hid_SendReport(DataParser::GetInstance().getHidObject(), HID_OUTPUT_REPORT, dataBuff,
                                       sizeof(dataBuff));
       if (ret != HID_DDK_SUCCESS) {
           OH_LOG_ERROR(LOG_APP, "OH_Hid_SendReport failed. ret: %{public}u", ret);
       }
       ```


     - If the report type is **HID_FEATURE_REPORT** (feature report), call **OH_Hid_SendReport** in **hid_ddk_api.h** to send a feature report to the HID device.

       <!-- @[driver_hid_report_step3_3](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/DriverDevelopmentKit/HidDriverDemo/entry/src/main/cpp/hello.cpp) --> 
       
       ``` C++
       uint8_t dataBuff[NUM_EIGHT] = { 0x00 };
       string str(hexFormat);
       HexStringToUint8Array(str, dataBuff, sizeof(dataBuff));
       // Send a feature report.
       int32_t ret = OH_Hid_SendReport(DataParser::GetInstance().getHid2Object(), HID_FEATURE_REPORT, dataBuff,
                                       sizeof(dataBuff));
       if (ret != HID_DDK_SUCCESS) {
           OH_LOG_ERROR(LOG_APP, "OH_Hid_SendReport failed. ret: %{public}u", ret);
       }
       ```

4. (Optional) Read reports from the HID device.
   - If the report type is **HID_INPUT_REPORT** (input report), you can read the report in any of the following ways:
     - Use **OH_Hid_SetNonBlocking** in **hid_ddk_api.h** to set the read mode.

       <!-- @[driver_hid_report_step4_1](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/DriverDevelopmentKit/HidDriverDemo/entry/src/main/cpp/hello.cpp) --> 
       
       ``` C++
       // nonblock: 1 (enabled); 0 (disabled)
       ret = OH_Hid_SetNonBlocking(DataParser::GetInstance().getHidObject(), nonblockTag);
       if (ret != HID_DDK_SUCCESS) {
           OH_LOG_ERROR(LOG_APP, "OH_Hid_SetNonBlocking failed. ret: %{public}u", ret);
           return false;
       }
       ```


     - Use **OH_Hid_Read** or **OH_Hid_ReadTimeout** in **hid_ddk_api.h** to read an input report from the HID device in non-blocking or blocking mode.

       <!-- @[driver_hid_report_step4_2](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/DriverDevelopmentKit/HidDriverDemo/entry/src/main/cpp/hello.cpp) --> 
       
       ``` C++
       if (nonblock) {
           ret = OH_Hid_Read(DataParser::GetInstance().getHidObject(), dataBuff, sizeof(dataBuff), &bytesRead);
       } else {
           ret = OH_Hid_ReadTimeout(DataParser::GetInstance().getHidObject(), dataBuff, sizeof(dataBuff),
                                    CONST_TIMEOUT, &bytesRead);
       }
       ```


     - Call **OH_Hid_GetReport** in **hid_ddk_api.h** to obtain an input report from the HID device.

       <!-- @[driver_hid_report_step4_3](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/DriverDevelopmentKit/HidDriverDemo/entry/src/main/cpp/hello.cpp) --> 
       
       ``` C++
       uint8_t dataBuff[NUM_NINE] = { 0x00 };
       // Obtain an input report.
       int32_t ret = OH_Hid_GetReport(DataParser::GetInstance().getHidObject(), HID_INPUT_REPORT, dataBuff,
                                      sizeof(dataBuff));
       if (ret != HID_DDK_SUCCESS) {
           OH_LOG_ERROR(LOG_APP, "OH_Hid_GetReport failed. ret: %{public}u", ret);
           return nullptr;
       }
       ```


     - If the report type is **HID_FEATURE_REPORT** (feature report), call **OH_Hid_GetReport** in **hid_ddk_api.h** to obtain a feature report from a HID device.

       <!-- @[driver_hid_report_step4_4](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/DriverDevelopmentKit/HidDriverDemo/entry/src/main/cpp/hello.cpp) --> 
       
       ``` C++
       uint8_t dataBuff[NUM_EIGHT] = { 0x00 };
       // Specify the report ID.
       dataBuff[0] = 0x07;
       // Obtain a feature report.
       int32_t ret = OH_Hid_GetReport(DataParser::GetInstance().getHid2Object(), HID_FEATURE_REPORT, dataBuff,
                                      sizeof(dataBuff));
       if (ret != HID_DDK_SUCCESS) {
           OH_LOG_ERROR(LOG_APP, "OH_Hid_GetReport failed. ret: %{public}u", ret);
           return nullptr;
       }
       ```

5. (Optional) Obtain the raw device information, raw name, physical address, and raw unique identifier of a HID device.

    Call **OH_Hid_GetRawInfo** in **hid_ddk_api.h** to obtain the raw information about a HID device.<br>Call **OH_Hid_GetRawName** to obtain the raw name of a HID device.<br>Call **OH_Hid_GetPhysicalAddress** to obtain the physical address of a HID device.<br>Call **OH_Hid_GetRawUniqueId** to obtain the raw unique identifier of a HID device. The obtained information can be referenced by applications, for example, displaying device information on the GUI.

   <!-- @[driver_hid_report_step5_1](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/DriverDevelopmentKit/HidDriverDemo/entry/src/main/cpp/hello.cpp) --> 
   
   ``` C++
   Hid_RawDevInfo rawDevInfo;
   int32_t ret = OH_Hid_GetRawInfo(DataParser::GetInstance().getHidObject(), &rawDevInfo);
   if (ret != HID_DDK_SUCCESS) {
       OH_LOG_ERROR(LOG_APP, "OH_Hid_GetRawInfo failed, ret:%{public}d", ret);
       return nullptr;
   }
   ```
   
   <!-- @[driver_hid_report_step5_2](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/DriverDevelopmentKit/HidDriverDemo/entry/src/main/cpp/hello.cpp) --> 
   
   ``` C++
   char dataBuff[DATA_BUFF_SIZE];
   int32_t ret = OH_Hid_GetRawName(DataParser::GetInstance().getHidObject(), dataBuff, sizeof(dataBuff));
   if (ret != HID_DDK_SUCCESS) {
       OH_LOG_ERROR(LOG_APP, "OH_Hid_GetRawName failed, ret:%{public}d", ret);
       return nullptr;
   }
   ```

   <!-- @[driver_hid_report_step5_3](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/DriverDevelopmentKit/HidDriverDemo/entry/src/main/cpp/hello.cpp) --> 
   
   ``` C++
   char dataBuff[DATA_BUFF_SIZE];
   int32_t ret = OH_Hid_GetPhysicalAddress(DataParser::GetInstance().getHidObject(), dataBuff, sizeof(dataBuff));
   if (ret != HID_DDK_SUCCESS) {
       OH_LOG_ERROR(LOG_APP, "OH_Hid_GetPhysicalAddress failed, ret:%{public}d", ret);
       return nullptr;
   }
   ```

   <!-- @[driver_hid_report_step5_4](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/DriverDevelopmentKit/HidDriverDemo/entry/src/main/cpp/hello.cpp) --> 	
   
   ``` C++
   uint8_t dataBuff[NUM_SIXTY_FOUR];
   int32_t ret = OH_Hid_GetRawUniqueId(DataParser::GetInstance().getHidObject(), dataBuff, sizeof(dataBuff));
   if (ret != HID_DDK_SUCCESS) {
       OH_LOG_ERROR(LOG_APP, "OH_Hid_GetRawUniqueId failed, ret:%{public}d", ret);
       return nullptr;
   }
   ```

6. (Optional) Obtain the report descriptor.

   Call **OH_Hid_GetReportDescriptor** in **hid_ddk_api.h** to obtain the HID device report descriptor.

   <!-- @[driver_hid_report_step6](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/DriverDevelopmentKit/HidDriverDemo/entry/src/main/cpp/hello.cpp) --> 
   
   ``` C++
   uint8_t dataBuff[DATA_BUFF_SIZE1];
   uint32_t bytesRead;
   int32_t ret = OH_Hid_GetReportDescriptor(DataParser::GetInstance().getHidObject(), dataBuff, sizeof(dataBuff),
                                            &bytesRead);
   if (ret != HID_DDK_SUCCESS) {
       OH_LOG_ERROR(LOG_APP, "OH_Hid_GetReportDescriptor failed, ret:%{public}d", ret);
       return nullptr;
   }
   ```

7. Close the HID device.

   Call **OH_Hid_Close** in **hid_ddk_api.h** to close the device.

   <!-- @[driver_hid_report_step7](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/DriverDevelopmentKit/HidDriverDemo/entry/src/main/cpp/hello.cpp) --> 
   
   ``` C++
   Hid_DeviceHandle *hid = DataParser::GetInstance().getHidObject();
   int32_t ret1 = OH_Hid_Close(&hid);
   DataParser::GetInstance().UpdateHid(hid);
   ```

8. Release the HidDdk.

   After the HID device is closed, call **OH_Hid_Release** in **hid_ddk_api.h** to release the HidDdk.

   <!-- @[driver_hid_report_step8](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/DriverDevelopmentKit/HidDriverDemo/entry/src/main/cpp/hello.cpp) --> 
   
   ``` C++
   ret1 = OH_Hid_Release();
   if (ret1 != HID_DDK_SUCCESS) {
       OH_LOG_ERROR(LOG_APP, "OH_Hid_Init() return failed: %{public}d", ret1);
   }
   ```
