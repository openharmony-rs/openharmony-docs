# UniformDataType

标准化数据类型之间存在归属关系，例如JPEG图片类型归属于IMAGE类型。更多预置数据类型参考[UTD预置列表](../../../database/uniform-data-type-list.md)。下表以枚举形式，列举了常用的标准化数据类型定义。

**起始版本：** 10

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## ENTITY

```TypeScript
ENTITY = 'general.entity'
```

所有表示物理存储类型的基类型，无归属类型。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## OBJECT

```TypeScript
OBJECT = 'general.object'
```

所有表示逻辑内容类型的基类型，无归属类型。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## COMPOSITE_OBJECT

```TypeScript
COMPOSITE_OBJECT = 'general.composite-object'
```

所有组合内容类型（例如PDF文件类型混合了文本和图片类数据）的基类型，归属类型为OBJECT。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## TEXT

```TypeScript
TEXT = 'general.text'
```

所有文本的基类型，归属类型为OBJECT。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## PLAIN_TEXT

```TypeScript
PLAIN_TEXT = 'general.plain-text'
```

未指定编码的文本类型，没有标识符，归属类型为TEXT。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## HTML

```TypeScript
HTML = 'general.html'
```

HTML文本类型，归属类型为TEXT。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## HYPERLINK

```TypeScript
HYPERLINK = 'general.hyperlink'
```

超链接类型，归属类型为TEXT。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## XML

```TypeScript
XML = 'general.xml'
```

XML文本类型，归属类型为TEXT。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## XHTML

```TypeScript
XHTML = 'general.xhtml'
```

XHTML文本类型，归属类型为XML。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## RSS

```TypeScript
RSS = 'general.rss'
```

RSS文本类型，归属类型为XML。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## SMIL

```TypeScript
SMIL = 'com.real.smil'
```

同步多媒体集成语言类型，归属类型为XML。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## SOURCE_CODE

```TypeScript
SOURCE_CODE = 'general.source-code'
```

所有源代码的基类型，归属类型为TEXT。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## SCRIPT

```TypeScript
SCRIPT = 'general.script'
```

所有脚本语言源代码的基类型，归属类型为SOURCE_CODE。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## SHELL_SCRIPT

```TypeScript
SHELL_SCRIPT = 'general.shell-script'
```

shell脚本类型，归属类型为SCRIPT。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## CSH_SCRIPT

```TypeScript
CSH_SCRIPT = 'general.csh-script'
```

C-shell脚本类型，归属类型为SHELL_SCRIPT。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## PERL_SCRIPT

```TypeScript
PERL_SCRIPT = 'general.perl-script'
```

Perl脚本类型，归属类型为SHELL_SCRIPT。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## PHP_SCRIPT

```TypeScript
PHP_SCRIPT = 'general.php-script'
```

PHP脚本类型，归属类型为SHELL_SCRIPT。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## PYTHON_SCRIPT

```TypeScript
PYTHON_SCRIPT = 'general.python-script'
```

Python脚本类型，归属类型为SHELL_SCRIPT。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## RUBY_SCRIPT

```TypeScript
RUBY_SCRIPT = 'general.ruby-script'
```

Ruby脚本类型，归属类型为SHELL_SCRIPT。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## TYPE_SCRIPT

```TypeScript
TYPE_SCRIPT = 'general.type-script'
```

TypeScript源代码类型，归属类型为SOURCE_CODE。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## JAVA_SCRIPT

```TypeScript
JAVA_SCRIPT = 'general.java-script'
```

JavaScript源代码类型，归属类型为SOURCE_CODE。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## CSS

```TypeScript
CSS = 'general.css'
```

CSS样式表类型，归属类型为SCRIPT。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## C_HEADER

```TypeScript
C_HEADER = 'general.c-header'
```

C头文件类型，归属类型为SOURCE_CODE。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## C_SOURCE

```TypeScript
C_SOURCE = 'general.c-source'
```

