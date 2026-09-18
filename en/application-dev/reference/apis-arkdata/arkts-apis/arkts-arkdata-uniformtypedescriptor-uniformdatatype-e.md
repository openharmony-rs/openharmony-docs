# UniformDataType

Enumerates the uniform data types. Some data types are related. For example, the JPEG type belongs to the IMAGE type. For more preset data types, see [Preset UTD List].

The following table lists the common uniform data types.

**Since:** 10

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core

## ENTITY

```TypeScript
ENTITY = 'general.entity'
```

Generic physical storage type.

This type is uncategorized.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core

## OBJECT

```TypeScript
OBJECT = 'general.object'
```

Generic logical content type.

This type is uncategorized.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core

## COMPOSITE_OBJECT

```TypeScript
COMPOSITE_OBJECT = 'general.composite-object'
```

Generic composite content type. For example, a PDF file that contains text and image.

This type belongs to **OBJECT**.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core

## TEXT

```TypeScript
TEXT = 'general.text'
```

Generic text type.

This type belongs to **OBJECT**.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core

## PLAIN_TEXT

```TypeScript
PLAIN_TEXT = 'general.plain-text'
```

Text without specific encoding or identifier.

This type belongs to **TEXT**.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core

## HTML

```TypeScript
HTML = 'general.html'
```

HTML.

This type belongs to **TEXT**.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core

## HYPERLINK

```TypeScript
HYPERLINK = 'general.hyperlink'
```

Hyperlink.

This type belongs to **TEXT**.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core

## XML

```TypeScript
XML = 'general.xml'
```

XML.

This type belongs to **TEXT**.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core

## XHTML

```TypeScript
XHTML = 'general.xhtml'
```

XHTML.

This type belongs to **XML**.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core

## RSS

```TypeScript
RSS = 'general.rss'
```

RSS.

This type belongs to **XML**.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core

## SMIL

```TypeScript
SMIL = 'com.real.smil'
```

Synchronized Multimedia Integration Language (SMIL).

This type belongs to **XML**.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core

## SOURCE_CODE

```TypeScript
SOURCE_CODE = 'general.source-code'
```

Generic source code type.

This type belongs to **TEXT**.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core

## SCRIPT

```TypeScript
SCRIPT = 'general.script'
```

Source code in any scripting language.

This type belongs to **SOURCE_CODE**.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core

## SHELL_SCRIPT

```TypeScript
SHELL_SCRIPT = 'general.shell-script'
```

Shell script.

This type belongs to **SCRIPT**.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core

## CSH_SCRIPT

```TypeScript
CSH_SCRIPT = 'general.csh-script'
```

C shell script.

This type belongs to **SHELL_SCRIPT**.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core

## PERL_SCRIPT

```TypeScript
PERL_SCRIPT = 'general.perl-script'
```

Perl script.

This type belongs to **SHELL_SCRIPT**.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core

## PHP_SCRIPT

```TypeScript
PHP_SCRIPT = 'general.php-script'
```

PHP script.

This type belongs to **SHELL_SCRIPT**.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core

## PYTHON_SCRIPT

```TypeScript
PYTHON_SCRIPT = 'general.python-script'
```

Python script.

This type belongs to **SHELL_SCRIPT**.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core

## RUBY_SCRIPT

```TypeScript
RUBY_SCRIPT = 'general.ruby-script'
```

Ruby script.

This type belongs to **SHELL_SCRIPT**.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core

## TYPE_SCRIPT

```TypeScript
TYPE_SCRIPT = 'general.type-script'
```

TypeScript source code.

This type belongs to **SOURCE_CODE**.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core

## JAVA_SCRIPT

```TypeScript
JAVA_SCRIPT = 'general.java-script'
```

JavaScript source code.

This type belongs to **SOURCE_CODE**.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core

## CSS

```TypeScript
CSS = 'general.css'
```

CSS.

This type belongs to **SCRIPT**.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core

## C_HEADER

```TypeScript
C_HEADER = 'general.c-header'
```

Header file in C.

This type belongs to **SOURCE_CODE**.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core

## C_SOURCE

```TypeScript
C_SOURCE = 'general.c-source'
```

