# uds.h
<!--Kit: ArkData-->
<!--Subsystem: DistributedDataManager-->
<!--Owner: @jcwen-->
<!--Designer: @junathuawei1; @zph000-->
<!--Tester: @lj_liujing; @yippo; @logic42-->
<!--Adviser: @ge-yafang-->

## 概述

提供标准化数据结构相关接口函数、结构体定义。当参数类型为char*时，字符串必须以空字符（'\0'）结尾。

**引用文件：** <database/udmf/uds.h>

**库：** libudmf.so

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

**起始版本：** 12

**相关模块：** [UDMF](capi-udmf.md)

## 汇总

### 结构体

| 名称                                           | typedef关键字     | 描述                                   |
| ---------------------------------------------- | ----------------- | -------------------------------------- |
| [OH_UdsPlainText](capi-udmf-oh-udsplaintext.md)    | OH_UdsPlainText   | 描述纯文本类型数据的统一数据结构。     |
| [OH_UdsHyperlink](capi-udmf-oh-udshyperlink.md)    | OH_UdsHyperlink   | 描述超链接类型的统一数据结构。         |
| [OH_UdsHtml](capi-udmf-oh-udshtml.md)              | OH_UdsHtml        | 描述超文本标记语言类型的统一数据结构。 |
| [OH_UdsAppItem](capi-udmf-oh-udsappitem.md)        | OH_UdsAppItem     | 描述桌面图标类型的统一数据结构。       |
| [OH_UdsFileUri](capi-udmf-oh-udsfileuri.md)        | OH_UdsFileUri     | 描述文件Uri类型的统一数据结构。        |
| [OH_UdsPixelMap](capi-udmf-oh-udspixelmap.md)      | OH_UdsPixelMap    | 描述像素图片类型的统一数据结构。       |
| [OH_UdsArrayBuffer](capi-udmf-oh-udsarraybuffer.md)| OH_UdsArrayBuffer | 描述ArrayBuffer类型的统一数据结构。    |
| [OH_UdsContentForm](capi-udmf-oh-udscontentform.md)| OH_UdsContentForm | 描述内容卡片类型的统一数据结构。       |
| [OH_UdsDetails](capi-udmf-oh-udsdetails.md)| OH_UdsDetails | 描述字典类型的统一数据结构。 |
| [OH_UDMF_VirtualFileCallbacks](capi-udmf-oh-udmf-virtualfilecallbacks.md)| OH_UDMF_VirtualFileCallbacks | 描述用于提供虚拟文件元数据和内容的回调。 |
| [OH_UDMF_VirtualItem](capi-udmf-oh-udmf-virtualitem.md)| OH_UDMF_VirtualItem | 描述虚拟文件或虚拟目录节点。 |
| [OH_UDMF_VirtualFileInfo](capi-udmf-oh-udmf-virtualfileinfo.md)| OH_UDMF_VirtualFileInfo | 描述虚拟文件入口及其数据回调。 |

### 枚举