C源代码类型，归属类型为SOURCE_CODE。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## C_PLUS_PLUS_HEADER

```TypeScript
C_PLUS_PLUS_HEADER = 'general.c-plus-plus-header'
```

C++头文件类型，归属类型为SOURCE_CODE。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## C_PLUS_PLUS_SOURCE

```TypeScript
C_PLUS_PLUS_SOURCE = 'general.c-plus-plus-source'
```

C++源代码类型，归属类型为SOURCE_CODE。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## JAVA_SOURCE

```TypeScript
JAVA_SOURCE = 'general.java-source'
```

Java源代码类型，归属类型为SOURCE_CODE。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## TEX

```TypeScript
TEX = 'general.tex'
```

TEX源代码类型，归属类型为SOURCE_CODE。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## MARKDOWN

```TypeScript
MARKDOWN = 'general.markdown'
```

标记语言文本类型，归属类型为TEXT。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## ASC_TEXT

```TypeScript
ASC_TEXT = 'general.asc-text'
```

ASCII文本类型，归属类型为TEXT。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## RICH_TEXT

```TypeScript
RICH_TEXT = 'general.rich-text'
```

富文本类型，归属类型为TEXT。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## DELIMITED_VALUES_TEXT

```TypeScript
DELIMITED_VALUES_TEXT = 'general.delimited-values-text'
```

所有分隔值文本的基类型，归属类型为TEXT。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## COMMA_SEPARATED_VALUES_TEXT

```TypeScript
COMMA_SEPARATED_VALUES_TEXT = 'general.comma-separated-values-text'
```

CSV文本类型，归属类型为DELIMITED_VALUES_TEXT。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## TAB_SEPARATED_VALUES_TEXT

```TypeScript
TAB_SEPARATED_VALUES_TEXT = 'general.tab-separated-values-text'
```

TSV文本类型，归属类型为DELIMITED_VALUES_TEXT。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## EBOOK

```TypeScript
EBOOK = 'general.ebook'
```

所有电子书文件格式的基类型，归属类型为COMPOSITE_OBJECT。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## EPUB

```TypeScript
EPUB = 'general.epub'
```

电子出版物（EPUB）文件格式类型，归属类型为EBOOK。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## AZW

```TypeScript
AZW = 'com.amazon.azw'
```

AZW电子书文件格式类型，归属类型为EBOOK。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## AZW3

```TypeScript
AZW3 = 'com.amazon.azw3'
```

AZW3电子书文件格式类型，归属类型为EBOOK。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## KFX

```TypeScript
KFX = 'com.amazon.kfx'
```

KFX电子书文件格式类型，归属类型为EBOOK。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## MOBI

```TypeScript
MOBI = 'com.amazon.mobi'
```

MOBI电子书文件格式类型，归属类型为EBOOK。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## MEDIA

```TypeScript
MEDIA = 'general.media'
```

所有媒体的基类型，归属类型为OBJECT。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## IMAGE

```TypeScript
IMAGE = 'general.image'
```

所有图片的基类型，归属类型为MEDIA。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## JPEG

```TypeScript
JPEG = 'general.jpeg'
```

JPEG图片类型，归属类型为IMAGE。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## PNG

```TypeScript
PNG = 'general.png'
```

PNG图片类型，归属类型为IMAGE。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## RAW_IMAGE

```TypeScript
RAW_IMAGE = 'general.raw-image'
```

所有原始图像格式的基类型，归属类型为IMAGE。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## TIFF

```TypeScript
TIFF = 'general.tiff'
```

TIFF图片类型，归属类型为IMAGE。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## BMP

```TypeScript
BMP = 'com.microsoft.bmp'
```

WINDOWS位图图像类型，归属类型为IMAGE。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## ICO

```TypeScript
ICO = 'com.microsoft.ico'
```

WINDOWS图标图像类型，归属类型为IMAGE。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## PHOTOSHOP_IMAGE