Source code in C.

This type belongs to **SOURCE_CODE**.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core

## C_PLUS_PLUS_HEADER

```TypeScript
C_PLUS_PLUS_HEADER = 'general.c-plus-plus-header'
```

Header file in C++.

This type belongs to **SOURCE_CODE**.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core

## C_PLUS_PLUS_SOURCE

```TypeScript
C_PLUS_PLUS_SOURCE = 'general.c-plus-plus-source'
```

Source code in C++.

This type belongs to **SOURCE_CODE**.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core

## JAVA_SOURCE

```TypeScript
JAVA_SOURCE = 'general.java-source'
```

Source code in Java.

This type belongs to **SOURCE_CODE**.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core

## TEX

```TypeScript
TEX = 'general.tex'
```

Source code in TEX format.

This type belongs to **SOURCE_CODE**.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core

## MARKDOWN

```TypeScript
MARKDOWN = 'general.markdown'
```

Markdown.

This type belongs to **TEXT**.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core

## ASC_TEXT

```TypeScript
ASC_TEXT = 'general.asc-text'
```

ASCII.

This type belongs to **TEXT**.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core

## RICH_TEXT

```TypeScript
RICH_TEXT = 'general.rich-text'
```

Rich text.

This type belongs to **TEXT**.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core

## DELIMITED_VALUES_TEXT

```TypeScript
DELIMITED_VALUES_TEXT = 'general.delimited-values-text'
```

Generic type of all delimited value texts.

This type belongs to **TEXT**.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core

## COMMA_SEPARATED_VALUES_TEXT

```TypeScript
COMMA_SEPARATED_VALUES_TEXT = 'general.comma-separated-values-text'
```

Comma-separated values (CSV).

This type belongs to **DELIMITED_VALUES_TEXT**.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core

## TAB_SEPARATED_VALUES_TEXT

```TypeScript
TAB_SEPARATED_VALUES_TEXT = 'general.tab-separated-values-text'
```

Tab-separated values (TSV).

This type belongs to **DELIMITED_VALUES_TEXT**.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core

## EBOOK

```TypeScript
EBOOK = 'general.ebook'
```

Generic eBook file format type.

This type belongs to **COMPOSITE_OBJECT**.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core

## EPUB

```TypeScript
EPUB = 'general.epub'
```

Electronic publication (EPUB).

This type belongs to **EBOOK**.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core

## AZW

```TypeScript
AZW = 'com.amazon.azw'
```

AZW.

This type belongs to **EBOOK**.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core

## AZW3

```TypeScript
AZW3 = 'com.amazon.azw3'
```

AZW3.

This type belongs to **EBOOK**.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core

## KFX

```TypeScript
KFX = 'com.amazon.kfx'
```

KFX.

This type belongs to **EBOOK**.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core

## MOBI

```TypeScript
MOBI = 'com.amazon.mobi'
```

MOBI.

This type belongs to **EBOOK**.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core

## MEDIA

```TypeScript
MEDIA = 'general.media'
```

Generic media type.

This type belongs to **OBJECT**.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core

## IMAGE

```TypeScript
IMAGE = 'general.image'
```

Image.

This type belongs to **MEDIA**.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core

## JPEG

```TypeScript
JPEG = 'general.jpeg'
```

JPEG.

This type belongs to **IMAGE**.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core

## PNG

```TypeScript
PNG = 'general.png'
```

PNG.

This type belongs to **IMAGE**.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core

## RAW_IMAGE

```TypeScript
RAW_IMAGE = 'general.raw-image'
```

Raw image.

This type belongs to **IMAGE**.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core

## TIFF

```TypeScript
TIFF = 'general.tiff'
```

TIFF.

This type belongs to **IMAGE**.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core

## BMP

```TypeScript
BMP = 'com.microsoft.bmp'
```

BMP.

This type belongs to **IMAGE**.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core

## ICO

```TypeScript
ICO = 'com.microsoft.ico'
```

Windows icon.

This type belongs to **IMAGE**.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core

## PHOTOSHOP_IMAGE

```TypeScript
PHOTOSHOP_IMAGE = 'com.adobe.photoshop-image'
```

