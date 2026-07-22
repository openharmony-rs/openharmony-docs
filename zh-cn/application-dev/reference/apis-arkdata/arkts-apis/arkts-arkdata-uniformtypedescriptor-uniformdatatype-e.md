# UniformDataType

标准化数据类型之间存在归属关系，例如JPEG图片类型归属于IMAGE类型。更多预置数据类型参考[UTD预置列表](../../../database/uniform-data-type-list.md)。

下表以枚举形式，列举了常用的标准化数据类型定义。

**起始版本：** 10

<!--Device-uniformTypeDescriptor-enum UniformDataType--><!--Device-uniformTypeDescriptor-enum UniformDataType-End-->

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## ENTITY

```TypeScript
ENTITY = 'general.entity'
```

所有表示物理存储类型的基类型，无归属类型。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UniformDataType-ENTITY = 'general.entity'--><!--Device-UniformDataType-ENTITY = 'general.entity'-End-->

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## OBJECT

```TypeScript
OBJECT = 'general.object'
```

所有表示逻辑内容类型的基类型，无归属类型。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UniformDataType-OBJECT = 'general.object'--><!--Device-UniformDataType-OBJECT = 'general.object'-End-->

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## COMPOSITE_OBJECT

```TypeScript
COMPOSITE_OBJECT = 'general.composite-object'
```

所有组合内容类型（例如PDF文件类型混合了文本和图片类数据）的基类型，归属类型为OBJECT。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UniformDataType-COMPOSITE_OBJECT = 'general.composite-object'--><!--Device-UniformDataType-COMPOSITE_OBJECT = 'general.composite-object'-End-->

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## TEXT

```TypeScript
TEXT = 'general.text'
```

所有文本的基类型，归属类型为OBJECT。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-UniformDataType-TEXT = 'general.text'--><!--Device-UniformDataType-TEXT = 'general.text'-End-->

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## PLAIN_TEXT

```TypeScript
PLAIN_TEXT = 'general.plain-text'
```

未指定编码的文本类型，没有标识符，归属类型为TEXT。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-UniformDataType-PLAIN_TEXT = 'general.plain-text'--><!--Device-UniformDataType-PLAIN_TEXT = 'general.plain-text'-End-->

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## HTML

```TypeScript
HTML = 'general.html'
```

HTML文本类型，归属类型为TEXT。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-UniformDataType-HTML = 'general.html'--><!--Device-UniformDataType-HTML = 'general.html'-End-->

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## HYPERLINK

```TypeScript
HYPERLINK = 'general.hyperlink'
```

超链接类型，归属类型为TEXT。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-UniformDataType-HYPERLINK = 'general.hyperlink'--><!--Device-UniformDataType-HYPERLINK = 'general.hyperlink'-End-->

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## XML

```TypeScript
XML = 'general.xml'
```

XML文本类型，归属类型为TEXT。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UniformDataType-XML = 'general.xml'--><!--Device-UniformDataType-XML = 'general.xml'-End-->

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## XHTML

```TypeScript
XHTML = 'general.xhtml'
```

XHTML文本类型，归属类型为XML。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UniformDataType-XHTML = 'general.xhtml'--><!--Device-UniformDataType-XHTML = 'general.xhtml'-End-->

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## RSS

```TypeScript
RSS = 'general.rss'
```

RSS文本类型，归属类型为XML。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UniformDataType-RSS = 'general.rss'--><!--Device-UniformDataType-RSS = 'general.rss'-End-->

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## SMIL

```TypeScript
SMIL = 'com.real.smil'
```

同步多媒体集成语言类型，归属类型为XML。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UniformDataType-SMIL = 'com.real.smil'--><!--Device-UniformDataType-SMIL = 'com.real.smil'-End-->

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## SOURCE_CODE

```TypeScript
SOURCE_CODE = 'general.source-code'
```

所有源代码的基类型，归属类型为TEXT。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UniformDataType-SOURCE_CODE = 'general.source-code'--><!--Device-UniformDataType-SOURCE_CODE = 'general.source-code'-End-->

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## SCRIPT

```TypeScript
SCRIPT = 'general.script'
```

所有脚本语言源代码的基类型，归属类型为SOURCE_CODE。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UniformDataType-SCRIPT = 'general.script'--><!--Device-UniformDataType-SCRIPT = 'general.script'-End-->

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## SHELL_SCRIPT

```TypeScript
SHELL_SCRIPT = 'general.shell-script'
```

shell脚本类型，归属类型为SCRIPT。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UniformDataType-SHELL_SCRIPT = 'general.shell-script'--><!--Device-UniformDataType-SHELL_SCRIPT = 'general.shell-script'-End-->

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## CSH_SCRIPT

```TypeScript
CSH_SCRIPT = 'general.csh-script'
```

C-shell脚本类型，归属类型为SHELL_SCRIPT。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UniformDataType-CSH_SCRIPT = 'general.csh-script'--><!--Device-UniformDataType-CSH_SCRIPT = 'general.csh-script'-End-->

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## PERL_SCRIPT

```TypeScript
PERL_SCRIPT = 'general.perl-script'
```

Perl脚本类型，归属类型为SHELL_SCRIPT。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UniformDataType-PERL_SCRIPT = 'general.perl-script'--><!--Device-UniformDataType-PERL_SCRIPT = 'general.perl-script'-End-->

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## PHP_SCRIPT

```TypeScript
PHP_SCRIPT = 'general.php-script'
```

PHP脚本类型，归属类型为SHELL_SCRIPT。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UniformDataType-PHP_SCRIPT = 'general.php-script'--><!--Device-UniformDataType-PHP_SCRIPT = 'general.php-script'-End-->

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## PYTHON_SCRIPT

```TypeScript
PYTHON_SCRIPT = 'general.python-script'
```

Python脚本类型，归属类型为SHELL_SCRIPT。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UniformDataType-PYTHON_SCRIPT = 'general.python-script'--><!--Device-UniformDataType-PYTHON_SCRIPT = 'general.python-script'-End-->

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## RUBY_SCRIPT

```TypeScript
RUBY_SCRIPT = 'general.ruby-script'
```

Ruby脚本类型，归属类型为SHELL_SCRIPT。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UniformDataType-RUBY_SCRIPT = 'general.ruby-script'--><!--Device-UniformDataType-RUBY_SCRIPT = 'general.ruby-script'-End-->

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## TYPE_SCRIPT

```TypeScript
TYPE_SCRIPT = 'general.type-script'
```

TypeScript源代码类型，归属类型为SOURCE_CODE。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UniformDataType-TYPE_SCRIPT = 'general.type-script'--><!--Device-UniformDataType-TYPE_SCRIPT = 'general.type-script'-End-->

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## JAVA_SCRIPT

```TypeScript
JAVA_SCRIPT = 'general.java-script'
```

JavaScript源代码类型，归属类型为SOURCE_CODE。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UniformDataType-JAVA_SCRIPT = 'general.java-script'--><!--Device-UniformDataType-JAVA_SCRIPT = 'general.java-script'-End-->

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## CSS

```TypeScript
CSS = 'general.css'
```

CSS样式表类型，归属类型为SCRIPT。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UniformDataType-CSS = 'general.css'--><!--Device-UniformDataType-CSS = 'general.css'-End-->

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## C_HEADER

```TypeScript
C_HEADER = 'general.c-header'
```

C头文件类型，归属类型为SOURCE_CODE。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UniformDataType-C_HEADER = 'general.c-header'--><!--Device-UniformDataType-C_HEADER = 'general.c-header'-End-->

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## C_SOURCE

```TypeScript
C_SOURCE = 'general.c-source'
```

C源代码类型，归属类型为SOURCE_CODE。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UniformDataType-C_SOURCE = 'general.c-source'--><!--Device-UniformDataType-C_SOURCE = 'general.c-source'-End-->

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## C_PLUS_PLUS_HEADER