```TypeScript
PHOTOSHOP_IMAGE = 'com.adobe.photoshop-image'
```

Adobe Photoshop图片类型，归属类型为IMAGE。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## AI_IMAGE

```TypeScript
AI_IMAGE = 'com.adobe.illustrator.ai-image'
```

Adobe Illustrator图片类型，归属类型为IMAGE。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## FAX

```TypeScript
FAX = 'general.fax'
```

传真图像的基本类型，归属类型为IMAGE。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## JFX_FAX

```TypeScript
JFX_FAX = 'com.j2.jfx-fax'
```

J2 jConnect传真文件类型，归属类型为FAX。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## EFX_FAX

```TypeScript
EFX_FAX = 'com.js.efx-fax'
```

电子传真文件类型，归属类型为FAX。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## XBITMAP_IMAGE

```TypeScript
XBITMAP_IMAGE = 'general.xbitmap-image'
```

X Window系统（X11）中使用的位图图像格式，归属类型为IMAGE。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## GIF

```TypeScript
GIF = 'general.gif'
```

GIF图像类型，归属类型为IMAGE。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## TGA_IMAGE

```TypeScript
TGA_IMAGE = 'com.truevision.tga-image'
```

标签图形（TaggedGraphics）图像类型，归属类型为IMAGE。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## SGI_IMAGE

```TypeScript
SGI_IMAGE = 'com.sgi.sgi-image'
```

硅图（Silicon Graphics）图像类型，归属类型为IMAGE。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## OPENEXR_IMAGE

```TypeScript
OPENEXR_IMAGE = 'com.ilm.openexr-image'
```

开放标准的高动态范围图像格式类型，归属类型为IMAGE。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## FLASHPIX_IMAGE

```TypeScript
FLASHPIX_IMAGE = 'com.kodak.flashpix.image'
```

FlashPix 图像文件类型，归属类型为IMAGE。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## WORD_DOC

```TypeScript
WORD_DOC = 'com.microsoft.word.doc'
```

Microsoft Word数据类型，归属类型为COMPOSITE_OBJECT。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## EXCEL

```TypeScript
EXCEL = 'com.microsoft.excel.xls'
```

Microsoft Excel数据类型，归属类型为COMPOSITE_OBJECT。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## PPT

```TypeScript
PPT = 'com.microsoft.powerpoint.ppt'
```

Microsoft PowerPoint演示文稿类型，归属类型为COMPOSITE_OBJECT。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## WORD_DOT

```TypeScript
WORD_DOT = 'com.microsoft.word.dot'
```

Microsoft Word模板类型，归属类型为COMPOSITE_OBJECT。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## POWERPOINT_PPS

```TypeScript
POWERPOINT_PPS = 'com.microsoft.powerpoint.pps'
```

Microsoft PowerPoint演示文稿幻灯片放映类型，归属类型为COMPOSITE_OBJECT。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## POWERPOINT_POT

```TypeScript
POWERPOINT_POT = 'com.microsoft.powerpoint.pot'
```

Microsoft PowerPoint演示文稿模板类型，归属类型为COMPOSITE_OBJECT。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## EXCEL_XLT

```TypeScript
EXCEL_XLT = 'com.microsoft.excel.xlt'
```

Microsoft Excel模板类型，归属类型为COMPOSITE_OBJECT。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## VISIO_VSD

```TypeScript
VISIO_VSD = 'com.microsoft.visio.vsd'
```

Microsoft Visio数据类型，归属类型为COMPOSITE_OBJECT。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## PDF

```TypeScript
PDF = 'com.adobe.pdf'
```

PDF数据类型，归属类型为COMPOSITE_OBJECT。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## POSTSCRIPT

```TypeScript
POSTSCRIPT = 'com.adobe.postscript'
```

PostScript数据类型，归属类型为COMPOSITE_OBJECT。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## ENCAPSULATED_POSTSCRIPT

```TypeScript
ENCAPSULATED_POSTSCRIPT = 'com.adobe.encapsulated-postscript'
```