Adobe Photoshop image.

This type belongs to **IMAGE**.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core

## AI_IMAGE

```TypeScript
AI_IMAGE = 'com.adobe.illustrator.ai-image'
```

Adobe Illustrator image (.ai).

This type belongs to **IMAGE**.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core

## FAX

```TypeScript
FAX = 'general.fax'
```

Generic type of the fax.

This type belongs to **IMAGE**.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core

## JFX_FAX

```TypeScript
JFX_FAX = 'com.j2.jfx-fax'
```

J2 jConnect fax file format.

This type belongs to **FAX**.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core

## EFX_FAX

```TypeScript
EFX_FAX = 'com.js.efx-fax'
```

EFX file format.

This type belongs to **FAX**.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core

## XBITMAP_IMAGE

```TypeScript
XBITMAP_IMAGE = 'general.xbitmap-image'
```

X BitMAP (XBM) used in the X Window system (X11).

This type belongs to **IMAGE**.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core

## GIF

```TypeScript
GIF = 'general.gif'
```

GIF.

This type belongs to **IMAGE**.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core

## TGA_IMAGE

```TypeScript
TGA_IMAGE = 'com.truevision.tga-image'
```

Tagged Graphics (TGA) format.

This type belongs to **IMAGE**.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core

## SGI_IMAGE

```TypeScript
SGI_IMAGE = 'com.sgi.sgi-image'
```

Silicon Graphics image (SGI) format.

This type belongs to **IMAGE**.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core

## OPENEXR_IMAGE

```TypeScript
OPENEXR_IMAGE = 'com.ilm.openexr-image'
```

OpenXR image format.

This type belongs to **IMAGE**.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core

## FLASHPIX_IMAGE

```TypeScript
FLASHPIX_IMAGE = 'com.kodak.flashpix.image'
```

FlashPix image format.

This type belongs to **IMAGE**.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core

## WORD_DOC

```TypeScript
WORD_DOC = 'com.microsoft.word.doc'
```

Microsoft Word.

This type belongs to **COMPOSITE_OBJECT**.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core

## EXCEL

```TypeScript
EXCEL = 'com.microsoft.excel.xls'
```

Microsoft Excel.

This type belongs to **COMPOSITE_OBJECT**.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core

## PPT

```TypeScript
PPT = 'com.microsoft.powerpoint.ppt'
```

Microsoft PowerPoint presentation format.

This type belongs to **COMPOSITE_OBJECT**.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core

## WORD_DOT

```TypeScript
WORD_DOT = 'com.microsoft.word.dot'
```

Microsoft Word template.

This type belongs to **COMPOSITE_OBJECT**.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core

## POWERPOINT_PPS

```TypeScript
POWERPOINT_PPS = 'com.microsoft.powerpoint.pps'
```

Microsoft PowerPoint slide show format.

This type belongs to **COMPOSITE_OBJECT**.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core

## POWERPOINT_POT

```TypeScript
POWERPOINT_POT = 'com.microsoft.powerpoint.pot'
```

Microsoft PowerPoint template.

This type belongs to **COMPOSITE_OBJECT**.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core

## EXCEL_XLT

```TypeScript
EXCEL_XLT = 'com.microsoft.excel.xlt'
```

Microsoft Excel template.

This type belongs to **COMPOSITE_OBJECT**.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core

## VISIO_VSD

```TypeScript
VISIO_VSD = 'com.microsoft.visio.vsd'
```

Microsoft Visio.

This type belongs to **COMPOSITE_OBJECT**.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core

## PDF

```TypeScript
PDF = 'com.adobe.pdf'
```

PDF.

This type belongs to **COMPOSITE_OBJECT**.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core

## POSTSCRIPT

```TypeScript
POSTSCRIPT = 'com.adobe.postscript'
```

PostScript.

This type belongs to **COMPOSITE_OBJECT**.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core

## ENCAPSULATED_POSTSCRIPT

```TypeScript
ENCAPSULATED_POSTSCRIPT = 'com.adobe.encapsulated-postscript'
```

Encapsulated PostScript.

