# 组件介绍
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @fenglinbailu-->
<!--Designer: @lanshouren-->
<!--Tester: @liuli0427-->
<!--Adviser: @Brilliantry_Rui-->

组件（Component）是构建页面的核心，每个组件通过对数据和方法的简单封装，实现独立的可视、可交互功能单元。组件之间相互独立，随取随用，也可以在需求相同的地方重复使用。


开发者还可以通过组件间合理的搭配定义满足业务需求的新组件，减少开发量，自定义组件的开发方法请参见[自定义组件](ui-js-custom-components.md)。


## 组件分类

根据组件的功能，可以分为以下六大类：

<!--Table: 10%; 90%-->
| 组件类型 | 主要组件 |
| -------- | -------- |
| 容器组件 | [badge/apis-arkui/arkui-js/js-components-container-badge.md)、[dialog/apis-arkui/arkui-js/js-components-container-dialog.md)、[div/apis-arkui/arkui-js/js-components-container-div.md)、[form/apis-arkui/arkui-js/js-components-container-form.md)、[list/apis-arkui/arkui-js/js-components-container-list.md)、[list-item/apis-arkui/arkui-js/js-components-container-list-item.md)、[list-item-group/apis-arkui/arkui-js/js-components-container-list-item-group.md)、[panel/apis-arkui/arkui-js/js-components-container-panel.md)、[popup/apis-arkui/arkui-js/js-components-container-popup.md)、[refresh/apis-arkui/arkui-js/js-components-container-refresh.md)、[stack/apis-arkui/arkui-js/js-components-container-stack.md)、[stepper/apis-arkui/arkui-js/js-components-container-stepper.md)、[stepper-item/apis-arkui/arkui-js/js-components-container-stepper-item.md)、[swiper/apis-arkui/arkui-js/js-components-container-swiper.md)、[tabs/apis-arkui/arkui-js/js-components-container-tabs.md)、[tab-bar/apis-arkui/arkui-js/js-components-container-tab-bar.md)、[tab-content/apis-arkui/arkui-js/js-components-container-tab-content.md) |
| 基础组件 | [button/apis-arkui/arkui-js/js-components-basic-button.md)、[chart/apis-arkui/arkui-js/js-components-basic-chart.md)、[divider/apis-arkui/arkui-js/js-components-basic-divider.md)、[image/apis-arkui/arkui-js/js-components-basic-image.md)、[image-animator/apis-arkui/arkui-js/js-components-basic-image-animator.md)、[input/apis-arkui/arkui-js/js-components-basic-input.md)、[label/apis-arkui/arkui-js/js-components-basic-label.md)、[marquee/apis-arkui/arkui-js/js-components-basic-marquee.md)、[menu/apis-arkui/arkui-js/js-components-basic-menu.md)、[option/apis-arkui/arkui-js/js-components-basic-option.md)、[picker/apis-arkui/arkui-js/js-components-basic-picker.md)、[picker-view/apis-arkui/arkui-js/js-components-basic-picker-view.md)、[piece/apis-arkui/arkui-js/js-components-basic-piece.md)、[progress/apis-arkui/arkui-js/js-components-basic-progress.md)、[qrcode/apis-arkui/arkui-js/js-components-basic-qrcode.md)、[rating/apis-arkui/arkui-js/js-components-basic-rating.md)、[richtext/apis-arkui/arkui-js/js-components-basic-richtext.md)、[search/apis-arkui/arkui-js/js-components-basic-search.md)、[select/apis-arkui/arkui-js/js-components-basic-select.md)、[slider/apis-arkui/arkui-js/js-components-basic-slider.md)、[span/apis-arkui/arkui-js/js-components-basic-span.md)、[switch/apis-arkui/arkui-js/js-components-basic-switch.md)、[text/apis-arkui/arkui-js/js-components-basic-text.md)、[textarea/apis-arkui/arkui-js/js-components-basic-textarea.md)、[toolbar/apis-arkui/arkui-js/js-components-basic-toolbar.md)、[toolbar-item/apis-arkui/arkui-js/js-components-basic-toolbar-item.md)、[toggle/apis-arkui/arkui-js/js-components-basic-toggle.md) |
| 媒体组件 | [video/apis-arkui/arkui-js/js-components-media-video.md) |
| 画布组件 | [canvas/apis-arkui/arkui-js/js-components-canvas-canvas.md) |
| 栅格组件 | [grid-container/apis-arkui/arkui-js/js-components-grid-container.md)、[grid-row/apis-arkui/arkui-js/js-components-grid-row.md)、[grid-col/apis-arkui/arkui-js/js-components-grid-col.md) |
| svg组件 | [svg/apis-arkui/arkui-js/js-components-svg.md)、[rect/apis-arkui/arkui-js/js-components-svg-rect.md)、[circle/apis-arkui/arkui-js/js-components-svg-circle.md)、[ellipse/apis-arkui/arkui-js/js-components-svg-ellipse.md)、[path/apis-arkui/arkui-js/js-components-svg-path.md)、[line/apis-arkui/arkui-js/js-components-svg-line.md)、[polyline/apis-arkui/arkui-js/js-components-svg-polyline.md)、[polygon/apis-arkui/arkui-js/js-components-svg-polygon.md)、[text/apis-arkui/arkui-js/js-components-svg-text.md)、[tspan/apis-arkui/arkui-js/js-components-svg-tspan.md)、[textPath/apis-arkui/arkui-js/js-components-svg-textpath.md)、[animate/apis-arkui/arkui-js/js-components-svg-animate.md)、[animateMotion/apis-arkui/arkui-js/js-components-svg-animatemotion.md)、[animateTransform/apis-arkui/arkui-js/js-components-svg-animatetransform.md) |



## 相关实例

针对组件开发，有以下相关实例可供参考：

- [rating组件的使用（JS）（API9）](https://gitcode.com/openharmony/codelabs/tree/master/JSUI/RatingApplication)

- [简易视频播放器（JS）（API9）](https://gitcode.com/openharmony/codelabs/tree/master/Media/VideoOpenHarmony)

- [购物应用（JS）（API9）](https://gitcode.com/openharmony/codelabs/tree/master/JSUI/ShoppingSample)

- [图片常见操作（JS）（API9）](https://gitcode.com/openharmony/codelabs/tree/master/Media/ImageOperation)