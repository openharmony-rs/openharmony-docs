# Drawing

## 概述

Drawing模块提供包括2D图形渲染、文字绘制和图片显示等功能函数。<br>本模块采用屏幕物理像素单位px。<br>本模块为单线程模型策略，需要调用方自行管理线程安全和上下文状态的切换。

**起始版本：** 8
## 文件汇总

| 名称 | 描述 |
| -- | -- |
| [drawing_lattice.h](capi-drawing-lattice-h.md) | 声明与矩形网格对象相关的函数。矩形网格（Lattice）用于将图像划分为固定区域和可缩放区域，解决图像缩放时关键区域变形的问题，保持关键区域清晰不变形的同时实现其余区域的灵活缩放。固定区域在目标网格足够大时以原始大小绘制，目标网格太小时按比例缩小以适应目标网格，其余区域缩放以适应剩余空间。<br>本模块为单线程模型策略，需要调用方自行管理线程安全和上下文状态的切换。 |
| [drawing_point.h](capi-drawing-point-h.md) | 文件中定义了与坐标点相关的功能函数，支持创建、获取、设置、取反、偏移及销毁坐标点对象等操作，便于在2D图形绘制中对坐标点进行管理与变换。<br>本模块为单线程模型策略，需要调用方自行管理线程安全和上下文状态的切换。 |
| [drawing_round_rect.h](capi-drawing-round-rect-h.md) | 文件中定义了与圆角矩形相关的功能函数。<br>本模块为单线程模型策略，需要调用方自行管理线程安全和上下文状态的切换。 |
| [drawing_shadow_layer.h](capi-drawing-shadow-layer-h.md) | 声明与绘图模块中的阴影层对象相关的函数，用于创建和销毁阴影层对象。阴影层用于为绘图内容添加阴影效果，支持通过设置模糊半径、偏移量和颜色来创建阴影层，适用于需要为图形或文本添加阴影渲染的场景。<br>本模块为单线程模型策略，需要调用方自行管理线程安全和上下文状态的切换。 |
| [drawing_text_line.h](capi-drawing-text-line-h.md) | 提供获取文本行内的字符位置、获取渲染单元信息和按行截断等功能。 |
| [drawing_color_space.h](capi-drawing-color-space-h.md) | 声明与绘图模块中的颜色空间对象相关的函数。颜色空间用于定义颜色的解释和映射方式，确保图像在不同显示设备上的一致性呈现。本文件提供创建标准颜色空间（sRGB）和线性颜色空间（sRGB Linear）的函数，以及销毁颜色空间对象并回收内存的函数，用于图像渲染和色彩管理等场景。<br>本模块为单线程模型策略，需要调用方自行管理线程安全和上下文状态的切换。 |
| [drawing_path_iterator.h](capi-drawing-path-iterator-h.md) | 声明与路径操作迭代器对象相关的函数。路径操作迭代器用于遍历路径中的操作指令（如移动、连线、贝塞尔曲线、闭合等），迭代器从路径起始位置依次遍历各操作指令，内部维护当前遍历位置。支持创建和销毁迭代器、判断是否还有下一个操作、读取下一个操作并将迭代器前移、查看下一个操作但不移动迭代器。通过迭代器可在不修改原始路径的情况下逐条读取路径操作信息。<br>本模块为单线程模型策略，需要调用方自行管理线程安全和上下文状态的切换。 |
| [drawing_text_run.h](capi-drawing-text-run-h.md) | 提供字体渲染单元的相关接口，比如绘制功能、获取排版边界功能等。 |
| [drawing_text_global.h](capi-drawing-text-global-h.md) | 提供文本全局信息的相关接口，如设置文本渲染高对比度模式、未定义字型的呈现方式等。 |
| [drawing_pen.h](capi-drawing-pen-h.md) | 文件中定义了与画笔相关的功能函数。<br>本模块为单线程模型策略，需要调用方自行管理线程安全和上下文状态的切换。 |
| [drawing_bitmap.h](capi-drawing-bitmap-h.md) | 文件中定义了位图相关的功能函数，支持位图的创建与销毁、初始化宽高与像素格式、获取位图宽度、高度、行字节数、像素存储格式、透明度分量、像素地址及位图信息，以及将位图像素数据读取到指定内存缓冲区等操作。<br>本模块为单线程模型策略，需要调用方自行管理线程安全和上下文状态的切换。 |
| [drawing_matrix.h](capi-drawing-matrix-h.md) | 文件中定义了矩阵的创建、拷贝、变换（旋转、缩放、平移、倾斜）、查询（判断相等、判断单位矩阵、获取元素值）和映射等功能函数。<br>本模块为单线程模型策略，需要调用方自行管理线程安全和上下文状态的切换。 |
| [drawing_memory_stream.h](capi-drawing-memory-stream-h.md) | 文件中定义了与内存流相关的功能函数，支持基于内存数据创建和销毁内存流对象。内存流支持数据拷贝或直接引用两种访问方式。<br>本模块为单线程模型策略，需要调用方自行管理线程安全和上下文状态的切换。 |
| [drawing_canvas.h](capi-drawing-canvas-h.md) | 文件中定义了画布（Canvas）的创建、绑定、绘制、变换、裁剪及状态管理等功能函数。画布是ArkGraphics 2D中用于2D图形渲染的核心组件，支持绘制形状、路径、图像、像素图和文字，并提供画布变换（旋转、平移、缩放、倾斜）、裁剪、矩阵操作等能力。<br>画布自带一个默认画刷，画刷为黑色、开启抗锯齿、不具备其他任何样式，当且仅当画布中主动设置的画刷和画笔都不存在时生效。<br>本模块为单线程模型策略，需要调用方自行管理线程安全和上下文状态的切换。 |
| [drawing_error_code.h](capi-drawing-error-code-h.md) | 声明与绘图模块中的错误码相关的函数。<br>本模块为单线程模型策略，需要调用方自行管理线程安全和上下文状态的切换。 |
| [drawing_gpu_context.h](capi-drawing-gpu-context-h.md) | 声明与绘图模块中的图形处理器上下文对象相关的函数，用于创建、配置和销毁图形处理器上下文对象，为绘图模块提供图形处理器加速渲染所需的上下文环境。<br>本模块为单线程模型策略，需要调用方自行管理线程安全和上下文状态的切换。 |
| [drawing_filter.h](capi-drawing-filter-h.md) | 声明与绘图模块中的滤波器对象相关的函数。<br>本模块为单线程模型策略，需要调用方自行管理线程安全和上下文状态的切换。 |
| [drawing_text_blob.h](capi-drawing-text-blob-h.md) | 文件中定义了与文字相关的功能函数。<br>本模块为单线程模型策略，需要调用方自行管理线程安全和上下文状态的切换。 |
| [drawing_surface.h](capi-drawing-surface-h.md) | 本文件定义了与surface相关的功能函数，包括surface的创建、销毁和使用等。surface对象用于管理画布绘制的内容，支持通过图形处理器上下文创建离屏surface和与屏幕窗口绑定的surface。<br>本模块为单线程模型策略，需要调用方自行管理线程安全和上下文状态的切换。 |
| [drawing_brush.h](capi-drawing-brush-h.md) | 文件中定义了与画刷相关的功能函数。<br>本模块为单线程模型策略，需要调用方自行管理线程安全和上下文状态的切换。 |
| [drawing_mask_filter.h](capi-drawing-mask-filter-h.md) | 声明与绘图模块中的对象相关的函数。<br>本模块为单线程模型策略，需要调用方自行管理线程安全和上下文状态的切换。 |
| [drawing_text_declaration.h](capi-drawing-text-declaration-h.md) | 提供2D绘制文本相关的数据结构声明。 |
| [drawing_text_font_descriptor.h](capi-drawing-text-font-descriptor-h.md) | 定义了字体信息的相关接口，比如获取字体信息、查找和匹配指定字体、读取字体描述符属性以及获取字体的Unicode码和字体数量等。 |
| [drawing_record_cmd.h](capi-drawing-record-cmd-h.md) | 文件中定义了与录制指令对象相关的功能函数。用于录制和回放绘制指令序列，支持创建录制画布、记录绘制操作、生成可回放的指令对象。<br>本模块为单线程模型策略，需要调用方自行管理线程安全和上下文状态的切换。 |
| [drawing_font_collection.h](capi-drawing-font-collection-h.md) | 定义绘制模块中与字体集相关的函数，用于管理文本排版所需的字体资源，支持创建独立的或可共享的字体集对象，满足不同场景下的文本排版需求。通过字体集对象，可实现自定义字体加载、系统字体管理、字体缓存清理等功能。 |
| [drawing_sampling_options.h](capi-drawing-sampling-options-h.md) | 文件中定义了与采样选项相关的功能函数，用于创建、拷贝和销毁采样选项对象，以及指定图像采样时的过滤模式和纹理采样时的多级渐远纹理模式。<br>本模块为单线程模型策略，需要调用方自行管理线程安全和上下文状态的切换。 |
| [drawing_text_lineTypography.h](capi-drawing-text-lineTypography-h.md) | 提供排版行相关的接口，如获取指定位置处开始可以排版的字符个数等函数。 |
| [drawing_pixel_map.h](capi-drawing-pixel-map-h.md) | 声明与绘图模块中的像素图对象相关的函数。支持从图像框架定义的像素图对象中获取本模块定义的像素图对象，支持解除两者之间的关系。<br>本模块为单线程模型策略，需要调用方自行管理线程安全和上下文状态的切换。 |
| [drawing_typeface.h](capi-drawing-typeface-h.md) | 文件中定义了与字形相关的功能函数，支持创建默认字形、从文件或内存流创建指定字形、通过字型参数自定义字体的可变维度，以及查询字形的粗体、斜体属性等。<br>不同的平台有自己的默认字形，也可以从ttf文件解析出三方指定字形，如宋体、黑体字形等。<br>本模块为单线程模型策略，需要调用方自行管理线程安全和上下文状态的切换。 |
| [drawing_color.h](capi-drawing-color-h.md) | 文件中定义了与颜色相关的功能函数。<br>本模块为单线程模型策略，需要调用方自行管理线程安全和上下文状态的切换。 |
| [drawing_shader_effect.h](capi-drawing-shader-effect-h.md) | 声明与绘图模块中的着色器对象相关的函数，用于创建单色、线性渐变、径向渐变、扇形渐变、两点锥形渐变、图像和像素图等类型的着色器效果，按指定混合模式叠加两个着色器生成新的着色器效果；同时提供销毁着色器对象的函数，回收该对象占用的内存。<br>本模块为单线程模型策略，需要调用方自行管理线程安全和上下文状态的切换。 |
| [drawing_font.h](capi-drawing-font-h.md) | 文件中定义了与字体相关的功能函数。<br>本模块为单线程模型策略，需要调用方自行管理线程安全和上下文状态的切换。 |
| [drawing_rect.h](capi-drawing-rect-h.md) | 文件中定义了与矩形相关的功能函数。<br>本模块为单线程模型策略，需要调用方自行管理线程安全和上下文状态的切换。 |
| [drawing_types.h](capi-drawing-types-h.md) | 文件中定义了用于绘制2D图形的数据类型，包括画布、画笔、画刷、位图和路径。这些数据类型提供了2D图形绘制能力，适用于需要在画布上绑定画笔和画刷绘制各种形状、图片和文字的场景，可以灵活定义路径和位图，帮助开发者高效实现自定义图形绘制、图像处理等功能，满足复杂的2D图形绘制需求。<br>本模块为单线程模型策略，需要调用方自行管理线程安全和上下文状态的切换。 |
| [drawing_font_mgr.h](capi-drawing-font-mgr-h.md) | 文件中定义了与系统字体管理相关的功能函数，用于匹配与获取系统中预置的字体。OH_Drawing_FontMgr（字体管理器）管理系统中预置的字体家族，每个字体家族对应一个字体样式集[OH_Drawing_FontStyleSet](capi-drawing-oh-drawing-fontstyleset.md)，每个样式集中包含多个字型对象[OH_Drawing_Typeface](capi-drawing-oh-drawing-typeface.md)。 |
| [drawing_text_typography.h](capi-drawing-text-typography-h.md) | 定义绘制模块中排版相关的函数。 |
| [drawing_path.h](capi-drawing-path-h.md) | 文件中定义了与自定义路径相关的功能函数，能够高效构建复杂几何路径、支持SVG数据交换实现跨平台兼容，并通过配对创建与销毁机制保障内存安全。主要支持以下能力： |
| [drawing_color_filter.h](capi-drawing-color-filter-h.md) | 声明与绘图模块中的颜色滤波器对象相关的函数。支持创建混合模式、组合、矩阵、伽马转换、亮度和光照等多种颜色滤波器效果，适用于图像渲染中的色彩调整与特效处理场景。<br>本模块为单线程模型策略，需要调用方自行管理线程安全和上下文状态的切换。 |
| [drawing_register_font.h](capi-drawing-register-font-h.md) | 定义绘制模块中字体管理器相关的函数，提供自定义字体的注册、注销以及字体格式检测能力，支持ttf、otf、ttc和otc等多种字体文件格式。 |
| [drawing_image.h](capi-drawing-image-h.md) | 文件中定义了与图片相关的功能函数。<br>本模块为单线程模型策略，需要调用方自行管理线程安全和上下文状态的切换。 |
| [drawing_image_filter.h](capi-drawing-image-filter-h.md) | 声明与绘图模块中的图像滤波器对象相关的函数。支持创建模糊、颜色变换、偏移、基于着色器等多种图像滤波器效果，并支持销毁滤波器对象，适用于图像处理和视觉特效增强的场景。<br>本模块为单线程模型策略，需要调用方自行管理线程安全和上下文状态的切换。 |
| [drawing_path_effect.h](capi-drawing-path-effect-h.md) | 文件中定义了与路径效果相关的功能函数。路径效果是对绘制路径进行几何变换的效果处理机制，在路径绘制到画布之前对路径的几何形状进行修改，例如将尖角变为圆角、将连续路径变为虚线等。多个路径效果可以通过组合（按顺序依次应用）或叠加（各自独立应用后合并结果）的方式一起使用。支持创建组合路径效果、圆角路径效果、虚线路径效果、打散路径效果、叠加路径效果等。<br>本模块为单线程模型策略，需要调用方自行管理线程安全和上下文状态的切换。 |
| [drawing_region.h](capi-drawing-region-h.md) | 定义了与区域相关的功能函数，包括区域的创建，边界设置和销毁等。<br>本模块为单线程模型策略，需要调用方自行管理线程安全和上下文状态的切换。 |
