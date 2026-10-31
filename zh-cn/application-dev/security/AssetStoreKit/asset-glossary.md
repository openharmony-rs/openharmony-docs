# Asset Store Kit术语

<!--Kit: Asset Store Kit-->
<!--Subsystem: Security-->
<!--Owner: @HarMonkey-->
<!--Designer: @wkr321_ent-->
<!--Tester: @nacyli-->
<!--Adviser: @zengyawen-->

## A

### Asset；关键资产

用户短敏感数据，如密码、令牌、银行卡号等。由业务写入关键资产存储服务，以密文形式存储在Asset Store Kit数据库中。每条关键资产包含明文、别名及多个可自定义的附属属性。

### AuthToken；用户身份认证通过证明

统一用户认证框架签发的用户身份认证的通过证明，用于在查询需要用户认证的关键资产时与[挑战值](#challenge挑战值)一同传入，以完成身份验证并授权关键资产的访问。

## C

### Challenge；挑战值

[preQuery](../../reference/apis-asset-store-kit/js-apis-asset.md#assetprequery)接口返回的用于用户认证的随机值。

## I

### Integrity Protection；完整性保护

对关键资产部分属性（名称以DATA_LABEL_CRITICAL开头的属性）提供的防篡改保护机制，受完整性保护的属性写入后不可更新，确保不被非法篡改。