This type belongs to **POSTSCRIPT**.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core

## VIDEO

```TypeScript
VIDEO = 'general.video'
```

Generic video type.

This type belongs to **MEDIA**.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core

## AVI

```TypeScript
AVI = 'general.avi'
```

AVI.

This type belongs to **VIDEO**.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core

## MPEG

```TypeScript
MPEG = 'general.mpeg'
```

MPEG-1 or MPEG-2.

This type belongs to **VIDEO**.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core

## MPEG4

```TypeScript
MPEG4 = 'general.mpeg-4'
```

MPEG-4.

This type belongs to **VIDEO**.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core

## VIDEO_3GPP

```TypeScript
VIDEO_3GPP = 'general.3gpp'
```

3GP (3GPP file format).

This type belongs to **VIDEO**.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core

## VIDEO_3GPP2

```TypeScript
VIDEO_3GPP2 = 'general.3gpp2'
```

3G2 (3GPP2 file format).

This type belongs to **VIDEO**.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core

## TS

```TypeScript
TS = 'general.ts'
```

MPEG-TS.

This type belongs to **VIDEO**.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core

## MPEGURL_VIDEO

```TypeScript
MPEGURL_VIDEO = 'general.mpegurl-video'
```

MPEG video playlist format.

This type belongs to **VIDEO**.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core

## WINDOWS_MEDIA_WM

```TypeScript
WINDOWS_MEDIA_WM = 'com.microsoft.windows-media-wm'
```

Windows WM format.

This type belongs to **VIDEO**.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core

## WINDOWS_MEDIA_WMV

```TypeScript
WINDOWS_MEDIA_WMV = 'com.microsoft.windows-media-wmv'
```

Windows WMV format.

This type belongs to **VIDEO**.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core

## WINDOWS_MEDIA_WMP

```TypeScript
WINDOWS_MEDIA_WMP = 'com.microsoft.windows-media-wmp'
```

Windows WMP format.

This type belongs to **VIDEO**.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core

## WINDOWS_MEDIA_WVX

```TypeScript
WINDOWS_MEDIA_WVX = 'com.microsoft.windows-media-wvx'
```

Windows WVX format.

This type belongs to **VIDEO**.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core

## WINDOWS_MEDIA_WMX

```TypeScript
WINDOWS_MEDIA_WMX = 'com.microsoft.windows-media-wmx'
```

Windows WMX format.

This type belongs to **VIDEO**.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core

## REALMEDIA

```TypeScript
REALMEDIA = 'com.real.realmedia'
```

RealMedia format.

This type belongs to **VIDEO**.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core

## MATROSKA_VIDEO

```TypeScript
MATROSKA_VIDEO = 'org.matroska.mkv'
```

MKV.

This type belongs to **VIDEO**.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core

## FLASH

```TypeScript
FLASH = 'com.adobe.flash'
```

Flash.

This type belongs to **VIDEO**.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core

## AUDIO

```TypeScript
AUDIO = 'general.audio'
```

Generic audio type.

This type belongs to **MEDIA**.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core

## AAC

```TypeScript
AAC = 'general.aac'
```

AAC.

This type belongs to **AUDIO**.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core

## AIFF

```TypeScript
AIFF = 'general.aiff'
```

AIFF.

This type belongs to **AUDIO**.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core

## ALAC

```TypeScript
ALAC = 'general.alac'
```

ALAC.

This type belongs to **AUDIO**.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core

## FLAC

```TypeScript
FLAC = 'general.flac'
```

FLAC.

This type belongs to **AUDIO**.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core

## MP3

```TypeScript
MP3 = 'general.mp3'
```

MP3.

This type belongs to **AUDIO**.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core

## OGG

```TypeScript
OGG = 'general.ogg'
```

OGG.

This type belongs to **AUDIO**.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core

## PCM

```TypeScript
PCM = 'general.pcm'
```

PCM.

This type belongs to **AUDIO**.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core

## WINDOWS_MEDIA_WMA

```TypeScript
WINDOWS_MEDIA_WMA = 'com.microsoft.windows-media-wma'
```

Windows WMA.

This type belongs to **AUDIO**.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core

