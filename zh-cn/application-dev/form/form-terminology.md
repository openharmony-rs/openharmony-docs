# 术语
<!--Kit: Form Kit-->
<!--Subsystem: Ability-->
<!--Owner: @Qian-Win-->
<!--Designer: @cx983299475-->
<!--Tester: @mahailong123456-->
<!--Adviser: @HelloShuo-->

## A

- ### ArkTS卡片

  基于ArkTS声明式开发范式语言开发的服务卡片。相较于JS卡片，ArkTS卡片支持在卡片中运行逻辑代码，支持属性动画、显式动画、Canvas画布组件自定义绘制等能力，统一了卡片和应用页面的开发范式，可以复用应用页面的布局到卡片中，提供更丰富的交互体验。

## D

- ### 动态卡片

  ArkTS卡片的一种类型，除了支持UI组件和布局能力外，还支持通用事件能力和自定义动效能力，允许在卡片中运行逻辑代码。适用于有复杂业务逻辑和交互的场景，如卡片页面图片刷新、内容刷新等。通过postCardAction接口实现卡片与应用间的router、message和call三种事件交互。

- ### 独立包方式

  ArkTS卡片创建方式之一，卡片UI和应用代码在不同module内，最终编译产物分为独立的卡片包和应用包。从API version 20开始支持，便于卡片和应用独立迭代更新，但需注意保持应用包和卡片包版本号一致。

## F

- ### Form Kit；卡片开发服务

  提供在桌面上嵌入显示应用信息的开发框架和API的Kit。支持将应用内用户关注的重要信息或常用操作抽取到服务卡片上，通过将卡片添加到桌面实现信息展示、服务直达的便捷体验。支持ArkTS卡片（推荐）和JS卡片两种开发范式，同时支持动态卡片、静态卡片和互动卡片三种卡片类型。

- ### FormBindingData；卡片数据绑定类

  用于卡片数据绑定的对象类，包含卡片要展示的数据。通过formBindingData.createFormBindingData接口创建，可以传入包含若干键值对的Object或JSON格式字符串。支持图片数据传递，通过'formImages'标识图片标识与文件描述符的键值对。

- ### FormDimension；卡片尺寸

  定义卡片外观规格的枚举类型。包括多种尺寸规格，如1×2、2×2、2×4、4×4、1×1、6×4等。不同尺寸对应不同的卡片形态，开发者在form_config.json配置文件中通过supportDimensions和defaultDimension字段配置卡片支持的尺寸和默认尺寸。

- ### FormEditExtensionAbility；卡片编辑扩展模块

  提供卡片编辑功能的ExtensionAbility组件，继承自UIExtensionAbility。从API version 18开始支持，用于实现卡片编辑页面的功能，配合FormEditExtensionContext上下文环境使用，支持半模态卡片编辑页的开发。

- ### FormEditExtensionContext；卡片编辑扩展上下文

  FormEditExtensionAbility的上下文环境，继承自UIExtensionContext。提供FormEditExtensionAbility具有的接口和能力，用于卡片编辑功能实现过程中的上下文信息获取和操作。

- ### FormExtensionAbility；卡片扩展模块

  卡片提供方的核心ExtensionAbility组件，提供卡片创建、销毁、刷新等生命周期回调接口。包含onAddForm、onUpdateForm、onRemoveForm、onFormEvent等生命周期方法，卡片提供方需要实现这些接口来完成卡片的生命周期管理。创建后10秒内无操作将会被清理。

- ### FormExtensionContext；卡片扩展上下文

  FormExtensionAbility的上下文环境，继承自ExtensionContext。提供FormExtensionAbility具有的接口和能力，主要用于查询所属FormExtensionAbility的信息、Module的配置信息以及HAP包的信息，开发者可根据业务需求使用对应的信息。