```TypeScript
C_PLUS_PLUS_HEADER = 'general.c-plus-plus-header'
```

C++头文件类型，归属类型为SOURCE_CODE。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UniformDataType-C_PLUS_PLUS_HEADER = 'general.c-plus-plus-header'--><!--Device-UniformDataType-C_PLUS_PLUS_HEADER = 'general.c-plus-plus-header'-End-->

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## C_PLUS_PLUS_SOURCE

```TypeScript
C_PLUS_PLUS_SOURCE = 'general.c-plus-plus-source'
```

C++源代码类型，归属类型为SOURCE_CODE。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UniformDataType-C_PLUS_PLUS_SOURCE = 'general.c-plus-plus-source'--><!--Device-UniformDataType-C_PLUS_PLUS_SOURCE = 'general.c-plus-plus-source'-End-->

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## JAVA_SOURCE

```TypeScript
JAVA_SOURCE = 'general.java-source'
```

Java源代码类型，归属类型为SOURCE_CODE。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UniformDataType-JAVA_SOURCE = 'general.java-source'--><!--Device-UniformDataType-JAVA_SOURCE = 'general.java-source'-End-->

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## TEX

```TypeScript
TEX = 'general.tex'
```

TEX源代码类型，归属类型为SOURCE_CODE。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UniformDataType-TEX = 'general.tex'--><!--Device-UniformDataType-TEX = 'general.tex'-End-->

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## MARKDOWN

```TypeScript
MARKDOWN = 'general.markdown'
```

标记语言文本类型，归属类型为TEXT。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UniformDataType-MARKDOWN = 'general.markdown'--><!--Device-UniformDataType-MARKDOWN = 'general.markdown'-End-->

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## ASC_TEXT

```TypeScript
ASC_TEXT = 'general.asc-text'
```

ASCII文本类型，归属类型为TEXT。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UniformDataType-ASC_TEXT = 'general.asc-text'--><!--Device-UniformDataType-ASC_TEXT = 'general.asc-text'-End-->

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## RICH_TEXT

```TypeScript
RICH_TEXT = 'general.rich-text'
```

富文本类型，归属类型为TEXT。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UniformDataType-RICH_TEXT = 'general.rich-text'--><!--Device-UniformDataType-RICH_TEXT = 'general.rich-text'-End-->

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## DELIMITED_VALUES_TEXT

```TypeScript
DELIMITED_VALUES_TEXT = 'general.delimited-values-text'
```

所有分隔值文本的基类型，归属类型为TEXT。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UniformDataType-DELIMITED_VALUES_TEXT = 'general.delimited-values-text'--><!--Device-UniformDataType-DELIMITED_VALUES_TEXT = 'general.delimited-values-text'-End-->

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## COMMA_SEPARATED_VALUES_TEXT

```TypeScript
COMMA_SEPARATED_VALUES_TEXT = 'general.comma-separated-values-text'
```

CSV文本类型，归属类型为DELIMITED_VALUES_TEXT。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UniformDataType-COMMA_SEPARATED_VALUES_TEXT = 'general.comma-separated-values-text'--><!--Device-UniformDataType-COMMA_SEPARATED_VALUES_TEXT = 'general.comma-separated-values-text'-End-->

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## TAB_SEPARATED_VALUES_TEXT

```TypeScript
TAB_SEPARATED_VALUES_TEXT = 'general.tab-separated-values-text'
```

TSV文本类型，归属类型为DELIMITED_VALUES_TEXT。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UniformDataType-TAB_SEPARATED_VALUES_TEXT = 'general.tab-separated-values-text'--><!--Device-UniformDataType-TAB_SEPARATED_VALUES_TEXT = 'general.tab-separated-values-text'-End-->

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## EBOOK

```TypeScript
EBOOK = 'general.ebook'
```

所有电子书文件格式的基类型，归属类型为COMPOSITE_OBJECT。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UniformDataType-EBOOK = 'general.ebook'--><!--Device-UniformDataType-EBOOK = 'general.ebook'-End-->

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## EPUB

```TypeScript
EPUB = 'general.epub'
```

电子出版物（EPUB）文件格式类型，归属类型为EBOOK。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UniformDataType-EPUB = 'general.epub'--><!--Device-UniformDataType-EPUB = 'general.epub'-End-->

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## AZW

```TypeScript
AZW = 'com.amazon.azw'
```

AZW电子书文件格式类型，归属类型为EBOOK。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UniformDataType-AZW = 'com.amazon.azw'--><!--Device-UniformDataType-AZW = 'com.amazon.azw'-End-->

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## AZW3

```TypeScript
AZW3 = 'com.amazon.azw3'
```

AZW3电子书文件格式类型，归属类型为EBOOK。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UniformDataType-AZW3 = 'com.amazon.azw3'--><!--Device-UniformDataType-AZW3 = 'com.amazon.azw3'-End-->

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## KFX

```TypeScript
KFX = 'com.amazon.kfx'
```

KFX电子书文件格式类型，归属类型为EBOOK。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UniformDataType-KFX = 'com.amazon.kfx'--><!--Device-UniformDataType-KFX = 'com.amazon.kfx'-End-->

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## MOBI

```TypeScript
MOBI = 'com.amazon.mobi'
```

MOBI电子书文件格式类型，归属类型为EBOOK。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UniformDataType-MOBI = 'com.amazon.mobi'--><!--Device-UniformDataType-MOBI = 'com.amazon.mobi'-End-->

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## MEDIA

```TypeScript
MEDIA = 'general.media'
```

所有媒体的基类型，归属类型为OBJECT。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UniformDataType-MEDIA = 'general.media'--><!--Device-UniformDataType-MEDIA = 'general.media'-End-->

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## IMAGE

```TypeScript
IMAGE = 'general.image'
```

所有图片的基类型，归属类型为MEDIA。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-UniformDataType-IMAGE = 'general.image'--><!--Device-UniformDataType-IMAGE = 'general.image'-End-->

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## JPEG

```TypeScript
JPEG = 'general.jpeg'
```

JPEG图片类型，归属类型为IMAGE。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UniformDataType-JPEG = 'general.jpeg'--><!--Device-UniformDataType-JPEG = 'general.jpeg'-End-->

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## PNG

```TypeScript
PNG = 'general.png'
```

PNG图片类型，归属类型为IMAGE。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UniformDataType-PNG = 'general.png'--><!--Device-UniformDataType-PNG = 'general.png'-End-->

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## RAW_IMAGE

```TypeScript
RAW_IMAGE = 'general.raw-image'
```

所有原始图像格式的基类型，归属类型为IMAGE。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UniformDataType-RAW_IMAGE = 'general.raw-image'--><!--Device-UniformDataType-RAW_IMAGE = 'general.raw-image'-End-->

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## TIFF

```TypeScript
TIFF = 'general.tiff'
```

TIFF图片类型，归属类型为IMAGE。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UniformDataType-TIFF = 'general.tiff'--><!--Device-UniformDataType-TIFF = 'general.tiff'-End-->

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## BMP

```TypeScript
BMP = 'com.microsoft.bmp'
```

WINDOWS位图图像类型，归属类型为IMAGE。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UniformDataType-BMP = 'com.microsoft.bmp'--><!--Device-UniformDataType-BMP = 'com.microsoft.bmp'-End-->

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## ICO

```TypeScript
ICO = 'com.microsoft.ico'
```

WINDOWS图标图像类型，归属类型为IMAGE。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UniformDataType-ICO = 'com.microsoft.ico'--><!--Device-UniformDataType-ICO = 'com.microsoft.ico'-End-->

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## PHOTOSHOP_IMAGE

```TypeScript
PHOTOSHOP_IMAGE = 'com.adobe.photoshop-image'
```