## WAVEFORM_AUDIO

```TypeScript
WAVEFORM_AUDIO = 'com.microsoft.waveform-audio'
```

Windows Waveform.

This type belongs to **AUDIO**.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core

## WINDOWS_MEDIA_WAX

```TypeScript
WINDOWS_MEDIA_WAX = 'com.microsoft.windows-media-wax'
```

Windows WAX.

This type belongs to **AUDIO**.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core

## AU_AUDIO

```TypeScript
AU_AUDIO = 'general.au-audio'
```

AU format.

This type belongs to **AUDIO**.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core

## AIFC_AUDIO

```TypeScript
AIFC_AUDIO = 'general.aifc-audio'
```

AIFC.

This type belongs to **AUDIO**.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core

## MPEGURL_AUDIO

```TypeScript
MPEGURL_AUDIO = 'general.mpegurl-audio'
```

MPEG audio playlist format.

This type belongs to **AUDIO**.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core

## MPEG_4_AUDIO

```TypeScript
MPEG_4_AUDIO = 'general.mpeg-4-audio'
```

MPEG-4.

This type belongs to **AUDIO**.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core

## MP2

```TypeScript
MP2 = 'general.mp2'
```

MP2.

This type belongs to **AUDIO**.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core

## MPEG_AUDIO

```TypeScript
MPEG_AUDIO = 'general.mpeg-audio'
```

MPEG audio format.

This type belongs to **AUDIO**.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core

## ULAW_AUDIO

```TypeScript
ULAW_AUDIO = 'general.ulaw-audio'
```

ULAW.

This type belongs to **AUDIO**.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core

## SD2_AUDIO

```TypeScript
SD2_AUDIO = 'com.digidesign.sd2-audio'
```

Digidesign Sound Designer II (SDII).

This type belongs to **AUDIO**.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core

## REALAUDIO

```TypeScript
REALAUDIO = 'com.real.realaudio'
```

RealAudio.

This type belongs to **AUDIO**.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core

## MATROSKA_AUDIO

```TypeScript
MATROSKA_AUDIO = 'org.matroska.mka'
```

MKA.

This type belongs to **AUDIO**.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core

## FILE

```TypeScript
FILE = 'general.file'
```

Generic file type.

This type belongs to **ENTITY**.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core

## DIRECTORY

```TypeScript
DIRECTORY = 'general.directory'
```

Generic directory type.

This type belongs to **ENTITY**.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core

## FOLDER

```TypeScript
FOLDER = 'general.folder'
```

Generic folder type.

This type belongs to **DIRECTORY**.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core

## SYMLINK

```TypeScript
SYMLINK = 'general.symlink'
```

Generic symbolic type.

This type belongs to **ENTITY**.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core

## ARCHIVE

```TypeScript
ARCHIVE = 'general.archive'
```

Generic archive file type.

This type belongs to **OBJECT**.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core

## BZ2_ARCHIVE

```TypeScript
BZ2_ARCHIVE = 'general.bz2-archive'
```

BZ2.

This type belongs to **ARCHIVE**.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core

## OPG

```TypeScript
OPG = 'general.opg'
```

OPG.

This type belongs to **ARCHIVE**.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core

## TAZ_ARCHIVE

```TypeScript
TAZ_ARCHIVE = 'general.taz-archive'
```

TAR.

This type belongs to **TAR_ARCHIVE**.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core

## WEB_ARCHIVE

```TypeScript
WEB_ARCHIVE = 'general.web-archive'
```

MHTML format for web page archiving.

This type belongs to **ARCHIVE**.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core

## DISK_IMAGE

```TypeScript
DISK_IMAGE = 'general.disk-image'
```

Generic type of any file that can be mounted as a volume.

This type belongs to **ARCHIVE**.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core

## ISO

```TypeScript
ISO = 'general.iso'
```

ISO image (optical disk image) format.

This type belongs to **DISK_IMAGE**.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core

## TAR_ARCHIVE

```TypeScript
TAR_ARCHIVE = 'general.tar-archive'
```

TAR.

This type belongs to ARCHIVE.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core

## ZIP_ARCHIVE