Encapsulated PostScript类型，归属类型为POSTSCRIPT。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## VIDEO

```TypeScript
VIDEO = 'general.video'
```

所有视频的基类型，归属类型为MEDIA。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## AVI

```TypeScript
AVI = 'general.avi'
```

AVI视频类型，归属类型为VIDEO。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## MPEG

```TypeScript
MPEG = 'general.mpeg'
```

MPEG-1或MPEG-2视频类型，归属类型为VIDEO。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## MPEG4

```TypeScript
MPEG4 = 'general.mpeg-4'
```

MPEG-4视频类型，归属类型为VIDEO。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## VIDEO_3GPP

```TypeScript
VIDEO_3GPP = 'general.3gpp'
```

3GPP视频类型，归属类型为VIDEO。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## VIDEO_3GPP2

```TypeScript
VIDEO_3GPP2 = 'general.3gpp2'
```

3GPP2视频类型，归属类型为VIDEO。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## TS

```TypeScript
TS = 'general.ts'
```

MPEG-TS类型，归属类型为VIDEO。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## MPEGURL_VIDEO

```TypeScript
MPEGURL_VIDEO = 'general.mpegurl-video'
```

MPEG视频播放列表文件类型，归属类型为VIDEO。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## WINDOWS_MEDIA_WM

```TypeScript
WINDOWS_MEDIA_WM = 'com.microsoft.windows-media-wm'
```

WINDOWS WM视频类型，归属类型为VIDEO。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## WINDOWS_MEDIA_WMV

```TypeScript
WINDOWS_MEDIA_WMV = 'com.microsoft.windows-media-wmv'
```

WINDOWS WMV视频类型，归属类型为VIDEO。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## WINDOWS_MEDIA_WMP

```TypeScript
WINDOWS_MEDIA_WMP = 'com.microsoft.windows-media-wmp'
```

WINDOWS WMP视频类型，归属类型为VIDEO。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## WINDOWS_MEDIA_WVX

```TypeScript
WINDOWS_MEDIA_WVX = 'com.microsoft.windows-media-wvx'
```

WINDOWS WVX视频类型，归属类型为VIDEO。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## WINDOWS_MEDIA_WMX

```TypeScript
WINDOWS_MEDIA_WMX = 'com.microsoft.windows-media-wmx'
```

WINDOWS WMX视频类型，归属类型为VIDEO。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## REALMEDIA

```TypeScript
REALMEDIA = 'com.real.realmedia'
```

流媒体视频类型，归属类型为VIDEO。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## MATROSKA_VIDEO

```TypeScript
MATROSKA_VIDEO = 'org.matroska.mkv'
```

MKV视频类型，归属类型为VIDEO。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## FLASH

```TypeScript
FLASH = 'com.adobe.flash'
```

FLASH视频类型，归属类型为VIDEO。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## AUDIO

```TypeScript
AUDIO = 'general.audio'
```

所有音频的基类型，归属类型为MEDIA。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## AAC

```TypeScript
AAC = 'general.aac'
```

AAC音频类型，归属类型为AUDIO。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## AIFF

```TypeScript
AIFF = 'general.aiff'
```

AIFF音频类型，归属类型为AUDIO。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## ALAC

```TypeScript
ALAC = 'general.alac'
```

ALAC音频类型，归属类型为AUDIO。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## FLAC

```TypeScript
FLAC = 'general.flac'
```

FLAC音频类型，归属类型为AUDIO。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## MP3

```TypeScript
MP3 = 'general.mp3'
```

MP3音频类型，归属类型为AUDIO。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## OGG

```TypeScript
OGG = 'general.ogg'
```

OGG音频类型，归属类型为AUDIO。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## PCM

```TypeScript
PCM = 'general.pcm'
```

PCM音频类型，归属类型为AUDIO。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## WINDOWS_MEDIA_WMA

```TypeScript
WINDOWS_MEDIA_WMA = 'com.microsoft.windows-media-wma'
```