Adobe Photoshop图片类型，归属类型为IMAGE。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UniformDataType-PHOTOSHOP_IMAGE = 'com.adobe.photoshop-image'--><!--Device-UniformDataType-PHOTOSHOP_IMAGE = 'com.adobe.photoshop-image'-End-->

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## AI_IMAGE

```TypeScript
AI_IMAGE = 'com.adobe.illustrator.ai-image'
```

Adobe Illustrator图片类型，归属类型为IMAGE。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UniformDataType-AI_IMAGE = 'com.adobe.illustrator.ai-image'--><!--Device-UniformDataType-AI_IMAGE = 'com.adobe.illustrator.ai-image'-End-->

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## FAX

```TypeScript
FAX = 'general.fax'
```

传真图像的基本类型，归属类型为IMAGE。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UniformDataType-FAX = 'general.fax'--><!--Device-UniformDataType-FAX = 'general.fax'-End-->

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## JFX_FAX

```TypeScript
JFX_FAX = 'com.j2.jfx-fax'
```

J2 jConnect传真文件类型，归属类型为FAX。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UniformDataType-JFX_FAX = 'com.j2.jfx-fax'--><!--Device-UniformDataType-JFX_FAX = 'com.j2.jfx-fax'-End-->

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## EFX_FAX

```TypeScript
EFX_FAX = 'com.js.efx-fax'
```

电子传真文件类型，归属类型为FAX。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UniformDataType-EFX_FAX = 'com.js.efx-fax'--><!--Device-UniformDataType-EFX_FAX = 'com.js.efx-fax'-End-->

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## XBITMAP_IMAGE

```TypeScript
XBITMAP_IMAGE = 'general.xbitmap-image'
```

X Window系统（X11）中使用的位图图像格式，归属类型为IMAGE。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UniformDataType-XBITMAP_IMAGE = 'general.xbitmap-image'--><!--Device-UniformDataType-XBITMAP_IMAGE = 'general.xbitmap-image'-End-->

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## GIF

```TypeScript
GIF = 'general.gif'
```

GIF图像类型，归属类型为IMAGE。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UniformDataType-GIF = 'general.gif'--><!--Device-UniformDataType-GIF = 'general.gif'-End-->

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## TGA_IMAGE

```TypeScript
TGA_IMAGE = 'com.truevision.tga-image'
```

标签图形（TaggedGraphics）图像类型，归属类型为IMAGE。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UniformDataType-TGA_IMAGE = 'com.truevision.tga-image'--><!--Device-UniformDataType-TGA_IMAGE = 'com.truevision.tga-image'-End-->

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## SGI_IMAGE

```TypeScript
SGI_IMAGE = 'com.sgi.sgi-image'
```

硅图（Silicon Graphics）图像类型，归属类型为IMAGE。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UniformDataType-SGI_IMAGE = 'com.sgi.sgi-image'--><!--Device-UniformDataType-SGI_IMAGE = 'com.sgi.sgi-image'-End-->

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## OPENEXR_IMAGE

```TypeScript
OPENEXR_IMAGE = 'com.ilm.openexr-image'
```

开放标准的高动态范围图像格式类型，归属类型为IMAGE。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UniformDataType-OPENEXR_IMAGE = 'com.ilm.openexr-image'--><!--Device-UniformDataType-OPENEXR_IMAGE = 'com.ilm.openexr-image'-End-->

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## FLASHPIX_IMAGE

```TypeScript
FLASHPIX_IMAGE = 'com.kodak.flashpix.image'
```

FlashPix 图像文件类型，归属类型为IMAGE。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UniformDataType-FLASHPIX_IMAGE = 'com.kodak.flashpix.image'--><!--Device-UniformDataType-FLASHPIX_IMAGE = 'com.kodak.flashpix.image'-End-->

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## WORD_DOC

```TypeScript
WORD_DOC = 'com.microsoft.word.doc'
```

Microsoft Word数据类型，归属类型为COMPOSITE_OBJECT。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UniformDataType-WORD_DOC = 'com.microsoft.word.doc'--><!--Device-UniformDataType-WORD_DOC = 'com.microsoft.word.doc'-End-->

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## EXCEL

```TypeScript
EXCEL = 'com.microsoft.excel.xls'
```

Microsoft Excel数据类型，归属类型为COMPOSITE_OBJECT。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UniformDataType-EXCEL = 'com.microsoft.excel.xls'--><!--Device-UniformDataType-EXCEL = 'com.microsoft.excel.xls'-End-->

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## PPT

```TypeScript
PPT = 'com.microsoft.powerpoint.ppt'
```

Microsoft PowerPoint演示文稿类型，归属类型为COMPOSITE_OBJECT。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UniformDataType-PPT = 'com.microsoft.powerpoint.ppt'--><!--Device-UniformDataType-PPT = 'com.microsoft.powerpoint.ppt'-End-->

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## WORD_DOT

```TypeScript
WORD_DOT = 'com.microsoft.word.dot'
```

Microsoft Word模板类型，归属类型为COMPOSITE_OBJECT。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UniformDataType-WORD_DOT = 'com.microsoft.word.dot'--><!--Device-UniformDataType-WORD_DOT = 'com.microsoft.word.dot'-End-->

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## POWERPOINT_PPS

```TypeScript
POWERPOINT_PPS = 'com.microsoft.powerpoint.pps'
```

Microsoft PowerPoint演示文稿幻灯片放映类型，归属类型为COMPOSITE_OBJECT。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UniformDataType-POWERPOINT_PPS = 'com.microsoft.powerpoint.pps'--><!--Device-UniformDataType-POWERPOINT_PPS = 'com.microsoft.powerpoint.pps'-End-->

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## POWERPOINT_POT

```TypeScript
POWERPOINT_POT = 'com.microsoft.powerpoint.pot'
```

Microsoft PowerPoint演示文稿模板类型，归属类型为COMPOSITE_OBJECT。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UniformDataType-POWERPOINT_POT = 'com.microsoft.powerpoint.pot'--><!--Device-UniformDataType-POWERPOINT_POT = 'com.microsoft.powerpoint.pot'-End-->

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## EXCEL_XLT

```TypeScript
EXCEL_XLT = 'com.microsoft.excel.xlt'
```

Microsoft Excel模板类型，归属类型为COMPOSITE_OBJECT。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UniformDataType-EXCEL_XLT = 'com.microsoft.excel.xlt'--><!--Device-UniformDataType-EXCEL_XLT = 'com.microsoft.excel.xlt'-End-->

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## VISIO_VSD

```TypeScript
VISIO_VSD = 'com.microsoft.visio.vsd'
```

Microsoft Visio数据类型，归属类型为COMPOSITE_OBJECT。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UniformDataType-VISIO_VSD = 'com.microsoft.visio.vsd'--><!--Device-UniformDataType-VISIO_VSD = 'com.microsoft.visio.vsd'-End-->

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## PDF

```TypeScript
PDF = 'com.adobe.pdf'
```

PDF数据类型，归属类型为COMPOSITE_OBJECT。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UniformDataType-PDF = 'com.adobe.pdf'--><!--Device-UniformDataType-PDF = 'com.adobe.pdf'-End-->

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## POSTSCRIPT

```TypeScript
POSTSCRIPT = 'com.adobe.postscript'
```

PostScript数据类型，归属类型为COMPOSITE_OBJECT。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UniformDataType-POSTSCRIPT = 'com.adobe.postscript'--><!--Device-UniformDataType-POSTSCRIPT = 'com.adobe.postscript'-End-->

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## ENCAPSULATED_POSTSCRIPT

```TypeScript
ENCAPSULATED_POSTSCRIPT = 'com.adobe.encapsulated-postscript'
```

Encapsulated PostScript类型，归属类型为POSTSCRIPT。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UniformDataType-ENCAPSULATED_POSTSCRIPT = 'com.adobe.encapsulated-postscript'--><!--Device-UniformDataType-ENCAPSULATED_POSTSCRIPT = 'com.adobe.encapsulated-postscript'-End-->

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## VIDEO