```TypeScript
ZIP_ARCHIVE = 'general.zip-archive'
```

ZIP.

This type belongs to **ARCHIVE**.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core

## JAVA_ARCHIVE

```TypeScript
JAVA_ARCHIVE = 'com.sun.java-archive'
```

JAR (Java archive).

This type belongs to **ARCHIVE** and **EXECUTABLE**.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core

## GNU_TAR_ARCHIVE

```TypeScript
GNU_TAR_ARCHIVE = 'org.gnu.gnu-tar-archive'
```

GNU.

This type belongs to **ARCHIVE**.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core

## GNU_ZIP_ARCHIVE

```TypeScript
GNU_ZIP_ARCHIVE = 'org.gnu.gnu-zip-archive'
```

GZIP archive.

This type belongs to **ARCHIVE**.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core

## GNU_ZIP_TAR_ARCHIVE

```TypeScript
GNU_ZIP_TAR_ARCHIVE = 'org.gnu.gnu-zip-tar-archive'
```

GZIP TAR.

This type belongs to **ARCHIVE**.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core

## OPENXML

```TypeScript
OPENXML = 'org.openxmlformats.openxml'
```

OpenXML base type.

This type belongs to **ARCHIVE**.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core

## WORDPROCESSINGML_DOCUMENT

```TypeScript
WORDPROCESSINGML_DOCUMENT = 'org.openxmlformats.wordprocessingml.document'
```

WordProcessingML format.

This type belongs to **OPENXML** and **COMPOSITE_OBJECT**.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core

## SPREADSHEETML_SHEET

```TypeScript
SPREADSHEETML_SHEET = 'org.openxmlformats.spreadsheetml.sheet'
```

SpreadsheetML format.

This type belongs to **OPENXML** and **COMPOSITE_OBJECT**.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core

## PRESENTATIONML_PRESENTATION

```TypeScript
PRESENTATIONML_PRESENTATION = 'org.openxmlformats.presentationml.presentation'
```

PresentationML format.

This type belongs to **OPENXML** and **COMPOSITE_OBJECT**.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core

## DRAWINGML_VISIO

```TypeScript
DRAWINGML_VISIO = 'org.openxmlformats.drawingml.visio'
```

DrawingML file format of Office Open XML (OOXML).

This type belongs to **OPENXML** and **COMPOSITE_OBJECT**.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core

## DRAWINGML_TEMPLATE

```TypeScript
DRAWINGML_TEMPLATE = 'org.openxmlformats.drawingml.template'
```

DrawingML template format of OOXML.

This type belongs to **OPENXML** and **COMPOSITE_OBJECT**.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core

## WORDPROCESSINGML_TEMPLATE

```TypeScript
WORDPROCESSINGML_TEMPLATE = 'org.openxmlformats.wordprocessingml.template'
```

WordProcessingML template format of OOXML.

This type belongs to **OPENXML** and **COMPOSITE_OBJECT**.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core

## PRESENTATIONML_TEMPLATE

```TypeScript
PRESENTATIONML_TEMPLATE = 'org.openxmlformats.presentationml.template'
```

PresentationML template format of OOXML.

This type belongs to **OPENXML** and **COMPOSITE_OBJECT**.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core

## PRESENTATIONML_SLIDESHOW

```TypeScript
PRESENTATIONML_SLIDESHOW = 'org.openxmlformats.presentationml.slideshow'
```

PresentationML slide show format of OOXML.

This type belongs to **OPENXML** and **COMPOSITE_OBJECT**.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core

## SPREADSHEETML_TEMPLATE

```TypeScript
SPREADSHEETML_TEMPLATE = 'org.openxmlformats.spreadsheetml.template'
```

SpreadsheetML template format of OOXML.

This type belongs to **OPENXML** and **COMPOSITE_OBJECT**.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core

## OPENDOCUMENT

```TypeScript
OPENDOCUMENT = 'org.oasis.opendocument'
```

OpenDocument format for Office applications.

This type belongs to **ARCHIVE**.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core

## OPENDOCUMENT_TEXT

```TypeScript
OPENDOCUMENT_TEXT = 'org.oasis.opendocument.text'
```