WINDOWS WMA音频类型，归属类型为AUDIO。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## WAVEFORM_AUDIO

```TypeScript
WAVEFORM_AUDIO = 'com.microsoft.waveform-audio'
```

WINDOWS波形音频类型，归属类型为AUDIO。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## WINDOWS_MEDIA_WAX

```TypeScript
WINDOWS_MEDIA_WAX = 'com.microsoft.windows-media-wax'
```

WINDOWS WAX音频类型，归属类型为AUDIO。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## AU_AUDIO

```TypeScript
AU_AUDIO = 'general.au-audio'
```

Au数据格式，归属类型为AUDIO。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## AIFC_AUDIO

```TypeScript
AIFC_AUDIO = 'general.aifc-audio'
```

音频交换数据类型，归属类型为AUDIO。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## MPEGURL_AUDIO

```TypeScript
MPEGURL_AUDIO = 'general.mpegurl-audio'
```

MPEG音频播放列表文件类型，归属类型为AUDIO。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## MPEG_4_AUDIO

```TypeScript
MPEG_4_AUDIO = 'general.mpeg-4-audio'
```

MPEG-4音频类型，归属类型为AUDIO。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## MP2

```TypeScript
MP2 = 'general.mp2'
```

MP2音频类型，归属类型为AUDIO。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## MPEG_AUDIO

```TypeScript
MPEG_AUDIO = 'general.mpeg-audio'
```

MPEG音频类型，归属类型为AUDIO。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## ULAW_AUDIO

```TypeScript
ULAW_AUDIO = 'general.ulaw-audio'
```

ULAW音频类型，归属类型为AUDIO。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## SD2_AUDIO

```TypeScript
SD2_AUDIO = 'com.digidesign.sd2-audio'
```

单声道/立体声音频类型（Digidesign Sound Designer II），归属类型为AUDIO。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## REALAUDIO

```TypeScript
REALAUDIO = 'com.real.realaudio'
```

RealMedia音频类型，归属类型为AUDIO。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## MATROSKA_AUDIO

```TypeScript
MATROSKA_AUDIO = 'org.matroska.mka'
```

MKA音频类型，归属类型为AUDIO。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## FILE

```TypeScript
FILE = 'general.file'
```

所有文件的基类型，归属类型为ENTITY。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## DIRECTORY

```TypeScript
DIRECTORY = 'general.directory'
```

所有目录的基类型，归属类型为ENTITY。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## FOLDER

```TypeScript
FOLDER = 'general.folder'
```

所有文件夹的基类型，归属类型为DIRECTORY。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## SYMLINK

```TypeScript
SYMLINK = 'general.symlink'
```

所有符号链接的基类型，归属类型为ENTITY。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## ARCHIVE

```TypeScript
ARCHIVE = 'general.archive'
```

所有文件和目录存档文件的基类型，归属类型为OBJECT。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## BZ2_ARCHIVE

```TypeScript
BZ2_ARCHIVE = 'general.bz2-archive'
```

BZ2存档文件类型，归属类型为ARCHIVE。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## OPG

```TypeScript
OPG = 'general.opg'
```

OPG存档文件类型，归属类型为ARCHIVE。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## TAZ_ARCHIVE

```TypeScript
TAZ_ARCHIVE = 'general.taz-archive'
```

TAR压缩文件类型，归属类型为TAR_ARCHIVE。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## WEB_ARCHIVE

```TypeScript
WEB_ARCHIVE = 'general.web-archive'
```

MHTML网页归档文件类型，归属类型为ARCHIVE。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## DISK_IMAGE

```TypeScript
DISK_IMAGE = 'general.disk-image'
```

所有可作为卷挂载项的文件类型的基类型，归属类型为ARCHIVE。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## ISO

```TypeScript
ISO = 'general.iso'
```

光盘映像文件类型，归属类型为DISK_IMAGE。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## TAR_ARCHIVE