```TypeScript
VIDEO = 'general.video'
```

所有视频的基类型，归属类型为MEDIA。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-UniformDataType-VIDEO = 'general.video'--><!--Device-UniformDataType-VIDEO = 'general.video'-End-->

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## AVI

```TypeScript
AVI = 'general.avi'
```

AVI视频类型，归属类型为VIDEO。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UniformDataType-AVI = 'general.avi'--><!--Device-UniformDataType-AVI = 'general.avi'-End-->

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## MPEG

```TypeScript
MPEG = 'general.mpeg'
```

MPEG-1或MPEG-2视频类型，归属类型为VIDEO。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UniformDataType-MPEG = 'general.mpeg'--><!--Device-UniformDataType-MPEG = 'general.mpeg'-End-->

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## MPEG4

```TypeScript
MPEG4 = 'general.mpeg-4'
```

MPEG-4视频类型，归属类型为VIDEO。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UniformDataType-MPEG4 = 'general.mpeg-4'--><!--Device-UniformDataType-MPEG4 = 'general.mpeg-4'-End-->

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## VIDEO_3GPP

```TypeScript
VIDEO_3GPP = 'general.3gpp'
```

3GPP视频类型，归属类型为VIDEO。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UniformDataType-VIDEO_3GPP = 'general.3gpp'--><!--Device-UniformDataType-VIDEO_3GPP = 'general.3gpp'-End-->

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## VIDEO_3GPP2

```TypeScript
VIDEO_3GPP2 = 'general.3gpp2'
```

3GPP2视频类型，归属类型为VIDEO。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UniformDataType-VIDEO_3GPP2 = 'general.3gpp2'--><!--Device-UniformDataType-VIDEO_3GPP2 = 'general.3gpp2'-End-->

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## TS

```TypeScript
TS = 'general.ts'
```

MPEG-TS类型，归属类型为VIDEO。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UniformDataType-TS = 'general.ts'--><!--Device-UniformDataType-TS = 'general.ts'-End-->

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## MPEGURL_VIDEO

```TypeScript
MPEGURL_VIDEO = 'general.mpegurl-video'
```

MPEG视频播放列表文件类型，归属类型为VIDEO。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UniformDataType-MPEGURL_VIDEO = 'general.mpegurl-video'--><!--Device-UniformDataType-MPEGURL_VIDEO = 'general.mpegurl-video'-End-->

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## WINDOWS_MEDIA_WM

```TypeScript
WINDOWS_MEDIA_WM = 'com.microsoft.windows-media-wm'
```

WINDOWS WM视频类型，归属类型为VIDEO。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UniformDataType-WINDOWS_MEDIA_WM = 'com.microsoft.windows-media-wm'--><!--Device-UniformDataType-WINDOWS_MEDIA_WM = 'com.microsoft.windows-media-wm'-End-->

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## WINDOWS_MEDIA_WMV

```TypeScript
WINDOWS_MEDIA_WMV = 'com.microsoft.windows-media-wmv'
```

WINDOWS WMV视频类型，归属类型为VIDEO。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UniformDataType-WINDOWS_MEDIA_WMV = 'com.microsoft.windows-media-wmv'--><!--Device-UniformDataType-WINDOWS_MEDIA_WMV = 'com.microsoft.windows-media-wmv'-End-->

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## WINDOWS_MEDIA_WMP

```TypeScript
WINDOWS_MEDIA_WMP = 'com.microsoft.windows-media-wmp'
```

WINDOWS WMP视频类型，归属类型为VIDEO。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UniformDataType-WINDOWS_MEDIA_WMP = 'com.microsoft.windows-media-wmp'--><!--Device-UniformDataType-WINDOWS_MEDIA_WMP = 'com.microsoft.windows-media-wmp'-End-->

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## WINDOWS_MEDIA_WVX

```TypeScript
WINDOWS_MEDIA_WVX = 'com.microsoft.windows-media-wvx'
```

WINDOWS WVX视频类型，归属类型为VIDEO。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UniformDataType-WINDOWS_MEDIA_WVX = 'com.microsoft.windows-media-wvx'--><!--Device-UniformDataType-WINDOWS_MEDIA_WVX = 'com.microsoft.windows-media-wvx'-End-->

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## WINDOWS_MEDIA_WMX

```TypeScript
WINDOWS_MEDIA_WMX = 'com.microsoft.windows-media-wmx'
```

WINDOWS WMX视频类型，归属类型为VIDEO。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UniformDataType-WINDOWS_MEDIA_WMX = 'com.microsoft.windows-media-wmx'--><!--Device-UniformDataType-WINDOWS_MEDIA_WMX = 'com.microsoft.windows-media-wmx'-End-->

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## REALMEDIA

```TypeScript
REALMEDIA = 'com.real.realmedia'
```

流媒体视频类型，归属类型为VIDEO。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UniformDataType-REALMEDIA = 'com.real.realmedia'--><!--Device-UniformDataType-REALMEDIA = 'com.real.realmedia'-End-->

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## MATROSKA_VIDEO

```TypeScript
MATROSKA_VIDEO = 'org.matroska.mkv'
```

MKV视频类型，归属类型为VIDEO。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UniformDataType-MATROSKA_VIDEO = 'org.matroska.mkv'--><!--Device-UniformDataType-MATROSKA_VIDEO = 'org.matroska.mkv'-End-->

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## FLASH

```TypeScript
FLASH = 'com.adobe.flash'
```

FLASH视频类型，归属类型为VIDEO。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UniformDataType-FLASH = 'com.adobe.flash'--><!--Device-UniformDataType-FLASH = 'com.adobe.flash'-End-->

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## AUDIO

```TypeScript
AUDIO = 'general.audio'
```

所有音频的基类型，归属类型为MEDIA。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-UniformDataType-AUDIO = 'general.audio'--><!--Device-UniformDataType-AUDIO = 'general.audio'-End-->

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## AAC

```TypeScript
AAC = 'general.aac'
```

AAC音频类型，归属类型为AUDIO。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UniformDataType-AAC = 'general.aac'--><!--Device-UniformDataType-AAC = 'general.aac'-End-->

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## AIFF

```TypeScript
AIFF = 'general.aiff'
```

AIFF音频类型，归属类型为AUDIO。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UniformDataType-AIFF = 'general.aiff'--><!--Device-UniformDataType-AIFF = 'general.aiff'-End-->

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## ALAC

```TypeScript
ALAC = 'general.alac'
```

ALAC音频类型，归属类型为AUDIO。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UniformDataType-ALAC = 'general.alac'--><!--Device-UniformDataType-ALAC = 'general.alac'-End-->

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## FLAC

```TypeScript
FLAC = 'general.flac'
```

FLAC音频类型，归属类型为AUDIO。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UniformDataType-FLAC = 'general.flac'--><!--Device-UniformDataType-FLAC = 'general.flac'-End-->

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## MP3

```TypeScript
MP3 = 'general.mp3'
```

MP3音频类型，归属类型为AUDIO。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UniformDataType-MP3 = 'general.mp3'--><!--Device-UniformDataType-MP3 = 'general.mp3'-End-->

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## OGG

```TypeScript
OGG = 'general.ogg'
```

OGG音频类型，归属类型为AUDIO。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UniformDataType-OGG = 'general.ogg'--><!--Device-UniformDataType-OGG = 'general.ogg'-End-->

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## PCM

```TypeScript
PCM = 'general.pcm'
```

PCM音频类型，归属类型为AUDIO。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UniformDataType-PCM = 'general.pcm'--><!--Device-UniformDataType-PCM = 'general.pcm'-End-->

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## WINDOWS_MEDIA_WMA

```TypeScript
WINDOWS_MEDIA_WMA = 'com.microsoft.windows-media-wma'
```

