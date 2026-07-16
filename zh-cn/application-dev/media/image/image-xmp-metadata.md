# 读取和编辑图片XMP元数据
<!--Kit: Image Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @aulight02-->
<!--Designer: @XiaoYao555-->
<!--Tester: @xchaosioda-->
<!--Adviser: @w_Machine_cc-->

XMP（Extensible Metadata Platform，可扩展元数据平台）是一种用于描述数字资源（如图片、文档、音频等）元数据的标准格式。以XML为基础，允许为资源添加丰富的描述性信息，支持自定义命名空间和扩展。XMP元数据通常内嵌在JPEG、PNG、GIF、DNG、TIFF等格式图片中。

从API版本26.0.0开始，Image Kit支持对JPEG、PNG、GIF、DNG、TIFF格式图片的XMP元数据进行读取，同时也支持对JPEG、PNG、GIF格式图片的XMP元数据进行编辑。

## 开发步骤

获取图片，创建ImageSource（可选），再获取XMPMetadata对象，使用XMP路径语法读写标签。XMP元数据的操作方法请参考[XMPMetadata](../../reference/apis-image-kit/arkts-apis-image-XMPMetadata.md)。

1. 导入相关模块。

   <!-- @[xmp_import](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Image/ImageArkTSSample/entry/src/main/ets/tools/XMPUtility.ets) -->
   
   ``` TypeScript
   // 导入相关模块。
   import { image } from '@kit.ImageKit';
   import { BusinessError } from '@kit.BasicServicesKit';
   ```