```TypeScript
TAR_ARCHIVE = 'general.tar-archive'
```

TAR存档文件类型，归属类型为ARCHIVE。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## ZIP_ARCHIVE

```TypeScript
ZIP_ARCHIVE = 'general.zip-archive'
```

ZIP存档文件类型，归属类型为ARCHIVE。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## JAVA_ARCHIVE

```TypeScript
JAVA_ARCHIVE = 'com.sun.java-archive'
```

JAVA存档文件类型，归属类型为ARCHIVE和EXECUTABLE。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## GNU_TAR_ARCHIVE

```TypeScript
GNU_TAR_ARCHIVE = 'org.gnu.gnu-tar-archive'
```

GNU存档文件类型，归属类型为ARCHIVE。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## GNU_ZIP_ARCHIVE

```TypeScript
GNU_ZIP_ARCHIVE = 'org.gnu.gnu-zip-archive'
```

GZIP存档文件类型，归属类型为ARCHIVE。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## GNU_ZIP_TAR_ARCHIVE

```TypeScript
GNU_ZIP_TAR_ARCHIVE = 'org.gnu.gnu-zip-tar-archive'
```

GZIP TAR存档文件类型，归属类型为ARCHIVE。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## OPENXML

```TypeScript
OPENXML = 'org.openxmlformats.openxml'
```

开源XML基类型，归属类型为ARCHIVE。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## WORDPROCESSINGML_DOCUMENT

```TypeScript
WORDPROCESSINGML_DOCUMENT = 'org.openxmlformats.wordprocessingml.document'
```

开源XML文档类型，归属类型为OPENXML和COMPOSITE_OBJECT。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## SPREADSHEETML_SHEET

```TypeScript
SPREADSHEETML_SHEET = 'org.openxmlformats.spreadsheetml.sheet'
```

开源XML电子表格类型，归属类型为OPENXML和COMPOSITE_OBJECT。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## PRESENTATIONML_PRESENTATION

```TypeScript
PRESENTATIONML_PRESENTATION = 'org.openxmlformats.presentationml.presentation'
```

开源XML演示文稿类型，归属类型为OPENXML和COMPOSITE_OBJECT。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## DRAWINGML_VISIO

```TypeScript
DRAWINGML_VISIO = 'org.openxmlformats.drawingml.visio'
```

开源XML绘图文件类型，归属类型为OPENXML和COMPOSITE_OBJECT。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## DRAWINGML_TEMPLATE

```TypeScript
DRAWINGML_TEMPLATE = 'org.openxmlformats.drawingml.template'
```

开源XML绘图模板类型，归属类型为OPENXML和COMPOSITE_OBJECT。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## WORDPROCESSINGML_TEMPLATE

```TypeScript
WORDPROCESSINGML_TEMPLATE = 'org.openxmlformats.wordprocessingml.template'
```

开源XML文档模板类型，归属类型为OPENXML和COMPOSITE_OBJECT。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## PRESENTATIONML_TEMPLATE

```TypeScript
PRESENTATIONML_TEMPLATE = 'org.openxmlformats.presentationml.template'
```

开源XML演示文稿模板类型，归属类型为OPENXML和COMPOSITE_OBJECT。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## PRESENTATIONML_SLIDESHOW

```TypeScript
PRESENTATIONML_SLIDESHOW = 'org.openxmlformats.presentationml.slideshow'
```

开源XML演示文稿幻灯片放映类型，归属类型为OPENXML和COMPOSITE_OBJECT。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## SPREADSHEETML_TEMPLATE

```TypeScript
SPREADSHEETML_TEMPLATE = 'org.openxmlformats.spreadsheetml.template'
```

开源XML电子表格模板类型，归属类型为OPENXML和COMPOSITE_OBJECT。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## OPENDOCUMENT

```TypeScript
OPENDOCUMENT = 'org.oasis.opendocument'
```

Office应用程序的开源文档类型，归属类型为ARCHIVE。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## OPENDOCUMENT_TEXT

