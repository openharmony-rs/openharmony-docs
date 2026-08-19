# Tokenizer

描述fts（全文搜索）场景下使用的分词器枚举。请使用枚举名称而非枚举值。 在使用不同的分词器时，使用的建表语句会有所区别。 示例代码中this.context定义见Stage模型的应用Context。 使用ICU_TOKENIZER分词器时，创建表的示例： 使用CUSTOM_TOKENIZER分词器时，创建表的示例： 使用CUSTOM_TOKENIZER分词器，并指定分词模式时，创建表的示例：

**起始版本：** 23

<!--Device-relationalStore-enum Tokenizer--><!--Device-relationalStore-enum Tokenizer-End-->

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

## NONE_TOKENIZER

```TypeScript
NONE_TOKENIZER = 0
```

不使用分词器。

**起始版本：** 23

<!--Device-Tokenizer-NONE_TOKENIZER = 0--><!--Device-Tokenizer-NONE_TOKENIZER = 0-End-->

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

## ICU_TOKENIZER

```TypeScript
ICU_TOKENIZER = 1
```

表示使用icu分词器，支持中文以及多国语言。指定icu分词器时，可指定使用哪种语言，例如zh_CN表示中文，tr_TR表示土耳其语等。支持的语言种类，请查阅 [ICU分词器](https://gitcode.com/openharmony/third_party_icu/blob/master/icu4c/source/data/lang/zh.txt)。语言缩写请查阅该目录（ [ICU支持的语言缩写](https://gitcode.com/openharmony/third_party_icu/tree/master/icu4c/source/data/locales)）下的文件名。

**起始版本：** 23

<!--Device-Tokenizer-ICU_TOKENIZER = 1--><!--Device-Tokenizer-ICU_TOKENIZER = 1-End-->

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

## CUSTOM_TOKENIZER

```TypeScript
CUSTOM_TOKENIZER = 2
```

表示使用自研分词器，可支持中文（简体、繁体）、英文、阿拉伯数字。CUSTOM_TOKENIZER相比ICU_TOKENIZER在分词准确率、常驻内存占用上更有优势。自研分词器支持默认分词模式和短词分词模式（ short_words）两种，使用参数cut_mode可指定模式，不指定模式时使用默认模式。

**起始版本：** 23

<!--Device-Tokenizer-CUSTOM_TOKENIZER = 2--><!--Device-Tokenizer-CUSTOM_TOKENIZER = 2-End-->

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