2. 获取XMPMetadata对象。

   在使用XMP元数据相关接口前，需要先获取一个[XMPMetadata](../../reference/apis-image-kit/arkts-apis-image-XMPMetadata.md)实例。当前支持以下方式：

   - 方式一：手动创建新的XMPMetadata对象。适用于需要构造全新XMP元数据的场景。

     <!-- @[create_xmp_metadata](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Image/ImageArkTSSample/entry/src/main/ets/tools/XMPUtility.ets) -->
     
     ``` TypeScript
     async createXMPMetadata(): Promise<image.XMPMetadata> {
       let xmpMetadata = new image.XMPMetadata();
       console.info('Succeeded in creating XMPMetadata.');
       return xmpMetadata;
     }
     ```

   - 方式二：通过ImageSource读取图片中的XMP元数据。适用于需要读取或修改已有图片中XMP元数据的场景。<br>推荐使用[readImageMetadataByType](../../reference/apis-image-kit/arkts-apis-image-ImageSource.md#readimagemetadatabytype24)接口获取XMP元数据，可以直接传入`MetadataType.XMP_METADATA`，精准获取XMP类型的元数据，避免读取其他无关元数据。

     <!-- @[read_xmp_metadata_from_image](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Image/ImageArkTSSample/entry/src/main/ets/tools/XMPUtility.ets) -->
     
     ``` TypeScript
     async readXMPMetadataFromImage(imageSource: image.ImageSource): Promise<image.XMPMetadata | undefined> {
       let types: image.MetadataType[] = [image.MetadataType.XMP_METADATA];
       try {
         let metaData: image.ImageMetadata = await imageSource.readImageMetadataByType(types);
         if (metaData != undefined && metaData.xmpMetadata != undefined) {
           // 成功获取XMPMetadata对象。
           let xmpMetadata = metaData.xmpMetadata;
           console.info('Succeeded in reading XMP metadata from image.');
           return xmpMetadata;
         }
         console.info('Failed to read XMP metadata from image.');
         return undefined;
       } catch (error) {
         console.error(`Failed to read XMP metadata. code is ${(error as BusinessError).code}, message is ${(error as BusinessError).message}`);
         return undefined;
       }
     }
     ```

3. 编辑XMP元数据。

   使用XMP路径定位到目标标签后，调用对应的方法进行编辑。例如：通过[setValue](../../reference/apis-image-kit/arkts-apis-image-XMPMetadata.md#setvalue)设置标签值，通过[getTag](../../reference/apis-image-kit/arkts-apis-image-XMPMetadata.md#gettag)获取标签值，通过[removeTag](../../reference/apis-image-kit/arkts-apis-image-XMPMetadata.md#removetag)删除标签。

   <!-- @[operate_xmp_metadata](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Image/ImageArkTSSample/entry/src/main/ets/tools/XMPUtility.ets) -->
   
   ``` TypeScript
   async operateXMPMetadata(xmpMetadata: image.XMPMetadata): Promise<void> {
     try {
       // 设置xmp:title标签的值。
       await xmpMetadata.setValue(`${image.XMP_BASIC.prefix}:title`, image.XMPTagType.STRING, 'My Title');
   
       // 获取xmp:title路径的标签。
       let tag: image.XMPTag | null = await xmpMetadata.getTag(`${image.XMP_BASIC.prefix}:title`);
       console.info(`${image.XMP_BASIC.prefix}:title: ${tag?.value}`);
   
       // 删除xmp:title标签。
       await xmpMetadata.removeTag(`${image.XMP_BASIC.prefix}:title`);
     } catch (error) {
       console.error(`Failed to operate XMP tags. code is ${(error as BusinessError).code}, message is ${(error as BusinessError).message}`);
     }
   }
   ```

4. 将编辑后的XMP元数据写回图片。

   编辑后的XMPMetadata对象可通过[writeImageMetadata](../../reference/apis-image-kit/arkts-apis-image-ImageSource.md#writeimagemetadata23)写回图片文件。

   > **注意：**
   >
   > DNG和TIFF格式的图片不支持将XMP元数据写回图片文件。

   <!-- @[write_xmp_metadata_to_image](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Image/ImageArkTSSample/entry/src/main/ets/tools/XMPUtility.ets) -->
   
   ``` TypeScript
   async writeXMPMetadataToImage(imageSource: image.ImageSource, xmpMetadata: image.XMPMetadata): Promise<void> {
     try {
       // 将修改后的ImageMetadata（包含XMPMetadata）写回图片。
       let metaData: image.ImageMetadata = { xmpMetadata: xmpMetadata } as image.ImageMetadata;
       await imageSource.writeImageMetadata(metaData);
       console.info('Succeeded in writing XMP metadata to image.');
     } catch (error) {
       console.error(`Failed to write XMP metadata. code is ${(error as BusinessError).code}, message is ${(error as BusinessError).message}`);
     }
   }
   ```

## XMP路径语法详解

XMP路径由以下语法构件组合而成。在使用[getTag](../../reference/apis-image-kit/arkts-apis-image-XMPMetadata.md#gettag)、[setValue](../../reference/apis-image-kit/arkts-apis-image-XMPMetadata.md#setvalue)、[removeTag](../../reference/apis-image-kit/arkts-apis-image-XMPMetadata.md#removetag)等接口时，均需通过XMP路径指定目标标签。

### 基本属性路径

使用`":"`将命名空间前缀和标签名分隔开，用于定位指定命名空间下的某个具体标签。

> **说明：**
>
> - 使用标准命名空间（如`xmp`、`dc`、`exif`等）时，无需额外注册。Image Kit支持但不限于[常量](../../reference/apis-image-kit/arkts-apis-image-c.md#常量)中定义的标准命名空间。
> - 使用自定义命名空间时，需要先通过[registerXMPNamespace](../../reference/apis-image-kit/arkts-apis-image-XMPMetadata.md#registerxmpnamespace)完成注册。

**示例：**

<!-- @[set_and_get_basic_tag](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Image/ImageArkTSSample/entry/src/main/ets/tools/XMPUtility.ets) -->

``` TypeScript
async setAndGetBasicTag(xmpMetadata: image.XMPMetadata): Promise<void> {
  try {
    // 设置xmp:title标签的值，类型为字符串，值为'My Title'。
    await xmpMetadata.setValue(`${image.XMP_BASIC.prefix}:title`, image.XMPTagType.STRING, 'My Title');

    // 获取xmp:title路径的标签。
    let tag: image.XMPTag | null = await xmpMetadata.getTag(`${image.XMP_BASIC.prefix}:title`);
    console.info(`${image.XMP_BASIC.prefix}:title: ${tag?.value}`);
  } catch (error) {
    console.error(`Failed to set or get basic tag. code is ${(error as BusinessError).code}, message is ${(error as BusinessError).message}`);
  }
}
```

### 数组索引

使用`"[]"`配合索引值定位数组中的元素，索引从1开始计数（1代表第一个元素），或使用`"last()"`访问最后一个元素。

> **注意：**
>
> 在使用数组索引添加数组元素前，必须先确保已创建数组容器节点。使用`setValue`为数组路径设置`UNORDERED_ARRAY`、`ORDERED_ARRAY`、`ALTERNATE_ARRAY`或`ALTERNATE_TEXT`类型，即可创建数组容器。

**示例1：创建数组容器并添加元素**

以下示例假设已注册自定义命名空间`book`。如果尚未注册，请先调用[registerXMPNamespace](../../reference/apis-image-kit/arkts-apis-image-XMPMetadata.md#registerxmpnamespace)完成注册。

<!-- @[create_array_and_add_elements](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Image/ImageArkTSSample/entry/src/main/ets/tools/XMPUtility.ets) -->

``` TypeScript
async createArrayAndAddElements(xmpMetadata: image.XMPMetadata): Promise<void> {
  try {
    // 创建无序数组容器。
    await xmpMetadata.setValue('book:fruits', image.XMPTagType.UNORDERED_ARRAY, undefined);

    // 向数组中添加多个元素，数组索引起始值为1。
    let fruits: string[] = ['apple', 'banana'];
    for (let i = 0; i < fruits.length; i++) {
      await xmpMetadata.setValue(`book:fruits[${i + 1}]`, image.XMPTagType.STRING, fruits[i]);
    }
    console.info('Succeeded in creating array and adding elements.');
  } catch (error) {
    console.error(`Failed to create array or add elements. code is ${(error as BusinessError).code}, message is ${(error as BusinessError).message}`);
  }
}
```

**示例2：通过索引获取数组元素**

以下示例假设已注册自定义命名空间`book`。如果尚未注册，请先调用[registerXMPNamespace](../../reference/apis-image-kit/arkts-apis-image-XMPMetadata.md#registerxmpnamespace)完成注册。

<!-- @[get_array_elements](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Image/ImageArkTSSample/entry/src/main/ets/tools/XMPUtility.ets) -->

``` TypeScript
async getArrayElements(xmpMetadata: image.XMPMetadata): Promise<void> {
  try {
    // 获取第二个元素。
    let tag2: image.XMPTag | null = await xmpMetadata.getTag('book:fruits[2]');
    console.info(`book:fruits[2]: ${tag2?.value}`);

    // 获取最后一个元素。
    let lastTag: image.XMPTag | null = await xmpMetadata.getTag('book:fruits[last()]');
    console.info(`book:fruits[last()]: ${lastTag?.value}`);
  } catch (error) {
    console.error(`Failed to get array elements. code is ${(error as BusinessError).code}, message is ${(error as BusinessError).message}`);
  }
}
```

### 结构体成员

使用`"/"`指定结构体成员。当某个标签的类型是`STRUCTURE`时，可通过该语法访问其内部的子成员。

> **注意：**
>
> 在使用结构体成员路径添加子成员前，必须先创建结构体父节点。使用`setValue`为结构体路径设置`STRUCTURE`类型，即可创建结构体容器。

**示例：创建结构体父节点并操作成员**

以下示例假设已注册自定义命名空间`book`。如果尚未注册，请先调用[registerXMPNamespace](../../reference/apis-image-kit/arkts-apis-image-XMPMetadata.md#registerxmpnamespace)完成注册。

<!-- @[create_struct_and_operate_members](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Image/ImageArkTSSample/entry/src/main/ets/tools/XMPUtility.ets) -->

``` TypeScript
async createStructAndOperateMembers(xmpMetadata: image.XMPMetadata): Promise<void> {
  try {
    // 创建结构体父节点。
    await xmpMetadata.setValue('book:parentNode', image.XMPTagType.STRUCTURE, undefined);

    // 添加结构体成员。
    let members: Record<string, string> = {
      'child1': 'child1 value',
      'child2': 'child2 value'
    };
    for (const entry of Object.entries(members)) {
      await xmpMetadata.setValue(`book:parentNode/book:${entry[0]}`, image.XMPTagType.STRING, entry[1]);
    }

    // 获取结构体成员的值。
    let childTag: image.XMPTag | null = await xmpMetadata.getTag('book:parentNode/book:child1');
    console.info(`book:parentNode/book:child1: ${childTag?.value}`);
  } catch (error) {
    console.error(`Failed to operate structure members. code is ${(error as BusinessError).code}, message is ${(error as BusinessError).message}`);
  }
}
```

### 限定符访问

使用`"/?"`指定限定符。限定符用于对主标签提供额外的修饰信息，也常用于访问多语言文本数组中元素的语言属性。

> **注意：**
>
> 在使用限定符路径添加限定符前，必须先创建主标签。使用`setValue`为主标签路径设置适当类型，即可创建主标签。

**示例1：设置并获取限定符的值**

以下示例假设已注册自定义命名空间`book`。如果尚未注册，请先调用[registerXMPNamespace](../../reference/apis-image-kit/arkts-apis-image-XMPMetadata.md#registerxmpnamespace)完成注册。

<!-- @[set_and_get_qualifier](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Image/ImageArkTSSample/entry/src/main/ets/tools/XMPUtility.ets) -->

``` TypeScript
async setAndGetQualifierValue(xmpMetadata: image.XMPMetadata): Promise<void> {
  try {
    // 设置主标签 book:bookTitle
    await xmpMetadata.setValue('book:bookTitle', image.XMPTagType.STRING, 'My Book Title');
    // 为主标签添加限定符 book:lastUpdated
    await xmpMetadata.setValue('book:bookTitle/?book:lastUpdated', image.XMPTagType.STRING, '2024-01-15');
    console.info('Succeeded in setting tag and qualifier.');

    // 获取限定符的值
    let qualifierTag: image.XMPTag | null = await xmpMetadata.getTag('book:bookTitle/?book:lastUpdated');
    console.info(`book:bookTitle/?book:lastUpdated: ${qualifierTag?.value}`);
  } catch (error) {
    console.error(`Failed to operate qualifier. code is ${(error as BusinessError).code}, message is ${(error as BusinessError).message}`);
  }
}
```

**示例2：为多语言文本设置语言限定符**

多语言文本（语言替代数组）本质上也是一种数组，类型为`ALTERNATE_TEXT`。在添加元素前，必须先创建数组容器；且每个元素**必须**通过`"xml:lang"`限定符指定语言，否则在序列化时会失败，导致无法写回文件。

<!-- @[set_language_qualifier](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Image/ImageArkTSSample/entry/src/main/ets/tools/XMPUtility.ets) -->

``` TypeScript
async setLanguageQualifier(xmpMetadata: image.XMPMetadata): Promise<void> {
  try {
    // 创建语言替代数组容器。
    await xmpMetadata.setValue(`${image.DUBLIN_CORE.prefix}:title`, image.XMPTagType.ALTERNATE_TEXT, undefined);

    // 添加第一个多语言文本元素，并设置其语言限定符。
    await xmpMetadata.setValue(`${image.DUBLIN_CORE.prefix}:title[1]`, image.XMPTagType.STRING, 'Hello');
    await xmpMetadata.setValue(`${image.DUBLIN_CORE.prefix}:title[1]/?xml:lang`, image.XMPTagType.STRING, 'en-US');

    // 添加第二个多语言文本元素及语言限定符。
    await xmpMetadata.setValue(`${image.DUBLIN_CORE.prefix}:title[2]`, image.XMPTagType.STRING, '你好');
    await xmpMetadata.setValue(`${image.DUBLIN_CORE.prefix}:title[2]/?xml:lang`, image.XMPTagType.STRING, 'zh-CN');

    // 获取第一个元素的语言限定符。
    let langTag: image.XMPTag | null = await xmpMetadata.getTag(`${image.DUBLIN_CORE.prefix}:title[1]/?xml:lang`);
    console.info(`dc:title[1]/?xml:lang: ${langTag?.value}`);
  } catch (error) {
    console.error(`Failed to set language qualifier. code is ${(error as BusinessError).code}, message is ${(error as BusinessError).message}`);
  }
}
```

### 命名空间前缀（仅rootPath支持）

仅指定命名空间前缀，遍历该命名空间下所有标签。

> **注意：**
>
> 该语法仅适用于[enumerateTags](../../reference/apis-image-kit/arkts-apis-image-XMPMetadata.md#enumeratetags)和[getTags](../../reference/apis-image-kit/arkts-apis-image-XMPMetadata.md#gettags)接口的`rootPath`参数。

**示例：**

<!-- @[enumerate_namespace_tags](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Image/ImageArkTSSample/entry/src/main/ets/tools/XMPUtility.ets) -->

``` TypeScript
async enumerateNamespaceTags(xmpMetadata: image.XMPMetadata): Promise<void> {
  try {
    // 遍历Dublin Core命名空间下的全部字段。
    xmpMetadata.enumerateTags((path: string, tag: image.XMPTag): boolean => {
      console.info(`path: ${path}, name: ${tag.name}, value: ${tag.value}`);
      return true;  // 返回true继续遍历。
    }, `${image.DUBLIN_CORE.prefix}`, { isRecursive: true, onlyQualifier: false });
    console.info('Succeeded in enumerating namespace tags.');
  } catch (error) {
    console.error(`Failed to enumerate namespace tags. code is ${(error as BusinessError).code}, message is ${(error as BusinessError).message}`);
  }
}
```