```TypeScript
OPENDOCUMENT_TEXT = 'org.oasis.opendocument.text'
```

开源文档类型，归属类型为OPENDOCUMENT和COMPOSITE_OBJECT。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## OPENDOCUMENT_SPREADSHEET

```TypeScript
OPENDOCUMENT_SPREADSHEET = 'org.oasis.opendocument.spreadsheet'
```

开源文档电子表格类型，归属类型为OPENDOCUMENT和COMPOSITE_OBJECT。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## OPENDOCUMENT_PRESENTATION

```TypeScript
OPENDOCUMENT_PRESENTATION = 'org.oasis.opendocument.presentation'
```

开源文档演示类型，归属类型为OPENDOCUMENT和COMPOSITE_OBJECT。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## OPENDOCUMENT_GRAPHICS

```TypeScript
OPENDOCUMENT_GRAPHICS = 'org.oasis.opendocument.graphics'
```

开源文档图形类型，归属类型为OPENDOCUMENT和COMPOSITE_OBJECT。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## OPENDOCUMENT_FORMULA

```TypeScript
OPENDOCUMENT_FORMULA = 'org.oasis.opendocument.formula'
```

开源文档公式集类型，归属类型为OPENDOCUMENT。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## STUFFIT_ARCHIVE

```TypeScript
STUFFIT_ARCHIVE = 'com.allume.stuffit-archive'
```

Stuffit压缩格式类型（Stuffit archive），归属类型为ARCHIVE。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## RAR_ARCHIVE

```TypeScript
RAR_ARCHIVE = 'com.rarlab.rar-archive'
```

WinRAR压缩格式类型，归属类型为ARCHIVE。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## SEVEN_ZIP_ARCHIVE

```TypeScript
SEVEN_ZIP_ARCHIVE = 'org.7-zip.7-zip-archive'
```

7-zip压缩格式类型，归属类型为ARCHIVE。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## CALENDAR

```TypeScript
CALENDAR = 'general.calendar'
```

所有日程类数据的基类型，归属类型为OBJECT。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## VCS

```TypeScript
VCS = 'general.vcs'
```

VCalendar日历数据类型，归属类型为CALENDAR和TEXT。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## ICS

```TypeScript
ICS = 'general.ics'
```

ICalendar日历数据类型，归属类型为CALENDAR和TEXT。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## CONTACT

```TypeScript
CONTACT = 'general.contact'
```

所有联系人类数据的基类型，归属类型为OBJECT。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## DATABASE

```TypeScript
DATABASE = 'general.database'
```

所有数据库文件的基类型，归属类型为OBJECT。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## MESSAGE

```TypeScript
MESSAGE = 'general.message'
```

所有消息类数据的基类型，归属类型为OBJECT。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## EXECUTABLE

```TypeScript
EXECUTABLE = 'general.executable'
```

所有可执行文件的基类型，归属类型为OBJECT。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## PORTABLE_EXECUTABLE

```TypeScript
PORTABLE_EXECUTABLE = 'com.microsoft.portable-executable'
```

Microsoft Windows应用程序类型，归属类型为EXECUTABLE。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## SUN_JAVA_CLASS

```TypeScript
SUN_JAVA_CLASS = 'com.sun.java-class'
```

Java类文件类型，归属类型为EXECUTABLE。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## VCARD

```TypeScript
VCARD = 'general.vcard'
```

所有电子名片类数据的基类型，归属类型为OBJECT。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## NAVIGATION

```TypeScript
NAVIGATION = 'general.navigation'
```

所有导航类数据的基类型，归属类型为OBJECT。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## LOCATION

```TypeScript
LOCATION = 'general.location'
```

导航定位类型，归属类型为NAVIGATION。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## FONT

```TypeScript
FONT = 'general.font'
```

所有字体数据类型的基础类型，归属类型为OBJECT。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## TRUETYPE_FONT

