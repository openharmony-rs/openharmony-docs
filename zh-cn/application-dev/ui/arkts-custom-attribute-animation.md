# 自定义属性动画
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @CCFFWW-->
<!--Designer: @CCFFWW-->
<!--Tester: @lxl007-->
<!--Adviser: @HelloCrease-->


属性动画是可动画属性的参数值发生变化时，引起UI上产生的连续视觉效果。当参数值发生连续变化，且设置到可以引起UI发生变化的属性接口上时，就可以实现属性动画。


ArkUI提供[@AnimatableExtend装饰器](../ui/state-management/arkts-animatable-extend.md)，用于自定义可动画属性接口。由于参数的数据类型必须具备一定程度的连续性，自定义可动画属性接口的参数类型仅支持number类型和实现[AnimatableArithmetic\<T>接口](../ui/state-management/arkts-animatable-extend.md#animatablearithmetict接口说明)的自定义类型。通过自定义可动画属性接口和可动画数据类型，在使用animateTo或animation执行动画时，通过逐帧回调函数修改不可动画属性接口的值，能够让不可动画属性接口实现动画效果。也可通过逐帧回调函数每帧修改可动画属性的值，实现逐帧布局的效果。


## 使用number数据类型和\@AnimatableExtend装饰器改变Text组件宽度实现逐帧布局的效果


<!-- @[Animation_AnimatableProperty](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/Animation/entry/src/main/ets/pages/animatableProperty/template1/Index.ets) -->


![zh-cn_image_0000001600119626](figures/zh-cn_image_0000001600119626.gif)


## 使用自定义数据类型和\@AnimatableExtend装饰器改变图形形状


<!-- @[Animation_AnimatableProperty](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/Animation/entry/src/main/ets/pages/animatableProperty/template2/Index.ets) -->



![zh-cn_image_0000001592669598](figures/zh-cn_image_0000001592669598.gif)

## 相关实例

针对自定义属性动画开发，有以下相关实例可供参考：

- [自定义下拉刷新动画（ArkTS）（API9）](https://gitcode.com/openharmony/codelabs/tree/master/ETSUI/AnimateRefresh)