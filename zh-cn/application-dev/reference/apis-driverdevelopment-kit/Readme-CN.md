# Driver Development Kit（驱动开发服务）
<!--Kit: Driver Development Kit-->
<!--Subsystem: Driver-->
<!--Owner: @lixinsheng2-->
<!--Designer: @w00373942-->
<!--Tester: @dong-dongzhen-->
<!--Adviser: @w_Machine_cc-->

- ArkTS API<!--driver-development-arkts-->
  - [@ohos.app.ability.DriverExtensionAbility (驱动程序扩展能力)](js-apis-app-ability-driverExtensionAbility.md)
  - [@ohos.driver.deviceManager (外设管理)](js-apis-driver-deviceManager.md)
  <!--Del-->
  - [@ohos.driver.deviceManager (外设管理)(系统接口)](js-apis-driver-deviceManager-sys.md)
  <!--DelEnd-->
  - application
    - [DriverExtensionContext](js-apis-inner-application-driverExtensionContext.md)
- C API<!--driver-development-c-->
  - 模块<!--driver-development-module-->
    - [BaseDdk](capi-baseddk.md)
    - [HidDdk](capi-hidddk.md)
    - [SCSIPeripheralDDK](capi-scsiperipheralddk.md)
    - [UsbDDK](capi-usbddk.md)
    - [SerialDdk](capi-serialddk.md)
  - 头文件<!--driver-development-headerfile-->
    - [ddk_api.h](capi-ddk-api-h.md)
    - [ddk_types.h](capi-ddk-types-h.md)
    - [hid_ddk_api.h](capi-hid-ddk-api-h.md)
    - [hid_ddk_types.h](capi-hid-ddk-types-h.md)
    - [scsi_peripheral_api.h](capi-scsi-peripheral-api-h.md)
    - [scsi_peripheral_types.h](capi-scsi-peripheral-types-h.md)
    - [usb_ddk_api.h](capi-usb-ddk-api-h.md)
    - [usb_ddk_types.h](capi-usb-ddk-types-h.md)
    - [usb_serial_api.h](capi-usb-serial-api-h.md)
    - [usb_serial_types.h](capi-usb-serial-types-h.md)
  - 结构体<!--driver-development-struct-->
    - [DDK_Ashmem](capi-baseddk-ddk-ashmem.md)
    - [Hid_EmitItem](capi-hidddk-hid-emititem.md)
    - [Hid_Device](capi-hidddk-hid-device.md)
    - [Hid_EventTypeArray](capi-hidddk-hid-eventtypearray.md)
    - [Hid_KeyCodeArray](capi-hidddk-hid-keycodearray.md)
    - [Hid_AbsAxesArray](capi-hidddk-hid-absaxesarray.md)
    - [Hid_RelAxesArray](capi-hidddk-hid-relaxesarray.md)
    - [Hid_MscEventArray](capi-hidddk-hid-msceventarray.md)
    - [Hid_EventProperties](capi-hidddk-hid-eventproperties.md)
    - [Hid_RawDevInfo](capi-hidddk-hid-rawdevinfo.md)
    - [Hid_DeviceHandle](capi-hidddk-hid-devicehandle.md)
    - [ScsiPeripheral_DeviceMemMap](capi-scsiperipheralddk-scsiperipheral-devicememmap.md)
    - [ScsiPeripheral_IORequest](capi-scsiperipheralddk-scsiperipheral-iorequest.md)
    - [ScsiPeripheral_Request](capi-scsiperipheralddk-scsiperipheral-request.md)
    - [ScsiPeripheral_Response](capi-scsiperipheralddk-scsiperipheral-response.md)
    - [ScsiPeripheral_TestUnitReadyRequest](capi-scsiperipheralddk-scsiperipheral-testunitreadyrequest.md)
    - [ScsiPeripheral_InquiryRequest](capi-scsiperipheralddk-scsiperipheral-inquiryrequest.md)
    - [ScsiPeripheral_InquiryInfo](capi-scsiperipheralddk-scsiperipheral-inquiryinfo.md)
    - [ScsiPeripheral_ReadCapacityRequest](capi-scsiperipheralddk-scsiperipheral-readcapacityrequest.md)
    - [ScsiPeripheral_CapacityInfo](capi-scsiperipheralddk-scsiperipheral-capacityinfo.md)
    - [ScsiPeripheral_RequestSenseRequest](capi-scsiperipheralddk-scsiperipheral-requestsenserequest.md)
    - [ScsiPeripheral_BasicSenseInfo](capi-scsiperipheralddk-scsiperipheral-basicsenseinfo.md)
    - [ScsiPeripheral_VerifyRequest](capi-scsiperipheralddk-scsiperipheral-verifyrequest.md)
    - [ScsiPeripheral_Device](capi-scsiperipheralddk-scsiperipheral-device.md)
    - [UsbControlRequestSetup](capi-usbddk-usbcontrolrequestsetup.md)
    - [UsbDeviceDescriptor](capi-usbddk-usbdevicedescriptor.md)
    - [UsbConfigDescriptor](capi-usbddk-usbconfigdescriptor.md)
    - [UsbInterfaceDescriptor](capi-usbddk-usbinterfacedescriptor.md)
    - [UsbEndpointDescriptor](capi-usbddk-usbendpointdescriptor.md)
    - [UsbDdkEndpointDescriptor](capi-usbddk-usbddkendpointdescriptor.md)
    - [UsbDdkInterfaceDescriptor](capi-usbddk-usbddkinterfacedescriptor.md)
    - [UsbDdkInterface](capi-usbddk-usbddkinterface.md)
    - [UsbDdkConfigDescriptor](capi-usbddk-usbddkconfigdescriptor.md)
    - [UsbRequestPipe](capi-usbddk-usbrequestpipe.md)
    - [UsbDeviceMemMap](capi-usbddk-usbdevicememmap.md)
    - [Usb_DeviceArray](capi-usbddk-usb-devicearray.md)
    - [UsbSerial_Params](capi-serialddk-usbserial-params.md)
    - [UsbSerial_DeviceHandle](capi-serialddk-usbserial-devicehandle.md)
- 错误码
  - [驱动错误码](errorcode-deviceManager.md)