WINDOWS WMA音频类型，归属类型为AUDIO。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UniformDataType-WINDOWS_MEDIA_WMA = 'com.microsoft.windows-media-wma'--><!--Device-UniformDataType-WINDOWS_MEDIA_WMA = 'com.microsoft.windows-media-wma'-End-->

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## WAVEFORM_AUDIO

```TypeScript
WAVEFORM_AUDIO = 'com.microsoft.waveform-audio'
```

WINDOWS波形音频类型，归属类型为AUDIO。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UniformDataType-WAVEFORM_AUDIO = 'com.microsoft.waveform-audio'--><!--Device-UniformDataType-WAVEFORM_AUDIO = 'com.microsoft.waveform-audio'-End-->

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## WINDOWS_MEDIA_WAX

```TypeScript
WINDOWS_MEDIA_WAX = 'com.microsoft.windows-media-wax'
```

WINDOWS WAX音频类型，归属类型为AUDIO。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UniformDataType-WINDOWS_MEDIA_WAX = 'com.microsoft.windows-media-wax'--><!--Device-UniformDataType-WINDOWS_MEDIA_WAX = 'com.microsoft.windows-media-wax'-End-->

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## AU_AUDIO

```TypeScript
AU_AUDIO = 'general.au-audio'
```

Au数据格式，归属类型为AUDIO。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UniformDataType-AU_AUDIO = 'general.au-audio'--><!--Device-UniformDataType-AU_AUDIO = 'general.au-audio'-End-->

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## AIFC_AUDIO

```TypeScript
AIFC_AUDIO = 'general.aifc-audio'
```

音频交换数据类型，归属类型为AUDIO。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UniformDataType-AIFC_AUDIO = 'general.aifc-audio'--><!--Device-UniformDataType-AIFC_AUDIO = 'general.aifc-audio'-End-->

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## MPEGURL_AUDIO

```TypeScript
MPEGURL_AUDIO = 'general.mpegurl-audio'
```

MPEG音频播放列表文件类型，归属类型为AUDIO。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UniformDataType-MPEGURL_AUDIO = 'general.mpegurl-audio'--><!--Device-UniformDataType-MPEGURL_AUDIO = 'general.mpegurl-audio'-End-->

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## MPEG_4_AUDIO

```TypeScript
MPEG_4_AUDIO = 'general.mpeg-4-audio'
```

MPEG-4音频类型，归属类型为AUDIO。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UniformDataType-MPEG_4_AUDIO = 'general.mpeg-4-audio'--><!--Device-UniformDataType-MPEG_4_AUDIO = 'general.mpeg-4-audio'-End-->

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## MP2

```TypeScript
MP2 = 'general.mp2'
```

MP2音频类型，归属类型为AUDIO。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UniformDataType-MP2 = 'general.mp2'--><!--Device-UniformDataType-MP2 = 'general.mp2'-End-->

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## MPEG_AUDIO

```TypeScript
MPEG_AUDIO = 'general.mpeg-audio'
```

MPEG音频类型，归属类型为AUDIO。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UniformDataType-MPEG_AUDIO = 'general.mpeg-audio'--><!--Device-UniformDataType-MPEG_AUDIO = 'general.mpeg-audio'-End-->

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## ULAW_AUDIO

```TypeScript
ULAW_AUDIO = 'general.ulaw-audio'
```

ULAW音频类型，归属类型为AUDIO。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UniformDataType-ULAW_AUDIO = 'general.ulaw-audio'--><!--Device-UniformDataType-ULAW_AUDIO = 'general.ulaw-audio'-End-->

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## SD2_AUDIO

```TypeScript
SD2_AUDIO = 'com.digidesign.sd2-audio'
```

单声道/立体声音频类型（Digidesign Sound Designer II），归属类型为AUDIO。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UniformDataType-SD2_AUDIO = 'com.digidesign.sd2-audio'--><!--Device-UniformDataType-SD2_AUDIO = 'com.digidesign.sd2-audio'-End-->

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## REALAUDIO

```TypeScript
REALAUDIO = 'com.real.realaudio'
```

RealMedia音频类型，归属类型为AUDIO。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UniformDataType-REALAUDIO = 'com.real.realaudio'--><!--Device-UniformDataType-REALAUDIO = 'com.real.realaudio'-End-->

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## MATROSKA_AUDIO

```TypeScript
MATROSKA_AUDIO = 'org.matroska.mka'
```

MKA音频类型，归属类型为AUDIO。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UniformDataType-MATROSKA_AUDIO = 'org.matroska.mka'--><!--Device-UniformDataType-MATROSKA_AUDIO = 'org.matroska.mka'-End-->

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## FILE

```TypeScript
FILE = 'general.file'
```

所有文件的基类型，归属类型为ENTITY。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-UniformDataType-FILE = 'general.file'--><!--Device-UniformDataType-FILE = 'general.file'-End-->

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## DIRECTORY

```TypeScript
DIRECTORY = 'general.directory'
```

所有目录的基类型，归属类型为ENTITY。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UniformDataType-DIRECTORY = 'general.directory'--><!--Device-UniformDataType-DIRECTORY = 'general.directory'-End-->

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## FOLDER

```TypeScript
FOLDER = 'general.folder'
```

所有文件夹的基类型，归属类型为DIRECTORY。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-UniformDataType-FOLDER = 'general.folder'--><!--Device-UniformDataType-FOLDER = 'general.folder'-End-->

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## SYMLINK

```TypeScript
SYMLINK = 'general.symlink'
```

所有符号链接的基类型，归属类型为ENTITY。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UniformDataType-SYMLINK = 'general.symlink'--><!--Device-UniformDataType-SYMLINK = 'general.symlink'-End-->

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## ARCHIVE

```TypeScript
ARCHIVE = 'general.archive'
```

所有文件和目录存档文件的基类型，归属类型为OBJECT。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UniformDataType-ARCHIVE = 'general.archive'--><!--Device-UniformDataType-ARCHIVE = 'general.archive'-End-->

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## BZ2_ARCHIVE

```TypeScript
BZ2_ARCHIVE = 'general.bz2-archive'
```

BZ2存档文件类型，归属类型为ARCHIVE。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UniformDataType-BZ2_ARCHIVE = 'general.bz2-archive'--><!--Device-UniformDataType-BZ2_ARCHIVE = 'general.bz2-archive'-End-->

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## OPG

```TypeScript
OPG = 'general.opg'
```

OPG存档文件类型，归属类型为ARCHIVE。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UniformDataType-OPG = 'general.opg'--><!--Device-UniformDataType-OPG = 'general.opg'-End-->

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## TAZ_ARCHIVE

```TypeScript
TAZ_ARCHIVE = 'general.taz-archive'
```

TAR压缩文件类型，归属类型为TAR_ARCHIVE。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UniformDataType-TAZ_ARCHIVE = 'general.taz-archive'--><!--Device-UniformDataType-TAZ_ARCHIVE = 'general.taz-archive'-End-->

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## WEB_ARCHIVE

```TypeScript
WEB_ARCHIVE = 'general.web-archive'
```

MHTML网页归档文件类型，归属类型为ARCHIVE。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UniformDataType-WEB_ARCHIVE = 'general.web-archive'--><!--Device-UniformDataType-WEB_ARCHIVE = 'general.web-archive'-End-->

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## DISK_IMAGE

```TypeScript
DISK_IMAGE = 'general.disk-image'
```

所有可作为卷挂载项的文件类型的基类型，归属类型为ARCHIVE。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UniformDataType-DISK_IMAGE = 'general.disk-image'--><!--Device-UniformDataType-DISK_IMAGE = 'general.disk-image'-End-->

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## ISO

```TypeScript
ISO = 'general.iso'
```

