# ArkUI指南配套示例代码
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @oh_wangxk-->
<!--Designer: @wulong158-->
<!--Tester: @LiTongguan2026-->
<!--Adviser: @ge-yafang-->

# 窗口与屏幕管理

| 场景分类 | Sample名称 | 语言 | 场景介绍 |
| -------- | -------- | -------- | -------- |
| 屏幕属性查询及状态监听 | [DisplayBasicSample](https://gitcode.com/openharmony/applications_app_samples/tree/master/code/DocsSample/ArkUISample/DisplayBasicSample) | ArkTS | 使用@ohos.display模块获取默认屏幕及全部屏幕的属性信息（分辨率、像素密度、刷新率、挖孔信息、截屏、录屏状态等），并监听屏幕插拔、旋转、分辨率、刷新率等状态变化以及折叠设备的折叠状态变化。 |
| 扩展屏坐标转换 | [DisplayBasicSample](https://gitcode.com/openharmony/applications_app_samples/tree/master/code/DocsSample/ArkUISample/DisplayBasicSample) | ArkTS | 查询扩展模式下各屏幕的显示模式（主屏/扩展屏）并监听其变化，获取屏幕在全局坐标系中的位置，实现全局坐标与相对坐标的相互转换，并判断全局坐标所在的屏幕。 |
| 显示大小缩放系数（Density）适配 | [WindowDensitySample](https://gitcode.com/openharmony/applications_app_samples/tree/master/code/DocsSample/ArkUISample/ArkUIWindowSamples/WindowDensitySample) | ArkTS | 使用Window接口查询并监听窗口所在屏幕的Density信息，演示主窗口Density的三种跟随策略（默认Density、系统Density、自定义Density）及窗口跨屏移动后的Density适配。 |
| 屏幕属性查询及状态监听 | [NativeDisplayBasicSample](https://gitcode.com/openharmony/applications_app_samples/tree/master/code/DocsSample/ArkUISample/NativeDisplayBasicSample) | C/C++ | 使用OH_DisplayManager查询屏幕Rotation、挖孔信息等基础属性，监听屏幕状态变化以及折叠设备的折叠状态变化。 |
