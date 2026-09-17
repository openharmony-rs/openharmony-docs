# udmf_meta.h

## Overview

Declaration the uniform data type information.

**Library**: libudmf.so

**System capability**: SystemCapability.DistributedDataManager.UDMF.Core

**Since**: 12

**Related module**: [UDMF](capi-udmf.md)

## Summary

### Macro

| Name | Description |
| -- | -- |
| UDMF_META_ENTITY "general.entity" | A specific type of uniform data type.<br>**Since**: 12 |
| UDMF_META_OBJECT "general.object" | A specific type of uniform data type.<br>**Since**: 12 |
| UDMF_META_COMPOSITE_OBJECT "general.composite-object" | A specific type of uniform data type.<br>**Since**: 12 |
| UDMF_META_TEXT "general.text" | A specific type of uniform data type.<br>**Since**: 12 |
| UDMF_META_PLAIN_TEXT "general.plain-text" | A specific type of uniform data type.<br>**Since**: 12 |
| UDMF_META_HTML "general.html" | A specific type of uniform data type.<br>**Since**: 12 |
| UDMF_META_HYPERLINK "general.hyperlink" | A specific type of uniform data type.<br>**Since**: 12 |
| UDMF_META_XML "general.xml" | A specific type of uniform data type.<br>**Since**: 12 |
| UDMF_META_SOURCE_CODE "general.source-code" | A specific type of uniform data type.<br>**Since**: 12 |
| UDMF_META_SCRIPT "general.script" | A specific type of uniform data type.<br>**Since**: 12 |
| UDMF_META_SHELL_SCRIPT "general.shell-script" | A specific type of uniform data type.<br>**Since**: 12 |
| UDMF_META_CSH_SCRIPT "general.csh-script" | A specific type of uniform data type.<br>**Since**: 12 |
| UDMF_META_PERL_SCRIPT "general.perl-script" | A specific type of uniform data type.<br>**Since**: 12 |
| UDMF_META_PHP_SCRIPT "general.php-script" | A specific type of uniform data type.<br>**Since**: 12 |
| UDMF_META_PYTHON_SCRIPT "general.python-script" | A specific type of uniform data type.<br>**Since**: 12 |
| UDMF_META_RUBY_SCRIPT "general.ruby-script" | A specific type of uniform data type.<br>**Since**: 12 |
| UDMF_META_TYPE_SCRIPT "general.type-script" | A specific type of uniform data type.<br>**Since**: 12 |
| UDMF_META_JAVA_SCRIPT "general.java-script" | A specific type of uniform data type.<br>**Since**: 12 |
| UDMF_META_C_HEADER "general.c-header" | A specific type of uniform data type.<br>**Since**: 12 |
| UDMF_META_C_SOURCE "general.c-source" | A specific type of uniform data type.<br>**Since**: 12 |
| UDMF_META_C_PLUS_PLUS_HEADER "general.c-plus-plus-header" | A specific type of uniform data type.<br>**Since**: 12 |
| UDMF_META_C_PLUS_PLUS_SOURCE "general.c-plus-plus-source" | A specific type of uniform data type.<br>**Since**: 12 |
| UDMF_META_JAVA_SOURCE "general.java-source" | A specific type of uniform data type.<br>**Since**: 12 |
| UDMF_META_EBOOK "general.ebook" | A specific type of uniform data type.<br>**Since**: 12 |
| UDMF_META_EPUB "general.epub" | A specific type of uniform data type.<br>**Since**: 12 |
| UDMF_META_AZW "com.amazon.azw" | A specific type of uniform data type.<br>**Since**: 12 |
| UDMF_META_AZW3 "com.amazon.azw3" | A specific type of uniform data type.<br>**Since**: 12 |
| UDMF_META_KFX "com.amazon.kfx" | A specific type of uniform data type.<br>**Since**: 12 |
| UDMF_META_MOBI "com.amazon.mobi" | A specific type of uniform data type.<br>**Since**: 12 |
| UDMF_META_MEDIA "general.media" | A specific type of uniform data type.<br>**Since**: 12 |
| UDMF_META_IMAGE "general.image" | A specific type of uniform data type.<br>**Since**: 12 |
| UDMF_META_JPEG "general.jpeg" | A specific type of uniform data type.<br>**Since**: 12 |
| UDMF_META_PNG "general.png" | A specific type of uniform data type.<br>**Since**: 12 |
| UDMF_META_RAW_IMAGE "general.raw-image" | A specific type of uniform data type.<br>**Since**: 12 |
| UDMF_META_TIFF "general.tiff" | A specific type of uniform data type.<br>**Since**: 12 |
| UDMF_META_BMP "com.microsoft.bmp" | A specific type of uniform data type.<br>**Since**: 12 |
| UDMF_META_ICO "com.microsoft.ico" | A specific type of uniform data type.<br>**Since**: 12 |
| UDMF_META_PHOTOSHOP_IMAGE "com.adobe.photoshop-image" | A specific type of uniform data type.<br>**Since**: 12 |
| UDMF_META_AI_IMAGE "com.adobe.illustrator.ai-image" | A specific type of uniform data type.<br>**Since**: 12 |
| UDMF_META_WORD_DOC "com.microsoft.word.doc" | A specific type of uniform data type.<br>**Since**: 12 |
| UDMF_META_EXCEL "com.microsoft.excel.xls" | A specific type of uniform data type.<br>**Since**: 12 |
| UDMF_META_PPT "com.microsoft.powerpoint.ppt" | A specific type of uniform data type.<br>**Since**: 12 |
| UDMF_META_PDF "com.adobe.pdf" | A specific type of uniform data type.<br>**Since**: 12 |
| UDMF_META_POSTSCRIPT "com.adobe.postscript" | A specific type of uniform data type.<br>**Since**: 12 |
| UDMF_META_ENCAPSULATED_POSTSCRIPT "com.adobe.encapsulated-postscript" | A specific type of uniform data type.<br>**Since**: 12 |
| UDMF_META_VIDEO "general.video" | A specific type of uniform data type.<br>**Since**: 12 |
| UDMF_META_AVI "general.avi" | A specific type of uniform data type.<br>**Since**: 12 |
| UDMF_META_MPEG "general.mpeg" | A specific type of uniform data type.<br>**Since**: 12 |
| UDMF_META_MPEG4 "general.mpeg-4" | A specific type of uniform data type.<br>**Since**: 12 |
| UDMF_META_VIDEO_3GPP "general.3gpp" | A specific type of uniform data type.<br>**Since**: 12 |
| UDMF_META_VIDEO_3GPP2 "general.3gpp2" | A specific type of uniform data type.<br>**Since**: 12 |
| UDMF_META_WINDOWS_MEDIA_WM "com.microsoft.windows-media-wm" | A specific type of uniform data type.<br>**Since**: 12 |
| UDMF_META_WINDOWS_MEDIA_WMV "com.microsoft.windows-media-wmv" | A specific type of uniform data type.<br>**Since**: 12 |
| UDMF_META_WINDOWS_MEDIA_WMP "com.microsoft.windows-media-wmp" | A specific type of uniform data type.<br>**Since**: 12 |
| UDMF_META_AUDIO "general.audio" | A specific type of uniform data type.<br>**Since**: 12 |
| UDMF_META_AAC "general.aac" | A specific type of uniform data type.<br>**Since**: 12 |
| UDMF_META_AIFF "general.aiff" | A specific type of uniform data type.<br>**Since**: 12 |
| UDMF_META_ALAC "general.alac" | A specific type of uniform data type.<br>**Since**: 12 |
| UDMF_META_FLAC "general.flac" | A specific type of uniform data type.<br>**Since**: 12 |
| UDMF_META_MP3 "general.mp3" | A specific type of uniform data type.<br>**Since**: 12 |
| UDMF_META_OGG "general.ogg" | A specific type of uniform data type.<br>**Since**: 12 |
| UDMF_META_PCM "general.pcm" | A specific type of uniform data type.<br>**Since**: 12 |
| UDMF_META_WINDOWS_MEDIA_WMA "com.microsoft.windows-media-wma" | A specific type of uniform data type.<br>**Since**: 12 |
| UDMF_META_WAVEFORM_AUDIO "com.microsoft.waveform-audio" | A specific type of uniform data type.<br>**Since**: 12 |
| UDMF_META_WINDOWS_MEDIA_WMX "com.microsoft.windows-media-wmx" | A specific type of uniform data type.<br>**Since**: 12 |
| UDMF_META_WINDOWS_MEDIA_WVX "com.microsoft.windows-media-wvx" | A specific type of uniform data type.<br>**Since**: 12 |
| UDMF_META_WINDOWS_MEDIA_WAX "com.microsoft.windows-media-wax" | A specific type of uniform data type.<br>**Since**: 12 |
| UDMF_META_GENERAL_FILE "general.file" | A specific type of uniform data type.<br>**Since**: 12 |
| UDMF_META_DIRECTORY "general.directory" | A specific type of uniform data type.<br>**Since**: 12 |
| UDMF_META_FOLDER "general.folder" | A specific type of uniform data type.<br>**Since**: 12 |
| UDMF_META_SYMLINK "general.symlink" | A specific type of uniform data type.<br>**Since**: 12 |
| UDMF_META_ARCHIVE "general.archive" | A specific type of uniform data type.<br>**Since**: 12 |
| UDMF_META_BZ2_ARCHIVE "general.bz2-archive" | A specific type of uniform data type.<br>**Since**: 12 |
| UDMF_META_DISK_IMAGE "general.disk-image" | A specific type of uniform data type.<br>**Since**: 12 |
| UDMF_META_TAR_ARCHIVE "general.tar-archive" | A specific type of uniform data type.<br>**Since**: 12 |
| UDMF_META_ZIP_ARCHIVE "general.zip-archive" | A specific type of uniform data type.<br>**Since**: 12 |
| UDMF_META_JAVA_ARCHIVE "com.sun.java-archive" | A specific type of uniform data type.<br>**Since**: 12 |
| UDMF_META_GNU_TAR_ARCHIVE "org.gnu.gnu-tar-archive" | A specific type of uniform data type.<br>**Since**: 12 |
| UDMF_META_GNU_ZIP_ARCHIVE "org.gnu.gnu-zip-archive" | A specific type of uniform data type.<br>**Since**: 12 |
| UDMF_META_GNU_ZIP_TAR_ARCHIVE "org.gnu.gnu-zip-tar-archive" | A specific type of uniform data type.<br>**Since**: 12 |
| UDMF_META_CALENDAR "general.calendar" | A specific type of uniform data type.<br>**Since**: 12 |
| UDMF_META_CONTACT "general.contact" | A specific type of uniform data type.<br>**Since**: 12 |
| UDMF_META_DATABASE "general.database" | A specific type of uniform data type.<br>**Since**: 12 |
| UDMF_META_MESSAGE "general.message" | A specific type of uniform data type.<br>**Since**: 12 |
| UDMF_META_VCARD "general.vcard" | A specific type of uniform data type.<br>**Since**: 12 |
| UDMF_META_NAVIGATION "general.navigation" | A specific type of uniform data type.<br>**Since**: 12 |
| UDMF_META_LOCATION "general.location" | A specific type of uniform data type.<br>**Since**: 12 |
| UDMF_META_OPENHARMONY_FORM "openharmony.form" | A specific type of uniform data type.<br>**Since**: 12 |
| UDMF_META_OPENHARMONY_APP_ITEM "openharmony.app-item" | A specific type of uniform data type.<br>**Since**: 12 |
| UDMF_META_OPENHARMONY_PIXEL_MAP "openharmony.pixel-map" | A specific type of uniform data type.<br>**Since**: 12 |
| UDMF_META_OPENHARMONY_ATOMIC_SERVICE "openharmony.atomic-service" | A specific type of uniform data type.<br>**Since**: 12 |
| UDMF_META_OPENHARMONY_PACKAGE "openharmony.package" | A specific type of uniform data type.<br>**Since**: 12 |
| UDMF_META_OPENHARMONY_HAP "openharmony.hap" | A specific type of uniform data type.<br>**Since**: 12 |
| UDMF_META_SMIL "com.real.smil" | A specific type of uniform data type.<br>**Since**: 12 |
| UDMF_META_MARKDOWN "general.markdown" | A specific type of uniform data type.<br>**Since**: 12 |
| UDMF_META_FAX "general.fax" | A specific type of uniform data type.<br>**Since**: 12 |
| UDMF_META_JFX_FAX "com.j2.jfx-fax" | A specific type of uniform data type.<br>**Since**: 12 |
| UDMF_META_EFX_FAX "com.js.efx-fax" | A specific type of uniform data type.<br>**Since**: 12 |
| UDMF_META_XBITMAP_IMAGE "general.xbitmap-image" | A specific type of uniform data type.<br>**Since**: 12 |
| UDMF_META_TGA_IMAGE "com.truevision.tga-image" | A specific type of uniform data type.<br>**Since**: 12 |
| UDMF_META_SGI_IMAGE "com.sgi.sgi-image" | A specific type of uniform data type.<br>**Since**: 12 |
| UDMF_META_OPENEXR_IMAGE "com.ilm.openexr-image" | A specific type of uniform data type.<br>**Since**: 12 |
| UDMF_META_FLASHPIX_IMAGE "com.kodak.flashpix.image" | A specific type of uniform data type.<br>**Since**: 12 |
| UDMF_META_REALMEDIA "com.real.realmedia" | A specific type of uniform data type.<br>**Since**: 12 |
| UDMF_META_AU_AUDIO "general.au-audio" | A specific type of uniform data type.<br>**Since**: 12 |
| UDMF_META_AIFC_AUDIO "general.aifc-audio" | A specific type of uniform data type.<br>**Since**: 12 |
| UDMF_META_SD2_AUDIO "com.digidesign.sd2-audio" | A specific type of uniform data type.<br>**Since**: 12 |
| UDMF_META_REALAUDIO "com.real.realaudio" | A specific type of uniform data type.<br>**Since**: 12 |
| UDMF_META_OPENXML "org.openxmlformats.openxml" | A specific type of uniform data type.<br>**Since**: 12 |
| UDMF_META_WORDPROCESSINGML_DOCUMENT "org.openxmlformats.wordprocessingml.document" | A specific type of uniform data type.<br>**Since**: 12 |
| UDMF_META_SPREADSHEETML_SHEET "org.openxmlformats.spreadsheetml.sheet" | A specific type of uniform data type.<br>**Since**: 12 |
| UDMF_META_PRESENTATIONML_PRESENTATION "org.openxmlformats.presentationml.presentation" | A specific type of uniform data type.<br>**Since**: 12 |
| UDMF_META_OPENDOCUMENT "org.oasis.opendocument" | A specific type of uniform data type.<br>**Since**: 12 |
| UDMF_META_OPENDOCUMENT_TEXT "org.oasis.opendocument.text" | A specific type of uniform data type.<br>**Since**: 12 |
| UDMF_META_OPENDOCUMENT_SPREADSHEET "org.oasis.opendocument.spreadsheet" | A specific type of uniform data type.<br>**Since**: 12 |
| UDMF_META_OPENDOCUMENT_PRESENTATION "org.oasis.opendocument.presentation" | A specific type of uniform data type.<br>**Since**: 12 |
| UDMF_META_OPENDOCUMENT_GRAPHICS "org.oasis.opendocument.graphics" | A specific type of uniform data type.<br>**Since**: 12 |
| UDMF_META_OPENDOCUMENT_FORMULA "org.oasis.opendocument.formula" | A specific type of uniform data type.<br>**Since**: 12 |
| UDMF_META_STUFFIT_ARCHIVE "com.allume.stuffit-archive" | A specific type of uniform data type.<br>**Since**: 12 |
| UDMF_META_VCS "general.vcs" | A specific type of uniform data type.<br>**Since**: 12 |
| UDMF_META_ICS "general.ics" | A specific type of uniform data type.<br>**Since**: 12 |
| UDMF_META_EXECUTABLE "general.executable" | A specific type of uniform data type.<br>**Since**: 12 |
| UDMF_META_PORTABLE_EXECUTABLE "com.microsoft.portable-executable" | A specific type of uniform data type.<br>**Since**: 12 |
| UDMF_META_SUN_JAVA_CLASS "com.sun.java-class" | A specific type of uniform data type.<br>**Since**: 12 |
| UDMF_META_FONT "general.font" | A specific type of uniform data type.<br>**Since**: 12 |
| UDMF_META_TRUETYPE_FONT "general.truetype-font" | A specific type of uniform data type.<br>**Since**: 12 |
| UDMF_META_TRUETYPE_COLLECTION_FONT "general.truetype-collection-font" | A specific type of uniform data type.<br>**Since**: 12 |
| UDMF_META_OPENTYPE_FONT "general.opentype-font" | A specific type of uniform data type.<br>**Since**: 12 |
| UDMF_META_POSTSCRIPT_FONT "com.adobe.postscript-font" | A specific type of uniform data type.<br>**Since**: 12 |
| UDMF_META_POSTSCRIPT_PFB_FONT "com.adobe.postscript-pfb-font" | A specific type of uniform data type.<br>**Since**: 12 |
| UDMF_META_POSTSCRIPT_PFA_FONT "com.adobe.postscript-pfa-font" | A specific type of uniform data type.<br>**Since**: 12 |
| UDMF_META_OPENHARMONY_HDOC "openharmony.hdoc" | A specific type of uniform data type.<br>**Since**: 12 |
| UDMF_META_OPENHARMONY_HINOTE "openharmony.hinote" | A specific type of uniform data type.<br>**Since**: 12 |
| UDMF_META_OPENHARMONY_STYLED_STRING "openharmony.styled-string" | A specific type of uniform data type.<br>**Since**: 12 |
| UDMF_META_OPENHARMONY_WANT "openharmony.want" | A specific type of uniform data type.<br>**Since**: 12 |
| UDMF_META_GENERAL_FILE_URI "general.file-uri" | A specific type of uniform data type.<br>**Since**: 13 |
| UDMF_METE_GENERAL_CONTENT_FORM "general.content-form" | A specific type of uniform data type.<br>**Since**: 14 |

