# 入门<!--application-getting-started-->
<!--Kit: Common-->
<!--Subsystem: Common-->
<!--Owner: @wanghang904-->
<!--Designer: @hanfeng6-->
<!--Tester: @kongjing2-->
<!--Adviser: @HelloCrease-->

<!--Del-->
- 快速入门<!--quick-start-->
  - [开发准备](start-overview.md)
  - [构建第一个ArkTS应用（Stage模型）](start-with-ets-stage.md)
<!--DelEnd-->
<!--RP1-->
<!--RP1End-->
- 开发基础知识<!--development-fundamentals-->
  - 应用程序包基础知识<!--application-package-fundamentals-->
    - [应用程序包概述](application-package-overview.md)
    - [应用程序包结构](application-package-structure-stage.md)
    - 应用程序包开发与使用<!--application-package-dev-->
      - [HAP](hap-package.md)
      - [HAR](har-package.md)
      - [HSP](in-app-hsp.md)
    - 应用程序包安装卸载与更新<!--application-package-install-->
      - [应用安装卸载与更新开发指导](application-package-install-uninstall.md)
      - [应用安装与更新一致性校验](install-and-update-consistency-verification.md)
  - 应用配置文件<!--application-configuration-file-stage-->
    - [应用配置文件概述](application-configuration-file-overview-stage.md)
    - [app.json5配置文件](app-configuration-file.md)
    - [module.json5配置文件](module-configuration-file.md)
  - 典型场景的开发指导<!--application-typical-scenarios-->
    - [创建应用静态快捷方式](typical-scenario-configuration.md)
    - [创建应用分身](app-clone.md)
    - [创建应用多实例](multiInstance.md)
    - [配置应用图标和名称](layered-image.md)
    - [HAR转HSP指导](har-to-hsp.md)
    - [HSP转HAR指导](hsp-to-har.md)
    - [HAP转HAR指导](hap-to-har.md)
    - [集成态HSP](integrated-hsp.md)<!--RP3--><!--RP3End-->
  - [应用程序包常见问题](common-problem-of-application.md)
  - [应用程序包术语](application-package-glossary.md)