OpenDocument format for word processing (text) documents.

This type belongs to **OPENDOCUMENT** and **COMPOSITE_OBJECT**.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core

## OPENDOCUMENT_SPREADSHEET

```TypeScript
OPENDOCUMENT_SPREADSHEET = 'org.oasis.opendocument.spreadsheet'
```

OpenDocument format for spreadsheets.

This type belongs to **OPENDOCUMENT** and **COMPOSITE_OBJECT**.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core

## OPENDOCUMENT_PRESENTATION

```TypeScript
OPENDOCUMENT_PRESENTATION = 'org.oasis.opendocument.presentation'
```

OpenDocument format for presentations.

This type belongs to **OPENDOCUMENT** and **COMPOSITE_OBJECT**.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core

## OPENDOCUMENT_GRAPHICS

```TypeScript
OPENDOCUMENT_GRAPHICS = 'org.oasis.opendocument.graphics'
```

OpenDocument format for graphics.

This type belongs to **OPENDOCUMENT** and **COMPOSITE_OBJECT**.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core

## OPENDOCUMENT_FORMULA

```TypeScript
OPENDOCUMENT_FORMULA = 'org.oasis.opendocument.formula'
```

OpenDocument format for formula.

This type belongs to **OPENDOCUMENT**.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core

## STUFFIT_ARCHIVE

```TypeScript
STUFFIT_ARCHIVE = 'com.allume.stuffit-archive'
```

Stuffit compression format (stuffit archive).

This type belongs to **ARCHIVE**.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core

## RAR_ARCHIVE

```TypeScript
RAR_ARCHIVE = 'com.rarlab.rar-archive'
```

WinRAR.

This type belongs to **ARCHIVE**.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core

## SEVEN_ZIP_ARCHIVE

```TypeScript
SEVEN_ZIP_ARCHIVE = 'org.7-zip.7-zip-archive'
```

7-Zip.

This type belongs to **ARCHIVE**.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core

## CALENDAR

```TypeScript
CALENDAR = 'general.calendar'
```

Generic calendar type.

This type belongs to **OBJECT**.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core

## VCS

```TypeScript
VCS = 'general.vcs'
```

VCalendar (VCS) format.

This type belongs to **CALENDAR** and **TEXT**.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core

## ICS

```TypeScript
ICS = 'general.ics'
```

Internet Calendaring and Scheduling (ICS) format.

This type belongs to **CALENDAR** and **TEXT**.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core

## CONTACT

```TypeScript
CONTACT = 'general.contact'
```

Generic contact type.

This type belongs to **OBJECT**.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core

## DATABASE

```TypeScript
DATABASE = 'general.database'
```

Generic database file type.

This type belongs to **OBJECT**.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core

## MESSAGE

```TypeScript
MESSAGE = 'general.message'
```

Generic message type.

This type belongs to **OBJECT**.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core

## EXECUTABLE

```TypeScript
EXECUTABLE = 'general.executable'
```

Generic type of all executable files.

This type belongs to **OBJECT**.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core

## PORTABLE_EXECUTABLE

```TypeScript
PORTABLE_EXECUTABLE = 'com.microsoft.portable-executable'
```

Microsoft Windows portable executable format.

This type belongs to **EXECUTABLE**.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core

## SUN_JAVA_CLASS

```TypeScript
SUN_JAVA_CLASS = 'com.sun.java-class'
```

Java class file format.

This type belongs to **EXECUTABLE**.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core

## VCARD

```TypeScript
VCARD = 'general.vcard'
```

Generic electronic business card type.

This type belongs to **OBJECT**.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core

## NAVIGATION

```TypeScript
NAVIGATION = 'general.navigation'
```

Generic navigation data type.

This type belongs to **OBJECT**.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core

## LOCATION

```TypeScript
LOCATION = 'general.location'
```

Location data.

This type belongs to **NAVIGATION**.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core

## FONT

```TypeScript
FONT = 'general.font'
```

Basic type of fonts.

This type belongs to **OBJECT**.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core

## TRUETYPE_FONT

```TypeScript
TRUETYPE_FONT = 'general.truetype-font'
```

