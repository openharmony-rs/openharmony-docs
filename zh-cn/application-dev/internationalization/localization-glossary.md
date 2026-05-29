# Localization Kit术语

<!--Kit: Localization Kit-->
<!--Subsystem: Global-->
<!--Owner: @yliupy-->
<!--Designer: @sunyaozu-->
<!--Tester: @lpw_work-->
<!--Adviser: @ningningW-->

## A

- ### Application Preferred Language；应用偏好语言

   应用设置的语言偏好。设置了应用偏好语言的应用，会加载该语言对应的资源；未设置应用偏好语言的应用，会加载系统偏好语言对应的资源。

## L

- ### Linguistic Testing；语言测试

   应用国际化和本地化完成后，由本地用户专家进行的巡检测试。包括界面翻译的地道性、术语一致性、界面显示是否存在截断、换行错误等多语言问题，界面中的日期时间格式、数字格式等全球化特性的显示风格是否正确等。

- ### Local Digit；本地数字

   特定语言区域使用的本地数字符号系统，如阿拉伯语可以使用阿拉伯数字(latn)和阿拉伯本地数字(arab)。

## S

- ### System Preferred Language；系统偏好语言

   系统设置的语言偏好。该语言偏好为列表形式，预期效果为系统优先加载列表中的第一个语言对应的资源。若资源不存在，则加载第二个语言对应的资源，以此类推。当前系统暂不支持上述功能，仅会加载列表中的第一个语言（系统语言）对应的资源。
