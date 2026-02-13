# 签名工具错误码

<!--Kit: Common-->
<!--Subsystem: Security-->
<!--Owner: @scuteehuangjun-->
<!--Designer: @scuteehuangjun; @liuchibin-->
<!--Tester: @wwrongs-->
<!--Adviser: @zengyawen-->

## 11010001 未知错误

**错误信息**

Unknown error.

**错误描述**

签名过程中出现系统内部错误。

**可能原因**

签名过程发生了错误，请查看日志中的签名验证失败详情。

**处理步骤**

结合控制台输出的错误日志信息及应用包进一步分析。

<!--Del-->
## 11011001 不支持当前命令

**错误信息**

Unsupported command method.

**错误描述**

不支持当前命令。

**可能原因**

签名过程输入了签名工具不支持的参数。

**处理步骤**

参考[签名工具使用指导](hapsigntool-guidelines.md#开发指导)，检查命令行参数是否正确。

## 11011002 参数检查错误

**错误信息**

xxx param is incorrect.

**错误描述**

签名参数验证失败。

**可能原因**

1. 枚举类型参数值超出枚举值范围。
2. 输入文件不存在或不可读。

**处理步骤**

1. 参考[签名工具使用指导](hapsigntool-guidelines.md#开发指导)，检查命令行参数是否正确。
2. 检查inFile参数对应文件是否可读。

## 11011003 参数数量错误

**错误信息**

Check param num failed.

**错误描述**

签名参数数量不正确。

**可能原因**

签名过程需要提供的参数数量与实际提供的数量不相等。

**处理步骤**

参考[签名工具使用指导](hapsigntool-guidelines.md#开发指导)，检查命令行参数是否正确。

## 11011004 空参错误

**错误信息**

Check param failed.

**错误描述**

参数为空的错误。

**可能原因**

输入的参数值为空字符串。

**处理步骤**

检查签名命令行参数值是否包含空字符串。

## 11011005 不受信任的参数

**错误信息**

Param is not trusted.

**错误描述**

不受信任的参数。

**可能原因**

签名过程使用了不受信任的参数。

**处理步骤**

参考[签名工具使用指导](hapsigntool-guidelines.md#开发指导)，检查命令行参数是否正确。

## 11011006 参数名与参数值不成对

**错误信息**

Param {-key value} must in pairs.

**错误描述**

参数名与参数值不成对。

**可能原因**

签名过程输入了参数名，未指定参数值。

**处理步骤**

参考[签名工具使用指导](hapsigntool-guidelines.md#开发指导)，检查命令行参数是否正确。

## 11011007 参数重复错误

**错误信息**

Param xxx is duplicated.

**错误描述**

参数重复错误。

**可能原因**

签名过程输入了重复的参数名称。

**处理步骤**

参考[签名工具使用指导](hapsigntool-guidelines.md#开发指导)，检查命令行参数是否正确。

## 11011008 缺少必选参数

**错误信息**

Check param failed.

**错误描述**

缺少必选参数。

**可能原因**

签名过程未输入必须的参数（如inFile、keyAlias等）。

**处理步骤**

参考[签名工具使用指导](hapsigntool-guidelines.md#开发指导)，检查命令行参数是否正确。

## 11012001 加载远程签名插件错误

**错误信息**

Load remote sign plugin failed.

**错误描述**

加载远程签名插件错误。

**可能原因**

mode参数值为remoteSign时，加载远程签名插件过程中出现连接错误或插件加载失败。

**处理步骤**

remoteSign远程签名模式是签名工具预留的扩展模式，目前暂不支持此模式，建议使用localSign模式。
<!--DelEnd-->

## 11012002 输入文件不存在

**错误信息**

File not exist.

**错误描述**

输入文件不存在。

**可能原因**

1. inFile参数指定的输入文件不存在。
2. appCertFile参数指定的证书文件不存在。
3. profileFile参数指定的profile文件不存在。

**处理步骤**

1. 检查inFile参数指定的输入文件是否存在。
2. 检查appCertFile参数指定的证书文件是否存在。
3. 检查profileFile参数指定的profile文件是否存在。

## 11012003 写文件错误

**错误信息**

Write file failed.

**错误描述**

写文件错误。

**可能原因**

当前系统用户没有outFile参数指定的输出文件的写权限。

**处理步骤**

检查当前用户是否有outFile参数指定的输出文件的写权限。

## 11012004 读文件错误

**错误信息**

Read file failed.

**错误描述**

读文件错误。

**可能原因**

1. profileFile参数指定的profile文件不存在。
2. 当前系统用户没有profileFile参数指定的profile文件的读权限。

**处理步骤**

1. 检查profileFile参数指定的profile文件是否存在。
2. 检查当前系统用户是否有profileFile参数指定的profile文件的读权限。

## 11012005 不支持的文件格式

**错误信息**

Not support file.

**错误描述**

不支持的文件格式。

**可能原因**

签名过程输入了不支持的文件后缀。

**处理步骤**
输入正确的文件格式。具体格式如下：
1. 已签名的profile文件后缀为p7b。
2. 未签名的profile文件后缀为json。
3. 证书或证书链文件后缀为cer。
4. 密钥库文件后缀为：jks、p12。

## 11012006 文件IO错误

**错误信息**

File IO failed.

**错误描述**

签名过程中发生文件读取或写入错误。

**可能原因**

1. inFile、keystoreFile、profileFile或appCertFile参数指定的文件不存在或当前用户没有读权限。
2. 当前用户没有outFile参数指定的输出文件的写权限。

**处理步骤**

1. 检查inFile、keystoreFile、profileFile或appCertFile参数指定的文件是否存在，且当前用户是否有读权限。
2. 检查当前用户是否有outFile参数指定的输出文件的写权限。

<!--Del-->
## 11013001 证书主题或签发者格式错误

**错误信息**

Check DN format failed.

**错误描述**

证书主题或签发者的格式不符合RFC 2253标准要求。

**可能原因**

issuer或subject参数格式错误。

**处理步骤**

检查issuer或subject参数格式。

issuer或subject参数支持的格式为：X=xx,XX=xxx。示例：C=CN,O=OpenHarmony,CN=hapsigntool。
<!--DelEnd-->

## 11013002 证书链文件错误

**错误信息**

Certificate format is in correct, please check your appCertFile parameter.

**错误描述**

证书链文件错误。

**可能原因**

1. appCertFile参数指定的证书链文件内容不是X.509标准证书或文件内容被修改。
2. appCertFile参数指定的证书链文件内的证书已过期。

**处理步骤**

1. 检查appCertFile指定的文件内容是否标准X.509证书。
2. 更新证书链文件。

<!--Del-->
## 11013003 生成CA证书错误

**错误信息**

Generate CA failed.

**错误描述**

生成CA证书错误。

**可能原因**

生成根CA证书时，keystoreFile指定的证书库文件与issuerKeystoreFile指定的证书库文件不相同，或者keystorePwd指定的证书库口令与issuerKeystorePwd证书库口令不相同。

**处理步骤**

参考[签名工具使用指导](hapsigntool-guidelines.md#开发指导)，检查命令行参数是否正确。

## 11013004 证书链文件内证书数量错误

**错误信息**

Profile cert must a cert chain.

**错误描述**

证书链文件内证书数量错误。

**可能原因**

appCertFile、profileCertFile参数指定的证书链文件内必须包含2或3个证书。

**处理步骤**

检查appCertFile、profileCertFile参数指定的证书链文件内证书数量。

## 11013005 不支持的算法

**错误信息**

No such algorithm.

**错误描述**

不支持的签名算法。

**可能原因**

signAlg参数指定了签名工具不支持的签名算法，支持的签名算法包括：SHA256withECDSA、SHA384withECDSA。

**处理步骤**

签名工具支持的签名算法包括：SHA256withECDSA、SHA384withECDSA。

## 11013006 证书IO错误

**错误信息**

Certificate IO failed.

**错误描述**

生成CA证书过程中发生文件读写异常。

**可能原因**

当前用户没有outFile参数指定的输出文件的写权限。

**处理步骤**

检查当前用户是否有outFile参数指定的输出文件的写权限。

## 11013007 证书主题错误

**错误信息**

Certificate check failed.

**错误描述**

证书主题检查错误。

**可能原因**

profile文件distribution-certificate或development-certificate指定的证书主题缺少common name字段。

**处理步骤**

检查profile文件distribution-certificate或development-certificate的证书内容。

## 11013008 生成证书签名请求错误

**错误信息**

generate csr failed.

**错误描述**

生成证书签名请求错误。

**可能原因**

生成证书签名请求过程中发生了文件读写异常。

**处理步骤**

结合错误日志及命令行参数进一步分析。
<!--DelEnd-->

## 11014001 秘钥不存在

**错误信息**

key alias not found.

**错误描述**

秘钥库中不存在指定别名的秘钥。

**可能原因**

秘钥库中不存在keyAlias参数指定的秘钥。

**处理步骤**

检查秘钥库是否存在keyAlias参数指定的秘钥。

<!--Del-->
## 11014002 秘钥别名已存在

**错误信息**

Key alias is exist.

**错误描述**

秘钥别名已存在。

**可能原因**

生成秘钥对时，keystoreFile参数指定的秘钥库文件已存在与keyAlias参数值同名的秘钥。

**处理步骤**

检查keystoreFile参数指定的秘钥库文件的条目信息。
<!--DelEnd-->

## 11014003 Keystore初始化失败

**错误信息**

Init keystore failed.

**错误描述**

Keystore初始化失败。

**可能原因**

1. 秘钥库文件不存在。
2. 秘钥库文件口令不正确。
3. 当前运行环境的JDK版本低于生成秘钥库文件使用的JDK版本。

**处理步骤**

1. 检查秘钥库文件是否存在。
2. 检查秘钥库文件口令是否正确。
3. 检查当前运行环境的JDK版本。

<!--Del-->
## 11014004 签名秘钥错误

**错误信息**

Invalid Key.

**错误描述**

签名秘钥错误。

**可能原因**

keyAlias参数指定的秘钥算法与signAlg指定的签名算法不匹配。例如：keyAlias指定的秘钥为RSA秘钥，signAlg指定的签名算法为SHA256withECDSA。

**处理步骤**

检查keyAlias参数指定的秘钥算法与signAlg指定的签名算法是否匹配。

## 11014005 签名参数错误

**错误信息**

Not support algorithm.

**错误描述**

签名参数不合法或格式错误。

**可能原因**

1. 签名工具不支持signAlg参数指定的算法。
2. signAlg参数指定的算法与秘钥算法不匹配。

**处理步骤**

1. 参考[签名工具使用指导](hapsigntool-guidelines.md#开发指导)，检查signAlg参数值是否正确。
2. 检查signAlg参数指定的算法与秘钥算法是否匹配。

## 11014006 秘钥库错误

**错误信息**

Keystore exception.

**错误描述**

无法访问或读取秘钥库文件。

**可能原因**

无法访问或读取秘钥库文件。

**处理步骤**

结合控制台输出的故障日志及秘钥库文件进一步分析。
<!--DelEnd-->

## 11014007 秘钥口令错误

**错误信息**

Key alias xxx password error.

**错误描述**

秘钥口令错误。

**可能原因**

秘钥口令错误。

**处理步骤**

检查keyAlias指定的秘钥口令。

## 11014008 找不到可用证书

**错误信息**

No usable cert found in xxx.

**错误描述**

找不到可用证书。

**可能原因**

秘钥库文件keyAlias指定的秘钥条目对应的证书已过期。

**处理步骤**

检查秘钥库文件keyAlias指定的秘钥条目对应的证书是否过期。

## 11015001 签名异常

**错误信息**

Signature failed.

**错误描述**

签名验证失败，返回无效签名。

**可能原因**

签名验证或签名生成过程失败。

**处理步骤**

结合控制台输出的错误日志及命令行参数进一步分析。

## 11015002 证书与私钥不匹配

**错误信息**

Signature not matched.

**错误描述**

证书与私钥不匹配。

**可能原因**

profile文件签名使用的秘钥与证书不匹配。

**处理步骤**

检查profile文件签名使用的秘钥与证书是否匹配。

## 11015003 签名验证错误

**错误信息**

Verify signature failed.

**错误描述**

签名过程中，验证签名结果不匹配。

**可能原因**

1. 签名过程中的keyAlias秘钥与appCertFile证书不匹配。
2. appCertFile指定的证书已过期。

**处理步骤**

1. 检查签名过程keyAlias指定的秘钥与appCertFile指定的证书是否匹配。
2. 更新证书链文件。

<!--Del-->
## 11015004 Profile文件内容校验错误

**错误信息**

Verify profile failed.

**错误描述**

Profile文件内容校验错误。

**可能原因**

profile文件内容未遵循HarmonyAppProvision配置文件的格式要求。

**处理步骤**

参考[HarmonyAppProvision配置文件说明](app-provision-structure.md#配置文件的内部结构)，检查profile文件内容。

## 11015005 Profile文件完整性校验错误

**错误信息**

Verify profile failed.

**错误描述**

Profile文件完整性校验错误。

**可能原因**

已签名的Profile文件内容被未经授权的修改。

**处理步骤**

重新生成已签名的Profile文件，参考[Profile文件签名指导](hapsigntool-guidelines.md#场景介绍)。
<!--DelEnd-->

## 11017001 软件包格式错误

**错误信息**

Read zip file failed.

**错误描述**

待签名的软件包格式错误。

**可能原因**

1. 待签名的HAP、HSP、HNP软件包不符合zip规范。
2. 待签名的HAP、HSP、HNP软件包大小超过4G或软件包内条目数（包括文件和目录）超过65535，超过了zip格式对文件大小（4GB）和条目数（65535）的限制，因此被打包成了zip64格式。

**处理步骤**

1. 重新打包签名。
2. 减少软件包的大小，减少软件包的文件和目录数目。

## 11017002 软件包复制异常

**错误信息**

Write zip file failed.

**错误描述**

复制待签名的HAP、HSP、HNP软件包异常。

**可能原因**

当前系统用户没有outFile参数指定的输出文件的写权限。

**处理步骤**

检查当前用户是否有outFile参数指定的输出文件的写权限。

## 11017003 HAP包字节对齐错误

**错误信息**

Alignment zip file failed

**错误描述**

HAP包字节对齐错误。

**可能原因**

HAP包字节对齐错误。

**处理步骤**

结合控制台输出的故障日志及应用包进一步分析。

## 11017004 待签名的软件包格式错误

**错误信息**

Zip format failed

**错误描述**

待签名的软件包格式错误。

**可能原因**

待签名的HAP、HSP、HNP软件包未满足zip格式规范（如压缩方式、文件结构等要求）。

**处理步骤**

重新打包签名。

## 11106001 无效的文件格式

**错误信息**

Invalid File Format.

**错误描述**

输入文件格式错误。

**可能原因**

代码签名不支持输入的文件格式。

**处理步骤**

代码签名支持的文件格式为：hap、hsp、hqf。

## 11110001 文件流读取错误

**错误信息**

Input Stream Read Error.

**错误描述**

文件读取错误。

**可能原因**

文件读取错误。

**处理步骤**

请重试，或结合故障日志及应用包进一步分析。

## 11111002 证书错误

**错误信息**

Certificates Error.

**错误描述**

证书验证失败。

**可能原因**

1. 证书不正确。

2. 签名参数keyAlias的值不正确。

**处理步骤**

1. 检查证书格式内容是否正确。

2. 检查参数keyAlias的值是否正确。

## 11112001 Profile内容错误

**错误信息**

Profile Content Error.

**错误描述**

Profile内容错误。

**可能原因**

1. profile json内容格式不符合规范。

2. type缺失或值不合法。

3. bundle-info缺失。

4. app-identifier值类型错误或长度不合法。

**处理步骤**

1. 检查json内容结构是否符合格式规范。

2. 检查type值是否正确。

3. 补充bundle-info内容。

4. 确认app-identifier值类型为String，并且字符长度要求大于0、小于等于32。

## 11112002 module.json内容错误

**错误信息**

module.json Content Error.

**错误描述**

module.json文件内容错误。

**可能原因**

1. module.json内容格式不符合格式规范。

2. 应用包中hnp文件未在module.json中描述。

**处理步骤**

1. 检查json内容结构是否符合格式规范。

2. 在module.json中添加hnp文件描述，[开发指导](../quick-start/module-configuration-file.md#hnppackages标签)。

## 11112003 ELF文件错误

**错误信息**

ELF is incorrect.

**错误描述**

ELF文件解析错误。

**可能原因**

ELF文件的头信息错误。

**处理步骤**

检查ELF文件的头信息是否符合格式规范。

## 11112004 HNP文件错误

**错误信息**

Extract hnp file error.

**错误描述**

解压hnp文件错误。

**可能原因**

1. 提取hnp文件错误。

2. 解压hnp文件错误。

**处理步骤**

1. 再次执行签名。

2. 检查hnp文件打包是否正确。

## 11113001 算法错误

**错误信息**

Invalid algorithm.

**错误描述**

签名算法错误。

**可能原因**

安装的Java版本不支持此摘要算法。

**处理步骤**

代码签名需要SHA-256和SHA-512算法支持，请检查Java版本是否正确，当前支持Java8以上Java环境运行。

## 11114001 签名内部错误

**错误信息**

Code Sign Internal Error.

**错误描述**

代码签名内部错误。

**可能原因**

工具签名过程中发生了内部错误。

**处理步骤**

结合故障日志及应用包进一步分析。