| 名称 | typedef关键字 | 描述 |
| -- | -- | -- |
| [Udmf_AuthPermission](#udmf_authpermission)| Udmf_AuthPermission | 拖拽场景下的URI授权策略。<br>说明：此授权策略仅在拖拽场景下生效，其他场景不生效。|

### 函数

| 名称                                                         | 描述                                                         |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| [OH_UdsPlainText* OH_UdsPlainText_Create()](#oh_udsplaintext_create)| 创建纯文本类型[OH_UdsPlainText](capi-udmf-oh-udsplaintext.md)指针及实例对象。当不再需要使用指针时，请使用[OH_UdsPlainText_Destroy](capi-uds-h.md#oh_udsplaintext_destroy)销毁实例对象，否则会导致内存泄漏。 |
| [void OH_UdsPlainText_Destroy(OH_UdsPlainText* pThis)](#oh_udsplaintext_destroy)| 销毁纯文本类型数据[OH_UdsPlainText](capi-udmf-oh-udsplaintext.md)指针指向的实例对象。 |
| [const char* OH_UdsPlainText_GetType(OH_UdsPlainText* pThis)](#oh_udsplaintext_gettype)| 从纯文本类型[OH_UdsPlainText](capi-udmf-oh-udsplaintext.md)中获取类型ID。 |
| [const char* OH_UdsPlainText_GetContent(OH_UdsPlainText* pThis)](#oh_udsplaintext_getcontent)| 从纯文本类型[OH_UdsPlainText](capi-udmf-oh-udsplaintext.md)中获取纯文本内容信息。 |
| [const char* OH_UdsPlainText_GetAbstract(OH_UdsPlainText* pThis)](#oh_udsplaintext_getabstract)| 从纯文本类型[OH_UdsPlainText](capi-udmf-oh-udsplaintext.md)中获取纯文本摘要信息。 |
| [int OH_UdsPlainText_SetContent(OH_UdsPlainText* pThis, const char* content)](#oh_udsplaintext_setcontent)| 设置纯文本类型[OH_UdsPlainText](capi-udmf-oh-udsplaintext.md)中的纯文本内容参数。 |
| [int OH_UdsPlainText_SetAbstract(OH_UdsPlainText* pThis, const char* abstract)](#oh_udsplaintext_setabstract)| 设置纯文本类型[OH_UdsPlainText](capi-udmf-oh-udsplaintext.md)中的纯文本摘要参数。 |
| [OH_UdsHyperlink* OH_UdsHyperlink_Create()](#oh_udshyperlink_create)| 创建超链接类型[OH_UdsHyperlink](capi-udmf-oh-udshyperlink.md)指针及实例对象。当不再需要使用指针时，请使用[OH_UdsHyperlink_Destroy](capi-uds-h.md#oh_udshyperlink_destroy)销毁实例对象，否则会导致内存泄漏。 |
| [void OH_UdsHyperlink_Destroy(OH_UdsHyperlink* pThis)](#oh_udshyperlink_destroy)| 销毁超链接类型[OH_UdsHyperlink](capi-udmf-oh-udshyperlink.md)指针指向的实例对象。 |
| [const char* OH_UdsHyperlink_GetType(OH_UdsHyperlink* pThis)](#oh_udshyperlink_gettype)| 从超链接类型[OH_UdsHyperlink](capi-udmf-oh-udshyperlink.md)中获取类型ID。 |
| [const char* OH_UdsHyperlink_GetUrl(OH_UdsHyperlink* pThis)](#oh_udshyperlink_geturl)| 从超链接类型[OH_UdsHyperlink](capi-udmf-oh-udshyperlink.md)中获取URL参数。 |
| [const char* OH_UdsHyperlink_GetDescription(OH_UdsHyperlink* pThis)](#oh_udshyperlink_getdescription)| 从超链接类型[OH_UdsHyperlink](capi-udmf-oh-udshyperlink.md)中获取描述参数。 |
| [int OH_UdsHyperlink_SetUrl(OH_UdsHyperlink* pThis, const char* url)](#oh_udshyperlink_seturl)| 设置超链接类型[OH_UdsHyperlink](capi-udmf-oh-udshyperlink.md)实例中URL参数。 |
| [int OH_UdsHyperlink_SetDescription(OH_UdsHyperlink* pThis, const char* description)](#oh_udshyperlink_setdescription)| 设置超链接类型[OH_UdsHyperlink](capi-udmf-oh-udshyperlink.md)实例中描述参数。 |
| [OH_UdsHtml* OH_UdsHtml_Create()](#oh_udshtml_create)       | 创建超文本标记语言类型[OH_UdsHtml](capi-udmf-oh-udshtml.md)指针及实例对象。当不再需要使用指针时，请使用[OH_UdsHtml_Destroy](capi-uds-h.md#oh_udshtml_destroy)销毁实例对象，否则会导致内存泄漏。 |
| [void OH_UdsHtml_Destroy(OH_UdsHtml* pThis)](#oh_udshtml_destroy)| 销毁超文本标记语言类型[OH_UdsHtml](capi-udmf-oh-udshtml.md)指针指向的实例对象。 |
| [const char* OH_UdsHtml_GetType(OH_UdsHtml* pThis)](#oh_udshtml_gettype)| 获取超文本标记语言类型[OH_UdsHtml](capi-udmf-oh-udshtml.md)对象中类型ID。 |
| [const char* OH_UdsHtml_GetContent(OH_UdsHtml* pThis)](#oh_udshtml_getcontent)| 获取超文本标记语言类型[OH_UdsHtml](capi-udmf-oh-udshtml.md)对象中HTML格式内容参数。 |
| [const char* OH_UdsHtml_GetPlainContent(OH_UdsHtml* pThis)](#oh_udshtml_getplaincontent)| 获取超文本标记语言类型[OH_UdsHtml](capi-udmf-oh-udshtml.md)对象中的纯文本内容参数。 |
| [int OH_UdsHtml_SetContent(OH_UdsHtml* pThis, const char* content)](#oh_udshtml_setcontent)| 设置超文本标记语言类型[OH_UdsHtml](capi-udmf-oh-udshtml.md)中的HTML格式内容参数。 |
| [int OH_UdsHtml_SetPlainContent(OH_UdsHtml* pThis, const char* plainContent)](#oh_udshtml_setplaincontent)| 设置超文本标记语言类型[OH_UdsHtml](capi-udmf-oh-udshtml.md)中的纯文本内容参数。 |
| [OH_UdsAppItem* OH_UdsAppItem_Create()](#oh_udsappitem_create)| 创建桌面图标类型[OH_UdsAppItem](capi-udmf-oh-udsappitem.md)指针及实例对象。当不再需要使用指针时，请使用[OH_UdsAppItem_Destroy](capi-uds-h.md#oh_udsappitem_destroy)销毁实例对象，否则会导致内存泄漏。 |
| [void OH_UdsAppItem_Destroy(OH_UdsAppItem* pThis)](#oh_udsappitem_destroy)| 销毁桌面图标类型[OH_UdsAppItem](capi-udmf-oh-udsappitem.md)指针指向的实例对象。 |
| [const char* OH_UdsAppItem_GetType(OH_UdsAppItem* pThis)](#oh_udsappitem_gettype)| 从桌面图标类型[OH_UdsAppItem](capi-udmf-oh-udsappitem.md)实例获取类型ID。 |
| [const char* OH_UdsAppItem_GetId(OH_UdsAppItem* pThis)](#oh_udsappitem_getid)| 从桌面图标类型[OH_UdsAppItem](capi-udmf-oh-udsappitem.md)实例中获取应用ID。 |
| [const char* OH_UdsAppItem_GetName(OH_UdsAppItem* pThis)](#oh_udsappitem_getname)| 从桌面图标类型[OH_UdsAppItem](capi-udmf-oh-udsappitem.md)实例中获取应用名称。 |
| [const char* OH_UdsAppItem_GetIconId(OH_UdsAppItem* pThis)](#oh_udsappitem_geticonid)| 从桌面图标类型[OH_UdsAppItem](capi-udmf-oh-udsappitem.md)实例中获取图片ID。 |
| [const char* OH_UdsAppItem_GetLabelId(OH_UdsAppItem* pThis)](#oh_udsappitem_getlabelid)| 从桌面图标类型[OH_UdsAppItem](capi-udmf-oh-udsappitem.md)实例中获取标签ID。 |
| [const char* OH_UdsAppItem_GetBundleName(OH_UdsAppItem* pThis)](#oh_udsappitem_getbundlename)| 从桌面图标类型[OH_UdsAppItem](capi-udmf-oh-udsappitem.md)实例中获取bundle名称。 |
| [const char* OH_UdsAppItem_GetAbilityName(OH_UdsAppItem* pThis)](#oh_udsappitem_getabilityname)| 从桌面图标类型[OH_UdsAppItem](capi-udmf-oh-udsappitem.md)实例中获取ability名称。 |
| [int OH_UdsAppItem_SetId(OH_UdsAppItem* pThis, const char* appId)](#oh_udsappitem_setid)| 设置桌面图标类型[OH_UdsAppItem](capi-udmf-oh-udsappitem.md)对象的应用ID。 |
| [int OH_UdsAppItem_SetName(OH_UdsAppItem* pThis, const char* appName)](#oh_udsappitem_setname)| 设置桌面图标类型[OH_UdsAppItem](capi-udmf-oh-udsappitem.md)对象的应用名称。 |
| [int OH_UdsAppItem_SetIconId(OH_UdsAppItem* pThis, const char* appIconId)](#oh_udsappitem_seticonid)| 设置桌面图标类型[OH_UdsAppItem](capi-udmf-oh-udsappitem.md)对象的图片ID。 |
| [int OH_UdsAppItem_SetLabelId(OH_UdsAppItem* pThis, const char* appLabelId)](#oh_udsappitem_setlabelid)| 设置桌面图标类型[OH_UdsAppItem](capi-udmf-oh-udsappitem.md)对象的标签ID。 |
| [int OH_UdsAppItem_SetBundleName(OH_UdsAppItem* pThis, const char* bundleName)](#oh_udsappitem_setbundlename)| 设置桌面图标类型[OH_UdsAppItem](capi-udmf-oh-udsappitem.md)对象的bundle名称。 |
| [int OH_UdsAppItem_SetAbilityName(OH_UdsAppItem* pThis, const char* abilityName)](#oh_udsappitem_setabilityname)| 设置桌面图标类型[OH_UdsAppItem](capi-udmf-oh-udsappitem.md)对象的ability名称。 |
| [OH_UdsFileUri* OH_UdsFileUri_Create()](#oh_udsfileuri_create)| 创建文件Uri类型[OH_UdsFileUri](capi-udmf-oh-udsfileuri.md)的实例对象以及指向它的指针。当不再需要使用指针时，请使用[OH_UdsFileUri_Destroy](capi-uds-h.md#oh_udsfileuri_destroy)销毁实例对象，否则会导致内存泄漏。 |
| [void OH_UdsFileUri_Destroy(OH_UdsFileUri* pThis)](#oh_udsfileuri_destroy)| 销毁文件Uri类型[OH_UdsFileUri](capi-udmf-oh-udsfileuri.md)的实例对象。 |
| [const char* OH_UdsFileUri_GetType(OH_UdsFileUri* pThis)](#oh_udsfileuri_gettype)| 从文件Uri类型[OH_UdsFileUri](capi-udmf-oh-udsfileuri.md)实例中获取类型ID。 |
| [const char* OH_UdsFileUri_GetFileUri(OH_UdsFileUri* pThis)](#oh_udsfileuri_getfileuri)| 从文件Uri类型[OH_UdsFileUri](capi-udmf-oh-udsfileuri.md)实例中获取文件Uri。 |
| [const char* OH_UdsFileUri_GetFileType(OH_UdsFileUri* pThis)](#oh_udsfileuri_getfiletype)| 从文件Uri类型[OH_UdsFileUri](capi-udmf-oh-udsfileuri.md)实例中获取文件类型。 |
| [int OH_UdsFileUri_SetFileUri(OH_UdsFileUri* pThis, const char* fileUri)](#oh_udsfileuri_setfileuri)| 设置文件Uri类型[OH_UdsFileUri](capi-udmf-oh-udsfileuri.md)对象的Uri信息。 |
| [int OH_UdsFileUri_SetFileType(OH_UdsFileUri* pThis, const char* fileType)](#oh_udsfileuri_setfiletype)| 设置文件Uri类型[OH_UdsFileUri](capi-udmf-oh-udsfileuri.md)对象的文件类型。 |
| [OH_UdsPixelMap* OH_UdsPixelMap_Create()](#oh_udspixelmap_create)| 创建像素图片类型[OH_UdsPixelMap](capi-udmf-oh-udspixelmap.md)的实例对象以及指向它的指针。当不再需要使用指针时，请使用[OH_UdsPixelMap_Destroy](capi-uds-h.md#oh_udspixelmap_destroy)销毁实例对象，否则会导致内存泄漏。 |
| [void OH_UdsPixelMap_Destroy(OH_UdsPixelMap* pThis)](#oh_udspixelmap_destroy)| 销毁像素图片类型[OH_UdsPixelMap](capi-udmf-oh-udspixelmap.md)的实例对象。 |
| [const char* OH_UdsPixelMap_GetType(OH_UdsPixelMap* pThis)](#oh_udspixelmap_gettype)| 从像素图片类型[OH_UdsPixelMap](capi-udmf-oh-udspixelmap.md)实例中获取类型ID。 |
| [void OH_UdsPixelMap_GetPixelMap(OH_UdsPixelMap* pThis, OH_PixelmapNative* pixelmapNative)](#oh_udspixelmap_getpixelmap)| 从像素图片类型[OH_UdsPixelMap](capi-udmf-oh-udspixelmap.md)实例中获取像素图片[OH_PixelmapNative](../apis-image-kit/capi-pixelmap-native-h.md#oh_pixelmapnative_antialiasinglevel)实例的指针。 |
| [int OH_UdsPixelMap_SetPixelMap(OH_UdsPixelMap* pThis, OH_PixelmapNative* pixelmapNative)](#oh_udspixelmap_setpixelmap)| 设置像素图片类型[OH_UdsPixelMap](capi-udmf-oh-udspixelmap.md)对象的像素图片内容。 |
| [OH_UdsArrayBuffer* OH_UdsArrayBuffer_Create()](#oh_udsarraybuffer_create)| 创建ArrayBuffer类型[OH_UdsArrayBuffer](capi-udmf-oh-udsarraybuffer.md)的实例对象以及指向它的指针。当不再需要使用指针时，请使用[OH_UdsArrayBuffer_Destroy](capi-uds-h.md#oh_udsarraybuffer_destroy)销毁实例对象，否则会导致内存泄漏。 |
| [int OH_UdsArrayBuffer_Destroy(OH_UdsArrayBuffer* buffer)](#oh_udsarraybuffer_destroy)| 销毁ArrayBuffer类型[OH_UdsArrayBuffer](capi-udmf-oh-udsarraybuffer.md)的实例对象。 |
| [int OH_UdsArrayBuffer_SetData(OH_UdsArrayBuffer* buffer, unsigned char* data, unsigned int len)](#oh_udsarraybuffer_setdata)| 设置ArrayBuffer类型[OH_UdsArrayBuffer](capi-udmf-oh-udsarraybuffer.md)对象的数据内容。 |
| [int OH_UdsArrayBuffer_GetData(OH_UdsArrayBuffer* buffer, unsigned char** data, unsigned int* len)](#oh_udsarraybuffer_getdata)| 从ArrayBuffer类型[OH_UdsArrayBuffer](capi-udmf-oh-udsarraybuffer.md)实例中获取用户自定义的ArrayBuffer数据内容。 |
| [OH_UdsContentForm* OH_UdsContentForm_Create()](#oh_udscontentform_create)| 创建内容卡片类型[OH_UdsContentForm](capi-udmf-oh-udscontentform.md)指针及实例对象。当不再需要使用指针时，请使用[OH_UdsContentForm_Destroy](capi-uds-h.md#oh_udscontentform_destroy)销毁实例对象，否则会导致内存泄漏。 |
| [void OH_UdsContentForm_Destroy(OH_UdsContentForm* pThis)](#oh_udscontentform_destroy)| 销毁内容卡片类型数据[OH_UdsContentForm](capi-udmf-oh-udscontentform.md)指针指向的实例对象。 |
| [const char* OH_UdsContentForm_GetType(OH_UdsContentForm* pThis)](#oh_udscontentform_gettype)| 从内容卡片类型[OH_UdsContentForm](capi-udmf-oh-udscontentform.md)中获取类型ID。 |
| [int OH_UdsContentForm_GetThumbData(OH_UdsContentForm* pThis, unsigned char** thumbData, unsigned int* len)](#oh_udscontentform_getthumbdata)| 从内容卡片类型[OH_UdsContentForm](capi-udmf-oh-udscontentform.md)中获取图片数据。 |
| [const char* OH_UdsContentForm_GetDescription(OH_UdsContentForm* pThis)](#oh_udscontentform_getdescription)| 从内容卡片类型[OH_UdsContentForm](capi-udmf-oh-udscontentform.md)中获取描述信息。 |
| [const char* OH_UdsContentForm_GetTitle(OH_UdsContentForm* pThis)](#oh_udscontentform_gettitle)| 从内容卡片类型[OH_UdsContentForm](capi-udmf-oh-udscontentform.md)中获取标题信息。 |
| [int OH_UdsContentForm_GetAppIcon(OH_UdsContentForm* pThis, unsigned char** appIcon, unsigned int* len)](#oh_udscontentform_getappicon)| 从内容卡片类型[OH_UdsContentForm](capi-udmf-oh-udscontentform.md)中获取应用图标数据。 |
| [const char* OH_UdsContentForm_GetAppName(OH_UdsContentForm* pThis)](#oh_udscontentform_getappname)| 从内容卡片类型[OH_UdsContentForm](capi-udmf-oh-udscontentform.md)中获取应用名称信息。 |
| [const char* OH_UdsContentForm_GetLinkUri(OH_UdsContentForm* pThis)](#oh_udscontentform_getlinkuri)| 从内容卡片类型[OH_UdsContentForm](capi-udmf-oh-udscontentform.md)中获取超链接信息。 |
| [int OH_UdsContentForm_SetThumbData(OH_UdsContentForm* pThis, const unsigned char* thumbData, unsigned int len)](#oh_udscontentform_setthumbdata)| 设置内容卡片类型[OH_UdsContentForm](capi-udmf-oh-udscontentform.md)中的图片数据。 |
| [int OH_UdsContentForm_SetDescription(OH_UdsContentForm* pThis, const char* description)](#oh_udscontentform_setdescription)| 设置内容卡片类型[OH_UdsContentForm](capi-udmf-oh-udscontentform.md)中的描述信息。 |
| [int OH_UdsContentForm_SetTitle(OH_UdsContentForm* pThis, const char* title)](#oh_udscontentform_settitle)| 设置内容卡片类型[OH_UdsContentForm](capi-udmf-oh-udscontentform.md)中的标题信息。 |
| [int OH_UdsContentForm_SetAppIcon(OH_UdsContentForm* pThis, const unsigned char* appIcon, unsigned int len)](#oh_udscontentform_setappicon)| 设置内容卡片类型[OH_UdsContentForm](capi-udmf-oh-udscontentform.md)中的应用图标数据。 |
| [int OH_UdsContentForm_SetAppName(OH_UdsContentForm* pThis, const char* appName)](#oh_udscontentform_setappname)| 设置内容卡片类型[OH_UdsContentForm](capi-udmf-oh-udscontentform.md)中的应用名称数据。 |
| [int OH_UdsContentForm_SetLinkUri(OH_UdsContentForm* pThis, const char* linkUri)](#oh_udscontentform_setlinkuri)| 设置内容卡片类型[OH_UdsContentForm](capi-udmf-oh-udscontentform.md)中的超链接数据。 |
| [int OH_UdsPlainText_GetDetails(OH_UdsPlainText* pThis, OH_UdsDetails* details)](#oh_udsplaintext_getdetails)| 从纯文本类型[OH_UdsPlainText](capi-udmf-oh-udsplaintext.md)中获取字典类型[OH_UdsDetails](capi-udmf-oh-udsdetails.md)实例的指针。 |
| [int OH_UdsPlainText_SetDetails(OH_UdsPlainText* pThis, const OH_UdsDetails* details)](#oh_udsplaintext_setdetails)| 设置纯文本类型[OH_UdsPlainText](capi-udmf-oh-udsplaintext.md)中的字典类型[OH_UdsDetails](capi-udmf-oh-udsdetails.md)参数。 |
| [int OH_UdsHyperlink_GetDetails(OH_UdsHyperlink* pThis, OH_UdsDetails* details)](#oh_udshyperlink_getdetails)| 从超链接类型[OH_UdsHyperlink](capi-udmf-oh-udshyperlink.md)中获取字典类型[OH_UdsDetails](capi-udmf-oh-udsdetails.md)实例的指针。 |
| [int OH_UdsHyperlink_SetDetails(OH_UdsHyperlink* pThis, const OH_UdsDetails* details)](#oh_udshyperlink_setdetails)| 设置超链接类型[OH_UdsHyperlink](capi-udmf-oh-udshyperlink.md)实例中的字典类型[OH_UdsDetails](capi-udmf-oh-udsdetails.md)参数。 |
| [int OH_UdsHtml_GetDetails(OH_UdsHtml* pThis, OH_UdsDetails* details)](#oh_udshtml_getdetails)| 从超文本标记语言类型[OH_UdsHtml](capi-udmf-oh-udshtml.md)对象中获取字典类型[OH_UdsDetails](capi-udmf-oh-udsdetails.md)实例的指针。 |
| [int OH_UdsHtml_SetDetails(OH_UdsHtml* pThis, const OH_UdsDetails* details)](#oh_udshtml_setdetails)| 设置超文本标记语言类型[OH_UdsHtml](capi-udmf-oh-udshtml.md)中的字典类型[OH_UdsDetails](capi-udmf-oh-udsdetails.md)参数。 |
| [int OH_UdsAppItem_GetDetails(OH_UdsAppItem* pThis, OH_UdsDetails* details)](#oh_udsappitem_getdetails)| 从桌面图标类型[OH_UdsAppItem](capi-udmf-oh-udsappitem.md)实例中获取字典类型[OH_UdsDetails](capi-udmf-oh-udsdetails.md)实例的指针。 |
| [int OH_UdsAppItem_SetDetails(OH_UdsAppItem* pThis, const OH_UdsDetails* details)](#oh_udsappitem_setdetails)| 设置桌面图标类型[OH_UdsAppItem](capi-udmf-oh-udsappitem.md)对象的字典类型[OH_UdsDetails](capi-udmf-oh-udsdetails.md)参数。 |
| [int OH_UdsFileUri_GetDetails(OH_UdsFileUri* pThis, OH_UdsDetails* details)](#oh_udsfileuri_getdetails)| 从文件Uri类型[OH_UdsFileUri](capi-udmf-oh-udsfileuri.md)实例中获取字典类型[OH_UdsDetails](capi-udmf-oh-udsdetails.md)实例的指针。 |
| [int OH_UdsFileUri_SetDetails(OH_UdsFileUri* pThis, const OH_UdsDetails* details)](#oh_udsfileuri_setdetails)| 设置文件Uri类型[OH_UdsFileUri](capi-udmf-oh-udsfileuri.md)对象的字典类型[OH_UdsDetails](capi-udmf-oh-udsdetails.md)参数。 |
| [int OH_UdsPixelMap_GetDetails(OH_UdsPixelMap* pThis, OH_UdsDetails* details)](#oh_udspixelmap_getdetails)| 从像素图片类型[OH_UdsPixelMap](capi-udmf-oh-udspixelmap.md)实例中获取字典类型[OH_UdsDetails](capi-udmf-oh-udsdetails.md)实例的指针。 |
| [int OH_UdsPixelMap_SetDetails(OH_UdsPixelMap* pThis, const OH_UdsDetails* details)](#oh_udspixelmap_setdetails)| 设置像素图片类型[OH_UdsPixelMap](capi-udmf-oh-udspixelmap.md)对象的字典类型[OH_UdsDetails](capi-udmf-oh-udsdetails.md)参数。 |
| [OH_UdsDetails* OH_UdsDetails_Create()](#oh_udsdetails_create)| 创建字典类型[OH_UdsDetails](capi-udmf-oh-udsdetails.md)指针及实例对象。<br>当不再需要使用指针时，请使用[OH_UdsDetails_Destroy](capi-uds-h.md#oh_udsdetails_destroy)销毁实例对象，否则会导致内存泄漏。 |
| [void OH_UdsDetails_Destroy(OH_UdsDetails* pThis)](#oh_udsdetails_destroy)| 销毁字典类型[OH_UdsDetails](capi-udmf-oh-udsdetails.md)指针指向的实例对象。 |
| [bool OH_UdsDetails_HasKey(const OH_UdsDetails* pThis, const char* key)](#oh_udsdetails_haskey)| 检查字典类型[OH_UdsDetails](capi-udmf-oh-udsdetails.md)中是否存在指定键。 |
| [int OH_UdsDetails_Remove(OH_UdsDetails* pThis, const char* key)](#oh_udsdetails_remove)| 删除字典类型[OH_UdsDetails](capi-udmf-oh-udsdetails.md)中指定键值对。 |
| [int OH_UdsDetails_Clear(OH_UdsDetails* pThis)](#oh_udsdetails_clear)| 清除字典类型[OH_UdsDetails](capi-udmf-oh-udsdetails.md)中所有数据。 |
| [int OH_UdsDetails_SetValue(OH_UdsDetails* pThis, const char* key, const char* value)](#oh_udsdetails_setvalue)| 向字典类型[OH_UdsDetails](capi-udmf-oh-udsdetails.md)中添加键值对数据。 |
| [const char* OH_UdsDetails_GetValue(const OH_UdsDetails* pThis, const char* key)](#oh_udsdetails_getvalue)| 获取字典类型[OH_UdsDetails](capi-udmf-oh-udsdetails.md)中指定的键对应的值。 |
| [char** OH_UdsDetails_GetAllKeys(OH_UdsDetails* pThis, unsigned int* count)](#oh_udsdetails_getallkeys)| 获取字典类型[OH_UdsDetails](capi-udmf-oh-udsdetails.md)中所有键的结果集。 |
| [int OH_UdsHtml_SetAuthPolicy(OH_UdsHtml* pThis, uint32_t authPolicy)](#oh_udshtml_setauthpolicy)| 给[OH_UdsHtml](capi-udmf-oh-udshtml.md)设置授权策略。<br>说明：此授权策略仅在拖拽场景下生效，其他场景不生效。 |
| [int OH_UdsFileUri_SetAuthPolicy(OH_UdsFileUri* pThis, uint32_t authPolicy)](#oh_udsfileuri_setauthpolicy)| 给[OH_UdsFileUri](capi-udmf-oh-udsfileuri.md)设置授权策略。<br>说明：此授权策略仅在拖拽场景下生效，其他场景不生效。 |
| [OH_UDMF_VirtualItem* OH_UDMF_CreateVirtualFileItem(const char* name, const char* id, int64_t modifyTime)](#oh_udmf_createvirtualfileitem)| 根据文件名、文件标识和修改时间创建虚拟文件节点。 |
| [OH_UDMF_VirtualItem* OH_UDMF_CreateVirtualDirectoryItem(const char* name, int64_t modifyTime)](#oh_udmf_createvirtualdirectoryitem)| 创建虚拟目录节点。 |
| [void OH_UDMF_DestroyVirtualItem(OH_UDMF_VirtualItem* item)](#oh_udmf_destroyvirtualitem)| 销毁虚拟节点。 |
| [int OH_UDMF_SetVirtualFileSize(OH_UDMF_VirtualItem* item, int64_t size)](#oh_udmf_setvirtualfilesize) | 设置虚拟文件节点的文件大小，单位为字节。 |
| [int OH_UDMF_AddVirtualItemChild(OH_UDMF_VirtualItem* directory, const OH_UDMF_VirtualItem* child)](#oh_udmf_addvirtualitemchild)| 向虚拟目录添加子节点。 |
| [typedef OH_UDMF_VirtualItem* (\*OH_UDMF_VirtualFileOnStat)(void* context, const char* id)](#oh_udmf_virtualfileonstat) | 根据文件标识返回对应虚拟文件的信息，如文件名、大小和修改时间。 |
| [typedef int (\*OH_UDMF_VirtualFileOnRead)(void* context, const char* id, int64_t offset, uint32_t length, uint8_t* data, uint32_t* bytesRead)](#oh_udmf_virtualfileonread)  | 根据文件标识、读取起始位置和请求长度，将文件内容写入提供的缓冲区，并返回实际读取的字节数和处理结果。|
| [typedef int (\*OH_UDMF_VirtualFileOnCancel)(void* context, const char* const *idList, uint32_t count)](#oh_udmf_virtualfileoncancel) | 根据文件标识列表取消对应文件的待处理任务。 |
| [typedef void (\*OH_UDMF_VirtualFileFinalize)(void* context)](#oh_udmf_virtualfilefinalize) | 释放UDMF持有的用户上下文。 |
| [OH_UDMF_VirtualFileInfo* OH_UDMF_CreateVirtualFileInfo(const OH_UDMF_VirtualItem* itemInfo, const OH_UDMF_VirtualFileCallbacks* callbacks, void* context, OH_UDMF_VirtualFileFinalize finalize)](#oh_udmf_createvirtualfileinfo)| 创建虚拟文件信息。 |
| [void OH_UDMF_DestroyVirtualFileInfo(OH_UDMF_VirtualFileInfo* info)](#oh_udmf_destroyvirtualfileinfo)| 销毁虚拟文件信息。 |
| [int OH_UDMF_SetFileUriVirtualEntry(OH_UdsFileUri* fileUri, const OH_UDMF_VirtualFileInfo* info)](#oh_udmf_setfileurivirtualentry)| 向文件Uri类型[OH_UdsFileUri](capi-udmf-oh-udsfileuri.md)附加虚拟文件信息。 |
| [int OH_UDMF_ClearFileUriVirtualEntry(OH_UdsFileUri* fileUri)](#oh_udmf_clearfileurivirtualentry)| 从文件Uri类型[OH_UdsFileUri](capi-udmf-oh-udsfileuri.md)移除虚拟文件信息。 |


## 枚举类型说明

### Udmf_AuthPermission

```c
enum Udmf_AuthPermission
```

**描述**

拖拽场景下的URI授权策略。

> **说明：**
>
> 此授权策略仅在拖拽场景下生效，其他场景不生效。

支持不授权、读、写、持久化四种权限策略，可组合使用，仅以下组合生效：

- 仅使用NONE：不做任何文件授权。

- 仅使用READ：仅做单次只读授权。

- 仅使用WRITE：做单次读、写授权（写授权包含读授权）。

- READ+WRITE：做单次读、写授权，与仅写授权等同。

- READ+PERSIST：做持久化读授权。

- WRITE+PERSIST：做持久化读写授权。

- READ+WRITE+PERSIST：做持久化读写授权。

拖拽授权策略应用规则（按优先级从高到低）：

- 单个数据级别：FileUri、HTML两个UDS支持配置授权策略参数，仅对单个record单次生效，优先级最高。

- [OH_UdmfData](capi-udmf-oh-udmfdata.md)级别：[OH_UdmfProperty](capi-udmf-oh-udmfproperty.md)中提供的授权参数对单次拖拽有效。若某个数据中配置了授权策略，则优先按照该数据的配置进行，优先级次之。

- 默认级别：若单个数据和[OH_UdmfProperty](capi-udmf-oh-udmfproperty.md)均未配置授权策略，则按照拖拽默认逻辑进行代理授权。默认逻辑如下：

- FileUri类型数据：拖拽场景下默认授权为READ+WRITE+PERSIST（读+写+持久化授权）。

- HTML类型数据：仅针对HTML文本中img标签下的uri做读授权。

**起始版本：** 26.0.0

| 枚举项 | 描述 |
| -- | -- |
| UDMF_PERM_NONE = 0 | 表示未授予任何权限。 |
| UDMF_PERM_READ = 1u << 0 | 表示读取或查看数据的权限。 |
| UDMF_PERM_WRITE = 1u << 1 | 表示修改数据的权限（包含READ）。 |
| UDMF_PERM_PERSIST = 1u << 2 | 表示持久化文件的权限。 |

## 函数说明

### OH_UdsPlainText_Create()

```c
OH_UdsPlainText* OH_UdsPlainText_Create()
```

**描述**

创建纯文本类型[OH_UdsPlainText](capi-udmf-oh-udsplaintext.md)指针及实例对象。当不再需要使用指针时，请使用[OH_UdsPlainText_Destroy](capi-uds-h.md#oh_udsplaintext_destroy)销毁实例对象，否则会导致内存泄漏。

**起始版本：** 12

**返回：**

| 类型                                        | 说明                                                         |
| ------------------------------------------- | ------------------------------------------------------------ |
| [OH_UdsPlainText](capi-udmf-oh-udsplaintext.md)* | 执行成功则返回一个指向纯文本类型[OH_UdsPlainText](capi-udmf-oh-udsplaintext.md)实例对象的指针，否则返回nullptr。 |

### OH_UdsPlainText_Destroy()

```c
void OH_UdsPlainText_Destroy(OH_UdsPlainText* pThis)
```

**描述**

销毁纯文本类型数据[OH_UdsPlainText](capi-udmf-oh-udsplaintext.md)指针指向的实例对象。

**起始版本：** 12


**参数：**

| 参数项                                            | 描述                                                         |
| ------------------------------------------------- | ------------------------------------------------------------ |
| [OH_UdsPlainText](capi-udmf-oh-udsplaintext.md)* pThis | 表示指向[OH_UdsPlainText](capi-udmf-oh-udsplaintext.md)实例的指针。 |

### OH_UdsPlainText_GetType()

```c
const char* OH_UdsPlainText_GetType(OH_UdsPlainText* pThis)
```

**描述**

从纯文本类型[OH_UdsPlainText](capi-udmf-oh-udsplaintext.md)中获取类型ID。

**起始版本：** 12


**参数：**

| 参数项                                            | 描述                                                         |
| ------------------------------------------------- | ------------------------------------------------------------ |
| [OH_UdsPlainText](capi-udmf-oh-udsplaintext.md)* pThis | 表示指向纯文本类型[OH_UdsPlainText](capi-udmf-oh-udsplaintext.md)实例的指针。 |

**返回：**

| 类型        | 说明                                                    |
| ----------- | ------------------------------------------------------- |
| const char* | 输入有效入参时返回类型ID的字符串指针，否则返回nullptr。 |

### OH_UdsPlainText_GetContent()

```c
const char* OH_UdsPlainText_GetContent(OH_UdsPlainText* pThis)
```

**描述**

从纯文本类型[OH_UdsPlainText](capi-udmf-oh-udsplaintext.md)中获取纯文本内容信息。

**起始版本：** 12


**参数：**

| 参数项                                            | 描述                                                         |
| ------------------------------------------------- | ------------------------------------------------------------ |
| [OH_UdsPlainText](capi-udmf-oh-udsplaintext.md)* pThis | 表示指向纯文本类型[OH_UdsPlainText](capi-udmf-oh-udsplaintext.md)实例的指针。 |

**返回：**

| 类型        | 说明                                                         |
| ----------- | ------------------------------------------------------------ |
| const char* | 输入有效入参时返回纯文本内容信息的字符串指针，否则返回nullptr。 |

### OH_UdsPlainText_GetAbstract()

```c
const char* OH_UdsPlainText_GetAbstract(OH_UdsPlainText* pThis)
```

**描述**

从纯文本类型[OH_UdsPlainText](capi-udmf-oh-udsplaintext.md)中获取纯文本摘要信息。

**起始版本：** 12


**参数：**

| 参数项                                            | 描述                                                         |
| ------------------------------------------------- | ------------------------------------------------------------ |
| [OH_UdsPlainText](capi-udmf-oh-udsplaintext.md)* pThis | 表示指向纯文本类型[OH_UdsPlainText](capi-udmf-oh-udsplaintext.md)实例的指针。 |

**返回：**

| 类型        | 说明                                                         |
| ----------- | ------------------------------------------------------------ |
| const char* | 输入有效入参时返回纯文本摘要信息的字符串指针，否则返回nullptr。 |

### OH_UdsPlainText_SetContent()

```c
int OH_UdsPlainText_SetContent(OH_UdsPlainText* pThis, const char* content)
```

**描述**

设置纯文本类型[OH_UdsPlainText](capi-udmf-oh-udsplaintext.md)中的纯文本内容参数。

**起始版本：** 12


**参数：**

| 参数项                                            | 描述                                                         |
| ------------------------------------------------- | ------------------------------------------------------------ |
| [OH_UdsPlainText](capi-udmf-oh-udsplaintext.md)* pThis | 表示指向纯文本类型[OH_UdsPlainText](capi-udmf-oh-udsplaintext.md)实例的指针。 |
| const char* content                               | 表示纯文本内容参数。                                         |

**返回：**

| 类型 | 说明                                                         |
| ---- | ------------------------------------------------------------ |
| int  | 返回执行的状态代码。<br>若返回UDMF_E_OK，表示执行成功。<br>若返回UDMF_E_INVALID_PARAM，表示传入了无效参数。具体请参阅错误码定义[Udmf_ErrCode](capi-udmf-err-code-h.md#udmf_errcode)。 |

### OH_UdsPlainText_SetAbstract()

```c
int OH_UdsPlainText_SetAbstract(OH_UdsPlainText* pThis, const char* abstract)
```

**描述**

设置纯文本类型[OH_UdsPlainText](capi-udmf-oh-udsplaintext.md)中的纯文本摘要参数。

**起始版本：** 12


**参数：**

| 参数项                                            | 描述                                                         |
| ------------------------------------------------- | ------------------------------------------------------------ |
| [OH_UdsPlainText](capi-udmf-oh-udsplaintext.md)* pThis | 表示指向纯文本类型[OH_UdsPlainText](capi-udmf-oh-udsplaintext.md)实例的指针。 |
| const char* abstract                              | 表示纯文本摘要参数。                                         |

**返回：**

| 类型 | 说明                                                         |
| ---- | ------------------------------------------------------------ |
| int  | 返回执行的状态代码。<br>若返回UDMF_E_OK，表示执行成功。<br>若返回UDMF_E_INVALID_PARAM，表示传入了无效参数。具体请参阅错误码定义[Udmf_ErrCode](capi-udmf-err-code-h.md#udmf_errcode)。 |

### OH_UdsHyperlink_Create()

```c
OH_UdsHyperlink* OH_UdsHyperlink_Create()
```

**描述**

创建超链接类型[OH_UdsHyperlink](capi-udmf-oh-udshyperlink.md)指针及实例对象。当不再需要使用指针时，请使用[OH_UdsHyperlink_Destroy](capi-uds-h.md#oh_udshyperlink_destroy)销毁实例对象，否则会导致内存泄漏。

**起始版本：** 12

**返回：**

| 类型             | 说明                                                         |
| ---------------- | ------------------------------------------------------------ |
| OH_UdsHyperlink* | 执行成功则返回一个指向超链接类型[OH_UdsHyperlink](capi-udmf-oh-udshyperlink.md)实例对象的指针，否则返回nullptr。 |

### OH_UdsHyperlink_Destroy()

```c
void OH_UdsHyperlink_Destroy(OH_UdsHyperlink* pThis)
```

**描述**

销毁超链接类型[OH_UdsHyperlink](capi-udmf-oh-udshyperlink.md)指针指向的实例对象。

**起始版本：** 12


**参数：**

| 参数项                                            | 描述                                                         |
| ------------------------------------------------- | ------------------------------------------------------------ |
| [OH_UdsHyperlink](capi-udmf-oh-udshyperlink.md)* pThis | 表示指向超链接类型[OH_UdsHyperlink](capi-udmf-oh-udshyperlink.md)实例的指针。 |

### OH_UdsHyperlink_GetType()

```c
const char* OH_UdsHyperlink_GetType(OH_UdsHyperlink* pThis)
```

**描述**

从超链接类型[OH_UdsHyperlink](capi-udmf-oh-udshyperlink.md)中获取类型ID。

**起始版本：** 12


**参数：**

| 参数项                                            | 描述                                                         |
| ------------------------------------------------- | ------------------------------------------------------------ |
| [OH_UdsHyperlink](capi-udmf-oh-udshyperlink.md)* pThis | 表示指向超链接类型[OH_UdsHyperlink](capi-udmf-oh-udshyperlink.md)实例的指针。 |

**返回：**

| 类型        | 说明                                                    |
| ----------- | ------------------------------------------------------- |
| const char* | 输入有效入参时返回类型ID的字符串指针，否则返回nullptr。 |

### OH_UdsHyperlink_GetUrl()

```c
const char* OH_UdsHyperlink_GetUrl(OH_UdsHyperlink* pThis)
```

**描述**

从超链接类型[OH_UdsHyperlink](capi-udmf-oh-udshyperlink.md)中获取URL参数。

**起始版本：** 12


**参数：**

| 参数项                                            | 描述                                                         |
| ------------------------------------------------- | ------------------------------------------------------------ |
| [OH_UdsHyperlink](capi-udmf-oh-udshyperlink.md)* pThis | 表示指向超链接类型[OH_UdsHyperlink](capi-udmf-oh-udshyperlink.md)实例的指针。 |

**返回：**

| 类型        | 说明                                                     |
| ----------- | -------------------------------------------------------- |
| const char* | 输入有效入参时返回URL参数的字符串指针，否则返回nullptr。 |

### OH_UdsHyperlink_GetDescription()

```c
const char* OH_UdsHyperlink_GetDescription(OH_UdsHyperlink* pThis)
```

**描述**

从超链接类型[OH_UdsHyperlink](capi-udmf-oh-udshyperlink.md)中获取描述参数。

**起始版本：** 12


**参数：**

| 参数项                                            | 描述                                                         |
| ------------------------------------------------- | ------------------------------------------------------------ |
| [OH_UdsHyperlink](capi-udmf-oh-udshyperlink.md)* pThis | 表示指向超链接类型[OH_UdsHyperlink](capi-udmf-oh-udshyperlink.md)实例的指针。 |

**返回：**

| 类型        | 说明                                                      |
| ----------- | --------------------------------------------------------- |
| const char* | 输入有效入参时返回描述参数的字符串指针，否则返回nullptr。 |

### OH_UdsHyperlink_SetUrl()

```c
int OH_UdsHyperlink_SetUrl(OH_UdsHyperlink* pThis, const char* url)
```

**描述**

设置超链接类型[OH_UdsHyperlink](capi-udmf-oh-udshyperlink.md)实例中URL参数。

**起始版本：** 12


**参数：**

| 参数项                                            | 描述                                                         |
| ------------------------------------------------- | ------------------------------------------------------------ |
| [OH_UdsHyperlink](capi-udmf-oh-udshyperlink.md)* pThis | 表示指向超链接类型[OH_UdsHyperlink](capi-udmf-oh-udshyperlink.md)实例的指针。 |
| const char* url                                   | 表示URL参数。                                                |

**返回：**

| 类型 | 说明                                                         |
| ---- | ------------------------------------------------------------ |
| int  | 返回执行的状态代码。<br>若返回UDMF_E_OK，表示执行成功。<br>若返回UDMF_E_INVALID_PARAM，表示传入了无效参数。具体请参阅错误码定义[Udmf_ErrCode](capi-udmf-err-code-h.md#udmf_errcode)。 |

### OH_UdsHyperlink_SetDescription()

```c
int OH_UdsHyperlink_SetDescription(OH_UdsHyperlink* pThis, const char* description)
```

**描述**

设置超链接类型[OH_UdsHyperlink](capi-udmf-oh-udshyperlink.md)实例中描述参数。

**起始版本：** 12


**参数：**

| 参数项                                            | 描述                                                         |
| ------------------------------------------------- | ------------------------------------------------------------ |
| [OH_UdsHyperlink](capi-udmf-oh-udshyperlink.md)* pThis | 表示指向超链接类型[OH_UdsHyperlink](capi-udmf-oh-udshyperlink.md)实例的指针。 |
| const char* description                           | 表示描述信息。                                               |

**返回：**

| 类型 | 说明                                                         |
| ---- | ------------------------------------------------------------ |
| int  | 返回执行的状态代码。<br>若返回UDMF_E_OK，表示执行成功。<br>若返回UDMF_E_INVALID_PARAM，表示传入了无效参数。具体请参阅错误码定义[Udmf_ErrCode](capi-udmf-err-code-h.md#udmf_errcode)。 |

### OH_UdsHtml_Create()

```c
OH_UdsHtml* OH_UdsHtml_Create()
```

**描述**

创建超文本标记语言类型[OH_UdsHtml](capi-udmf-oh-udshtml.md)指针及实例对象。当不再需要使用指针时，请使用[OH_UdsHtml_Destroy](capi-uds-h.md#oh_udshtml_destroy)销毁实例对象，否则会导致内存泄漏。

**起始版本：** 12

**返回：**

| 类型                              | 说明                                                         |
| --------------------------------- | ------------------------------------------------------------ |
| [OH_UdsHtml](capi-udmf-oh-udshtml.md)* | 执行成功则返回一个指向超文本标记语言类型[OH_UdsHtml](capi-udmf-oh-udshtml.md)实例对象的指针，否则返回nullptr。 |

### OH_UdsHtml_Destroy()

```c
void OH_UdsHtml_Destroy(OH_UdsHtml* pThis)
```

**描述**

销毁超文本标记语言类型[OH_UdsHtml](capi-udmf-oh-udshtml.md)指针指向的实例对象。

**起始版本：** 12


**参数：**

| 参数项                                  | 描述                                                         |
| --------------------------------------- | ------------------------------------------------------------ |
| [OH_UdsHtml](capi-udmf-oh-udshtml.md)* pThis | 表示指向超文本标记语言类型[OH_UdsHtml](capi-udmf-oh-udshtml.md)实例的指针。 |

### OH_UdsHtml_GetType()

```c
const char* OH_UdsHtml_GetType(OH_UdsHtml* pThis)
```

**描述**

获取超文本标记语言类型[OH_UdsHtml](capi-udmf-oh-udshtml.md)对象中类型ID。

**起始版本：** 12


**参数：**

| 参数项                                  | 描述                                                         |
| --------------------------------------- | ------------------------------------------------------------ |
| [OH_UdsHtml](capi-udmf-oh-udshtml.md)* pThis | 表示指向超文本标记语言类型[OH_UdsHtml](capi-udmf-oh-udshtml.md)实例的指针。 |

**返回：**

| 类型        | 说明                                                    |
| ----------- | ------------------------------------------------------- |
| const char* | 输入有效入参时返回类型ID的字符串指针，否则返回nullptr。 |

### OH_UdsHtml_GetContent()

```c
const char* OH_UdsHtml_GetContent(OH_UdsHtml* pThis)
```

**描述**

获取超文本标记语言类型[OH_UdsHtml](capi-udmf-oh-udshtml.md)对象中HTML格式内容参数。

**起始版本：** 12


**参数：**

| 参数项                                  | 描述                                                         |
| --------------------------------------- | ------------------------------------------------------------ |
| [OH_UdsHtml](capi-udmf-oh-udshtml.md)* pThis | 表示指向超文本标记语言类型[OH_UdsHtml](capi-udmf-oh-udshtml.md)实例的指针。 |

**返回：**

| 类型        | 说明                                                         |
| ----------- | ------------------------------------------------------------ |
| const char* | 输入有效入参时返回HTML格式内容的字符串指针，否则返回nullptr。 |

### OH_UdsHtml_GetPlainContent()

```c
const char* OH_UdsHtml_GetPlainContent(OH_UdsHtml* pThis)
```

**描述**

获取超文本标记语言类型[OH_UdsHtml](capi-udmf-oh-udshtml.md)对象中的纯文本内容参数。

**起始版本：** 12


**参数：**

| 参数项                                  | 描述                                                         |
| --------------------------------------- | ------------------------------------------------------------ |
| [OH_UdsHtml](capi-udmf-oh-udshtml.md)* pThis | 表示指向超文本标记语言类型[OH_UdsHtml](capi-udmf-oh-udshtml.md)实例的指针。 |

**返回：**

| 类型        | 说明                                                        |
| ----------- | ----------------------------------------------------------- |
| const char* | 输入有效入参时返回纯文本内容的字符串指针，否则返回nullptr。 |

### OH_UdsHtml_SetContent()

```c
int OH_UdsHtml_SetContent(OH_UdsHtml* pThis, const char* content)
```

**描述**

设置超文本标记语言类型[OH_UdsHtml](capi-udmf-oh-udshtml.md)中的HTML格式内容参数。

**起始版本：** 12


**参数：**

| 参数项                                  | 描述                                                         |
| --------------------------------------- | ------------------------------------------------------------ |
| [OH_UdsHtml](capi-udmf-oh-udshtml.md)* pThis | 表示指向超文本标记语言类型[OH_UdsHtml](capi-udmf-oh-udshtml.md)实例的指针。 |
| const char* content                     | 表示HTML格式内容参数。                                       |

**返回：**

| 类型 | 说明                                                         |
| ---- | ------------------------------------------------------------ |
| int  | 返回执行的状态代码。<br>若返回UDMF_E_OK，表示执行成功。<br>若返回UDMF_E_INVALID_PARAM，表示传入了无效参数。具体请参阅错误码定义[Udmf_ErrCode](capi-udmf-err-code-h.md#udmf_errcode)。 |

### OH_UdsHtml_SetPlainContent()

```c
int OH_UdsHtml_SetPlainContent(OH_UdsHtml* pThis, const char* plainContent)
```

**描述**

设置超文本标记语言类型[OH_UdsHtml](capi-udmf-oh-udshtml.md)中的纯文本内容参数。

**起始版本：** 12


**参数：**

| 参数项                                  | 描述                                                         |
| --------------------------------------- | ------------------------------------------------------------ |
| [OH_UdsHtml](capi-udmf-oh-udshtml.md)* pThis | 表示指向超文本标记语言类型[OH_UdsHtml](capi-udmf-oh-udshtml.md)实例的指针。 |
| const char* plainContent                | 表示纯文本内容参数。                                         |

**返回：**

| 类型 | 说明                                                         |
| ---- | ------------------------------------------------------------ |
| int  | 返回执行的状态代码。<br>若返回UDMF_E_OK，表示执行成功。<br>若返回UDMF_E_INVALID_PARAM，表示传入了无效参数。具体请参阅错误码定义[Udmf_ErrCode](capi-udmf-err-code-h.md#udmf_errcode)。 |

### OH_UdsAppItem_Create()

```c
OH_UdsAppItem* OH_UdsAppItem_Create()
```

**描述**

创建桌面图标类型[OH_UdsAppItem](capi-udmf-oh-udsappitem.md)指针及实例对象。当不再需要使用指针时，请使用[OH_UdsAppItem_Destroy](capi-uds-h.md#oh_udsappitem_destroy)销毁实例对象，否则会导致内存泄漏。

**起始版本：** 12

**返回：**

| 类型                                    | 说明                                                         |
| --------------------------------------- | ------------------------------------------------------------ |
| [OH_UdsAppItem](capi-udmf-oh-udsappitem.md)* | 执行成功则返回一个指向桌面图标类型[OH_UdsAppItem](capi-udmf-oh-udsappitem.md)实例对象的指针，否则返回nullptr。 |

### OH_UdsAppItem_Destroy()

```c
void OH_UdsAppItem_Destroy(OH_UdsAppItem* pThis)
```

**描述**

销毁桌面图标类型[OH_UdsAppItem](capi-udmf-oh-udsappitem.md)指针指向的实例对象。

**起始版本：** 12


**参数：**

| 参数项                                        | 描述                                                         |
| --------------------------------------------- | ------------------------------------------------------------ |
| [OH_UdsAppItem](capi-udmf-oh-udsappitem.md)* pThis | 表示指向桌面图标类型[OH_UdsAppItem](capi-udmf-oh-udsappitem.md)对象的指针。 |

### OH_UdsAppItem_GetType()

```c
const char* OH_UdsAppItem_GetType(OH_UdsAppItem* pThis)
```

**描述**

从桌面图标类型[OH_UdsAppItem](capi-udmf-oh-udsappitem.md)实例获取类型ID。

**起始版本：** 12


**参数：**

| 参数项                                        | 描述                                                         |
| --------------------------------------------- | ------------------------------------------------------------ |
| [OH_UdsAppItem](capi-udmf-oh-udsappitem.md)* pThis | 表示指向桌面图标类型[OH_UdsAppItem](capi-udmf-oh-udsappitem.md)对象的指针。 |

**返回：**

| 类型        | 说明                                                    |
| ----------- | ------------------------------------------------------- |
| const char* | 输入有效入参时返回类型ID的字符串指针，否则返回nullptr。 |

### OH_UdsAppItem_GetId()

```c
const char* OH_UdsAppItem_GetId(OH_UdsAppItem* pThis)
```

**描述**

从桌面图标类型[OH_UdsAppItem](capi-udmf-oh-udsappitem.md)实例中获取应用ID。

**起始版本：** 12


**参数：**

| 参数项                                        | 描述                                                         |
| --------------------------------------------- | ------------------------------------------------------------ |
| [OH_UdsAppItem](capi-udmf-oh-udsappitem.md)* pThis | 表示指向桌面图标类型[OH_UdsAppItem](capi-udmf-oh-udsappitem.md)对象的指针。 |

**返回：**

| 类型        | 说明                                                    |
| ----------- | ------------------------------------------------------- |
| const char* | 输入有效入参时返回应用ID的字符串指针，否则返回nullptr。 |

### OH_UdsAppItem_GetName()

```c
const char* OH_UdsAppItem_GetName(OH_UdsAppItem* pThis)
```

**描述**

从桌面图标类型[OH_UdsAppItem](capi-udmf-oh-udsappitem.md)实例中获取应用名称。

**起始版本：** 12


**参数：**

| 参数项                                        | 描述                                                         |
| --------------------------------------------- | ------------------------------------------------------------ |
| [OH_UdsAppItem](capi-udmf-oh-udsappitem.md)* pThis | 表示指向桌面图标类型[OH_UdsAppItem](capi-udmf-oh-udsappitem.md)对象的指针。 |

**返回：**

| 类型        | 说明                                                      |
| ----------- | --------------------------------------------------------- |
| const char* | 输入有效入参时返回应用名称的字符串指针，否则返回nullptr。 |

### OH_UdsAppItem_GetIconId()

```c
const char* OH_UdsAppItem_GetIconId(OH_UdsAppItem* pThis)
```

**描述**

从桌面图标类型[OH_UdsAppItem](capi-udmf-oh-udsappitem.md)实例中获取图片ID。

**起始版本：** 12


**参数：**

| 参数项                                        | 描述                                                         |
| --------------------------------------------- | ------------------------------------------------------------ |
| [OH_UdsAppItem](capi-udmf-oh-udsappitem.md)* pThis | 表示指向桌面图标类型[OH_UdsAppItem](capi-udmf-oh-udsappitem.md)对象的指针。 |

**返回：**

| 类型        | 说明                                                    |
| ----------- | ------------------------------------------------------- |
| const char* | 输入有效入参时返回图片ID的字符串指针，否则返回nullptr。 |

### OH_UdsAppItem_GetLabelId()

```c
const char* OH_UdsAppItem_GetLabelId(OH_UdsAppItem* pThis)
```

**描述**

从桌面图标类型[OH_UdsAppItem](capi-udmf-oh-udsappitem.md)实例中获取标签ID。

**起始版本：** 12


**参数：**

| 参数项                                        | 描述                                                         |
| --------------------------------------------- | ------------------------------------------------------------ |
| [OH_UdsAppItem](capi-udmf-oh-udsappitem.md)* pThis | 表示指向桌面图标类型[OH_UdsAppItem](capi-udmf-oh-udsappitem.md)对象的指针。 |

**返回：**

| 类型        | 说明                                                    |
| ----------- | ------------------------------------------------------- |
| const char* | 输入有效入参时返回标签ID的字符串指针，否则返回nullptr。 |

### OH_UdsAppItem_GetBundleName()

```c
const char* OH_UdsAppItem_GetBundleName(OH_UdsAppItem* pThis)
```

**描述**

从桌面图标类型[OH_UdsAppItem](capi-udmf-oh-udsappitem.md)实例中获取bundle名称。

**起始版本：** 12


**参数：**

| 参数项                                        | 描述                                                         |
| --------------------------------------------- | ------------------------------------------------------------ |
| [OH_UdsAppItem](capi-udmf-oh-udsappitem.md)* pThis | 表示指向桌面图标类型[OH_UdsAppItem](capi-udmf-oh-udsappitem.md)对象的指针。 |

**返回：**

| 类型        | 说明                                                        |
| ----------- | ----------------------------------------------------------- |
| const char* | 输入有效入参时返回bundle名称的字符串指针，否则返回nullptr。 |

### OH_UdsAppItem_GetAbilityName()

```c
const char* OH_UdsAppItem_GetAbilityName(OH_UdsAppItem* pThis)
```

**描述**

从桌面图标类型[OH_UdsAppItem](capi-udmf-oh-udsappitem.md)实例中获取ability名称。

**起始版本：** 12


**参数：**

| 参数项                                        | 描述                                                         |
| --------------------------------------------- | ------------------------------------------------------------ |
| [OH_UdsAppItem](capi-udmf-oh-udsappitem.md)* pThis | 表示指向桌面图标类型[OH_UdsAppItem](capi-udmf-oh-udsappitem.md)对象的指针。 |

**返回：**

| 类型        | 说明                                                         |
| ----------- | ------------------------------------------------------------ |
| const char* | 输入有效入参时返回ability名称的字符串指针，否则返回nullptr。 |

### OH_UdsAppItem_SetId()

```c
int OH_UdsAppItem_SetId(OH_UdsAppItem* pThis, const char* appId)
```

**描述**

设置桌面图标类型[OH_UdsAppItem](capi-udmf-oh-udsappitem.md)对象的应用ID。

**起始版本：** 12


**参数：**

| 参数项                                        | 描述                                                         |
| --------------------------------------------- | ------------------------------------------------------------ |
| [OH_UdsAppItem](capi-udmf-oh-udsappitem.md)* pThis | 表示指向桌面图标类型[OH_UdsAppItem](capi-udmf-oh-udsappitem.md)对象的指针。 |
| const char* appId                             | 表示应用ID。                                                 |

**返回：**

| 类型 | 说明                                                         |
| ---- | ------------------------------------------------------------ |
| int  | 返回执行的状态代码。<br>若返回UDMF_E_OK，表示执行成功。<br>若返回UDMF_E_INVALID_PARAM，表示传入了无效参数。具体请参阅错误码定义[Udmf_ErrCode](capi-udmf-err-code-h.md#udmf_errcode)。 |

### OH_UdsAppItem_SetName()

```c
int OH_UdsAppItem_SetName(OH_UdsAppItem* pThis, const char* appName)
```

**描述**

设置桌面图标类型[OH_UdsAppItem](capi-udmf-oh-udsappitem.md)对象的应用名称。

**起始版本：** 12


**参数：**

| 参数项                                        | 描述                                                         |
| --------------------------------------------- | ------------------------------------------------------------ |
| [OH_UdsAppItem](capi-udmf-oh-udsappitem.md)* pThis | 表示指向桌面图标类型[OH_UdsAppItem](capi-udmf-oh-udsappitem.md)对象的指针。 |
| const char* appName                           | 表示应用名称。                                               |

**返回：**

| 类型 | 说明                                                         |
| ---- | ------------------------------------------------------------ |
| int  | 返回执行的状态代码。<br>若返回UDMF_E_OK，表示执行成功。<br>若返回UDMF_E_INVALID_PARAM，表示传入了无效参数。具体请参阅错误码定义[Udmf_ErrCode](capi-udmf-err-code-h.md#udmf_errcode)。 |

### OH_UdsAppItem_SetIconId()

```c
int OH_UdsAppItem_SetIconId(OH_UdsAppItem* pThis, const char* appIconId)
```

**描述**

设置桌面图标类型[OH_UdsAppItem](capi-udmf-oh-udsappitem.md)对象的图片ID。

**起始版本：** 12


**参数：**

| 参数项                                        | 描述                                                         |
| --------------------------------------------- | ------------------------------------------------------------ |
| [OH_UdsAppItem](capi-udmf-oh-udsappitem.md)* pThis | 表示指向桌面图标类型[OH_UdsAppItem](capi-udmf-oh-udsappitem.md)对象的指针。 |
| const char* appIconId                         | 表示图片ID。                                                 |

**返回：**

| 类型 | 说明                                                         |
| ---- | ------------------------------------------------------------ |
| int  | 返回执行的状态代码。<br>若返回UDMF_E_OK，表示执行成功。<br>若返回UDMF_E_INVALID_PARAM，表示传入了无效参数。具体请参阅错误码定义[Udmf_ErrCode](capi-udmf-err-code-h.md#udmf_errcode)。 |

### OH_UdsAppItem_SetLabelId()

```c
int OH_UdsAppItem_SetLabelId(OH_UdsAppItem* pThis, const char* appLabelId)
```

**描述**

设置桌面图标类型[OH_UdsAppItem](capi-udmf-oh-udsappitem.md)对象的标签ID。

**起始版本：** 12


**参数：**

| 参数项                                        | 描述                                                         |
| --------------------------------------------- | ------------------------------------------------------------ |
| [OH_UdsAppItem](capi-udmf-oh-udsappitem.md)* pThis | 表示指向桌面图标类型[OH_UdsAppItem](capi-udmf-oh-udsappitem.md)对象的指针。 |
| const char* appLabelId                        | 表示标签ID。                                                 |

**返回：**

| 类型 | 说明                                                         |
| ---- | ------------------------------------------------------------ |
| int  | 返回执行的状态代码。<br>若返回UDMF_E_OK，表示执行成功。<br>若返回UDMF_E_INVALID_PARAM，表示传入了无效参数。具体请参阅错误码定义[Udmf_ErrCode](capi-udmf-err-code-h.md#udmf_errcode)。 |

### OH_UdsAppItem_SetBundleName()

```c
int OH_UdsAppItem_SetBundleName(OH_UdsAppItem* pThis, const char* bundleName)
```

**描述**

设置桌面图标类型[OH_UdsAppItem](capi-udmf-oh-udsappitem.md)对象的bundle名称。

**起始版本：** 12


**参数：**

| 参数项                                        | 描述                                                         |
| --------------------------------------------- | ------------------------------------------------------------ |
| [OH_UdsAppItem](capi-udmf-oh-udsappitem.md)* pThis | 表示指向桌面图标类型[OH_UdsAppItem](capi-udmf-oh-udsappitem.md)对象的指针。 |
| const char* bundleName                        | 表示bundle名称。                                             |

**返回：**

| 类型 | 说明                                                         |
| ---- | ------------------------------------------------------------ |
| int  |返回执行的状态代码。<br>若返回UDMF_E_OK，表示执行成功。<br>若返回UDMF_E_INVALID_PARAM，表示传入了无效参数。具体请参阅错误码定义[Udmf_ErrCode](capi-udmf-err-code-h.md#udmf_errcode)。 |

### OH_UdsAppItem_SetAbilityName()

```c
int OH_UdsAppItem_SetAbilityName(OH_UdsAppItem* pThis, const char* abilityName)
```

**描述**

设置桌面图标类型[OH_UdsAppItem](capi-udmf-oh-udsappitem.md)对象的ability名称。

**起始版本：** 12


**参数：**

| 参数项                                        | 描述                                                         |
| --------------------------------------------- | ------------------------------------------------------------ |
| [OH_UdsAppItem](capi-udmf-oh-udsappitem.md)* pThis | 表示指向桌面图标类型[OH_UdsAppItem](capi-udmf-oh-udsappitem.md)对象的指针。 |
| const char* abilityName                       | 表示ability名称。                                            |

**返回：**

| 类型 | 说明                                                         |
| ---- | ------------------------------------------------------------ |
| int  | 返回执行的状态代码。<br>若返回UDMF_E_OK，表示执行成功。<br>若返回UDMF_E_INVALID_PARAM，表示传入了无效参数。具体请参阅错误码定义[Udmf_ErrCode](capi-udmf-err-code-h.md#udmf_errcode)。 |

### OH_UdsFileUri_Create()

```c
OH_UdsFileUri* OH_UdsFileUri_Create()
```

**描述**

创建文件Uri类型[OH_UdsFileUri](capi-udmf-oh-udsfileuri.md)的实例对象以及指向它的指针。当不再需要使用指针时，请使用[OH_UdsFileUri_Destroy](capi-uds-h.md#oh_udsfileuri_destroy)销毁实例对象，否则会导致内存泄漏。

**起始版本：** 13

**返回：**

| 类型                                    | 说明                                                         |
| --------------------------------------- | ------------------------------------------------------------ |
| [OH_UdsFileUri](capi-udmf-oh-udsfileuri.md)* | 执行成功则返回一个指向文件Uri类型[OH_UdsFileUri](capi-udmf-oh-udsfileuri.md)实例对象的指针，否则返回nullptr。 |

### OH_UdsFileUri_Destroy()

```c
void OH_UdsFileUri_Destroy(OH_UdsFileUri* pThis)
```

**描述**

销毁文件Uri类型[OH_UdsFileUri](capi-udmf-oh-udsfileuri.md)的实例对象。

**起始版本：** 13


**参数：**

| 参数项                                        | 描述                                                         |
| --------------------------------------------- | ------------------------------------------------------------ |
| [OH_UdsFileUri](capi-udmf-oh-udsfileuri.md)* pThis | 表示指向文件Uri类型[OH_UdsFileUri](capi-udmf-oh-udsfileuri.md)实例的指针。 |

### OH_UdsFileUri_GetType()

```c
const char* OH_UdsFileUri_GetType(OH_UdsFileUri* pThis)
```

**描述**

从文件Uri类型[OH_UdsFileUri](capi-udmf-oh-udsfileuri.md)实例中获取类型ID。

**起始版本：** 13


**参数：**

| 参数项                                        | 描述                                                         |
| --------------------------------------------- | ------------------------------------------------------------ |
| [OH_UdsFileUri](capi-udmf-oh-udsfileuri.md)* pThis | 表示指向文件Uri类型[OH_UdsFileUri](capi-udmf-oh-udsfileuri.md)实例的指针。 |

**返回：**

| 类型        | 说明                                                    |
| ----------- | ------------------------------------------------------- |
| const char* | 输入有效入参时返回类型ID的字符串指针，否则返回nullptr。 |

### OH_UdsFileUri_GetFileUri()

```c
const char* OH_UdsFileUri_GetFileUri(OH_UdsFileUri* pThis)
```

**描述**

从文件Uri类型[OH_UdsFileUri](capi-udmf-oh-udsfileuri.md)实例中获取文件Uri。

**起始版本：** 13


**参数：**

| 参数项                                        | 描述                                                         |
| --------------------------------------------- | ------------------------------------------------------------ |
| [OH_UdsFileUri](capi-udmf-oh-udsfileuri.md)* pThis | 表示指向文件Uri类型[OH_UdsFileUri](capi-udmf-oh-udsfileuri.md)实例的指针。 |

**返回：**

| 类型        | 说明                                                     |
| ----------- | -------------------------------------------------------- |
| const char* | 输入有效入参时返回文件Uri的字符串指针，否则返回nullptr。 |

### OH_UdsFileUri_GetFileType()

```c
const char* OH_UdsFileUri_GetFileType(OH_UdsFileUri* pThis)
```

**描述**

从文件Uri类型[OH_UdsFileUri](capi-udmf-oh-udsfileuri.md)实例中获取文件类型。

**起始版本：** 13


**参数：**

| 参数项                                        | 描述                                                         |
| --------------------------------------------- | ------------------------------------------------------------ |
| [OH_UdsFileUri](capi-udmf-oh-udsfileuri.md)* pThis | 表示指向文件Uri类型[OH_UdsFileUri](capi-udmf-oh-udsfileuri.md)实例的指针。 |

**返回：**

| 类型        | 说明                                                      |
| ----------- | --------------------------------------------------------- |
| const char* | 输入有效入参时返回文件类型的字符串指针，否则返回nullptr。 |

### OH_UdsFileUri_SetFileUri()

```c
int OH_UdsFileUri_SetFileUri(OH_UdsFileUri* pThis, const char* fileUri)
```

**描述**

设置文件Uri类型[OH_UdsFileUri](capi-udmf-oh-udsfileuri.md)对象的Uri信息。若使用[OH_UDMF_SetFileUriVirtualEntry](oh_udmf_setfileurivirtualentry)函数设置了虚拟文件信息，`fileUri`可填写一个非空的占位文件 URI，不要求对应的真实文件已经存在。

**起始版本：** 13


**参数：**

| 参数项                                        | 描述                                                         |
| --------------------------------------------- | ------------------------------------------------------------ |
| [OH_UdsFileUri](capi-udmf-oh-udsfileuri.md)* pThis | 表示指向文件Uri类型[OH_UdsFileUri](capi-udmf-oh-udsfileuri.md)实例的指针。 |
| const char* fileUri                           | 表示文件Uri。                                                |

**返回：**

| 类型 | 说明                                                         |
| ---- | ------------------------------------------------------------ |
| int  | 返回执行的状态代码。<br>若返回UDMF_E_OK，表示执行成功。<br>若返回UDMF_E_INVALID_PARAM，表示传入了无效参数。具体请参阅错误码定义[Udmf_ErrCode](capi-udmf-err-code-h.md#udmf_errcode)。 |

### OH_UdsFileUri_SetFileType()

```c
int OH_UdsFileUri_SetFileType(OH_UdsFileUri* pThis, const char* fileType)
```

**描述**

设置文件Uri类型[OH_UdsFileUri](capi-udmf-oh-udsfileuri.md)对象的文件类型。

**起始版本：** 13


**参数：**

| 参数项                                        | 描述                                                         |
| --------------------------------------------- | ------------------------------------------------------------ |
| [OH_UdsFileUri](capi-udmf-oh-udsfileuri.md)* pThis | 表示指向文件Uri类型[OH_UdsFileUri](capi-udmf-oh-udsfileuri.md)实例的指针。 |
| const char* fileType                          | 表示文件类型。                                               |

**返回：**

| 类型 | 说明                                                         |
| ---- | ------------------------------------------------------------ |
| int  | 返回执行的状态代码。<br>若返回UDMF_E_OK，表示执行成功。<br>若返回UDMF_E_INVALID_PARAM，表示传入了无效参数。具体请参阅错误码定义[Udmf_ErrCode](capi-udmf-err-code-h.md#udmf_errcode)。 |

### OH_UDMF_VirtualFileOnStat()

```c
typedef OH_UDMF_VirtualItem* (*OH_UDMF_VirtualFileOnStat)(void* context, const char* id)
```

**描述：**

根据文件标识返回对应虚拟文件的信息，如文件名、大小和修改时间。

<!--Device-typedef OH_UDMF_VirtualItem* (*OH_UDMF_VirtualFileOnStat)(void* context, const char* id)--><!--Device-typedef OH_UDMF_VirtualItem* (*OH_UDMF_VirtualFileOnStat)(void* context, const char* id)-End-->

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

**起始版本：** 26.1.0

**参数：**

| 参数项 | 描述 |
| -- | -- |
| void* context | [入参] 通过[OH_UDMF_CreateVirtualFileInfo](capi-uds-h.md#oh_udmf_createvirtualfileinfo)传入的用户上下文。 |
| const char* id | [入参] 请求的虚拟文件标识。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| [OH_UDMF_VirtualItem*](capi-udmf-oh-udmf-virtualitem.md)| 成功时返回虚拟文件节点，失败时返回nullptr。 |

### OH_UDMF_VirtualFileOnRead()

```c
typedef int (*OH_UDMF_VirtualFileOnRead)(void* context, const char* id, int64_t offset, uint32_t length, uint8_t* data, uint32_t* bytesRead)
```

**描述：**

根据文件标识、读取起始位置和请求长度，将文件内容写入提供的缓冲区，并返回实际读取的字节数和处理结果。

<!--Device-typedef int (*OH_UDMF_VirtualFileOnRead)(void* context, const char* id, int64_t offset, uint32_t length, uint8_t* data, uint32_t* bytesRead)--><!--Device-typedef int (*OH_UDMF_VirtualFileOnRead)(void* context, const char* id, int64_t offset, uint32_t length, uint8_t* data, uint32_t* bytesRead)-End-->

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

**起始版本：** 26.1.0

**参数：**

| 参数项 | 描述 |
| -- | -- |
| void* context | [入参] 通过[OH_UDMF_CreateVirtualFileInfo](capi-uds-h.md#oh_udmf_createvirtualfileinfo)传入的用户上下文。 |
| const char* id | [入参] 请求的虚拟文件标识。 |
| int64_t offset | [入参] 读取偏移量，单位为字节。 |
| uint32_t length | [入参] 本次最多需要提供的字节数，正常FUSE回调中取值为1～5242880（5MiB），且不超过文件剩余大小。 |
| uint8_t* data | [出参] UDMF提供的目标缓冲区，仅在回调执行期间有效。 |
| uint32_t* bytesRead | [出参] 用于返回实际写入`data`的字节数。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| int | 返回执行状态码。具体请参阅[Udmf_ErrCode](capi-udmf-err-code-h.md#udmf_errcode)。<ul> <li>[UDMF_E_OK](capi-udmf-err-code-h.md#udmf_errcode)表示回调执行成功，包括到达文件末尾且无数据可返回的情况，实际字节数通过`*bytesRead`返回。</li> <li>[UDMF_E_INVALID_PARAM](capi-udmf-err-code-h.md#udmf_errcode)表示传入了无效参数。</li> <li>[UDMF_ERR](capi-udmf-err-code-h.md#udmf_errcode)表示发生内部错误，无法提供数据。</li> </ul> |

### OH_UDMF_VirtualFileOnCancel()

```c
typedef int (*OH_UDMF_VirtualFileOnCancel)(void* context, const char* const *idList, uint32_t count)
```

**描述：**

根据文件标识列表取消对应文件的待处理任务。

<!--Device-typedef int (*OH_UDMF_VirtualFileOnCancel)(void* context, const char* const *idList, uint32_t count)--><!--Device-typedef int (*OH_UDMF_VirtualFileOnCancel)(void* context, const char* const *idList, uint32_t count)-End-->

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

**起始版本：** 26.1.0

**参数：**

| 参数项 | 描述 |
| -- | -- |
| void* context | [入参] 通过[OH_UDMF_CreateVirtualFileInfo](capi-uds-h.md#oh_udmf_createvirtualfileinfo)传入的用户上下文。 |
| const char* const *idList | [入参] 需要取消待处理任务的虚拟文件标识列表，可能包含重复id。该数组及其中的字符串仅在回调执行期间有效。 |
| uint32_t count | [入参] `idList`中的文件标识数量。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| int | 返回执行状态码。具体请参阅[Udmf_ErrCode](capi-udmf-err-code-h.md#udmf_errcode)。<ul> <li>[UDMF_E_OK](capi-udmf-err-code-h.md#udmf_errcode)表示取消成功。</li> <li>[UDMF_E_INVALID_PARAM](capi-udmf-err-code-h.md#udmf_errcode)表示传入了无效参数。</li> <li>[UDMF_ERR](capi-udmf-err-code-h.md#udmf_errcode)表示发生内部错误，取消失败。</li> </ul> |

### OH_UDMF_VirtualFileFinalize()

```c
typedef void (*OH_UDMF_VirtualFileFinalize)(void* context)
```

**描述：**

释放UDMF持有的用户上下文。

<!--Device-typedef void (*OH_UDMF_VirtualFileFinalize)(void* context)--><!--Device-typedef void (*OH_UDMF_VirtualFileFinalize)(void* context)-End-->

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

**起始版本：** 26.1.0

**参数：**

| 参数项 | 描述 |
| -- | -- |
| void* context | [入参] 待释放的用户上下文。 |

### OH_UDMF_CreateVirtualFileItem()

```c
OH_UDMF_VirtualItem* OH_UDMF_CreateVirtualFileItem(const char* name, const char* id, int64_t modifyTime)
```

**描述：**

根据文件名、文件标识和修改时间创建虚拟文件节点。

<!--Device-OH_UDMF_VirtualItem* OH_UDMF_CreateVirtualFileItem(const char* name, const char* id, int64_t modifyTime)--><!--Device-OH_UDMF_VirtualItem* OH_UDMF_CreateVirtualFileItem(const char* name, const char* id, int64_t modifyTime)-End-->

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

**起始版本：** 26.1.0

**资源释放：** [OH_UDMF_DestroyVirtualItem](#oh_udmf_destroyvirtualitem)

**参数：**

| 参数项 | 描述 |
| -- | -- |
| const char* name | [入参] 文件名，最多255字节，不能为空、`.`、`..`，也不能包含斜杠、反斜杠或空字符。同一目录下子节点名称不得重复。 |
| const char* id | [入参] 传给虚拟文件回调的文件标识，最多1024字节，不同文件应使用不同id。 |
| int64_t modifyTime | [入参] 文件修改时间，以Unix时间戳表示，单位为ms。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| [OH_UDMF_VirtualItem*](capi-udmf-oh-udmf-virtualitem.md)| 成功时返回创建的虚拟节点；参数无效或内存分配失败时返回nullptr。 |

### OH_UDMF_CreateVirtualDirectoryItem()

```c
OH_UDMF_VirtualItem* OH_UDMF_CreateVirtualDirectoryItem(const char* name, int64_t modifyTime)
```

**描述：**

创建虚拟目录节点。

<!--Device-OH_UDMF_VirtualItem* OH_UDMF_CreateVirtualDirectoryItem(const char* name, int64_t modifyTime)--><!--Device-OH_UDMF_VirtualItem* OH_UDMF_CreateVirtualDirectoryItem(const char* name, int64_t modifyTime)-End-->

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

**起始版本：** 26.1.0

**资源释放：** [OH_UDMF_DestroyVirtualItem](#oh_udmf_destroyvirtualitem)

**参数：**

| 参数项 | 描述 |
| -- | -- |
| const char* name | [入参] 目录名，最多255字节。不能为空、`.`、`..`，也不能包含斜杠、反斜杠或空字符。同一目录下子节点名称不得重复。 |
| int64_t modifyTime | [入参] 目录修改时间，以Unix时间戳表示，单位为ms。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| [OH_UDMF_VirtualItem*](capi-udmf-oh-udmf-virtualitem.md)| 成功时返回创建的虚拟节点；参数无效或内存分配失败时返回nullptr。 |

### OH_UDMF_DestroyVirtualItem()

```c
void OH_UDMF_DestroyVirtualItem(OH_UDMF_VirtualItem* item)
```

**描述：**

销毁虚拟节点。

<!--Device-void OH_UDMF_DestroyVirtualItem(OH_UDMF_VirtualItem* item)--><!--Device-void OH_UDMF_DestroyVirtualItem(OH_UDMF_VirtualItem* item)-End-->

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

**起始版本：** 26.1.0

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_UDMF_VirtualItem](capi-udmf-oh-udmf-virtualitem.md)* item | [入参] 待销毁的虚拟节点。 |

### OH_UDMF_SetVirtualFileSize()

```c
int OH_UDMF_SetVirtualFileSize(OH_UDMF_VirtualItem* item, int64_t size)
```

**描述：**

设置虚拟文件节点的文件大小，单位为字节。

<!--Device-int OH_UDMF_SetVirtualFileSize(OH_UDMF_VirtualItem* item, int64_t size)--><!--Device-int OH_UDMF_SetVirtualFileSize(OH_UDMF_VirtualItem* item, int64_t size)-End-->

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

**起始版本：** 26.1.0

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_UDMF_VirtualItem](capi-udmf-oh-udmf-virtualitem.md)* item | [入参] 待设置文件大小的有效虚拟文件节点。 |
| int64_t size | [入参] 文件大小，单位为字节。取值范围为[0, INT64_MAX]，0表示空文件。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| int | 返回执行状态码。具体请参阅[Udmf_ErrCode](capi-udmf-err-code-h.md#udmf_errcode)。<ul> <li>[UDMF_E_OK](capi-udmf-err-code-h.md#udmf_errcode)表示设置成功。</li> <li>[UDMF_E_INVALID_PARAM](capi-udmf-err-code-h.md#udmf_errcode)表示`item`无效、不是文件节点或`size`为负数。</li> </ul> |

### OH_UDMF_AddVirtualItemChild()

```c
int OH_UDMF_AddVirtualItemChild(OH_UDMF_VirtualItem* directory, const OH_UDMF_VirtualItem* child)
```

**描述：**

向虚拟目录添加子节点。

<!--Device-int OH_UDMF_AddVirtualItemChild(OH_UDMF_VirtualItem* directory, const OH_UDMF_VirtualItem* child)--><!--Device-int OH_UDMF_AddVirtualItemChild(OH_UDMF_VirtualItem* directory, const OH_UDMF_VirtualItem* child)-End-->

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

**起始版本：** 26.1.0

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_UDMF_VirtualItem](capi-udmf-oh-udmf-virtualitem.md)* directory | [入参] 虚拟目录节点。 |
| [const OH_UDMF_VirtualItem](capi-udmf-oh-udmf-virtualitem.md)* child | [入参] 待添加的子节点。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| int | 返回执行状态码。具体请参阅[Udmf_ErrCode](capi-udmf-err-code-h.md#udmf_errcode)。<ul> <li>[UDMF_E_OK](capi-udmf-err-code-h.md#udmf_errcode)表示添加成功。</li> <li>[UDMF_E_INVALID_PARAM](capi-udmf-err-code-h.md#udmf_errcode)表示节点无效、`directory`不是目录，或结果违反虚拟文件树约束。</li> </ul> |

### OH_UDMF_CreateVirtualFileInfo()

```c
OH_UDMF_VirtualFileInfo* OH_UDMF_CreateVirtualFileInfo(const OH_UDMF_VirtualItem* itemInfo, const OH_UDMF_VirtualFileCallbacks* callbacks, void* context, OH_UDMF_VirtualFileFinalize finalize)
```

**描述：**

创建虚拟文件信息。

<!--Device-OH_UDMF_VirtualFileInfo* OH_UDMF_CreateVirtualFileInfo(const OH_UDMF_VirtualItem* itemInfo, const OH_UDMF_VirtualFileCallbacks* callbacks, void* context, OH_UDMF_VirtualFileFinalize finalize)--><!--Device-OH_UDMF_VirtualFileInfo* OH_UDMF_CreateVirtualFileInfo(const OH_UDMF_VirtualItem* itemInfo, const OH_UDMF_VirtualFileCallbacks* callbacks, void* context, OH_UDMF_VirtualFileFinalize finalize)-End-->

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

**起始版本：** 26.1.0

**资源释放：** [OH_UDMF_DestroyVirtualFileInfo](#oh_udmf_destroyvirtualfileinfo)

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [const OH_UDMF_VirtualItem](capi-udmf-oh-udmf-virtualitem.md)* itemInfo | [入参] 虚拟根节点。 |
| [const OH_UDMF_VirtualFileCallbacks](capi-udmf-oh-udmf-virtualfilecallbacks.md)* callbacks | [入参] 虚拟文件回调。 |
| void* context | [入参] 传递给各回调的用户上下文，可为nullptr。非空时，其释放责任仅在接口成功返回非空对象后交给UDMF；返回nullptr时由调用方自行释放。 |
| [OH_UDMF_VirtualFileFinalize](capi-uds-h.md#oh_udmf_virtualfilefinalize)finalize | [入参] 用于释放`context`及其关联资源的回调。`context`非nullptr时必须提供；`context`为nullptr时允许传入，但UDMF不会调用。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| [OH_UDMF_VirtualFileInfo*](capi-udmf-oh-udmf-virtualfileinfo.md)| 成功时返回创建的虚拟文件信息；节点或回调无效、内存分配失败时返回nullptr。 |

### OH_UDMF_DestroyVirtualFileInfo()

```c
void OH_UDMF_DestroyVirtualFileInfo(OH_UDMF_VirtualFileInfo* info)
```

**描述：**

销毁虚拟文件信息。

<!--Device-void OH_UDMF_DestroyVirtualFileInfo(OH_UDMF_VirtualFileInfo* info)--><!--Device-void OH_UDMF_DestroyVirtualFileInfo(OH_UDMF_VirtualFileInfo* info)-End-->

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

**起始版本：** 26.1.0

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_UDMF_VirtualFileInfo](capi-udmf-oh-udmf-virtualfileinfo.md)* info | [入参] 待销毁的虚拟文件信息。 |

### OH_UDMF_SetFileUriVirtualEntry()

```c
int OH_UDMF_SetFileUriVirtualEntry(OH_UdsFileUri* fileUri, const OH_UDMF_VirtualFileInfo* info)
```

**描述：**

为文件Uri类型[OH_UdsFileUri](capi-udmf-oh-udsfileuri.md)附加虚拟文件信息。

<!--Device-int OH_UDMF_SetFileUriVirtualEntry(OH_UdsFileUri* fileUri, const OH_UDMF_VirtualFileInfo* info)--><!--Device-int OH_UDMF_SetFileUriVirtualEntry(OH_UdsFileUri* fileUri, const OH_UDMF_VirtualFileInfo* info)-End-->

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

**起始版本：** 26.1.0

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_UdsFileUri](capi-udmf-oh-udsfileuri.md)* fileUri | [入参] 待更新的文件Uri实例。 |
| [const OH_UDMF_VirtualFileInfo](capi-udmf-oh-udmf-virtualfileinfo.md)* info | [入参] 待附加的虚拟文件信息。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| int | 返回执行状态码。具体请参阅[Udmf_ErrCode](capi-udmf-err-code-h.md#udmf_errcode)。<ul> <li>[UDMF_E_OK](capi-udmf-err-code-h.md#udmf_errcode)表示附加成功。</li> <li>[UDMF_E_INVALID_PARAM](capi-udmf-err-code-h.md#udmf_errcode)表示`fileUri`或`info`无效。</li> </ul> |

### OH_UDMF_ClearFileUriVirtualEntry()

```c
int OH_UDMF_ClearFileUriVirtualEntry(OH_UdsFileUri* fileUri)
```

**描述：**

从文件Uri类型[OH_UdsFileUri](capi-udmf-oh-udsfileuri.md)移除虚拟文件信息。

<!--Device-int OH_UDMF_ClearFileUriVirtualEntry(OH_UdsFileUri* fileUri)--><!--Device-int OH_UDMF_ClearFileUriVirtualEntry(OH_UdsFileUri* fileUri)-End-->

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

**起始版本：** 26.1.0

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_UdsFileUri](capi-udmf-oh-udsfileuri.md)* fileUri | [入参] 待更新的文件Uri实例。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| int | 返回执行状态码。具体请参阅[Udmf_ErrCode](capi-udmf-err-code-h.md#udmf_errcode)。<ul> <li>[UDMF_E_OK](capi-udmf-err-code-h.md#udmf_errcode)表示移除成功。</li> <li>[UDMF_E_INVALID_PARAM](capi-udmf-err-code-h.md#udmf_errcode)表示`fileUri`无效。</li> </ul> |

### OH_UdsPixelMap_Create()

```c
OH_UdsPixelMap* OH_UdsPixelMap_Create()
```

**描述**

创建像素图片类型[OH_UdsPixelMap](capi-udmf-oh-udspixelmap.md)的实例对象以及指向它的指针。当不再需要使用指针时，请使用[OH_UdsPixelMap_Destroy](capi-uds-h.md#oh_udspixelmap_destroy)销毁实例对象，否则会导致内存泄漏。

**起始版本：** 13

**返回：**

| 类型                                      | 说明                                                         |
| ----------------------------------------- | ------------------------------------------------------------ |
| [OH_UdsPixelMap](capi-udmf-oh-udspixelmap.md)* | 执行成功则返回一个指向像素图片类型[OH_UdsPixelMap](capi-udmf-oh-udspixelmap.md)实例对象的指针，否则返回nullptr。 |

### OH_UdsPixelMap_Destroy()

```c
void OH_UdsPixelMap_Destroy(OH_UdsPixelMap* pThis)
```

**描述**

销毁像素图片类型[OH_UdsPixelMap](capi-udmf-oh-udspixelmap.md)的实例对象。

**起始版本：** 13


**参数：**

| 参数项                                          | 描述                                                         |
| ----------------------------------------------- | ------------------------------------------------------------ |
| [OH_UdsPixelMap](capi-udmf-oh-udspixelmap.md)* pThis | 表示指向像素图片类型[OH_UdsPixelMap](capi-udmf-oh-udspixelmap.md)实例的指针。 |

### OH_UdsPixelMap_GetType()

```c
const char* OH_UdsPixelMap_GetType(OH_UdsPixelMap* pThis)
```

**描述**

从像素图片类型[OH_UdsPixelMap](capi-udmf-oh-udspixelmap.md)实例中获取类型ID。

**起始版本：** 13


**参数：**

| 参数项                                          | 描述                                                         |
| ----------------------------------------------- | ------------------------------------------------------------ |
| [OH_UdsPixelMap](capi-udmf-oh-udspixelmap.md)* pThis | 表示指向像素图片类型[OH_UdsPixelMap](capi-udmf-oh-udspixelmap.md)实例的指针。 |

**返回：**

| 类型        | 说明                                                    |
| ----------- | ------------------------------------------------------- |
| const char* | 输入有效入参时返回类型ID的字符串指针，否则返回nullptr。 |

### OH_UdsPixelMap_GetPixelMap()

```c
void OH_UdsPixelMap_GetPixelMap(OH_UdsPixelMap* pThis, OH_PixelmapNative* pixelmapNative)
```

**描述**

从像素图片类型[OH_UdsPixelMap](capi-udmf-oh-udspixelmap.md)实例中获取像素图片[OH_PixelmapNative](../apis-image-kit/capi-pixelmap-native-h.md#oh_pixelmapnative_antialiasinglevel)实例的指针。

**起始版本：** 13


**参数：**

| 参数项                                          | 描述                                                         |
| ----------------------------------------------- | ------------------------------------------------------------ |
| [OH_UdsPixelMap](capi-udmf-oh-udspixelmap.md)* pThis | 表示指向像素图片类型[OH_UdsPixelMap](capi-udmf-oh-udspixelmap.md)实例的指针。 |
| OH_PixelmapNative* pixelmapNative               | 该参数是输出参数，表示指向像素图片[OH_PixelmapNative](../apis-image-kit/capi-pixelmap-native-h.md#oh_pixelmapnative_antialiasinglevel)实例的指针。 |

### OH_UdsPixelMap_SetPixelMap()

```c
int OH_UdsPixelMap_SetPixelMap(OH_UdsPixelMap* pThis, OH_PixelmapNative* pixelmapNative)
```

**描述**

设置像素图片类型[OH_UdsPixelMap](capi-udmf-oh-udspixelmap.md)对象的像素图片内容。

**起始版本：** 13


**参数：**

| 参数项                                          | 描述                                                         |
| ----------------------------------------------- | ------------------------------------------------------------ |
| [OH_UdsPixelMap](capi-udmf-oh-udspixelmap.md)* pThis | 表示指向像素图片类型[OH_UdsPixelMap](capi-udmf-oh-udspixelmap.md)实例的指针。 |
| OH_PixelmapNative* pixelmapNative               | 表示指向像素图片[OH_PixelmapNative](../apis-image-kit/capi-pixelmap-native-h.md#oh_pixelmapnative_antialiasinglevel)实例的指针。 |

**返回：**

| 类型 | 说明                                                         |
| ---- | ------------------------------------------------------------ |
| int  | 返回执行的状态代码。<br>若返回UDMF_E_OK，表示执行成功。<br>若返回UDMF_E_INVALID_PARAM，表示传入了无效参数。具体请参阅错误码定义[Udmf_ErrCode](capi-udmf-err-code-h.md#udmf_errcode)。 |

### OH_UdsArrayBuffer_Create()

```c
OH_UdsArrayBuffer* OH_UdsArrayBuffer_Create()
```

**描述**

创建ArrayBuffer类型[OH_UdsArrayBuffer](capi-udmf-oh-udsarraybuffer.md)的实例对象以及指向它的指针。当不再需要使用指针时，请使用[OH_UdsArrayBuffer_Destroy](capi-uds-h.md#oh_udsarraybuffer_destroy)销毁实例对象，否则会导致内存泄漏。

**起始版本：** 13

**返回：**

| 类型                                            | 说明                                                         |
| ----------------------------------------------- | ------------------------------------------------------------ |
| [OH_UdsArrayBuffer](capi-udmf-oh-udsarraybuffer.md)* | 执行成功则返回一个指向ArrayBuffer类型[OH_UdsArrayBuffer](capi-udmf-oh-udsarraybuffer.md)实例对象的指针，否则返回nullptr。 |

### OH_UdsArrayBuffer_Destroy()

```c
int OH_UdsArrayBuffer_Destroy(OH_UdsArrayBuffer* buffer)
```

**描述**

销毁ArrayBuffer类型[OH_UdsArrayBuffer](capi-udmf-oh-udsarraybuffer.md)的实例对象。

**起始版本：** 13


**参数：**

| 参数项                                                 | 描述                                                         |
| ------------------------------------------------------ | ------------------------------------------------------------ |
| [OH_UdsArrayBuffer](capi-udmf-oh-udsarraybuffer.md)* buffer | 表示指向ArrayBuffer类型[OH_UdsArrayBuffer](capi-udmf-oh-udsarraybuffer.md)实例的指针。 |

**返回：**

| 类型 | 说明                                                         |
| ---- | ------------------------------------------------------------ |
| int  | 返回执行的状态代码。<br>若返回UDMF_E_OK，表示执行成功。<br>若返回UDMF_E_INVALID_PARAM，表示传入了无效参数。具体请参阅错误码定义[Udmf_ErrCode](capi-udmf-err-code-h.md#udmf_errcode)。 |

### OH_UdsArrayBuffer_SetData()

```c
int OH_UdsArrayBuffer_SetData(OH_UdsArrayBuffer* buffer, unsigned char* data, unsigned int len)
```

**描述**

设置ArrayBuffer类型[OH_UdsArrayBuffer](capi-udmf-oh-udsarraybuffer.md)对象的数据内容。

**起始版本：** 13


**参数：**

| 参数项                                                 | 描述                                                         |
| ------------------------------------------------------ | ------------------------------------------------------------ |
| [OH_UdsArrayBuffer](capi-udmf-oh-udsarraybuffer.md)* buffer | 表示指向ArrayBuffer类型[OH_UdsArrayBuffer](capi-udmf-oh-udsarraybuffer.md)实例的指针。 |
| unsigned char* data                                    | 表示用户自定义的ArrayBuffer数据。                            |
| unsigned int len                                       | 表示用户自定义的ArrayBuffer数据的大小。                      |

**返回：**

| 类型 | 说明                                                         |
| ---- | ------------------------------------------------------------ |
| int  | 返回执行的状态代码。<br>若返回UDMF_E_OK，表示执行成功。<br>若返回UDMF_E_INVALID_PARAM，表示传入了无效参数。具体请参阅错误码定义[Udmf_ErrCode](capi-udmf-err-code-h.md#udmf_errcode)。 |

### OH_UdsArrayBuffer_GetData()

```c
int OH_UdsArrayBuffer_GetData(OH_UdsArrayBuffer* buffer, unsigned char** data, unsigned int* len)
```

**描述**

从ArrayBuffer类型[OH_UdsArrayBuffer](capi-udmf-oh-udsarraybuffer.md)实例中获取用户自定义的ArrayBuffer数据内容。

**起始版本：** 13


**参数：**

| 参数项                                                 | 描述                                                         |
| ------------------------------------------------------ | ------------------------------------------------------------ |
| [OH_UdsArrayBuffer](capi-udmf-oh-udsarraybuffer.md)* buffer | 表示指向ArrayBuffer类型[OH_UdsArrayBuffer](capi-udmf-oh-udsarraybuffer.md)实例的指针。 |
| unsigned char** data                                   | 该参数是输出参数，表示用户自定义的ArrayBuffer数据。          |
| unsigned int* len                                      | 该参数是输出参数，表示用户自定义的ArrayBuffer数据的大小。    |

**返回：**

| 类型 | 说明                                                         |
| ---- | ------------------------------------------------------------ |
| int  | 返回执行的状态代码。<br>若返回UDMF_E_OK，表示执行成功。<br>若返回UDMF_E_INVALID_PARAM，表示传入了无效参数。具体请参阅错误码定义[Udmf_ErrCode](capi-udmf-err-code-h.md#udmf_errcode)。 |

### OH_UdsContentForm_Create()

```c
OH_UdsContentForm* OH_UdsContentForm_Create()
```

**描述**

创建内容卡片类型[OH_UdsContentForm](capi-udmf-oh-udscontentform.md)指针及实例对象。当不再需要使用指针时，请使用[OH_UdsContentForm_Destroy](capi-uds-h.md#oh_udscontentform_destroy)销毁实例对象，否则会导致内存泄漏。

**起始版本：** 14

**返回：**

| 类型                                            | 说明                                                         |
| ----------------------------------------------- | ------------------------------------------------------------ |
| [OH_UdsContentForm](capi-udmf-oh-udscontentform.md)* | 执行成功则返回一个指向内容卡片类型[OH_UdsContentForm](capi-udmf-oh-udscontentform.md)实例对象的指针，否则返回nullptr。 |

### OH_UdsContentForm_Destroy()

```c
void OH_UdsContentForm_Destroy(OH_UdsContentForm* pThis)
```

**描述**

销毁内容卡片类型数据[OH_UdsContentForm](capi-udmf-oh-udscontentform.md)指针指向的实例对象。

**起始版本：** 14


**参数：**

| 参数项                                                | 描述                                                         |
| ----------------------------------------------------- | ------------------------------------------------------------ |
| [OH_UdsContentForm](capi-udmf-oh-udscontentform.md)* pThis | 表示指向[OH_UdsContentForm](capi-udmf-oh-udscontentform.md)实例的指针。 |

### OH_UdsContentForm_GetType()

```c
const char* OH_UdsContentForm_GetType(OH_UdsContentForm* pThis)
```

**描述**

从内容卡片类型[OH_UdsContentForm](capi-udmf-oh-udscontentform.md)中获取类型ID。

**起始版本：** 14


**参数：**

| 参数项                                                | 描述                                                         |
| ----------------------------------------------------- | ------------------------------------------------------------ |
| [OH_UdsContentForm](capi-udmf-oh-udscontentform.md)* pThis | 表示指向[OH_UdsContentForm](capi-udmf-oh-udscontentform.md)实例的指针。 |

**返回：**

| 类型        | 说明                                                    |
| ----------- | ------------------------------------------------------- |
| const char* | 输入有效入参时返回类型ID的字符串指针，否则返回nullptr。 |

### OH_UdsContentForm_GetThumbData()

```c
int OH_UdsContentForm_GetThumbData(OH_UdsContentForm* pThis, unsigned char** thumbData, unsigned int* len)
```

**描述**

从内容卡片类型[OH_UdsContentForm](capi-udmf-oh-udscontentform.md)中获取图片数据。

**起始版本：** 14


**参数：**

| 参数项                                                | 描述                                                         |
| ----------------------------------------------------- | ------------------------------------------------------------ |
| [OH_UdsContentForm](capi-udmf-oh-udscontentform.md)* pThis | 表示指向[OH_UdsContentForm](capi-udmf-oh-udscontentform.md)实例的指针。 |
| unsigned char** thumbData                             | 该参数是输出参数，表示内容卡片中的图片二进制数据。           |
| unsigned int* len                                     | 该参数是输出参数，表示内容卡片中的图片二进制数据的大小。     |

**返回：**

| 类型 | 说明                                                         |
| ---- | ------------------------------------------------------------ |
| int  | 返回执行的状态代码。<br>若返回UDMF_E_OK，表示执行成功。<br>若返回UDMF_E_INVALID_PARAM，表示传入了无效参数。<br>若返回UDMF_ERR，表示内部数据错误。可能的原因是服务故障或者内存不足等。具体请参阅错误码定义[Udmf_ErrCode](capi-udmf-err-code-h.md#udmf_errcode)。 |

### OH_UdsContentForm_GetDescription()

```c
const char* OH_UdsContentForm_GetDescription(OH_UdsContentForm* pThis)
```

**描述**

从内容卡片类型[OH_UdsContentForm](capi-udmf-oh-udscontentform.md)中获取描述信息。

**起始版本：** 14


**参数：**

| 参数项                                                | 描述                                                         |
| ----------------------------------------------------- | ------------------------------------------------------------ |
| [OH_UdsContentForm](capi-udmf-oh-udscontentform.md)* pThis | 表示指向[OH_UdsContentForm](capi-udmf-oh-udscontentform.md)实例的指针。 |

**返回：**

| 类型        | 说明                                                      |
| ----------- | --------------------------------------------------------- |
| const char* | 输入有效入参时返回描述信息的字符串指针，否则返回nullptr。 |

### OH_UdsContentForm_GetTitle()

```c
const char* OH_UdsContentForm_GetTitle(OH_UdsContentForm* pThis)
```

**描述**

从内容卡片类型[OH_UdsContentForm](capi-udmf-oh-udscontentform.md)中获取标题信息。

**起始版本：** 14


**参数：**

| 参数项                                                | 描述                                                         |
| ----------------------------------------------------- | ------------------------------------------------------------ |
| [OH_UdsContentForm](capi-udmf-oh-udscontentform.md)* pThis | 表示指向[OH_UdsContentForm](capi-udmf-oh-udscontentform.md)实例的指针。 |

**返回：**

| 类型        | 说明                                                      |
| ----------- | --------------------------------------------------------- |
| const char* | 输入有效入参时返回标题信息的字符串指针，否则返回nullptr。 |

### OH_UdsContentForm_GetAppIcon()

```c
int OH_UdsContentForm_GetAppIcon(OH_UdsContentForm* pThis, unsigned char** appIcon, unsigned int* len)
```

**描述**

从内容卡片类型[OH_UdsContentForm](capi-udmf-oh-udscontentform.md)中获取应用图标数据。

**起始版本：** 14


**参数：**

| 参数项                                                | 描述                                                         |
| ----------------------------------------------------- | ------------------------------------------------------------ |
| [OH_UdsContentForm](capi-udmf-oh-udscontentform.md)* pThis | 表示指向[OH_UdsContentForm](capi-udmf-oh-udscontentform.md)实例的指针。 |
| unsigned char** appIcon                               | 该参数是输出参数，表示内容卡片中的应用图标二进制数据。       |
| unsigned int* len                                     | 该参数是输出参数，表示内容卡片中的应用图标二进制数据的大小。 |

**返回：**

| 类型 | 说明                                                         |
| ---- | ------------------------------------------------------------ |
| int  | 返回执行的状态代码。<br>若返回UDMF_E_OK，表示执行成功。<br>若返回UDMF_E_INVALID_PARAM，表示传入了无效参数。<br>若返回UDMF_ERR，表示内部数据错误。可能的原因是服务故障或者内存不足等。具体请参阅错误码定义[Udmf_ErrCode](capi-udmf-err-code-h.md#udmf_errcode)。 |

### OH_UdsContentForm_GetAppName()

```c
const char* OH_UdsContentForm_GetAppName(OH_UdsContentForm* pThis)
```

**描述**

从内容卡片类型[OH_UdsContentForm](capi-udmf-oh-udscontentform.md)中获取应用名称信息。

**起始版本：** 14


**参数：**

| 参数项                                                | 描述                                                         |
| ----------------------------------------------------- | ------------------------------------------------------------ |
| [OH_UdsContentForm](capi-udmf-oh-udscontentform.md)* pThis | 表示指向[OH_UdsContentForm](capi-udmf-oh-udscontentform.md)实例的指针。 |

**返回：**

| 类型        | 说明                                                         |
| ----------- | ------------------------------------------------------------ |
| const char* | 输入有效入参时返回应用名称信息的字符串指针，否则返回nullptr。 |

### OH_UdsContentForm_GetLinkUri()

```c
const char* OH_UdsContentForm_GetLinkUri(OH_UdsContentForm* pThis)
```

**描述**

从内容卡片类型[OH_UdsContentForm](capi-udmf-oh-udscontentform.md)中获取超链接信息。

**起始版本：** 14


**参数：**

| 参数项                                                | 描述                                                         |
| ----------------------------------------------------- | ------------------------------------------------------------ |
| [OH_UdsContentForm](capi-udmf-oh-udscontentform.md)* pThis | 表示指向[OH_UdsContentForm](capi-udmf-oh-udscontentform.md)实例的指针。 |

**返回：**

| 类型        | 说明                                                    |
| ----------- | ------------------------------------------------------- |
| const char* | 输入有效入参时返回超链接的字符串指针，否则返回nullptr。 |

### OH_UdsContentForm_SetThumbData()

```c
int OH_UdsContentForm_SetThumbData(OH_UdsContentForm* pThis, const unsigned char* thumbData, unsigned int len)
```

**描述**

设置内容卡片类型[OH_UdsContentForm](capi-udmf-oh-udscontentform.md)中的图片数据。

**起始版本：** 14


**参数：**

| 参数项                                                | 描述                                                         |
| ----------------------------------------------------- | ------------------------------------------------------------ |
| [OH_UdsContentForm](capi-udmf-oh-udscontentform.md)* pThis | 表示指向[OH_UdsContentForm](capi-udmf-oh-udscontentform.md)实例的指针。 |
| const unsigned char* thumbData                        | 表示内容卡片中的图片二进制数据。                             |
| unsigned int len                                      | 表示内容卡片中的图片二进制数据的大小。                       |

**返回：**

| 类型 | 说明                                                         |
| ---- | ------------------------------------------------------------ |
| int  | 返回执行的状态代码。<br>若返回UDMF_E_OK，表示执行成功。<br>若返回UDMF_E_INVALID_PARAM，表示传入了无效参数。具体请参阅错误码定义[Udmf_ErrCode](capi-udmf-err-code-h.md#udmf_errcode)。 |

### OH_UdsContentForm_SetDescription()

```c
int OH_UdsContentForm_SetDescription(OH_UdsContentForm* pThis, const char* description)
```

**描述**

设置内容卡片类型[OH_UdsContentForm](capi-udmf-oh-udscontentform.md)中的描述信息。

**起始版本：** 14


**参数：**

| 参数项                                                | 描述                                                         |
| ----------------------------------------------------- | ------------------------------------------------------------ |
| [OH_UdsContentForm](capi-udmf-oh-udscontentform.md)* pThis | 表示指向[OH_UdsContentForm](capi-udmf-oh-udscontentform.md)实例的指针。 |
| const char* description                               | 表示描述信息。                                               |

**返回：**

| 类型 | 说明                                                         |
| ---- | ------------------------------------------------------------ |
| int  | 返回执行的状态代码。<br>若返回UDMF_E_OK，表示执行成功。<br>若返回UDMF_E_INVALID_PARAM，表示传入了无效参数。具体请参阅错误码定义[Udmf_ErrCode](capi-udmf-err-code-h.md#udmf_errcode)。|

### OH_UdsContentForm_SetTitle()

```c
int OH_UdsContentForm_SetTitle(OH_UdsContentForm* pThis, const char* title)
```

**描述**

设置内容卡片类型[OH_UdsContentForm](capi-udmf-oh-udscontentform.md)中的标题信息。

**起始版本：** 14


**参数：**

| 参数项                                                | 描述                                                         |
| ----------------------------------------------------- | ------------------------------------------------------------ |
| [OH_UdsContentForm](capi-udmf-oh-udscontentform.md)* pThis | 表示指向[OH_UdsContentForm](capi-udmf-oh-udscontentform.md)实例的指针。 |
| const char* title                                     | 表示标题信息。                                               |

**返回：**

| 类型 | 说明                                                         |
| ---- | ------------------------------------------------------------ |
| int  | 返回执行的状态代码。<br>若返回UDMF_E_OK，表示执行成功。<br>若返回UDMF_E_INVALID_PARAM，表示传入了无效参数。具体请参阅错误码定义[Udmf_ErrCode](capi-udmf-err-code-h.md#udmf_errcode)。|

### OH_UdsContentForm_SetAppIcon()

```c
int OH_UdsContentForm_SetAppIcon(OH_UdsContentForm* pThis, const unsigned char* appIcon, unsigned int len)
```

**描述**

设置内容卡片类型[OH_UdsContentForm](capi-udmf-oh-udscontentform.md)中的应用图标数据。

**起始版本：** 14


**参数：**

| 参数项                                                | 描述                                                         |
| ----------------------------------------------------- | ------------------------------------------------------------ |
| [OH_UdsContentForm](capi-udmf-oh-udscontentform.md)* pThis | 表示指向[OH_UdsContentForm](capi-udmf-oh-udscontentform.md)实例的指针。 |
| const unsigned char* appIcon                          | 表示内容卡片中的应用图标二进制数据。                         |
| unsigned int len                                      | 表示内容卡片中的应用图标二进制数据的大小。                   |

**返回：**

| 类型 | 说明                                                         |
| ---- | ------------------------------------------------------------ |
| int  | 返回执行的状态代码。<br>若返回UDMF_E_OK，表示执行成功。<br>若返回UDMF_E_INVALID_PARAM，表示传入了无效参数。具体请参阅错误码定义[Udmf_ErrCode](capi-udmf-err-code-h.md#udmf_errcode)。 |

### OH_UdsContentForm_SetAppName()

```c
int OH_UdsContentForm_SetAppName(OH_UdsContentForm* pThis, const char* appName)
```

**描述**

设置内容卡片类型[OH_UdsContentForm](capi-udmf-oh-udscontentform.md)中的应用名称数据。

**起始版本：** 14


**参数：**

| 参数项                                                | 描述                                                         |
| ----------------------------------------------------- | ------------------------------------------------------------ |
| [OH_UdsContentForm](capi-udmf-oh-udscontentform.md)* pThis | 表示指向[OH_UdsContentForm](capi-udmf-oh-udscontentform.md)实例的指针。 |
| const char* appName                                   | 表示内容卡片中的应用名称。                                   |

**返回：**

| 类型 | 说明                                                         |
| ---- | ------------------------------------------------------------ |
| int  | 返回执行的状态代码。<br>若返回UDMF_E_OK，表示执行成功。<br>若返回UDMF_E_INVALID_PARAM，表示传入了无效参数。具体请参阅错误码定义[Udmf_ErrCode](capi-udmf-err-code-h.md#udmf_errcode)。 |

### OH_UdsContentForm_SetLinkUri()

```c
int OH_UdsContentForm_SetLinkUri(OH_UdsContentForm* pThis, const char* linkUri)
```

**描述**

设置内容卡片类型[OH_UdsContentForm](capi-udmf-oh-udscontentform.md)中的超链接数据。

**起始版本：** 14


**参数：**

| 参数项                                                | 描述                                                         |
| ----------------------------------------------------- | ------------------------------------------------------------ |
| [OH_UdsContentForm](capi-udmf-oh-udscontentform.md)* pThis | 表示指向[OH_UdsContentForm](capi-udmf-oh-udscontentform.md)实例的指针。 |
| const char* linkUri                                   | 表示内容卡片中的超链接。                                     |

**返回：**

| 类型 | 说明                                                         |
| ---- | ------------------------------------------------------------ |
| int  | 返回执行的状态代码。<br>若返回UDMF_E_OK，表示执行成功。<br>若返回UDMF_E_INVALID_PARAM，表示传入了无效参数。具体请参阅错误码定义[Udmf_ErrCode](capi-udmf-err-code-h.md#udmf_errcode)。 |


### OH_UdsPlainText_GetDetails()

```c
int OH_UdsPlainText_GetDetails(OH_UdsPlainText* pThis, OH_UdsDetails* details)
```

**描述**

从纯文本类型[OH_UdsPlainText](capi-udmf-oh-udsplaintext.md)中获取字典类型[OH_UdsDetails](capi-udmf-oh-udsdetails.md)实例的指针。

**起始版本：** 22

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_UdsPlainText](capi-udmf-oh-udsplaintext.md)* pThis | 表示指向纯文本类型[OH_UdsPlainText](capi-udmf-oh-udsplaintext.md)实例的指针。 |
| [OH_UdsDetails](capi-udmf-oh-udsdetails.md)* details | 该参数是输出参数，表示指向字典类型[OH_UdsDetails](capi-udmf-oh-udsdetails.md)实例的指针，该指针不能为空。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int | 返回执行的状态代码。<br>若返回UDMF_E_OK，表示执行成功。<br>若返回UDMF_E_INVALID_PARAM，表示传入了无效参数。具体请参阅错误码定义[Udmf_ErrCode](capi-udmf-err-code-h.md#udmf_errcode)。 |

### OH_UdsPlainText_SetDetails()

```c
int OH_UdsPlainText_SetDetails(OH_UdsPlainText* pThis, const OH_UdsDetails* details)
```

**描述**

设置纯文本类型[OH_UdsPlainText](capi-udmf-oh-udsplaintext.md)中的字典类型[OH_UdsDetails](capi-udmf-oh-udsdetails.md)参数。

**起始版本：** 22

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_UdsPlainText](capi-udmf-oh-udsplaintext.md)* pThis | 表示指向纯文本类型[OH_UdsPlainText](capi-udmf-oh-udsplaintext.md)实例的指针。 |
| const [OH_UdsDetails](capi-udmf-oh-udsdetails.md)* details | 表示指向字典类型[OH_UdsDetails](capi-udmf-oh-udsdetails.md)实例的指针，该指针不能为空。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int | 返回执行的状态代码。<br>若返回UDMF_E_OK，表示执行成功。<br>若返回UDMF_E_INVALID_PARAM，表示传入了无效参数。具体请参阅错误码定义[Udmf_ErrCode](capi-udmf-err-code-h.md#udmf_errcode)。 |

### OH_UdsHyperlink_GetDetails()

```c
int OH_UdsHyperlink_GetDetails(OH_UdsHyperlink* pThis, OH_UdsDetails* details)
```

**描述**

从超链接类型[OH_UdsHyperlink](capi-udmf-oh-udshyperlink.md)中获取字典类型[OH_UdsDetails](capi-udmf-oh-udsdetails.md)实例的指针。

**起始版本：** 22

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_UdsHyperlink](capi-udmf-oh-udshyperlink.md)* pThis | 表示指向超链接类型[OH_UdsHyperlink](capi-udmf-oh-udshyperlink.md)实例的指针。 |
| [OH_UdsDetails](capi-udmf-oh-udsdetails.md)* details | 该参数是输出参数，表示指向字典类型[OH_UdsDetails](capi-udmf-oh-udsdetails.md)实例的指针，该指针不能为空。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int | 返回执行的状态代码。<br>若返回UDMF_E_OK，表示执行成功。<br>若返回UDMF_E_INVALID_PARAM，表示传入了无效参数。具体请参阅错误码定义[Udmf_ErrCode](capi-udmf-err-code-h.md#udmf_errcode)。 |

### OH_UdsHyperlink_SetDetails()

```c
int OH_UdsHyperlink_SetDetails(OH_UdsHyperlink* pThis, const OH_UdsDetails* details)
```

**描述**

设置超链接类型[OH_UdsHyperlink](capi-udmf-oh-udshyperlink.md)实例中的字典类型[OH_UdsDetails](capi-udmf-oh-udsdetails.md)参数。

**起始版本：** 22

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_UdsHyperlink](capi-udmf-oh-udshyperlink.md)* pThis | 表示指向超链接类型[OH_UdsHyperlink](capi-udmf-oh-udshyperlink.md)实例的指针。 |
| const [OH_UdsDetails](capi-udmf-oh-udsdetails.md)* details | 表示指向字典类型[OH_UdsDetails](capi-udmf-oh-udsdetails.md)实例的指针，该指针不能为空。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int | 返回执行的状态代码。<br>若返回UDMF_E_OK，表示执行成功。<br>若返回UDMF_E_INVALID_PARAM，表示传入了无效参数。具体请参阅错误码定义[Udmf_ErrCode](capi-udmf-err-code-h.md#udmf_errcode)。 |

### OH_UdsHtml_GetDetails()

```c
int OH_UdsHtml_GetDetails(OH_UdsHtml* pThis, OH_UdsDetails* details)
```

**描述**

从超文本标记语言类型[OH_UdsHtml](capi-udmf-oh-udshtml.md)对象中获取字典类型[OH_UdsDetails](capi-udmf-oh-udsdetails.md)实例的指针。

**起始版本：** 22

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_UdsHtml](capi-udmf-oh-udshtml.md)* pThis | 表示指向超文本标记语言类型[OH_UdsHtml](capi-udmf-oh-udshtml.md)实例的指针。 |
| [OH_UdsDetails](capi-udmf-oh-udsdetails.md)* details | 该参数是输出参数，表示指向字典类型[OH_UdsDetails](capi-udmf-oh-udsdetails.md)实例的指针，该指针不能为空。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int | 返回执行的状态代码。<br>若返回UDMF_E_OK，表示执行成功。<br>若返回UDMF_E_INVALID_PARAM，表示传入了无效参数。具体请参阅错误码定义[Udmf_ErrCode](capi-udmf-err-code-h.md#udmf_errcode)。 |

### OH_UdsHtml_SetDetails()

```c
int OH_UdsHtml_SetDetails(OH_UdsHtml* pThis, const OH_UdsDetails* details)
```

**描述**

设置超文本标记语言类型[OH_UdsHtml](capi-udmf-oh-udshtml.md)中的字典类型[OH_UdsDetails](capi-udmf-oh-udsdetails.md)参数。

**起始版本：** 22

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_UdsHtml](capi-udmf-oh-udshtml.md)* pThis | 表示指向超文本标记语言类型[OH_UdsHtml](capi-udmf-oh-udshtml.md)实例的指针。 |
| const [OH_UdsDetails](capi-udmf-oh-udsdetails.md)* details | 表示指向字典类型[OH_UdsDetails](capi-udmf-oh-udsdetails.md)实例的指针，该指针不能为空。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int | 返回执行的状态代码。<br>若返回UDMF_E_OK，表示执行成功。<br>若返回UDMF_E_INVALID_PARAM，表示传入了无效参数。具体请参阅错误码定义[Udmf_ErrCode](capi-udmf-err-code-h.md#udmf_errcode)。 |

### OH_UdsAppItem_GetDetails()

```c
int OH_UdsAppItem_GetDetails(OH_UdsAppItem* pThis, OH_UdsDetails* details)
```

**描述**

从桌面图标类型[OH_UdsAppItem](capi-udmf-oh-udsappitem.md)实例中获取字典类型[OH_UdsDetails](capi-udmf-oh-udsdetails.md)实例的指针。

**起始版本：** 22

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_UdsAppItem](capi-udmf-oh-udsappitem.md)* pThis | 表示指向桌面图标类型[OH_UdsAppItem](capi-udmf-oh-udsappitem.md)对象的指针。 |
| [OH_UdsDetails](capi-udmf-oh-udsdetails.md)* details | 该参数是输出参数，表示指向字典类型[OH_UdsDetails](capi-udmf-oh-udsdetails.md)实例的指针，该指针不能为空。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int | 返回执行的状态代码。<br>若返回UDMF_E_OK，表示执行成功。<br>若返回UDMF_E_INVALID_PARAM，表示传入了无效参数。具体请参阅错误码定义[Udmf_ErrCode](capi-udmf-err-code-h.md#udmf_errcode)。 |

### OH_UdsAppItem_SetDetails()

```c
int OH_UdsAppItem_SetDetails(OH_UdsAppItem* pThis, const OH_UdsDetails* details)
```

**描述**

设置桌面图标类型[OH_UdsAppItem](capi-udmf-oh-udsappitem.md)对象的字典类型[OH_UdsDetails](capi-udmf-oh-udsdetails.md)参数。

**起始版本：** 22

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_UdsAppItem](capi-udmf-oh-udsappitem.md)* pThis | 表示指向桌面图标类型[OH_UdsAppItem](capi-udmf-oh-udsappitem.md)对象的指针。 |
| const [OH_UdsDetails](capi-udmf-oh-udsdetails.md)* details | 表示指向字典类型[OH_UdsDetails](capi-udmf-oh-udsdetails.md)实例的指针，该指针不能为空。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int | 返回执行的状态代码。<br>若返回UDMF_E_OK，表示执行成功。<br>若返回UDMF_E_INVALID_PARAM，表示传入了无效参数。具体请参阅错误码定义[Udmf_ErrCode](capi-udmf-err-code-h.md#udmf_errcode)。 |

### OH_UdsFileUri_GetDetails()

```c
int OH_UdsFileUri_GetDetails(OH_UdsFileUri* pThis, OH_UdsDetails* details)
```

**描述**

从文件Uri类型[OH_UdsFileUri](capi-udmf-oh-udsfileuri.md)实例中获取字典类型[OH_UdsDetails](capi-udmf-oh-udsdetails.md)实例的指针。

**起始版本：** 22

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_UdsFileUri](capi-udmf-oh-udsfileuri.md)* pThis | 表示指向文件Uri类型[OH_UdsFileUri](capi-udmf-oh-udsfileuri.md)实例的指针。 |
| [OH_UdsDetails](capi-udmf-oh-udsdetails.md)* details | 该参数是输出参数，表示指向字典类型[OH_UdsDetails](capi-udmf-oh-udsdetails.md)实例的指针，该指针不能为空。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int | 返回执行的状态代码。<br>若返回UDMF_E_OK，表示执行成功。<br>若返回UDMF_E_INVALID_PARAM，表示传入了无效参数。具体请参阅错误码定义[Udmf_ErrCode](capi-udmf-err-code-h.md#udmf_errcode)。 |

### OH_UdsFileUri_SetDetails()

```c
int OH_UdsFileUri_SetDetails(OH_UdsFileUri* pThis, const OH_UdsDetails* details)
```

**描述**

设置文件Uri类型[OH_UdsFileUri](capi-udmf-oh-udsfileuri.md)对象的字典类型[OH_UdsDetails](capi-udmf-oh-udsdetails.md)参数。

**起始版本：** 22

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_UdsFileUri](capi-udmf-oh-udsfileuri.md)* pThis | 表示指向文件Uri类型[OH_UdsFileUri](capi-udmf-oh-udsfileuri.md)实例的指针。 |
| const [OH_UdsDetails](capi-udmf-oh-udsdetails.md)* details | 表示指向字典类型[OH_UdsDetails](capi-udmf-oh-udsdetails.md)实例的指针，该指针不能为空。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int | 返回执行的状态代码。<br>若返回UDMF_E_OK，表示执行成功。<br>若返回UDMF_E_INVALID_PARAM，表示传入了无效参数。具体请参阅错误码定义[Udmf_ErrCode](capi-udmf-err-code-h.md#udmf_errcode)。 |

### OH_UdsPixelMap_GetDetails()

```c
int OH_UdsPixelMap_GetDetails(OH_UdsPixelMap* pThis, OH_UdsDetails* details)
```

**描述**

从像素图片类型[OH_UdsPixelMap](capi-udmf-oh-udspixelmap.md)实例中获取字典类型[OH_UdsDetails](capi-udmf-oh-udsdetails.md)实例的指针。

**起始版本：** 22

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_UdsPixelMap](capi-udmf-oh-udspixelmap.md)* pThis | 表示指向像素图片类型[OH_UdsPixelMap](capi-udmf-oh-udspixelmap.md)实例的指针。 |
| [OH_UdsDetails](capi-udmf-oh-udsdetails.md)* details | 该参数是输出参数，表示指向字典类型[OH_UdsDetails](capi-udmf-oh-udsdetails.md)实例的指针，该指针不能为空。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int | 返回执行的状态代码。<br>若返回UDMF_E_OK，表示执行成功。<br>若返回UDMF_E_INVALID_PARAM，表示传入了无效参数。具体请参阅错误码定义[Udmf_ErrCode](capi-udmf-err-code-h.md#udmf_errcode)。 |

### OH_UdsPixelMap_SetDetails()

```c
int OH_UdsPixelMap_SetDetails(OH_UdsPixelMap* pThis, const OH_UdsDetails* details)
```

**描述**

设置像素图片类型[OH_UdsPixelMap](capi-udmf-oh-udspixelmap.md)对象的字典类型[OH_UdsDetails](capi-udmf-oh-udsdetails.md)参数。

**起始版本：** 22

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_UdsPixelMap](capi-udmf-oh-udspixelmap.md)* pThis | 表示指向像素图片类型[OH_UdsPixelMap](capi-udmf-oh-udspixelmap.md)实例的指针。 |
| const [OH_UdsDetails](capi-udmf-oh-udsdetails.md)* details | 表示指向字典类型[OH_UdsDetails](capi-udmf-oh-udsdetails.md)实例的指针，该指针不能为空。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int | 返回执行的状态代码。<br>若返回UDMF_E_OK，表示执行成功。<br>若返回UDMF_E_INVALID_PARAM，表示传入了无效参数。具体请参阅错误码定义[Udmf_ErrCode](capi-udmf-err-code-h.md#udmf_errcode)。 |

### OH_UdsDetails_Create()

```c
OH_UdsDetails* OH_UdsDetails_Create()
```

**描述**

创建字典类型[OH_UdsDetails](capi-udmf-oh-udsdetails.md)指针及实例对象。

当不再需要使用指针时，请使用[OH_UdsDetails_Destroy](capi-uds-h.md#oh_udsdetails_destroy)销毁实例对象，否则会导致内存泄漏。

**起始版本：** 22

**返回：**

| 类型 | 说明 |
| -- | -- |
| [OH_UdsDetails](capi-udmf-oh-udsdetails.md)* | 执行成功则返回一个指向字典类型[OH_UdsDetails](capi-udmf-oh-udsdetails.md)实例对象的指针，否则返回nullptr。 |

### OH_UdsDetails_Destroy()

```c
void OH_UdsDetails_Destroy(OH_UdsDetails* pThis)
```

**描述**

销毁字典类型[OH_UdsDetails](capi-udmf-oh-udsdetails.md)指针指向的实例对象。

**起始版本：** 22

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_UdsDetails](capi-udmf-oh-udsdetails.md)* pThis | 表示指向字典类型[OH_UdsDetails](capi-udmf-oh-udsdetails.md)实例的指针。 |

### OH_UdsDetails_HasKey()

```c
bool OH_UdsDetails_HasKey(const OH_UdsDetails* pThis, const char* key)
```

**描述**

检查字典类型[OH_UdsDetails](capi-udmf-oh-udsdetails.md)中是否存在指定键。

**起始版本：** 22

**参数：**

| 参数项 | 描述 |
| -- | -- |
| const [OH_UdsDetails](capi-udmf-oh-udsdetails.md)* pThis | 表示指向字典类型[OH_UdsDetails](capi-udmf-oh-udsdetails.md)实例的指针。 |
| const char* key | 表示字典类型中键值对的键。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| bool | 返回查找结果的状态。返回false表示不存在指定键，返回true表示存在指定键。 |

### OH_UdsDetails_Remove()

```c
int OH_UdsDetails_Remove(OH_UdsDetails* pThis, const char* key)
```

**描述**

删除字典类型[OH_UdsDetails](capi-udmf-oh-udsdetails.md)中指定键值对。

**起始版本：** 22

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_UdsDetails](capi-udmf-oh-udsdetails.md)* pThis | 表示指向字典类型[OH_UdsDetails](capi-udmf-oh-udsdetails.md)实例的指针。 |
| const char* key | 表示字典类型中键值对的键。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int | 返回执行的状态代码。<br>若返回UDMF_E_OK，表示执行成功。<br>若返回UDMF_E_INVALID_PARAM，表示传入了无效参数。具体请参阅错误码定义[Udmf_ErrCode](capi-udmf-err-code-h.md#udmf_errcode)。 |

### OH_UdsDetails_Clear()

```c
int OH_UdsDetails_Clear(OH_UdsDetails* pThis)
```

**描述**

清除字典类型[OH_UdsDetails](capi-udmf-oh-udsdetails.md)中所有数据。

**起始版本：** 22

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_UdsDetails](capi-udmf-oh-udsdetails.md)* pThis | 表示指向字典类型[OH_UdsDetails](capi-udmf-oh-udsdetails.md)实例的指针。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int | 返回执行的状态代码。<br>若返回UDMF_E_OK，表示执行成功。<br>若返回UDMF_E_INVALID_PARAM，表示传入了无效参数。具体请参阅错误码定义[Udmf_ErrCode](capi-udmf-err-code-h.md#udmf_errcode)。 |

### OH_UdsDetails_SetValue()

```c
int OH_UdsDetails_SetValue(OH_UdsDetails* pThis, const char* key, const char* value)
```

**描述**

向字典类型[OH_UdsDetails](capi-udmf-oh-udsdetails.md)中添加键值对数据。

**起始版本：** 22

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_UdsDetails](capi-udmf-oh-udsdetails.md)* pThis | 表示指向字典类型[OH_UdsDetails](capi-udmf-oh-udsdetails.md)实例的指针。 |
| const char* key | 表示字典类型中键值对的键。 |
| const char* value | 表示字典类型中键值对的值。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int | 返回执行的状态代码。<br>若返回UDMF_E_OK，表示执行成功。<br>若返回UDMF_E_INVALID_PARAM，表示传入了无效参数。具体请参阅错误码定义[Udmf_ErrCode](capi-udmf-err-code-h.md#udmf_errcode)。 |

### OH_UdsDetails_GetValue()

```c
const char* OH_UdsDetails_GetValue(const OH_UdsDetails* pThis, const char* key)
```

**描述**

获取字典类型[OH_UdsDetails](capi-udmf-oh-udsdetails.md)中指定的键对应的值。

**起始版本：** 22

**参数：**

| 参数项 | 描述 |
| -- | -- |
| const [OH_UdsDetails](capi-udmf-oh-udsdetails.md)* pThis | 表示指向字典类型[OH_UdsDetails](capi-udmf-oh-udsdetails.md)实例的指针。 |
| const char* key | 表示字典类型中键值对的键。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| const char* | 当入参有效时返回指向字典类型中值的指针，否则返回nullptr。 |

### OH_UdsDetails_GetAllKeys()

```c
char** OH_UdsDetails_GetAllKeys(OH_UdsDetails* pThis, unsigned int* count)
```

**描述**

获取字典类型[OH_UdsDetails](capi-udmf-oh-udsdetails.md)中所有键的结果集。

**起始版本：** 22

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_UdsDetails](capi-udmf-oh-udsdetails.md)* pThis | 表示指向字典类型[OH_UdsDetails](capi-udmf-oh-udsdetails.md)实例的指针。 |
| unsigned int* count | 该参数是输出参数，表示结果集的长度。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| char** | 执行成功时返回字典类型中键的结果集，否则返回nullptr。<br>当使用[OH_UdsDetails_Destroy](capi-uds-h.md#oh_udsdetails_destroy)销毁字典类型[OH_UdsDetails](capi-udmf-oh-udsdetails.md)指针指向的实例对象，该返回值也会被释放。 |

### OH_UdsHtml_SetAuthPolicy()

```c
int OH_UdsHtml_SetAuthPolicy(OH_UdsHtml* pThis, uint32_t authPolicy)
```

**描述**

给[OH_UdsHtml](capi-udmf-oh-udshtml.md)设置授权策略。

> **说明：** 
>
> 此授权策略仅在拖拽场景下生效，其他场景不生效。

**起始版本：** 26.0.0

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_UdsHtml](capi-udmf-oh-udshtml.md)* pThis | 表示指向[OH_UdsHtml](capi-udmf-oh-udshtml.md)实例的指针。 |
| uint32_t authPolicy | 表示拖拽场景下的URI授权策略，默认值为READ（仅读授权），仅在img标签等场景下生效。只针对单个record使用，优先级最高。具体策略见[Udmf_AuthPermission](capi-uds-h.md#udmf_authpermission)。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int | 返回执行的状态代码。<br>返回UDMF_E_OK表示执行成功。<br>返回UDMF_E_INVALID_PARAM表示传入了无效参数。<br>具体请参见[Udmf_ErrCode](capi-udmf-err-code-h.md#udmf_errcode)。 |

### OH_UdsFileUri_SetAuthPolicy()

```c
int OH_UdsFileUri_SetAuthPolicy(OH_UdsFileUri* pThis, uint32_t authPolicy)
```

**描述**

给[OH_UdsFileUri](capi-udmf-oh-udsfileuri.md)设置授权策略。

> **说明：**
>
> 此授权策略仅在拖拽场景下生效，其他场景不生效。

**起始版本：** 26.0.0

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_UdsFileUri](capi-udmf-oh-udsfileuri.md)* pThis | 表示指向[OH_UdsFileUri](capi-udmf-oh-udsfileuri.md)实例的指针。 |
| uint32_t authPolicy | 表示拖拽场景下的URI授权策略，默认值为READ+WRITE+PERSIST（读+写+持久化授权），只针对单个record使用，优先级最高。具体策略见[Udmf_AuthPermission](capi-uds-h.md#udmf_authpermission)。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int | 返回执行的状态代码。<br>若返回UDMF_E_OK，表示执行成功。<br>若返回UDMF_E_INVALID_PARAM，表示传入了无效参数。具体请参阅错误码定义[Udmf_ErrCode](capi-udmf-err-code-h.md#udmf_errcode)。 |