- [资源分类与访问](resource-categories-and-access.md)
- 学习ArkTS语言<!--learning-arkts-->
  - [初识ArkTS语言](arkts-get-started.md)
  - [ArkTS语言介绍](introduction-to-arkts.md)
  - 基础语法<!--arkts-language-guide-->
    - [基础知识](arkts-language-guide-basics.md)
    - [基本操作符](arkts-language-guide-basic-operators.md)
    - [字符串](arkts-language-guide-strings.md)
    - [集合类型](arkts-language-guide-collection-types.md)
    - [控制语句](arkts-language-guide-control-statements.md)
    - [函数](arkts-language-guide-functions.md)
    - [枚举](arkts-language-guide-enums.md)
    - [类](arkts-language-guide-classes.md)
    - [属性](arkts-language-guide-properties.md)

    - [方法](arkts-language-guide-methods.md)
    - [初始化](arkts-language-guide-initialization.md)
    - [继承](arkts-language-guide-inheritance.md)
    - [接口](arkts-language-guide-interfaces.md)
    - [错误处理](arkts-language-guide-error-handling.md)
    - [类型转换](arkts-language-guide-type-conversion.md)
    - [泛型](arkts-language-guide-generics.md)
    - [异步并发](arkts-language-guide-async-concurrency.md)
    - [高级运算符](arkts-language-guide-advanced-operators.md)
    - [模块系统](arkts-language-guide-module-system.md)
    - [注解](arkts-language-guide-annotations.md)
  - [ArkTS语言规范](arkts-coding-style-guide.md)
  - 从TypeScript到ArkTS的适配指导<!--typescript-to-arkts-migration-->
    - [ArkTS语法适配背景](arkts-migration-background.md)
    - [从TypeScript到ArkTS的适配规则](typescript-to-arkts-migration-guide.md)
    - [适配指导案例](arkts-more-cases.md)
  - [ArkTS静态背景](arkts-sta-background.md)
  - [ArkTS静态语言介绍](introduction-to-arkts-sta.md)
  - 从ArkTS-Dyn到ArkTS-Sta的适配指导<!--arkts-dyn-to-arkts-sta-migration-->
    - [ArkTS-Sta语法迁移规则](arkts-dyn-to-sta-syntax-rules.md)
    - [ArkTS Migration Visualizer使用指南](arkts-migration-visualizer-instructions.md)
    - [ArkTS-Sta builtin迁移规则](arkts-dyn-to-sta-builtin-rules.md)
      - [Array](builtin/arkts-dyn-to-sta-builtin-Array.md)
      - [Constructor](builtin/arkts-dyn-to-sta-builtin-Constructor.md)
      - [ReadOnly](builtin/arkts-dyn-to-sta-builtin-ReadOnly.md)
      - [Annotations](builtin/arkts-dyn-to-sta-builtin-annotations.md)
      - [stdlib1](builtin/arkts-dyn-to-sta-builtin-stdlib1.md)
      - [stdlib2](builtin/arkts-dyn-to-sta-builtin-stdlib2.md)
      - [stdlib3](builtin/arkts-dyn-to-sta-builtin-stdlib3.md)
      - [BigUint64Array](builtin/arkts-dyn-to-sta-builtin-BigUint64Array.md)
      - [BigInt64Array](builtin/arkts-dyn-to-sta-builtin-BigInt64Array.md)
      - [Float32Array](builtin/arkts-dyn-to-sta-builtin-Float32Array.md)
      - [Float64Array](builtin/arkts-dyn-to-sta-builtin-Float64Array.md)
      - [Int8Array](builtin/arkts-dyn-to-sta-builtin-Int8Array.md)
      - [Int16Array](builtin/arkts-dyn-to-sta-builtin-Int16Array.md)
      - [Int32Array](builtin/arkts-dyn-to-sta-builtin-Int32Array.md)
      - [Uint8Array](builtin/arkts-dyn-to-sta-builtin-Uint8Array.md)
      - [Uint16Array](builtin/arkts-dyn-to-sta-builtin-Uint16Array.md)
      - [Uint32Array](builtin/arkts-dyn-to-sta-builtin-Uint32Array.md)
      - [Uint8ClampedArray](builtin/arkts-dyn-to-sta-builtin-Uint8ClampedArray.md)
    - [ArkTS-Sta 并发迁移规则](arkts-dyn-to-sta-concurrency-rules.md)
    - [ArkTS-Sta EAWorker迁移规则](arkts-dyn-to-sta-worker-migration-guide.md)
    - [ArkTS-Sta SDK迁移规则](arkts-dyn-to-sta-sdk-rules.md)
    - [ArkTS-Sta迁移工具使用指导](arkts-easytrans-cli-instructions.md)
    - [ArkTS-Sta迁移工具(EasyTrans)用户手册](arkts-easytrans-userguide.md)
  - ArkTS-Sta动静态类型互操作规范指导<!--arkts-dyn-to-arkts-sta-spec-->
    - [ArkTS-Sta互操作概述](arkts-interop-overview.md)
    - [ArkTS-Sta互操作类型映射规则](arkts-interop-type-mapping.md)
    - [ArkTS-Sta互操作场景](arkts-interop-more.md)
    - [ArkTS-Sta互操作特性规范](arkts-interop-spec.md)
    - [ArkTS动静态类型易用互操作规格指南](arkts-sta-interop-spec.md)
    - [ArkTS动静态类型互操作声明文件生成工具Declgen规格指南](arkts-sta-declgen-spec.md)
    - [ArkTS动静态类型互操作显式接口使用指南](./arkts-sta-interop-interface.md)
    - [ArkTS-Sta与ArkTS-Dyn互操作迁移规则](arkts-dyn-to-sta-interop-rules.md)
  - 从ArkTS-Dyn到ArkTS-Sta的改造指导<!--arkts-dyn-to-arkts-sta-transformation-->
    - [ArkTS静态类型及应用迁移改造概述](arkts-sta-additions-application-migration.md)
    - [ArkTS静态类型迁移改造案例](arkts-sta-migration-case.md)
    - [ArkTS静态类型改造案例](arkts-sta-transformation-case.md)
    - [ArkTS静态类型应用迁移改造常见问题](arkts-sta-migration-questions.md)
  - [ArkTS静态类型术语](arkts-sta-terminology.md)
  - [ArkTS高性能编程实践](arkts-high-performance-programming.md)
  - 面向其他语言的ArkTS迁移指导<!--arkts-for-other-languages-->
    - [从Java到ArkTS的迁移指导](getting-started-with-arkts-for-java-programmers.md)
    - [从Swift到ArkTS的迁移指导](getting-started-with-arkts-for-swift-programmers.md)
<!--RP2-->
<!--RP2End-->
