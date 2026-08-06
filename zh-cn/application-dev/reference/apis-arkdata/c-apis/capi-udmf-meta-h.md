# udmf_meta.h

## 概述

声明统一类型数据信息。

**库：** libudmf.so

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

**起始版本：** 12

**相关模块：** [UDMF](capi-udmf.md)

## 汇总

### 宏定义

| 名称 | 描述 |
| -- | -- |
| UDMF_META_ENTITY "general.entity" | 所有表示物理存储类型的基类型，用于描述类型的物理属性，无归属类型。<br>**起始版本：** 12 |
| UDMF_META_OBJECT "general.object" | 所有表示物理存储类型的基类型，用于描述类型的物理属性，无归属类型。<br>**起始版本：** 12 |
| UDMF_META_COMPOSITE_OBJECT "general.composite-object" | 所有表示物理存储类型的基类型，用于描述类型的物理属性，无归属类型。<br>**起始版本：** 12 |
| UDMF_META_TEXT "general.text" | 所有表示物理存储类型的基类型，用于描述类型的物理属性，无归属类型。<br>**起始版本：** 12 |
| UDMF_META_PLAIN_TEXT "general.plain-text" | 所有表示物理存储类型的基类型，用于描述类型的物理属性，无归属类型。<br>**起始版本：** 12 |
| UDMF_META_HTML "general.html" | 所有表示物理存储类型的基类型，用于描述类型的物理属性，无归属类型。<br>**起始版本：** 12 |
| UDMF_META_HYPERLINK "general.hyperlink" | 所有表示物理存储类型的基类型，用于描述类型的物理属性，无归属类型。<br>**起始版本：** 12 |
| UDMF_META_XML "general.xml" | 所有表示物理存储类型的基类型，用于描述类型的物理属性，无归属类型。<br>**起始版本：** 12 |
| UDMF_META_SOURCE_CODE "general.source-code" | 所有表示物理存储类型的基类型，用于描述类型的物理属性，无归属类型。<br>**起始版本：** 12 |
| UDMF_META_SCRIPT "general.script" | 所有表示物理存储类型的基类型，用于描述类型的物理属性，无归属类型。<br>**起始版本：** 12 |
| UDMF_META_SHELL_SCRIPT "general.shell-script" | 所有表示物理存储类型的基类型，用于描述类型的物理属性，无归属类型。<br>**起始版本：** 12 |
| UDMF_META_CSH_SCRIPT "general.csh-script" | 所有表示物理存储类型的基类型，用于描述类型的物理属性，无归属类型。<br>**起始版本：** 12 |
| UDMF_META_PERL_SCRIPT "general.perl-script" | 所有表示物理存储类型的基类型，用于描述类型的物理属性，无归属类型。<br>**起始版本：** 12 |
| UDMF_META_PHP_SCRIPT "general.php-script" | 所有表示物理存储类型的基类型，用于描述类型的物理属性，无归属类型。<br>**起始版本：** 12 |
| UDMF_META_PYTHON_SCRIPT "general.python-script" | 所有表示物理存储类型的基类型，用于描述类型的物理属性，无归属类型。<br>**起始版本：** 12 |
| UDMF_META_RUBY_SCRIPT "general.ruby-script" | 所有表示物理存储类型的基类型，用于描述类型的物理属性，无归属类型。<br>**起始版本：** 12 |
| UDMF_META_TYPE_SCRIPT "general.type-script" | 所有表示物理存储类型的基类型，用于描述类型的物理属性，无归属类型。<br>**起始版本：** 12 |
| UDMF_META_JAVA_SCRIPT "general.java-script" | 所有表示物理存储类型的基类型，用于描述类型的物理属性，无归属类型。<br>**起始版本：** 12 |
| UDMF_META_C_HEADER "general.c-header" | 所有表示物理存储类型的基类型，用于描述类型的物理属性，无归属类型。<br>**起始版本：** 12 |
| UDMF_META_C_SOURCE "general.c-source" | 所有表示物理存储类型的基类型，用于描述类型的物理属性，无归属类型。<br>**起始版本：** 12 |
| UDMF_META_C_PLUS_PLUS_HEADER "general.c-plus-plus-header" | 所有表示物理存储类型的基类型，用于描述类型的物理属性，无归属类型。<br>**起始版本：** 12 |
| UDMF_META_C_PLUS_PLUS_SOURCE "general.c-plus-plus-source" | 所有表示物理存储类型的基类型，用于描述类型的物理属性，无归属类型。<br>**起始版本：** 12 |
| UDMF_META_JAVA_SOURCE "general.java-source" | 所有表示物理存储类型的基类型，用于描述类型的物理属性，无归属类型。<br>**起始版本：** 12 |
| UDMF_META_EBOOK "general.ebook" | 所有表示物理存储类型的基类型，用于描述类型的物理属性，无归属类型。<br>**起始版本：** 12 |
| UDMF_META_EPUB "general.epub" | 所有表示物理存储类型的基类型，用于描述类型的物理属性，无归属类型。<br>**起始版本：** 12 |
| UDMF_META_AZW "com.amazon.azw" | 所有表示物理存储类型的基类型，用于描述类型的物理属性，无归属类型。<br>**起始版本：** 12 |
| UDMF_META_AZW3 "com.amazon.azw3" | 所有表示物理存储类型的基类型，用于描述类型的物理属性，无归属类型。<br>**起始版本：** 12 |
| UDMF_META_KFX "com.amazon.kfx" | 所有表示物理存储类型的基类型，用于描述类型的物理属性，无归属类型。<br>**起始版本：** 12 |
| UDMF_META_MOBI "com.amazon.mobi" | 所有表示物理存储类型的基类型，用于描述类型的物理属性，无归属类型。<br>**起始版本：** 12 |
| UDMF_META_MEDIA "general.media" | 所有表示物理存储类型的基类型，用于描述类型的物理属性，无归属类型。<br>**起始版本：** 12 |
| UDMF_META_IMAGE "general.image" | 所有表示物理存储类型的基类型，用于描述类型的物理属性，无归属类型。<br>**起始版本：** 12 |
| UDMF_META_JPEG "general.jpeg" | 所有表示物理存储类型的基类型，用于描述类型的物理属性，无归属类型。<br>**起始版本：** 12 |
| UDMF_META_PNG "general.png" | 所有表示物理存储类型的基类型，用于描述类型的物理属性，无归属类型。<br>**起始版本：** 12 |
| UDMF_META_RAW_IMAGE "general.raw-image" | 所有表示物理存储类型的基类型，用于描述类型的物理属性，无归属类型。<br>**起始版本：** 12 |
| UDMF_META_TIFF "general.tiff" | 所有表示物理存储类型的基类型，用于描述类型的物理属性，无归属类型。<br>**起始版本：** 12 |
| UDMF_META_BMP "com.microsoft.bmp" | 所有表示物理存储类型的基类型，用于描述类型的物理属性，无归属类型。<br>**起始版本：** 12 |
| UDMF_META_ICO "com.microsoft.ico" | 所有表示物理存储类型的基类型，用于描述类型的物理属性，无归属类型。<br>**起始版本：** 12 |
| UDMF_META_PHOTOSHOP_IMAGE "com.adobe.photoshop-image" | 所有表示物理存储类型的基类型，用于描述类型的物理属性，无归属类型。<br>**起始版本：** 12 |
| UDMF_META_AI_IMAGE "com.adobe.illustrator.ai-image" | 所有表示物理存储类型的基类型，用于描述类型的物理属性，无归属类型。<br>**起始版本：** 12 |
| UDMF_META_WORD_DOC "com.microsoft.word.doc" | 所有表示物理存储类型的基类型，用于描述类型的物理属性，无归属类型。<br>**起始版本：** 12 |
| UDMF_META_EXCEL "com.microsoft.excel.xls" | 所有表示物理存储类型的基类型，用于描述类型的物理属性，无归属类型。<br>**起始版本：** 12 |
| UDMF_META_PPT "com.microsoft.powerpoint.ppt" | 所有表示物理存储类型的基类型，用于描述类型的物理属性，无归属类型。<br>**起始版本：** 12 |
| UDMF_META_PDF "com.adobe.pdf" | 所有表示物理存储类型的基类型，用于描述类型的物理属性，无归属类型。<br>**起始版本：** 12 |
| UDMF_META_POSTSCRIPT "com.adobe.postscript" | 所有表示物理存储类型的基类型，用于描述类型的物理属性，无归属类型。<br>**起始版本：** 12 |
| UDMF_META_ENCAPSULATED_POSTSCRIPT "com.adobe.encapsulated-postscript" | 所有表示物理存储类型的基类型，用于描述类型的物理属性，无归属类型。<br>**起始版本：** 12 |
| UDMF_META_VIDEO "general.video" | 所有表示物理存储类型的基类型，用于描述类型的物理属性，无归属类型。<br>**起始版本：** 12 |
| UDMF_META_AVI "general.avi" | 所有表示物理存储类型的基类型，用于描述类型的物理属性，无归属类型。<br>**起始版本：** 12 |
| UDMF_META_MPEG "general.mpeg" | 所有表示物理存储类型的基类型，用于描述类型的物理属性，无归属类型。<br>**起始版本：** 12 |
| UDMF_META_MPEG4 "general.mpeg-4" | 所有表示物理存储类型的基类型，用于描述类型的物理属性，无归属类型。<br>**起始版本：** 12 |
| UDMF_META_VIDEO_3GPP "general.3gpp" | 所有表示物理存储类型的基类型，用于描述类型的物理属性，无归属类型。<br>**起始版本：** 12 |
| UDMF_META_VIDEO_3GPP2 "general.3gpp2" | 所有表示物理存储类型的基类型，用于描述类型的物理属性，无归属类型。<br>**起始版本：** 12 |
| UDMF_META_WINDOWS_MEDIA_WM "com.microsoft.windows-media-wm" | 所有表示物理存储类型的基类型，用于描述类型的物理属性，无归属类型。<br>**起始版本：** 12 |
| UDMF_META_WINDOWS_MEDIA_WMV "com.microsoft.windows-media-wmv" | 所有表示物理存储类型的基类型，用于描述类型的物理属性，无归属类型。<br>**起始版本：** 12 |
| UDMF_META_WINDOWS_MEDIA_WMP "com.microsoft.windows-media-wmp" | 所有表示物理存储类型的基类型，用于描述类型的物理属性，无归属类型。<br>**起始版本：** 12 |
| UDMF_META_AUDIO "general.audio" | 所有表示物理存储类型的基类型，用于描述类型的物理属性，无归属类型。<br>**起始版本：** 12 |
| UDMF_META_AAC "general.aac" | 所有表示物理存储类型的基类型，用于描述类型的物理属性，无归属类型。<br>**起始版本：** 12 |
| UDMF_META_AIFF "general.aiff" | 所有表示物理存储类型的基类型，用于描述类型的物理属性，无归属类型。<br>**起始版本：** 12 |
| UDMF_META_ALAC "general.alac" | 所有表示物理存储类型的基类型，用于描述类型的物理属性，无归属类型。<br>**起始版本：** 12 |
| UDMF_META_FLAC "general.flac" | 所有表示物理存储类型的基类型，用于描述类型的物理属性，无归属类型。<br>**起始版本：** 12 |
| UDMF_META_MP3 "general.mp3" | 所有表示物理存储类型的基类型，用于描述类型的物理属性，无归属类型。<br>**起始版本：** 12 |
| UDMF_META_OGG "general.ogg" | 所有表示物理存储类型的基类型，用于描述类型的物理属性，无归属类型。<br>**起始版本：** 12 |
| UDMF_META_PCM "general.pcm" | 所有表示物理存储类型的基类型，用于描述类型的物理属性，无归属类型。<br>**起始版本：** 12 |
| UDMF_META_WINDOWS_MEDIA_WMA "com.microsoft.windows-media-wma" | 所有表示物理存储类型的基类型，用于描述类型的物理属性，无归属类型。<br>**起始版本：** 12 |
| UDMF_META_WAVEFORM_AUDIO "com.microsoft.waveform-audio" | 所有表示物理存储类型的基类型，用于描述类型的物理属性，无归属类型。<br>**起始版本：** 12 |
| UDMF_META_WINDOWS_MEDIA_WMX "com.microsoft.windows-media-wmx" | 所有表示物理存储类型的基类型，用于描述类型的物理属性，无归属类型。<br>**起始版本：** 12 |
| UDMF_META_WINDOWS_MEDIA_WVX "com.microsoft.windows-media-wvx" | 所有表示物理存储类型的基类型，用于描述类型的物理属性，无归属类型。<br>**起始版本：** 12 |
| UDMF_META_WINDOWS_MEDIA_WAX "com.microsoft.windows-media-wax" | 所有表示物理存储类型的基类型，用于描述类型的物理属性，无归属类型。<br>**起始版本：** 12 |
| UDMF_META_GENERAL_FILE "general.file" | 所有表示物理存储类型的基类型，用于描述类型的物理属性，无归属类型。<br>**起始版本：** 12 |
| UDMF_META_DIRECTORY "general.directory" | 所有表示物理存储类型的基类型，用于描述类型的物理属性，无归属类型。<br>**起始版本：** 12 |
| UDMF_META_FOLDER "general.folder" | 所有表示物理存储类型的基类型，用于描述类型的物理属性，无归属类型。<br>**起始版本：** 12 |
| UDMF_META_SYMLINK "general.symlink" | 所有表示物理存储类型的基类型，用于描述类型的物理属性，无归属类型。<br>**起始版本：** 12 |
| UDMF_META_ARCHIVE "general.archive" | 所有表示物理存储类型的基类型，用于描述类型的物理属性，无归属类型。<br>**起始版本：** 12 |
| UDMF_META_BZ2_ARCHIVE "general.bz2-archive" | 所有表示物理存储类型的基类型，用于描述类型的物理属性，无归属类型。<br>**起始版本：** 12 |
| UDMF_META_DISK_IMAGE "general.disk-image" | 所有表示物理存储类型的基类型，用于描述类型的物理属性，无归属类型。<br>**起始版本：** 12 |
| UDMF_META_TAR_ARCHIVE "general.tar-archive" | 所有表示物理存储类型的基类型，用于描述类型的物理属性，无归属类型。<br>**起始版本：** 12 |
| UDMF_META_ZIP_ARCHIVE "general.zip-archive" | 所有表示物理存储类型的基类型，用于描述类型的物理属性，无归属类型。<br>**起始版本：** 12 |
| UDMF_META_JAVA_ARCHIVE "com.sun.java-archive" | 所有表示物理存储类型的基类型，用于描述类型的物理属性，无归属类型。<br>**起始版本：** 12 |
| UDMF_META_GNU_TAR_ARCHIVE "org.gnu.gnu-tar-archive" | 所有表示物理存储类型的基类型，用于描述类型的物理属性，无归属类型。<br>**起始版本：** 12 |
| UDMF_META_GNU_ZIP_ARCHIVE "org.gnu.gnu-zip-archive" | 所有表示物理存储类型的基类型，用于描述类型的物理属性，无归属类型。<br>**起始版本：** 12 |
| UDMF_META_GNU_ZIP_TAR_ARCHIVE "org.gnu.gnu-zip-tar-archive" | 所有表示物理存储类型的基类型，用于描述类型的物理属性，无归属类型。<br>**起始版本：** 12 |
| UDMF_META_CALENDAR "general.calendar" | 所有表示物理存储类型的基类型，用于描述类型的物理属性，无归属类型。<br>**起始版本：** 12 |
| UDMF_META_CONTACT "general.contact" | 所有表示物理存储类型的基类型，用于描述类型的物理属性，无归属类型。<br>**起始版本：** 12 |
| UDMF_META_DATABASE "general.database" | 所有表示物理存储类型的基类型，用于描述类型的物理属性，无归属类型。<br>**起始版本：** 12 |
| UDMF_META_MESSAGE "general.message" | 所有表示物理存储类型的基类型，用于描述类型的物理属性，无归属类型。<br>**起始版本：** 12 |
| UDMF_META_VCARD "general.vcard" | 所有表示物理存储类型的基类型，用于描述类型的物理属性，无归属类型。<br>**起始版本：** 12 |
| UDMF_META_NAVIGATION "general.navigation" | 所有表示物理存储类型的基类型，用于描述类型的物理属性，无归属类型。<br>**起始版本：** 12 |
| UDMF_META_LOCATION "general.location" | 所有表示物理存储类型的基类型，用于描述类型的物理属性，无归属类型。<br>**起始版本：** 12 |
| UDMF_META_OPENHARMONY_FORM "openharmony.form" | 所有表示物理存储类型的基类型，用于描述类型的物理属性，无归属类型。<br>**起始版本：** 12 |
| UDMF_META_OPENHARMONY_APP_ITEM "openharmony.app-item" | 所有表示物理存储类型的基类型，用于描述类型的物理属性，无归属类型。<br>**起始版本：** 12 |
| UDMF_META_OPENHARMONY_PIXEL_MAP "openharmony.pixel-map" | 所有表示物理存储类型的基类型，用于描述类型的物理属性，无归属类型。<br>**起始版本：** 12 |
| UDMF_META_OPENHARMONY_ATOMIC_SERVICE "openharmony.atomic-service" | 所有表示物理存储类型的基类型，用于描述类型的物理属性，无归属类型。<br>**起始版本：** 12 |
| UDMF_META_OPENHARMONY_PACKAGE "openharmony.package" | 所有表示物理存储类型的基类型，用于描述类型的物理属性，无归属类型。<br>**起始版本：** 12 |
| UDMF_META_OPENHARMONY_HAP "openharmony.hap" | 所有表示物理存储类型的基类型，用于描述类型的物理属性，无归属类型。<br>**起始版本：** 12 |
| UDMF_META_SMIL "com.real.smil" | 所有表示物理存储类型的基类型，用于描述类型的物理属性，无归属类型。<br>**起始版本：** 12 |
| UDMF_META_MARKDOWN "general.markdown" | 所有表示物理存储类型的基类型，用于描述类型的物理属性，无归属类型。<br>**起始版本：** 12 |
| UDMF_META_FAX "general.fax" | 所有表示物理存储类型的基类型，用于描述类型的物理属性，无归属类型。<br>**起始版本：** 12 |
| UDMF_META_JFX_FAX "com.j2.jfx-fax" | 所有表示物理存储类型的基类型，用于描述类型的物理属性，无归属类型。<br>**起始版本：** 12 |
| UDMF_META_EFX_FAX "com.js.efx-fax" | 所有表示物理存储类型的基类型，用于描述类型的物理属性，无归属类型。<br>**起始版本：** 12 |
| UDMF_META_XBITMAP_IMAGE "general.xbitmap-image" | 所有表示物理存储类型的基类型，用于描述类型的物理属性，无归属类型。<br>**起始版本：** 12 |
| UDMF_META_TGA_IMAGE "com.truevision.tga-image" | 所有表示物理存储类型的基类型，用于描述类型的物理属性，无归属类型。<br>**起始版本：** 12 |
| UDMF_META_SGI_IMAGE "com.sgi.sgi-image" | 所有表示物理存储类型的基类型，用于描述类型的物理属性，无归属类型。<br>**起始版本：** 12 |
| UDMF_META_OPENEXR_IMAGE "com.ilm.openexr-image" | 所有表示物理存储类型的基类型，用于描述类型的物理属性，无归属类型。<br>**起始版本：** 12 |
| UDMF_META_FLASHPIX_IMAGE "com.kodak.flashpix.image" | 所有表示物理存储类型的基类型，用于描述类型的物理属性，无归属类型。<br>**起始版本：** 12 |
| UDMF_META_REALMEDIA "com.real.realmedia" | 所有表示物理存储类型的基类型，用于描述类型的物理属性，无归属类型。<br>**起始版本：** 12 |
| UDMF_META_AU_AUDIO "general.au-audio" | 所有表示物理存储类型的基类型，用于描述类型的物理属性，无归属类型。<br>**起始版本：** 12 |
| UDMF_META_AIFC_AUDIO "general.aifc-audio" | 所有表示物理存储类型的基类型，用于描述类型的物理属性，无归属类型。<br>**起始版本：** 12 |
| UDMF_META_SD2_AUDIO "com.digidesign.sd2-audio" | 所有表示物理存储类型的基类型，用于描述类型的物理属性，无归属类型。<br>**起始版本：** 12 |
| UDMF_META_REALAUDIO "com.real.realaudio" | 所有表示物理存储类型的基类型，用于描述类型的物理属性，无归属类型。<br>**起始版本：** 12 |
| UDMF_META_OPENXML "org.openxmlformats.openxml" | 所有表示物理存储类型的基类型，用于描述类型的物理属性，无归属类型。<br>**起始版本：** 12 |
| UDMF_META_WORDPROCESSINGML_DOCUMENT "org.openxmlformats.wordprocessingml.document" | 所有表示物理存储类型的基类型，用于描述类型的物理属性，无归属类型。<br>**起始版本：** 12 |
| UDMF_META_SPREADSHEETML_SHEET "org.openxmlformats.spreadsheetml.sheet" | 所有表示物理存储类型的基类型，用于描述类型的物理属性，无归属类型。<br>**起始版本：** 12 |
| UDMF_META_PRESENTATIONML_PRESENTATION "org.openxmlformats.presentationml.presentation" | 所有表示物理存储类型的基类型，用于描述类型的物理属性，无归属类型。<br>**起始版本：** 12 |
| UDMF_META_OPENDOCUMENT "org.oasis.opendocument" | 所有表示物理存储类型的基类型，用于描述类型的物理属性，无归属类型。<br>**起始版本：** 12 |
| UDMF_META_OPENDOCUMENT_TEXT "org.oasis.opendocument.text" | 所有表示物理存储类型的基类型，用于描述类型的物理属性，无归属类型。<br>**起始版本：** 12 |
| UDMF_META_OPENDOCUMENT_SPREADSHEET "org.oasis.opendocument.spreadsheet" | 所有表示物理存储类型的基类型，用于描述类型的物理属性，无归属类型。<br>**起始版本：** 12 |
| UDMF_META_OPENDOCUMENT_PRESENTATION "org.oasis.opendocument.presentation" | 所有表示物理存储类型的基类型，用于描述类型的物理属性，无归属类型。<br>**起始版本：** 12 |
| UDMF_META_OPENDOCUMENT_GRAPHICS "org.oasis.opendocument.graphics" | 所有表示物理存储类型的基类型，用于描述类型的物理属性，无归属类型。<br>**起始版本：** 12 |
| UDMF_META_OPENDOCUMENT_FORMULA "org.oasis.opendocument.formula" | 所有表示物理存储类型的基类型，用于描述类型的物理属性，无归属类型。<br>**起始版本：** 12 |
| UDMF_META_STUFFIT_ARCHIVE "com.allume.stuffit-archive" | 所有表示物理存储类型的基类型，用于描述类型的物理属性，无归属类型。<br>**起始版本：** 12 |
| UDMF_META_VCS "general.vcs" | 所有表示物理存储类型的基类型，用于描述类型的物理属性，无归属类型。<br>**起始版本：** 12 |
| UDMF_META_ICS "general.ics" | 所有表示物理存储类型的基类型，用于描述类型的物理属性，无归属类型。<br>**起始版本：** 12 |
| UDMF_META_EXECUTABLE "general.executable" | 所有表示物理存储类型的基类型，用于描述类型的物理属性，无归属类型。<br>**起始版本：** 12 |
| UDMF_META_PORTABLE_EXECUTABLE "com.microsoft.portable-executable" | 所有表示物理存储类型的基类型，用于描述类型的物理属性，无归属类型。<br>**起始版本：** 12 |
| UDMF_META_SUN_JAVA_CLASS "com.sun.java-class" | 所有表示物理存储类型的基类型，用于描述类型的物理属性，无归属类型。<br>**起始版本：** 12 |
| UDMF_META_FONT "general.font" | 所有表示物理存储类型的基类型，用于描述类型的物理属性，无归属类型。<br>**起始版本：** 12 |
| UDMF_META_TRUETYPE_FONT "general.truetype-font" | 所有表示物理存储类型的基类型，用于描述类型的物理属性，无归属类型。<br>**起始版本：** 12 |
| UDMF_META_TRUETYPE_COLLECTION_FONT "general.truetype-collection-font" | 所有表示物理存储类型的基类型，用于描述类型的物理属性，无归属类型。<br>**起始版本：** 12 |
| UDMF_META_OPENTYPE_FONT "general.opentype-font" | 所有表示物理存储类型的基类型，用于描述类型的物理属性，无归属类型。<br>**起始版本：** 12 |
| UDMF_META_POSTSCRIPT_FONT "com.adobe.postscript-font" | 所有表示物理存储类型的基类型，用于描述类型的物理属性，无归属类型。<br>**起始版本：** 12 |
| UDMF_META_POSTSCRIPT_PFB_FONT "com.adobe.postscript-pfb-font" | 所有表示物理存储类型的基类型，用于描述类型的物理属性，无归属类型。<br>**起始版本：** 12 |
| UDMF_META_POSTSCRIPT_PFA_FONT "com.adobe.postscript-pfa-font" | 所有表示物理存储类型的基类型，用于描述类型的物理属性，无归属类型。<br>**起始版本：** 12 |
| UDMF_META_OPENHARMONY_HDOC "openharmony.hdoc" | 所有表示物理存储类型的基类型，用于描述类型的物理属性，无归属类型。<br>**起始版本：** 12 |
| UDMF_META_OPENHARMONY_HINOTE "openharmony.hinote" | 所有表示物理存储类型的基类型，用于描述类型的物理属性，无归属类型。<br>**起始版本：** 12 |
| UDMF_META_OPENHARMONY_STYLED_STRING "openharmony.styled-string" | 所有表示物理存储类型的基类型，用于描述类型的物理属性，无归属类型。<br>**起始版本：** 12 |
| UDMF_META_OPENHARMONY_WANT "openharmony.want" | 所有表示物理存储类型的基类型，用于描述类型的物理属性，无归属类型。<br>**起始版本：** 12 |
| UDMF_META_GENERAL_FILE_URI "general.file-uri" | 文件地址类型，归属类型为TEXT。<br>**起始版本：** 13 |
| UDMF_METE_GENERAL_CONTENT_FORM "general.content-form" | 内容卡片类型，归属类型为OBJECT。<br>**起始版本：** 14 |