- ### FormInfo；卡片配置信息

  描述卡片配置信息的对象类型，包含卡片所属包名、模块名、Ability名、卡片名称、描述、类型、尺寸规格、更新周期、是否默认卡片等属性。通过formProvider.getFormsInfo接口获取，用于查询和管理卡片的配置信息。

- ### FormLocation；卡片位置

  定义卡片当前位置的枚举类型。包括桌面、卡片中心、卡片管理器等位置，用于标识卡片当前所在的具体场景位置，从API version 20开始支持。

- ### FormState；卡片状态

  定义卡片状态的枚举类型。包括UNKNOWN（未知状态）、DEFAULT（默认状态）、READY（就绪状态）三种状态，用于标识卡片的当前状态信息。

- ### formBindingData；卡片数据绑定模块

  提供卡片数据绑定能力的模块。主要功能是创建FormBindingData对象，用于卡片数据的绑定和传递。通过createFormBindingData接口创建卡片要展示的数据对象，支持包含若干键值对的Object或JSON格式字符串。

- ### formInfo；卡片信息模块

  提供卡片信息和状态等相关类型和枚举的模块。包含FormInfo、FormState、FormDimension、FormLocation、FormParam等类型定义，用于卡片信息的描述、状态标识、尺寸定义和参数传递。

- ### formProvider；卡片提供方模块

  提供卡片提供方能力的模块。主要功能包括获取卡片信息、更新卡片、设置卡片下一次更新时间等。提供updateForm、setFormNextRefreshTime、getFormsInfo、requestOverflow、cancelOverflow、getFormRect等接口，用于卡片数据更新、刷新控制、信息查询、互动卡片动效请求等操作。

## G

- ### 共包方式

  ArkTS卡片创建方式之一，卡片UI和应用代码在同一个module内，最终编译产物在同一个HAP包内。便于开发调试，是卡片开发的传统方式。

## J

- ### JS卡片

  基于类Web范式（HML+CSS+JSON）语言开发的服务卡片。支持FA模型和Stage模型两种应用模型，但不支持自定义动效、自定义绘制和逻辑代码执行，能力相对ArkTS卡片较为基础。

- ### 静态卡片

  ArkTS卡片的一种类型，仅支持UI组件和布局能力，通过FormLink组件实现与应用间的交互。卡片渲染服务将卡片内容渲染完毕后，卡片使用方会使用最后一帧渲染的数据作为静态图片显示，并释放该卡片的所有运行资源以节省内存。适用于展示静态信息（UI相对固定）的场景，功能简单但可以有效控制内存开销。

## K

- ### 卡片管理服务

  操作系统内管理整机卡片信息的系统服务，作为卡片提供方和使用方的桥梁。向卡片使用方提供卡片信息查询、添加、删除等能力，同时向卡片提供方提供卡片被添加、被删除、刷新、点击事件等通知能力，还提供卡片对象的管理与使用以及卡片周期性刷新等能力。

- ### 卡片渲染服务

  用于管理卡片渲染实例的系统服务，渲染实例与卡片使用方的卡片组件一一绑定。根据form_config.json配置的卡片信息运行widget.abc文件的卡片页面代码进行渲染，并将渲染后的数据发送至卡片使用方对应的卡片组件。同一卡片提供方的渲染实例运行在同一个ArkTS虚拟机运行环境中，不同卡片提供方的渲染实例运行在不同的ArkTS虚拟机运行环境中，实现资源与状态隔离。

- ### 卡片使用方

  显示卡片内容的宿主应用，用于与用户直接进行交互，完成卡片添加、删除、显示功能，并能控制卡片在宿主中具体展示的位置。当前仅系统应用可以作为卡片使用方，桌面应用是典型的卡片使用方。

- ### 卡片提供方

  提供卡片显示内容的应用或原子化服务，是卡片功能的具体实现者。负责设计实现卡片UI、数据更新以及点击交互处理功能，实现FormExtensionAbility生命周期接口来管理卡片的创建、更新、删除等操作。

## H