TrueType font format.

This type belongs to **FONT**.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core

## TRUETYPE_COLLECTION_FONT

```TypeScript
TRUETYPE_COLLECTION_FONT = 'general.truetype-collection-font'
```

TrueType Collection font format.

This type belongs to **FONT**.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core

## OPENTYPE_FONT

```TypeScript
OPENTYPE_FONT = 'general.opentype-font'
```

OpenType font format.

This type belongs to **FONT**.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core

## POSTSCRIPT_FONT

```TypeScript
POSTSCRIPT_FONT = 'com.adobe.postscript-font'
```

PostScript font format.

This type belongs to **FONT**.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core

## POSTSCRIPT_PFB_FONT

```TypeScript
POSTSCRIPT_PFB_FONT = 'com.adobe.postscript-pfb-font'
```

PostScript Font Binary font format.

This type belongs to **FONT**.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core

## POSTSCRIPT_PFA_FONT

```TypeScript
POSTSCRIPT_PFA_FONT = 'com.adobe.postscript-pfa-font'
```

Adobe Type 1 font format.

This type belongs to **FONT**.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core

## OPENHARMONY_FORM

```TypeScript
OPENHARMONY_FORM = 'openharmony.form'
```

Widget defined for the system.

This type belongs to **OBJECT**.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core

## OPENHARMONY_APP_ITEM

```TypeScript
OPENHARMONY_APP_ITEM = 'openharmony.app-item'
```

Home screen icon defined for the system.

This type belongs to **OBJECT**.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core

## OPENHARMONY_PIXEL_MAP

```TypeScript
OPENHARMONY_PIXEL_MAP = 'openharmony.pixel-map'
```

Pixel map defined for the system.

This type belongs to **IMAGE**.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core

## OPENHARMONY_ATOMIC_SERVICE

```TypeScript
OPENHARMONY_ATOMIC_SERVICE = 'openharmony.atomic-service'
```

Atomic service type defined for the system.

This type belongs to **OBJECT**.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core

## OPENHARMONY_PACKAGE

```TypeScript
OPENHARMONY_PACKAGE = 'openharmony.package'
```

Package (compressed folder) defined for the system.

This type belongs to **DIRECTORY**.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core

## OPENHARMONY_HAP

```TypeScript
OPENHARMONY_HAP = 'openharmony.hap'
```

Ability package defined for the system.

This type belongs to **OPENHARMONY_PACKAGE**.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core

## OPENHARMONY_HDOC

```TypeScript
OPENHARMONY_HDOC = 'openharmony.hdoc'
```

Memo format defined for the system.

This type belongs to **COMPOSITE_OBJECT**.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core

## OPENHARMONY_HINOTE

```TypeScript
OPENHARMONY_HINOTE = 'openharmony.hinote'
```

Note format defined for the system.

This type belongs to **COMPOSITE_OBJECT**.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core

## OPENHARMONY_STYLED_STRING

```TypeScript
OPENHARMONY_STYLED_STRING = 'openharmony.styled-string'
```

Style string type defined for the system.

This type belongs to **COMPOSITE_OBJECT**.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core

## OPENHARMONY_WANT

```TypeScript
OPENHARMONY_WANT = 'openharmony.want'
```

Want defined for the system.

This type belongs to **OBJECT**.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core

## OFD

```TypeScript
OFD = 'general.ofd'
```

Open Fixed-layout Document (OFD).

This type belongs to **COMPOSITE_OBJECT**.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core

## CAD

```TypeScript
CAD = 'general.cad'
```

Generic type of all computer-aided design types.

This type belongs to **OBJECT**.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core

## OCTET_STREAM

```TypeScript
OCTET_STREAM = 'general.octet-stream'
```

Any binary data type.

This type belongs to **OBJECT**.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core

## FILE_URI

```TypeScript
FILE_URI = 'general.file-uri'
```

File address type.

This type belongs to **TEXT**.

**Since:** 15

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core

## CONTENT_FORM

```TypeScript
CONTENT_FORM = 'general.content-form'
```

Content widget type.

This type belongs to **OBJECT**.

**Since:** 15

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core