光盘映像文件类型，归属类型为DISK_IMAGE。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UniformDataType-ISO = 'general.iso'--><!--Device-UniformDataType-ISO = 'general.iso'-End-->

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## TAR_ARCHIVE

```TypeScript
TAR_ARCHIVE = 'general.tar-archive'
```

TAR存档文件类型，归属类型为ARCHIVE。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UniformDataType-TAR_ARCHIVE = 'general.tar-archive'--><!--Device-UniformDataType-TAR_ARCHIVE = 'general.tar-archive'-End-->

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## ZIP_ARCHIVE

```TypeScript
ZIP_ARCHIVE = 'general.zip-archive'
```

ZIP存档文件类型，归属类型为ARCHIVE。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UniformDataType-ZIP_ARCHIVE = 'general.zip-archive'--><!--Device-UniformDataType-ZIP_ARCHIVE = 'general.zip-archive'-End-->

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## JAVA_ARCHIVE

```TypeScript
JAVA_ARCHIVE = 'com.sun.java-archive'
```

JAVA存档文件类型，归属类型为ARCHIVE和EXECUTABLE。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UniformDataType-JAVA_ARCHIVE = 'com.sun.java-archive'--><!--Device-UniformDataType-JAVA_ARCHIVE = 'com.sun.java-archive'-End-->

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## GNU_TAR_ARCHIVE

```TypeScript
GNU_TAR_ARCHIVE = 'org.gnu.gnu-tar-archive'
```

GNU存档文件类型，归属类型为ARCHIVE。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UniformDataType-GNU_TAR_ARCHIVE = 'org.gnu.gnu-tar-archive'--><!--Device-UniformDataType-GNU_TAR_ARCHIVE = 'org.gnu.gnu-tar-archive'-End-->

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## GNU_ZIP_ARCHIVE

```TypeScript
GNU_ZIP_ARCHIVE = 'org.gnu.gnu-zip-archive'
```

GZIP存档文件类型，归属类型为ARCHIVE。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UniformDataType-GNU_ZIP_ARCHIVE = 'org.gnu.gnu-zip-archive'--><!--Device-UniformDataType-GNU_ZIP_ARCHIVE = 'org.gnu.gnu-zip-archive'-End-->

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## GNU_ZIP_TAR_ARCHIVE

```TypeScript
GNU_ZIP_TAR_ARCHIVE = 'org.gnu.gnu-zip-tar-archive'
```

GZIP TAR存档文件类型，归属类型为ARCHIVE。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UniformDataType-GNU_ZIP_TAR_ARCHIVE = 'org.gnu.gnu-zip-tar-archive'--><!--Device-UniformDataType-GNU_ZIP_TAR_ARCHIVE = 'org.gnu.gnu-zip-tar-archive'-End-->

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## OPENXML

```TypeScript
OPENXML = 'org.openxmlformats.openxml'
```

开源XML基类型，归属类型为ARCHIVE。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UniformDataType-OPENXML = 'org.openxmlformats.openxml'--><!--Device-UniformDataType-OPENXML = 'org.openxmlformats.openxml'-End-->

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## WORDPROCESSINGML_DOCUMENT

```TypeScript
WORDPROCESSINGML_DOCUMENT = 'org.openxmlformats.wordprocessingml.document'
```

开源XML文档类型，归属类型为OPENXML和COMPOSITE_OBJECT。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UniformDataType-WORDPROCESSINGML_DOCUMENT = 'org.openxmlformats.wordprocessingml.document'--><!--Device-UniformDataType-WORDPROCESSINGML_DOCUMENT = 'org.openxmlformats.wordprocessingml.document'-End-->

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## SPREADSHEETML_SHEET

```TypeScript
SPREADSHEETML_SHEET = 'org.openxmlformats.spreadsheetml.sheet'
```

开源XML电子表格类型，归属类型为OPENXML和COMPOSITE_OBJECT。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UniformDataType-SPREADSHEETML_SHEET = 'org.openxmlformats.spreadsheetml.sheet'--><!--Device-UniformDataType-SPREADSHEETML_SHEET = 'org.openxmlformats.spreadsheetml.sheet'-End-->

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## PRESENTATIONML_PRESENTATION

```TypeScript
PRESENTATIONML_PRESENTATION = 'org.openxmlformats.presentationml.presentation'
```

开源XML演示文稿类型，归属类型为OPENXML和COMPOSITE_OBJECT。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UniformDataType-PRESENTATIONML_PRESENTATION = 'org.openxmlformats.presentationml.presentation'--><!--Device-UniformDataType-PRESENTATIONML_PRESENTATION = 'org.openxmlformats.presentationml.presentation'-End-->

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## DRAWINGML_VISIO

```TypeScript
DRAWINGML_VISIO = 'org.openxmlformats.drawingml.visio'
```

开源XML绘图文件类型，归属类型为OPENXML和COMPOSITE_OBJECT。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UniformDataType-DRAWINGML_VISIO = 'org.openxmlformats.drawingml.visio'--><!--Device-UniformDataType-DRAWINGML_VISIO = 'org.openxmlformats.drawingml.visio'-End-->

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## DRAWINGML_TEMPLATE

```TypeScript
DRAWINGML_TEMPLATE = 'org.openxmlformats.drawingml.template'
```

开源XML绘图模板类型，归属类型为OPENXML和COMPOSITE_OBJECT。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UniformDataType-DRAWINGML_TEMPLATE = 'org.openxmlformats.drawingml.template'--><!--Device-UniformDataType-DRAWINGML_TEMPLATE = 'org.openxmlformats.drawingml.template'-End-->

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## WORDPROCESSINGML_TEMPLATE

```TypeScript
WORDPROCESSINGML_TEMPLATE = 'org.openxmlformats.wordprocessingml.template'
```

开源XML文档模板类型，归属类型为OPENXML和COMPOSITE_OBJECT。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UniformDataType-WORDPROCESSINGML_TEMPLATE = 'org.openxmlformats.wordprocessingml.template'--><!--Device-UniformDataType-WORDPROCESSINGML_TEMPLATE = 'org.openxmlformats.wordprocessingml.template'-End-->

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## PRESENTATIONML_TEMPLATE

```TypeScript
PRESENTATIONML_TEMPLATE = 'org.openxmlformats.presentationml.template'
```

开源XML演示文稿模板类型，归属类型为OPENXML和COMPOSITE_OBJECT。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UniformDataType-PRESENTATIONML_TEMPLATE = 'org.openxmlformats.presentationml.template'--><!--Device-UniformDataType-PRESENTATIONML_TEMPLATE = 'org.openxmlformats.presentationml.template'-End-->

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## PRESENTATIONML_SLIDESHOW

```TypeScript
PRESENTATIONML_SLIDESHOW = 'org.openxmlformats.presentationml.slideshow'
```

开源XML演示文稿幻灯片放映类型，归属类型为OPENXML和COMPOSITE_OBJECT。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UniformDataType-PRESENTATIONML_SLIDESHOW = 'org.openxmlformats.presentationml.slideshow'--><!--Device-UniformDataType-PRESENTATIONML_SLIDESHOW = 'org.openxmlformats.presentationml.slideshow'-End-->

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## SPREADSHEETML_TEMPLATE

```TypeScript
SPREADSHEETML_TEMPLATE = 'org.openxmlformats.spreadsheetml.template'
```

开源XML电子表格模板类型，归属类型为OPENXML和COMPOSITE_OBJECT。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UniformDataType-SPREADSHEETML_TEMPLATE = 'org.openxmlformats.spreadsheetml.template'--><!--Device-UniformDataType-SPREADSHEETML_TEMPLATE = 'org.openxmlformats.spreadsheetml.template'-End-->

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## OPENDOCUMENT

```TypeScript
OPENDOCUMENT = 'org.oasis.opendocument'
```

