# Localization Kit术语

<!--Kit: Localization Kit-->
<!--Subsystem: Global-->
<!--Owner: @yliupy-->
<!--Designer: @sunyaozu-->
<!--Tester: @lpw_work-->
<!--Adviser: @ningningW-->

## A

### Application Preferred Language；应用偏好语言

 应用设置的语言偏好。应用设置了应用偏好语言，会加载应用偏好语言对应的资源；应用未设置应用偏好语言，会加载系统偏好语言对应的资源。

## L

### Local Digit；本地数字

特定语言区域使用的本地数字符号系统。以阿拉伯语为例，除通用的阿拉伯数字（0123456789）外，也可以使用本地数字（٠١٢٣٤٥٦٧٨٩）。

## S

### System Preferred Language；系统偏好语言

系统设置的语言偏好。系统偏好语言为列表形式，预期效果为系统优先加载列表中的第一个语言对应的资源。若资源不存在，则加载第二个语言对应的资源，以此类推。当前系统暂不支持上述功能，仅会加载列表中的第一个语言（系统语言）对应的资源。
