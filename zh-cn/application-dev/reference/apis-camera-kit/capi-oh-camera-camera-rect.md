# Camera_Rect
<!--Kit: Camera Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @qano-->
<!--Designer: @leo_ysl-->
<!--Tester: @xchaosioda-->
<!--Adviser: @w_Machine_cc-->

```c
typedef struct Camera_Rect {...} Camera_Rect
```

## 概述

矩形定义，返回的检测点坐标系以设备充电口在右侧时的横向设备方向为基准。该坐标系左上角为（0，0），右下角为（1，1），其中（topLeftX，topLeftY）表示矩形区域的左上角坐标，width和height分别表示矩形区域的宽和高。因此在实际使用中根据业务诉求需要裁剪或者选择人脸区域时，必须将矩形区域的x坐标和y坐标分别乘以实际相机预览输出流的宽和高，即可得到裁剪后的人脸矩形区域。

实际预览流的宽高指的是相机输出流的分辨率，请参考[profile](arkts-apis-camera-i.md#profile)中的size。

预览流的数据获取请参考[预览流二次处理(C/C++)](../../media/camera/native-camera-preview-imageReceiver.md)。

**起始版本：** 11

**相关模块：** [OH_Camera](capi-oh-camera.md)

**所在头文件：** [camera.h](capi-camera-h.md)

## 汇总

### 成员变量

| 名称 | 描述 |
| -- | -- |
| int32_t topLeftX | 左上角的X坐标，范围[0, 1]。 |
| int32_t topLeftY | 左上角的Y坐标，范围[0, 1]。 |
| int32_t width | 矩形宽度，范围[0, 1]。 |
| int32_t height | 矩形高度，范围[0, 1]。 |