Office应用程序的开源文档类型，归属类型为ARCHIVE。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UniformDataType-OPENDOCUMENT = 'org.oasis.opendocument'--><!--Device-UniformDataType-OPENDOCUMENT = 'org.oasis.opendocument'-End-->

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## OPENDOCUMENT_TEXT

```TypeScript
OPENDOCUMENT_TEXT = 'org.oasis.opendocument.text'
```

开源文档类型，归属类型为OPENDOCUMENT和COMPOSITE_OBJECT。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UniformDataType-OPENDOCUMENT_TEXT = 'org.oasis.opendocument.text'--><!--Device-UniformDataType-OPENDOCUMENT_TEXT = 'org.oasis.opendocument.text'-End-->

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## OPENDOCUMENT_SPREADSHEET

```TypeScript
OPENDOCUMENT_SPREADSHEET = 'org.oasis.opendocument.spreadsheet'
```

开源文档电子表格类型，归属类型为OPENDOCUMENT和COMPOSITE_OBJECT。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UniformDataType-OPENDOCUMENT_SPREADSHEET = 'org.oasis.opendocument.spreadsheet'--><!--Device-UniformDataType-OPENDOCUMENT_SPREADSHEET = 'org.oasis.opendocument.spreadsheet'-End-->

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## OPENDOCUMENT_PRESENTATION

```TypeScript
OPENDOCUMENT_PRESENTATION = 'org.oasis.opendocument.presentation'
```

开源文档演示类型，归属类型为OPENDOCUMENT和COMPOSITE_OBJECT。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UniformDataType-OPENDOCUMENT_PRESENTATION = 'org.oasis.opendocument.presentation'--><!--Device-UniformDataType-OPENDOCUMENT_PRESENTATION = 'org.oasis.opendocument.presentation'-End-->

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## OPENDOCUMENT_GRAPHICS

```TypeScript
OPENDOCUMENT_GRAPHICS = 'org.oasis.opendocument.graphics'
```

开源文档图形类型，归属类型为OPENDOCUMENT和COMPOSITE_OBJECT。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UniformDataType-OPENDOCUMENT_GRAPHICS = 'org.oasis.opendocument.graphics'--><!--Device-UniformDataType-OPENDOCUMENT_GRAPHICS = 'org.oasis.opendocument.graphics'-End-->

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## OPENDOCUMENT_FORMULA

```TypeScript
OPENDOCUMENT_FORMULA = 'org.oasis.opendocument.formula'
```

开源文档公式集类型，归属类型为OPENDOCUMENT。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UniformDataType-OPENDOCUMENT_FORMULA = 'org.oasis.opendocument.formula'--><!--Device-UniformDataType-OPENDOCUMENT_FORMULA = 'org.oasis.opendocument.formula'-End-->

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## STUFFIT_ARCHIVE

```TypeScript
STUFFIT_ARCHIVE = 'com.allume.stuffit-archive'
```

Stuffit压缩格式类型（Stuffit archive），归属类型为ARCHIVE。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UniformDataType-STUFFIT_ARCHIVE = 'com.allume.stuffit-archive'--><!--Device-UniformDataType-STUFFIT_ARCHIVE = 'com.allume.stuffit-archive'-End-->

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## RAR_ARCHIVE

```TypeScript
RAR_ARCHIVE = 'com.rarlab.rar-archive'
```

WinRAR压缩格式类型，归属类型为ARCHIVE。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UniformDataType-RAR_ARCHIVE = 'com.rarlab.rar-archive'--><!--Device-UniformDataType-RAR_ARCHIVE = 'com.rarlab.rar-archive'-End-->

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## SEVEN_ZIP_ARCHIVE

```TypeScript
SEVEN_ZIP_ARCHIVE = 'org.7-zip.7-zip-archive'
```

7-zip压缩格式类型，归属类型为ARCHIVE。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UniformDataType-SEVEN_ZIP_ARCHIVE = 'org.7-zip.7-zip-archive'--><!--Device-UniformDataType-SEVEN_ZIP_ARCHIVE = 'org.7-zip.7-zip-archive'-End-->

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## CALENDAR

```TypeScript
CALENDAR = 'general.calendar'
```

所有日程类数据的基类型，归属类型为OBJECT。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UniformDataType-CALENDAR = 'general.calendar'--><!--Device-UniformDataType-CALENDAR = 'general.calendar'-End-->

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## VCS

```TypeScript
VCS = 'general.vcs'
```

VCalendar日历数据类型，归属类型为CALENDAR和TEXT。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UniformDataType-VCS = 'general.vcs'--><!--Device-UniformDataType-VCS = 'general.vcs'-End-->

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## ICS

```TypeScript
ICS = 'general.ics'
```

ICalendar日历数据类型，归属类型为CALENDAR和TEXT。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UniformDataType-ICS = 'general.ics'--><!--Device-UniformDataType-ICS = 'general.ics'-End-->

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## CONTACT

```TypeScript
CONTACT = 'general.contact'
```

所有联系人类数据的基类型，归属类型为OBJECT。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UniformDataType-CONTACT = 'general.contact'--><!--Device-UniformDataType-CONTACT = 'general.contact'-End-->

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## DATABASE

```TypeScript
DATABASE = 'general.database'
```

所有数据库文件的基类型，归属类型为OBJECT。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UniformDataType-DATABASE = 'general.database'--><!--Device-UniformDataType-DATABASE = 'general.database'-End-->

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## MESSAGE

```TypeScript
MESSAGE = 'general.message'
```

所有消息类数据的基类型，归属类型为OBJECT。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UniformDataType-MESSAGE = 'general.message'--><!--Device-UniformDataType-MESSAGE = 'general.message'-End-->

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## EXECUTABLE

```TypeScript
EXECUTABLE = 'general.executable'
```

所有可执行文件的基类型，归属类型为OBJECT。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UniformDataType-EXECUTABLE = 'general.executable'--><!--Device-UniformDataType-EXECUTABLE = 'general.executable'-End-->

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## PORTABLE_EXECUTABLE

```TypeScript
PORTABLE_EXECUTABLE = 'com.microsoft.portable-executable'
```

Microsoft Windows应用程序类型，归属类型为EXECUTABLE。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UniformDataType-PORTABLE_EXECUTABLE = 'com.microsoft.portable-executable'--><!--Device-UniformDataType-PORTABLE_EXECUTABLE = 'com.microsoft.portable-executable'-End-->

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## SUN_JAVA_CLASS

```TypeScript
SUN_JAVA_CLASS = 'com.sun.java-class'
```

Java类文件类型，归属类型为EXECUTABLE。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UniformDataType-SUN_JAVA_CLASS = 'com.sun.java-class'--><!--Device-UniformDataType-SUN_JAVA_CLASS = 'com.sun.java-class'-End-->

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## VCARD

```TypeScript
VCARD = 'general.vcard'
```

所有电子名片类数据的基类型，归属类型为OBJECT。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UniformDataType-VCARD = 'general.vcard'--><!--Device-UniformDataType-VCARD = 'general.vcard'-End-->

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## NAVIGATION

```TypeScript
NAVIGATION = 'general.navigation'
```

所有导航类数据的基类型，归属类型为OBJECT。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UniformDataType-NAVIGATION = 'general.navigation'--><!--Device-UniformDataType-NAVIGATION = 'general.navigation'-End-->

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## LOCATION

```TypeScript
LOCATION = 'general.location'
```

导航定位类型，归属类型为NAVIGATION。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UniformDataType-LOCATION = 'general.location'--><!--Device-UniformDataType-LOCATION = 'general.location'-End-->

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## FONT

```TypeScript
FONT = 'general.font'
```

所有字体数据类型的基础类型，归属类型为OBJECT。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UniformDataType-FONT = 'general.font'--><!--Device-UniformDataType-FONT = 'general.font'-End-->

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## TRUETYPE_FONT

```TypeScript
TRUETYPE_FONT = 'general.truetype-font'
```