- ### 互动卡片

  ArkTS卡片的一种类型，在动态卡片基础上额外支持破框动效能力。从API version 20开始支持，分为趣味交互类型互动卡片和场景动效类型互动卡片两种，用于有复杂业务逻辑和交互、需要执行破框动效呈现更好视觉体验的场景，如桌面卡片游戏、天气卡片动效展示等。

- ### LiveFormExtensionAbility；互动卡片扩展模块

  提供互动卡片功能的ExtensionAbility组件，继承自ExtensionAbility。从API version 20开始支持，包含onLiveFormCreate和onLiveFormDestroy生命周期接口，用于场景动效类型互动卡片激活态时的UI渲染和资源管理。

- ### LiveFormExtensionContext；互动卡片扩展上下文

  LiveFormExtensionAbility的上下文环境，继承自ExtensionContext。提供LiveFormExtensionAbility具有的接口和能力，用于互动卡片功能实现过程中的上下文信息获取和操作。

- ### LiveFormInfo；互动卡片信息

  描述互动卡片信息的对象类型，包含卡片ID、卡片位置和大小信息（rect）、卡片圆角半径信息（borderRadius）等属性。在LiveFormExtensionAbility生命周期回调中作为参数传递，用于标识和处理具体的互动卡片实例。

- ### OverflowInfo；互动卡片动效信息

  描述互动卡片动效请求参数的对象类型，包含动效区域范围（area）、动效持续时长（duration）、是否使用系统默认动效（useDefaultAnimation）等属性。通过formProvider.requestOverflow接口发起互动卡片动效请求时使用。

- ### 趣味交互类型互动卡片

  互动卡片的一种类型，提供卡片小游戏功能，当用户点击卡片时开始体验对应卡片小游戏。当前仅支持基于快游戏开发，适用于提升卡片趣味性和用户粘性的场景。

- ### 场景动效类型互动卡片

  互动卡片的一种类型，支持在特定场景下（如数据定时或定点刷新、用户点击等）触发互动卡片的特有效果。包含激活态和非激活态两种状态，激活态时卡片UI由LiveFormExtensionAbility对应page页面完成渲染，支持实现破框动效，适用于需要丰富信息提醒和浅层交互的场景。

## P

- ### ProxyData；代理刷新订阅数据

  卡片代理刷新订阅数据信息对象，包含订阅标识（key）和订阅条件（subscriberId）属性。用于卡片代理刷新功能的订阅配置，订阅标识需与数据发布者保持一致，订阅条件默认值为当前卡片的formId。

- ### 破框动效

  互动卡片提供的特有效果，允许动效渲染区域扩展到卡片自身的渲染区域之外，营造突破卡片边框的视觉效果。通过formProvider.requestOverflow接口触发，需要在指定约束范围内申请动效区域，最大动效时长为3500ms，仅支持特定机型且在非省电模式下生效。

## R

- ### Rect；矩形区域信息

  通用矩形区域信息对象，包含左上角顶点坐标（left、top）、宽度（width）、高度（height）属性。可用于描述卡片位置、互动卡片动效区域等信息，单位为vp。

- ### RunningFormInfo；运行中的卡片信息

  已添加到桌面的卡片信息对象，包含卡片标识、所属包名、模块名、Ability名、卡片名称、卡片尺寸、卡片位置等属性。从API version 20开始支持，通过formProvider.getPublishedRunningFormInfoById和getPublishedRunningFormInfos接口获取，用于查询和管理已加桌卡片的状态信息。

## S

- ### 临时卡片

  短期存在的卡片类型，在特定事件或用户行为后显示，完成后自动消失。与常态卡片相对，当前卡片使用方不会使用临时卡片，属于卡片使用方的概念。

- ### 常态卡片

  持久存在的卡片类型，在用户未进行清除或更改的情况下会一直存在。平时开发的功能卡片属于常态卡片，与临时卡片相对，属于卡片使用方的概念。