```TypeScript
TRUETYPE_FONT = 'general.truetype-font'
```

TrueType字体类型，归属类型为FONT。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## TRUETYPE_COLLECTION_FONT

```TypeScript
TRUETYPE_COLLECTION_FONT = 'general.truetype-collection-font'
```

TrueType collection字体类型，归属类型为FONT。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## OPENTYPE_FONT

```TypeScript
OPENTYPE_FONT = 'general.opentype-font'
```

OpenType 字体类型，归属类型为FONT。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## POSTSCRIPT_FONT

```TypeScript
POSTSCRIPT_FONT = 'com.adobe.postscript-font'
```

PostScript 字体类型，归属类型为FONT。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## POSTSCRIPT_PFB_FONT

```TypeScript
POSTSCRIPT_PFB_FONT = 'com.adobe.postscript-pfb-font'
```

PostScript Font Binary字体类型，归属类型为FONT。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## POSTSCRIPT_PFA_FONT

```TypeScript
POSTSCRIPT_PFA_FONT = 'com.adobe.postscript-pfa-font'
```

Adobe Type 1 字体类型，归属类型为FONT。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## OPENHARMONY_FORM

```TypeScript
OPENHARMONY_FORM = 'openharmony.form'
```

系统定义的卡片类型，归属类型为OBJECT。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## OPENHARMONY_APP_ITEM

```TypeScript
OPENHARMONY_APP_ITEM = 'openharmony.app-item'
```

系统定义的桌面图标类型，归属类型为OBJECT。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## OPENHARMONY_PIXEL_MAP

```TypeScript
OPENHARMONY_PIXEL_MAP = 'openharmony.pixel-map'
```

系统定义的像素图类型，归属类型为IMAGE。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## OPENHARMONY_ATOMIC_SERVICE

```TypeScript
OPENHARMONY_ATOMIC_SERVICE = 'openharmony.atomic-service'
```

系统定义的原子化服务类型，归属类型为OBJECT。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## OPENHARMONY_PACKAGE

```TypeScript
OPENHARMONY_PACKAGE = 'openharmony.package'
```

系统定义的包（即目录的打包文件），归属类型为DIRECTORY。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## OPENHARMONY_HAP

```TypeScript
OPENHARMONY_HAP = 'openharmony.hap'
```

系统定义的能力包，归属类型为OPENHARMONY_PACKAGE。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## OPENHARMONY_HDOC

```TypeScript
OPENHARMONY_HDOC = 'openharmony.hdoc'
```

系统定义的备忘录数据类型，归属类型为COMPOSITE_OBJECT。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## OPENHARMONY_HINOTE

```TypeScript
OPENHARMONY_HINOTE = 'openharmony.hinote'
```

系统定义的笔记数据类型，归属类型为COMPOSITE_OBJECT。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## OPENHARMONY_STYLED_STRING

```TypeScript
OPENHARMONY_STYLED_STRING = 'openharmony.styled-string'
```

系统定义的样式字符串类型，归属类型为COMPOSITE_OBJECT。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## OPENHARMONY_WANT

```TypeScript
OPENHARMONY_WANT = 'openharmony.want'
```

系统定义的Want类型，归属类型为OBJECT。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## OFD

```TypeScript
OFD = 'general.ofd'
```

开放版式文档类型，归属类型为COMPOSITE_OBJECT。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## CAD

```TypeScript
CAD = 'general.cad'
```

所有计算机辅助设计类型的基类型，归属类型为OBJECT。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## OCTET_STREAM

```TypeScript
OCTET_STREAM = 'general.octet-stream'
```

任意二进制数据类型，归属类型为OBJECT。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## FILE_URI

```TypeScript
FILE_URI = 'general.file-uri'
```

文件地址类型，归属类型为TEXT。

**起始版本：** 15

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## CONTENT_FORM

```TypeScript
CONTENT_FORM = 'general.content-form'
```

内容卡片类型，归属类型为OBJECT。

**起始版本：** 15

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core