TrueType字体类型，归属类型为FONT。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UniformDataType-TRUETYPE_FONT = 'general.truetype-font'--><!--Device-UniformDataType-TRUETYPE_FONT = 'general.truetype-font'-End-->

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## TRUETYPE_COLLECTION_FONT

```TypeScript
TRUETYPE_COLLECTION_FONT = 'general.truetype-collection-font'
```

TrueType collection字体类型，归属类型为FONT。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UniformDataType-TRUETYPE_COLLECTION_FONT = 'general.truetype-collection-font'--><!--Device-UniformDataType-TRUETYPE_COLLECTION_FONT = 'general.truetype-collection-font'-End-->

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## OPENTYPE_FONT

```TypeScript
OPENTYPE_FONT = 'general.opentype-font'
```

OpenType 字体类型，归属类型为FONT。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UniformDataType-OPENTYPE_FONT = 'general.opentype-font'--><!--Device-UniformDataType-OPENTYPE_FONT = 'general.opentype-font'-End-->

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## POSTSCRIPT_FONT

```TypeScript
POSTSCRIPT_FONT = 'com.adobe.postscript-font'
```

PostScript 字体类型，归属类型为FONT。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UniformDataType-POSTSCRIPT_FONT = 'com.adobe.postscript-font'--><!--Device-UniformDataType-POSTSCRIPT_FONT = 'com.adobe.postscript-font'-End-->

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## POSTSCRIPT_PFB_FONT

```TypeScript
POSTSCRIPT_PFB_FONT = 'com.adobe.postscript-pfb-font'
```

PostScript Font Binary字体类型，归属类型为FONT。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UniformDataType-POSTSCRIPT_PFB_FONT = 'com.adobe.postscript-pfb-font'--><!--Device-UniformDataType-POSTSCRIPT_PFB_FONT = 'com.adobe.postscript-pfb-font'-End-->

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## POSTSCRIPT_PFA_FONT

```TypeScript
POSTSCRIPT_PFA_FONT = 'com.adobe.postscript-pfa-font'
```

Adobe Type 1 字体类型，归属类型为FONT。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UniformDataType-POSTSCRIPT_PFA_FONT = 'com.adobe.postscript-pfa-font'--><!--Device-UniformDataType-POSTSCRIPT_PFA_FONT = 'com.adobe.postscript-pfa-font'-End-->

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## OPENHARMONY_FORM

```TypeScript
OPENHARMONY_FORM = 'openharmony.form'
```

系统定义的卡片类型，归属类型为OBJECT。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-UniformDataType-OPENHARMONY_FORM = 'openharmony.form'--><!--Device-UniformDataType-OPENHARMONY_FORM = 'openharmony.form'-End-->

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## OPENHARMONY_APP_ITEM

```TypeScript
OPENHARMONY_APP_ITEM = 'openharmony.app-item'
```

系统定义的桌面图标类型，归属类型为OBJECT。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-UniformDataType-OPENHARMONY_APP_ITEM = 'openharmony.app-item'--><!--Device-UniformDataType-OPENHARMONY_APP_ITEM = 'openharmony.app-item'-End-->

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## OPENHARMONY_PIXEL_MAP

```TypeScript
OPENHARMONY_PIXEL_MAP = 'openharmony.pixel-map'
```

系统定义的像素图类型，归属类型为IMAGE。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-UniformDataType-OPENHARMONY_PIXEL_MAP = 'openharmony.pixel-map'--><!--Device-UniformDataType-OPENHARMONY_PIXEL_MAP = 'openharmony.pixel-map'-End-->

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## OPENHARMONY_ATOMIC_SERVICE

```TypeScript
OPENHARMONY_ATOMIC_SERVICE = 'openharmony.atomic-service'
```

系统定义的原子化服务类型，归属类型为OBJECT。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UniformDataType-OPENHARMONY_ATOMIC_SERVICE = 'openharmony.atomic-service'--><!--Device-UniformDataType-OPENHARMONY_ATOMIC_SERVICE = 'openharmony.atomic-service'-End-->

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## OPENHARMONY_PACKAGE

```TypeScript
OPENHARMONY_PACKAGE = 'openharmony.package'
```

系统定义的包（即目录的打包文件），归属类型为DIRECTORY。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UniformDataType-OPENHARMONY_PACKAGE = 'openharmony.package'--><!--Device-UniformDataType-OPENHARMONY_PACKAGE = 'openharmony.package'-End-->

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## OPENHARMONY_HAP

```TypeScript
OPENHARMONY_HAP = 'openharmony.hap'
```

系统定义的能力包，归属类型为OPENHARMONY_PACKAGE。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UniformDataType-OPENHARMONY_HAP = 'openharmony.hap'--><!--Device-UniformDataType-OPENHARMONY_HAP = 'openharmony.hap'-End-->

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## OPENHARMONY_HDOC

```TypeScript
OPENHARMONY_HDOC = 'openharmony.hdoc'
```

系统定义的备忘录数据类型，归属类型为COMPOSITE_OBJECT。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UniformDataType-OPENHARMONY_HDOC = 'openharmony.hdoc'--><!--Device-UniformDataType-OPENHARMONY_HDOC = 'openharmony.hdoc'-End-->

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## OPENHARMONY_HINOTE

```TypeScript
OPENHARMONY_HINOTE = 'openharmony.hinote'
```

系统定义的笔记数据类型，归属类型为COMPOSITE_OBJECT。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UniformDataType-OPENHARMONY_HINOTE = 'openharmony.hinote'--><!--Device-UniformDataType-OPENHARMONY_HINOTE = 'openharmony.hinote'-End-->

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## OPENHARMONY_STYLED_STRING

```TypeScript
OPENHARMONY_STYLED_STRING = 'openharmony.styled-string'
```

系统定义的样式字符串类型，归属类型为COMPOSITE_OBJECT。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UniformDataType-OPENHARMONY_STYLED_STRING = 'openharmony.styled-string'--><!--Device-UniformDataType-OPENHARMONY_STYLED_STRING = 'openharmony.styled-string'-End-->

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## OPENHARMONY_WANT

```TypeScript
OPENHARMONY_WANT = 'openharmony.want'
```

系统定义的Want类型，归属类型为OBJECT。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UniformDataType-OPENHARMONY_WANT = 'openharmony.want'--><!--Device-UniformDataType-OPENHARMONY_WANT = 'openharmony.want'-End-->

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## OFD

```TypeScript
OFD = 'general.ofd'
```

开放版式文档类型，归属类型为COMPOSITE_OBJECT。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UniformDataType-OFD = 'general.ofd'--><!--Device-UniformDataType-OFD = 'general.ofd'-End-->

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## CAD

```TypeScript
CAD = 'general.cad'
```

所有计算机辅助设计类型的基类型，归属类型为OBJECT。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UniformDataType-CAD = 'general.cad'--><!--Device-UniformDataType-CAD = 'general.cad'-End-->

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## OCTET_STREAM

```TypeScript
OCTET_STREAM = 'general.octet-stream'
```

任意二进制数据类型，归属类型为OBJECT。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UniformDataType-OCTET_STREAM = 'general.octet-stream'--><!--Device-UniformDataType-OCTET_STREAM = 'general.octet-stream'-End-->

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## FILE_URI

```TypeScript
FILE_URI = 'general.file-uri'
```

文件地址类型，归属类型为TEXT。

**起始版本：** 15

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UniformDataType-FILE_URI = 'general.file-uri'--><!--Device-UniformDataType-FILE_URI = 'general.file-uri'-End-->

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## CONTENT_FORM

```TypeScript
CONTENT_FORM = 'general.content-form'
```

内容卡片类型，归属类型为OBJECT。

**起始版本：** 15

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UniformDataType-CONTENT_FORM = 'general.content-form'--><!--Device-UniformDataType-CONTENT_FORM = 'general.content-form'-End-->

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

