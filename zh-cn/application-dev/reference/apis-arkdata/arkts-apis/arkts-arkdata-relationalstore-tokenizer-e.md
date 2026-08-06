# Tokenizer

描述fts（全文搜索）场景下使用的分词器枚举。请使用枚举名称而非枚举值。 在使用不同的分词器时，使用的建表语句会有所区别。 示例代码中this.context定义见Stage模型的应用[Context]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_。 使用ICU\_TOKENIZER分词器时，创建表的示例： 使用CUSTOM\_TOKENIZER分词器时，创建表的示例： 使用CUSTOM\_TOKENIZER分词器，并指定分词模式时，创建表的示例：

**起始版本：** 17

**ArkTS模式：** ArkTS-Dyn起始版本为17；ArkTS-Sta起始版本为23。

<!--Device-relationalStore-enum Tokenizer--><!--Device-relationalStore-enum Tokenizer-End-->

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

## NONE_TOKENIZER

```TypeScript
NONE_TOKENIZER = 0
```

不使用分词器。

**起始版本：** 17

**ArkTS模式：** ArkTS-Dyn起始版本为17；ArkTS-Sta起始版本为23。

<!--Device-Tokenizer-NONE_TOKENIZER = 0--><!--Device-Tokenizer-NONE_TOKENIZER = 0-End-->

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

## ICU_TOKENIZER

```TypeScript
ICU_TOKENIZER = 1
```

表示使用icu分词器，支持中文以及多国语言。指定icu分词器时，可指定使用哪种语言，例如zh\_CN表示中文，tr\_TR表示土耳其语等。支持的语言种类，请查阅 \_\_\_MD\_LINK\_DESC\_USD\_0\_\_\_。语言缩写请查阅该目录（ \_\_\_MD\_LINK\_DESC\_USD\_1\_\_\_）下的文件名。

**起始版本：** 17

**ArkTS模式：** ArkTS-Dyn起始版本为17；ArkTS-Sta起始版本为23。

<!--Device-Tokenizer-ICU_TOKENIZER = 1--><!--Device-Tokenizer-ICU_TOKENIZER = 1-End-->

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

## CUSTOM_TOKENIZER

```TypeScript
CUSTOM_TOKENIZER = 2
```

表示使用自研分词器，可支持中文（简体、繁体）、英文、阿拉伯数字。CUSTOM\_TOKENIZER相比ICU\_TOKENIZER在分词准确率、常驻内存占用上更有优势。自研分词器支持默认分词模式和短词分词模式（ short\_words）两种，使用参数cut\_mode可指定模式，不指定模式时使用默认模式。

**起始版本：** 18

**ArkTS模式：** ArkTS-Dyn起始版本为18；ArkTS-Sta起始版本为23。

<!--Device-Tokenizer-CUSTOM_TOKENIZER = 2--><!--Device-Tokenizer-CUSTOM_TOKENIZER = 2-End-->

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

