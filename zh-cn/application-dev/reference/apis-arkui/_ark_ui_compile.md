# 编译错误码
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @zhangboren-->
<!--Designer: @zhangboren-->
<!--Tester: @TerryTsao-->
<!--Adviser: @zhang_yixin13-->

> **说明：**
>
> 以下仅介绍本模块特有错误码，通用错误码请参考[通用错误码说明文档](../errorcode-universal.md)。

## 10905301 @Watch装饰器回调函数未定义
**错误信息**<br>
\'@Watch\' cannot be used with \'xxx\'. Apply it only to parameters that correspond to existing methods.  

**错误描述**<br>
@Watch回调函数未定义。

**可能原因**<br>
在struct内定义了@Watch装饰器装饰的变量,但没有定义对应的@Watch回调函数。

**处理步骤**<br>
在struct内定义对应名称的监听函数即可。

## 10905101 @BuilderParam初始化异常
**错误信息**<br>
\'@BuilderParam\' property can only initialized by \'@Builder\' function or \'@LocalBuilder\' method in struct.

**错误描述**<br>
@BuilderParam装饰的变量只能被@Builder装饰的函数初始化。

**可能或原因**<br> 
用普通函数其他类型变量初始化@BuilderParam装饰的变量。

**处理步骤**<br>
定义@LocalBuilder或@Builder装饰的函数并用来初始化@BuilderParam装饰的变量。

## 10905302 多状态管理装饰器异常
**错误信息**<br>
The property \'xxx\' cannot have multiple state management decorators.

**错误描述**<br>
同一个变量不能被多个状态管理装饰器装饰。

**可能原因**<br>
同时使用了多个状态管理装饰器装饰同一个变量导致报错。

**处理步骤**<br>
仅使用一种合适的状态管理装饰器装饰该变量。

## 10905303 @State变量初始化校验异常
**错误信息**<br>
The \'xxx\' property \'yyy\' must be specified a default value.

**错误描述**<br>
@State、@StorageLink、@StorageProp、@LocalStorageLink、@LocalStorageProp以及@Provide装饰器装饰的变量必须初始化。

**可能原因**<br>
没有对@State、@StorageLink、@StorageProp、@LocalStorageLink、@LocalStorageProp以及@Provide装饰的变量进行初始化导致报错。

**处理步骤**<br>
给@State、@StorageLink、@StorageProp、@LocalStorageLink、@LocalStorageProp以及@Provide装饰的变量初始化即可。

## 10905304 特定装饰器变量初始化校验异常
**错误信息**<br>
The \'xxx\' property cannot be specified a default value.

**错误描述**<br>
特定装饰器变量定义的时候不能初始化。

**可能原因**<br>
定义有@Consume、@Link、@ObjectLink等装饰器装饰的变量时进行初始化导致报错。

**处理步骤**<br>
在@Consume、@Link、@ObjectLink等装饰器装饰的变量定义时不要初始化,参照装饰器正确赋值规则。

## 10905305 变量类型校验异常
**错误信息**<br>
The property \'xxx\' must specify a type.

**错误描述**<br>
装饰器装饰的变量应指定类型。

**可能原因**<br>
定义有装饰器装饰的变量时没有指定类型导致报错。

**处理步骤**<br>
给装饰器装饰的变量指定类型即可。

## 10905307 特定装饰器变量类型校验异常
**错误信息**<br>
\'@ObjectLink\' cannot be used with this type. Apply it only to classes decorated by \'@Observed\' or initialized using the return value of \'makeV1Observed\'.

**错误描述**<br>
@ObjectLink装饰的变量类型需要是在ets文件中定义的被@Observed装饰的类或者联合类型。

**可能原因**<br>
用未被@Observed装饰的类或其他类型初始化@ObjectLink装饰的变量导致报错。

**处理步骤**<br>
需要用@ObjectLink装饰器装饰由@Observed装饰的类实例。

## 10905308 特定变量类型装饰器校验异常
**错误信息**<br>
The \'xxx\' property \'yyy\' cannot be a \'zzz\' object.

**错误描述**<br>
@State等装饰器装饰的变量不能为CustomDialogController等类型变量。

**可能原因**<br>
用状态变量装饰器装饰CustomDialogController等类型变量导致报错。

**处理步骤**<br>
避免使用状态变量装饰器装饰CustomDialogController等变量类型。

## 10905309 自定义装饰器命名校验异常
**错误信息**<br>
The decorator \'xxx\' cannot have the same name as the built-in style attribute \'yyy\'. 

**错误描述**<br>
开发者自定义装饰器不能与内置属性名相同。

**可能原因**<br>
开发者给自定义装饰器命名与内置属性名相同导致报错。

**处理步骤**<br>
修改开发者自定义装饰器名称为不同于内置属性名的名称。

## 10905310 @Watch装饰器校验异常
**错误信息**<br>
Regular variable \'xxx\' can not be decorated with \'@Watch\'. 

**错误描述**<br>
常规变量不能被@Watch装饰。

**可能原因**<br>
用@Watch装饰器装饰了常规变量导致报错。

**处理步骤**<br>
用合适的状态变量装饰器搭配@Watch装饰变量即可。

## 10905311 @Watch装饰器参数校验异常
**错误信息**<br>
\'@Watch\' cannot be used with \'xxx\'. Apply it only to \'string\' parameters.

**错误描述**<br>
@Watch参数必须是字符串类型。

**可能原因**<br>
用非字符串类型的值作为@Watch装饰器的参数导致报错。

**处理步骤**<br>
将@Watch装饰器的参数修改为字符串类型即可。

## 10905312 自定义装饰器使用校验异常
**错误信息**<br>
The inner decorator \'xxx\' cannot be used together with custom decorator.

**错误描述**<br>
@State等内置组件装饰器不能和自定义装饰器一起使用。

**可能原因**<br>
自定义装饰器与@State等内置组件装饰器一起装饰变量导致报错。

**处理步骤**<br>
避免使用状态变量装饰器和自定义装饰器装饰同一变量。

## 10905201 父组件校验异常
**错误信息**<br>
The \'xxx\' component can only be nested in the \'yyy\' parent component.

**错误描述**<br>
组件的父组件不是特定组件时，编译报错。

**可能原因**<br>
@Blank等组件的父组件不在该组件特定父组件范围内导致报错。

**处理步骤**<br>
根据错误描述修改父组件或者添加中间层组件即可。

## 10905202 Button组件子组件校验异常
**错误信息**<br>
The Button component with a label parameter can not have any child.

**错误描述**<br>
Button组件在有标签时不能有子组件。

**可能原因**<br>
Button组件同时包含了标签与子组件导致报错。

**处理步骤**<br>
删除标签内容或者删除子组件内容（包括大括号）。

## 10905203 .stateStyles语法校验异常
**错误信息**<br>
\'.stateStyles\' doesn't conform standard.

**错误描述**<br>
stateStyles属性使用不符合语法。

**可能原因**<br>
没有正确指定stateStyles不同状态或没有遵循其他stateStyles属性语法。

**处理步骤**<br>
需要正确指定stateStyles的不同状态。

## 10905204 UI组件语法校验异常
**错误信息**<br>
\'xxx\' does not meet UI component syntax.

**错误描述**<br>
不符合UI组件语法。

**可能原因**<br>
开发者没有遵循基础的UI组件语法进行编码导致报错。

**处理步骤**<br>
需要参照正确UI组件语法修改。

## 10905207 if语句then部分校验异常
**错误信息**<br>
Then statement cannot be null in if statement.

**错误描述**<br>
if语句有缺失内容。

**可能原因**<br>
if语法then语句部分没有内容导致报错。

**处理步骤**<br>
需要在if判断条件后加入正确的then语句。

## 10905208 if语句判断条件校验异常
**错误信息**<br>
Condition expression cannot be null in if statement.

**错误描述**<br>
if语句有缺失条件。

**可能原因**<br>
if语法判断条件部分没有内容导致报错。

**处理步骤**<br>
需要给if语句加入正确的判断条件。

## 10905102 @BuilderParam尾随闭包场景校验异常
**错误信息**<br>
In the trailing lambda case, \'xxx\' must have one and only one property decorated with \'@BuilderParam\', and its \'@BuilderParam\' expects no parameter.

**错误描述**<br>
尾随闭包场景下有且只能有一个@BuilderParam装饰的变量（不包含参数）。

**可能原因**<br>
在尾随闭包场景下子组件定义了多个@BuilderParam装饰的变量或是@BuilderParam装饰的变量包含了参数。

**处理步骤**<br>
删除多余@BuilderParam装饰的方法，只保留一个@BuilderParam装饰器且不包含参数。

## 10905209 build()方法UI语法校验异常
**错误信息**<br>
Only UI component syntax can be written here.

**错误描述**<br>
该位置只能出现UI语法。

**可能原因**<br>
开发者报错位置使用了UI语法以外的内容。

**处理步骤**<br>
需要参照正确UI组件语法修改。

## 10905210 build()方法根容器校验异常
**错误信息**<br>
In an \'@Entry\' decorated component, the \'build\' method can have only one root node, which must be a container component.

**错误描述**<br>
build()方法内有多个根容器。

**可能原因**<br>
开发者在build()方法中定义了多个根容器。

**处理步骤**<br>
删除多余根容器，保证build()方法中仅有一个根容器。

## 10905103 build()方法校验异常
**错误信息**<br>
The struct \'xxx\' must have at least and at most one 'build' method.

**错误描述**<br>
组件内必须有且只有一个build()方法。

**可能原因**<br>
开发者在struct组件内定义了多个build()方法或是没有定义build()方法导致报错。

**处理步骤**<br>
在struct组件内定义唯一一个build()方法即可。

## 10905211 @CustomDialog成员属性校验异常
**错误信息**<br>
The \'@CustomDialog\' decorated custom component must contain a property of the CustomDialogController type.

**错误描述**<br>
@CustomDialog装饰的自定义组件必须要有一个CustomDialogController类型的成员属性。

**可能原因**<br>
开发者定义了@CustomDialog装饰器装饰的自定义组件，但是没有在其中定义CustomDialogController类型的成员属性导致报错。

**处理步骤**<br>
需要在@CustomDialog装饰的自定义组件中加入CustomDialogController类型参数。

## 10905212 struct校验异常
**错误信息**<br>
Structs are not allowed to inherit from classes or implement interfaces.

**错误描述**<br>
struct不允许扩展其他类或实现其它接口。

**可能原因**<br>
开发者定义struct为其他类的子类或其它接口的实现类导致报错。

**处理步骤**<br>
避免使用struct扩展其他类或实现其它接口。

## 10905104 自定义组件静态方法装饰器校验异常
**错误信息**<br>
Static methods in custom components cannot be decorated by \'@LocalBuilder\'.

**错误描述**<br>
自定义组件中的静态方法不能被@LocalBuilder装饰器装饰。

**可能原因**<br>
开发者在自定义组件中用@LocalBuilder装饰器装饰静态方法。

**处理步骤**<br>
删除static关键字即可。

## 10905105 @Styles装饰器校验异常
**错误信息**<br>
\'@Styles\' decorated functions and methods cannot have arguments.

**错误描述**<br>
@Styles装饰的函数不能带参数。

**可能原因**<br>
开发者在定义@Styles装饰器装饰的函数时包含了参数。

**处理步骤**<br>
删除@Styles装饰器装饰函数的参数即可。

## 10905106 build()方法校验异常
**错误信息**<br>
The \'build\' method can not have arguments.

**错误描述**<br>
build()方法不能有参数。

**可能原因**<br>
开发者在定义build()方法时包含了参数。

**处理步骤**<br>
删除build()方法的参数即可。

## 10905313 struct变量校验异常
**错误信息**<br>
The static variable of struct cannot be used together with built-in decorators.

**错误描述**<br>
struct的静态变量不能与内置装饰器一起使用。

**可能原因**<br>
开发者在struct中用内置装饰器装饰了静态变量导致报错。

**处理步骤**<br>
避免在struct中用内置装饰器装饰静态变量。

## 10905314 \$使用校验异常
**错误信息**<br>
Property \'xxx\' cannot initialize using \'\$\' to create a reference to a variable.

**错误描述**<br>
\$只能用在修饰子组件@Link上。

**可能原因**<br>
开发者使用\$修饰子组件中@Prop装饰器装饰的属性成员或者其他非@Link装饰的属性成员导致报错。

**处理步骤**<br>
用@Link装饰器装饰子组件中对应变量或者删除\$。

## 10905315 父子组件赋值校验异常
**错误信息**<br>
The \'xxx\' property \'yyy\' cannot be assigned to the \'zzz\' property \'nnn\'.

**错误描述**<br>
自定义父子组件赋值校验错误。

**可能原因**<br>
开发者使用常规变量初始化子组件中用@Link装饰器装饰的成员变量导致报错。

**处理步骤**<br>
避免使用常规变量初始化子组件中用@Link装饰器装饰的成员变量。

## 10905316 @Link装饰变量初始化校验异常
**错误信息**<br>
The property \'xxx\' in the custom component \'yyy\' is missing (mandatory to specify).

**错误描述**<br>
@Link装饰的变量未从父组件初始化校验。

**可能原因**<br>
开发者在子组件中使用@Link装饰器装饰的成员变量没有在父组件调用子组件时初始化该成员变量导致报错。

**处理步骤**<br>
@Link装饰的变量需要在父组件进行初始化。

## 10905317 装饰器变量初始化校验异常
**错误信息**<br>
The property \'xxx\' in the custom component \'yyy\' cannot be initialized here (fobidden to specify).

**错误描述**<br>
@StorageProp、@StorageLink、@Consume等装饰器装饰的变量不能在父组件调用子组件时初始化。

**可能原因**<br>
开发者在子组件中使用@StorageProp、@StorageLink、@Consume等装饰器装饰的成员变量在父组件调用子组件时初始化导致报错。

**处理步骤**<br>
参考@StorageProp、@StorageLink、@Consume等装饰器使用方法正确使用变量。

## 10905318 V2场景使用!!父传子校验异常
**错误信息**<br>
When the two-way binding syntax is used, the initial value of property \'xxx\' must be a variable.

**错误描述**<br>
V2组件在使用!!父传子的时候只能使用变量。

**可能原因**<br>
开发者在V2场景下!!父传子的时候使用了函数、常量或者字面量进行传递导致报错。

**处理步骤**<br>
在V2场景下!!父传子的时候需要使用变量进行传递。

## 10905319 V2场景使用!!子组件变量校验异常
**错误信息**<br>
When the two-way binding syntax is used, the variable \'xxx\' must be decorated with \'@Param\', and the \'@Event\' variable \'yyy\' must be defined in the \'zzz\'.

**错误描述**<br>
V2组件在使用!!时必须使用@Param且配合@Event使用。

**可能原因**<br>
开发者在V2场景下使用!!时子组件变量没有使用@Param装饰或者没有使用@Event装饰变量对应的回调方法导致报错。

**处理步骤**<br>
在V2场景下使用!!时需要用@Param装饰子组件变量且定义@Event装饰的回调方法。

## 10905320 V2场景下@Param初始化校验异常
**错误信息**<br>
The optional character can not be used in the initial value of property \'xxx\'.

**错误描述**<br>
V2组件不可使用可选符号传入子组件定义的@Param装饰的变量。

**可能原因**<br>
开发者在V2场景下初始化子组件中@Param装饰的变量时用了可选符号导致报错。

**处理步骤**<br>
避免在V2场景下使用可选符号初始化@Param装饰的变量。

## 10905321 @Prop和@BuilderParam装饰变量初始化校验异常
**错误信息**<br>
\'@Required\' decorated \'xxx\' must be initialized through the component constructor.

**错误描述**<br>
@Prop和@BuilderParam装饰变量初始化校验错误。

**可能原因**<br>
开发者用@Require装饰器与@Prop、@BuilderParam共同装饰子组件变量，但没有在父组件调用子组件时给对应变量进行初始化导致报错。

**处理步骤**<br>
@Require装饰的变量需要在父组件调用的时候初始化。

## 10905213 V2、V1混用校验异常
**错误信息**<br>
A V2 component cannot be used with any member property decorated by \'@Link\' in a V1 component.

**错误描述**<br>
V2组件不能和V1组件的@Link装饰器一起使用。

**可能原因**<br>
开发者在V2组件中使用了包含@Link装饰器的V1组件导致报错。

**处理步骤**<br>
避免在V2组件中使用包含@Link装饰器的V1组件。

## 10905323 V1组件赋值V2属性校验异常
**错误信息**<br>
Property \'xxx\' in the \'@ComponentV2\' component \'yyy\' is not allowed to be assigned values here.

**错误描述**<br>
V1组件不允许赋予V2属性。

**可能原因**<br>
开发者在调用V1组件时赋予其属性V2装饰器装饰的属性值导致报错。

**处理步骤**<br>
避免给V1子组件属性赋予V2装饰器装饰的变量值。

## 10905324 特定装饰器变量初始化校验异常
**错误信息**<br>
The \'xxx\' property \'yyy\' in the custom component \'zzz\' cannot be initialized here (forbidden to specify).

**错误描述**<br>
特定装饰器装饰的变量不能在父子组件调用时初始化。

**可能原因**<br>
开发者在子组件中使用特定装饰器装饰的变量在父组件中调用时初始化导致报错。

**处理步骤**<br>
参考特定装饰器使用方法正确使用变量。

## 10905325 V2场景@Require校验异常
**错误信息**<br>
In a struct decorated with \'@ComponentV2\', \'@Require\' can only be used with \'@Param\'.

**错误描述**<br>
V2组件中，@Require只能与特定装饰器一起使用。

**可能原因**<br>
开发者在V2场景下使用@Require装饰器搭配了@Param以外的V2装饰器一起使用导致报错。

**处理步骤**<br>
添加特定装饰器与@Require一起搭配使用即可。

## 10905326 V2场景@Once校验异常
**错误信息**<br>
When a variable decorated with \'@Once\', it must also be decorated with \'@Param\'.

**错误描述**<br>
V2组件中，使用@Once装饰时，它也必须被@Param装饰。

**可能原因**<br>
开发者在V2场景下使用@Once装饰器时没有使用@Param装饰器搭配导致报错。

**处理步骤**<br>
添加@Param装饰器与@Once装饰器一起使用即可。

## 10905327 V2场景@Param默认值校验异常
**错误信息**<br>
When a variable decorated with \'@Param\' is not assigned a default value, it must also be decorated with \'@Require\'. 

**错误描述**<br>
V2组件中@Param装饰的变量没有被赋予默认值时，它也必须用@Require装饰。

**可能原因**<br>
开发者在V2场景下使用@Param装饰器装饰变量但是没有赋予默认值且没有搭配使用@Require装饰器导致报错。

**处理步骤**<br>
给@Param装饰的变量赋予默认值或者用@Require一起装饰。

## 10905107 @BuilderParam初始化校验异常
**错误信息**<br>
\'@BuilderParam\' property can only be initialized by \'@Builder\' function.

**错误描述**<br>
@BuilderParam装饰的变量只能被@Builder装饰的函数初始化。

**可能原因**<br>
开发者使用其他类型变量或者普通函数给@BuilderParam装饰器装饰的函数进行初始化导致报错。

**处理步骤**<br>
修改@BuilderParam初始化的值为@Builder装饰器装饰的方法即可。

## 10905328 状态变量成员类型校验异常
**错误信息**<br>
The property \'xxx\' must specify a type.

**错误描述**<br>
状态变量成员属性类型校验错误。

**可能原因**<br>
开发者没有给状态变量声明类型导致报错。

**处理步骤**<br>
给状态变量声明正确类型满足类型校验即可。

## 10906217 卡片参数校验异常
**错误信息**<br>
\'@Entry\' doesn't support {} parameter in card. 

**错误描述**<br>
卡片中的@Entry不支持传入参数{}。

**可能原因**<br>
开发者在卡片中的@Entry传入了{}参数。

**处理步骤**<br>
根据报错日志说明进行整改即可。

## 10905108 @Extend装饰器参数校验异常
**错误信息**<br>
\'xxx\' should have one and only one parameter.

**错误描述**<br>
@Extend等装饰器应该有一个且只有一个参数。

**可能原因**<br>
开发者在使用@Extend等装饰器时未包含参数或包含了多个参数导致报错。

**处理步骤**<br>
给@Extend等装饰器添加一个参数即可。

## 10903329 资源名称使用校验异常
**错误信息**<br>
Unknown resouce name \'xxx\'.

**错误描述**<br>
资源名称校验失败。

**可能原因**<br>
开发者未提供正确的资源名称导致报错。

**处理步骤**<br>
需要使用正确的资源名称。

## 10903330 资源类型使用校验异常
**错误信息**<br>
Unknown resource type \'xxx\'.

**错误描述**<br>
资源类型校验失败。

**可能原因**<br>
开发者未提供正确的资源类型导致报错。

**处理步骤**<br>
需要使用正确的资源类型。

## 10903331 资源来源使用校验异常
**错误信息**<br>
Unknown resource source \'xxx\'.

**错误描述**<br>
资源来源校验失败。

**可能原因**<br>
开发者未提供正确的资源来源导致报错。

**处理步骤**<br>
需要使用正确的资源来源。

## 10905332 资源范式使用校验异常
**错误信息**<br>
Invalid resource file parameter. Enter a value in the format of \'xxx.yyy.zzz\'.

**错误描述**<br>
错误引用资源范式的报错。

**可能原因**<br>
开发者未正确引用资源范式导致报错。

**处理步骤**<br>
按照文档规范正确使用资源格式。

## 10904333 资源存在校验异常
**错误信息**<br>
No such \'xxx\' resource in current module.

**错误描述**<br>
针对\$rawfile\(\)引用不存在的资源。

**可能原因**<br>
开发者提供了不存在的资源导致报错。

**处理步骤**<br>
需要ets使用的资源名称和路径和\$rawfile匹配。

## 10905109 wrapBuilder参数校验异常
**错误信息**<br>
The wrapBuilder\'s parameter should be a \'@Builder\' function.

**错误描述**<br>
wrapBuilder的参数必须为@Builder方法。

**可能原因**<br>
开发者使用其他类型变量或是普通函数作为wrapBuilder函数的参数导致报错。

**处理步骤**<br>
修改wrapBuilder的参数为@Builder装饰器装饰的方法。

## 10905110 @Styles校验异常
**错误信息**<br>
\'@Styles\' decorated functions and methods cannot have arguments.

**错误描述**<br>
@Styles装饰的方法参数校验错误。

**可能原因**<br>
开发者在@Styles装饰器装饰的方法中包含了参数导致报错。

**处理步骤**<br>
删除@Styles装饰器装饰方法的参数即可。

## 10905111 @AnimatedExtend和@Extend混用校验异常
**错误信息**<br>
The function can not be decorated by \'@Extend\' and \'@AnimatedExtend\' at the same time.

**错误描述**<br>
@AnimatedExtend和@Extend装饰器不能同时装饰同一个函数。

**可能原因**<br>
开发者同时使用@AnimatedExtend和@Extend装饰器装饰同一个函数导致报错。

**处理步骤**<br>
删除@Extend或者@AnimatedExtend装饰器的其中一个即可。

## 10905112 装饰器使用校验异常
**错误信息**<br>
\'xxx\' can not decorate the method.

**错误描述**<br>
使用@State等非法装饰器装饰method。

**可能原因**<br>
开发者使用属性装饰器@State等装饰方法导致报错。

**处理步骤**<br>
避免使用@State等装饰器装饰属性的装饰器装饰方法。

## 10905219 特定组件子组件校验异常
**错误信息**<br>
The component \'xxx\' can only have the child component \'yyy\'.

**错误描述**<br>
ContainerSpan等组件只允许特定组件作为子组件。

**可能原因**<br>
开发者使用ContainerSpan等组件且调用不在其特定子组件范围内的组件作为子组件导致报错。

**处理步骤**<br>
修改子组件为特定组件范围内的组件。

## 10905220 Button等组件子组件校验异常
**错误信息**<br>
The \'xxx\' component can have only one child component.

**错误描述**<br>
Button等组件只能出现一个子组件。

**可能原因**<br>
开发者在使用Button等组件时定义了多个子组件导致报错。

**处理步骤**<br>
删除Button等组件多余子组件，最多保留一个子组件。

## 10905221 特定组件属性子组件数量校验异常
**错误信息**<br>
When the component \'xxx\' set \'yyy\' as \'zzz\', it can only have a single child component. 

**错误描述**<br>
特定组件属性只允许单个子组件。

**可能原因**<br>
开发者在使用特定组件属性值的时候定义了多个子组件导致报错。

**处理步骤**<br>
删除特定组件多余子组件，最多保留一个子组件。

## 10905222 image等组件校验异常
**错误信息**<br>
The component \'xxx\' can't have any child.

**错误描述**<br>
image等组件不能有大括号（子组件）。

**可能原因**<br>
开发者在使用image等组件时定义了子组件。

**处理步骤**<br>
删除image等组件的子组件。

## 10905223 特定组件属性子组件校验异常
**错误信息**<br>
When the component \'xxx\' set \'yyy\' as \'zzz\', it can't have any child. 

**错误描述**<br>
特定组件属性不允许有子组件。

**可能原因**<br>
开发者在使用特定组件属性值的时候定义了子组件导致报错。

**处理步骤**<br>
删除特定组件子组件即可。

## 10905113 @Extend等装饰器使用校验异常
**错误信息**<br>
Use the \'xxx\' decorator only in the global scope.

**错误描述**<br>
@Extend等装饰器不能是class或struct的成员属性方法。

**可能原因**<br>
开发者在class或者struct内使用@Extend等装饰器装饰方法导致报错。

**处理步骤**<br>
参照@Extend等装饰器正确使用方法，用以装饰全局函数。

## 10905337 装饰器使用校验异常
**错误信息**<br>
The \'xxx\' decorator can only be used with \'struct\'.

**错误描述**<br>
装饰器无法装饰非struct。

**可能原因**<br>
开发者使用了@Componet、@ComponentV2等struct装饰器装饰了非struct比如函数等导致报错。

**处理步骤**<br>
按照错误日志描述，正确使用对应装饰器即可。

## 10905338 V2装饰器使用校验异常
**错误信息**<br>
The \'xxx\' decorator can only be used in a \'struct\' decorated with \'@ComponentV2\'.

**错误描述**<br>
V2的成员装饰器只能用在@ComponentV2装饰的struct中。

**可能原因**<br>
开发者在@Component装饰的struct中使用了V2的成员装饰器导致报错。

**处理步骤**<br>
按照错误日志描述，在正确场景下使用V2成员装饰器即可。

## 10905339 V1装饰器使用校验异常
**错误信息**<br>
The \'xxx\' decorator can only be used in a \'struct\' decorated with \'@Component\'.

**错误描述**<br>
V1的成员装饰器只能在用\'@Component\'装饰的\'struct\'中使用。

**可能原因**<br>
开发者在@ComponentV2装饰的struct中使用了V1的成员装饰器导致报错。

**处理步骤**<br>
按照错误日志描述，在正确场景下使用V1成员装饰器即可。

## 10905224 @Observed类继承@ObservedV2类校验异常
**错误信息**<br>
A class decorated by \'@Observed\' cannot inherit from a class decorated by \'@ObservedV2\'.

**错误描述**<br>
因为当前类被\'@Observed\'装饰，所以它不能继承被\'@ObservedV2\'装饰的类。

**可能原因**<br>
开发者使用被\'@Observed\'装饰的类继承\'@ObservedV2\'装饰的类导致报错。

**处理步骤**<br>
继承\'@Observed\'装饰的类或者修改类装饰器为\'@ObservedV2\'。

## 10905225 @ObservedV2类继承@Observed类校验异常
**错误信息**<br>
A class decorated by \'@ObservedV2\' cannot inherit from a class decorated by \'@Observed\'.

**错误描述**<br>
因为当前类被\'@ObservedV2\'装饰，所以它不能继承被\'@Observed\'装饰的类。

**可能原因**<br>
开发者使用被\'@ObservedV2\'装饰的类继承\'@Observed\'装饰的类导致报错。

**处理步骤**<br>
继承\'@ObservedV2\'装饰的类或者修改类装饰器为\'@Observed\'。

## 10905226 @Observed、@ObservedV2同时使用校验异常
**错误信息**<br>
A class can not be decorated by \'@Observed\' and \'@ObservedV2\' at the same time.

**错误描述**<br>
一个类不能同时被\'@Observed\'和\'@ObservedV2\'修饰。

**可能原因**<br>
开发者同时使用\'@Observed\'和\'@ObservedV2\'装饰一个类导致报错。

**处理步骤**<br>
仅保留一个合适的类装饰器即可。

## 10905340 @Type等装饰器使用校验异常
**错误信息**<br>
The \'xxx\' can decorate only member variables in a \'class\'.

**错误描述**<br>
@Type等装饰器只能装饰class中的变量，不能装饰方法。

**可能原因**<br>
开发者使用@Type等装饰器装饰了class中的变量导致报错。

**处理步骤**<br>
删除去掉class中方法上的@Type等装饰器即可。

## 10905341 @Type等装饰器与@Observed同时使用校验异常
**错误信息**<br>
The \'xxx\' decorator can not be used in a \'class\' decorated with \'@Observed\'.

**错误描述**<br>
@Type等装饰器不能用在@Observed装饰的类中。

**可能原因**<br>
开发者在@Observed装饰的类中使用了@Type等装饰器导致报错。

**处理步骤**<br>
避免在@Observed装饰的类中使用@Type等装饰器。

## 10905342 @Type等装饰器与@Sendable共同使用校验异常
**错误信息**<br>
The \'xxx\' decorator can not be used in a \'class\' decorated with \'@Sendable\'.

**错误描述**<br>
@Type等装饰器不能用在@Sendable装饰的类中。

**可能原因**<br>
开发者在@Sendable装饰的类中使用了@Type等装饰器导致报错。

**处理步骤**<br>
避免在@Sendable装饰的类中使用@Type等装饰器。

## 10905343 @Monitor等装饰器使用校验异常
**错误信息**<br>
The \'xxx\' can decorate only member \'yyy\' within a \'class\' decorated with \'@ObservedV2\'.

**错误描述**<br>
@Monitor等装饰器只能装饰用@ObservedV2装饰的类中的成员方法。

**可能原因**<br>
开发者使用@Monitor等装饰器装饰了@Observed装饰器装饰的类中的成员方法导致报错。

**处理步骤**<br>
只能在@ObservedV2装饰的类中使用@Monitor等装饰器，@Observed类中可以尝试用@Watch装饰器实现功能。

## 10905344 @Track等装饰器V2使用校验异常
**错误信息**<br>
\'xxx\' cannot be used with classes decorated by \'@ObservedV2\'. Use the \'@Trace\' decorator instead.

**错误描述**<br>
@Track等装饰器不能用于@ObservedV2装饰的类中。

**可能原因**<br>
开发者在@ObservedV2装饰的类中使用了@Track等装饰器导致报错。

**处理步骤**<br>
避免在@ObservedV2装饰的类中使用@Track等装饰器即可。

## 10905345 @Track等装饰器class使用校验异常
**错误信息**<br>
The \'xxx\' decorator can decorate only member variables of a class.

**错误描述**<br>
@Track等装饰器只能在class中使用。

**可能原因**<br>
开发者在class外使用了@Track等装饰器导致报错。

**处理步骤**<br>
避免在class外使用@Track等装饰器。

## 10905346 V2装饰器使用校验异常
**错误信息**<br>
\'xxx\' can only decorate member property.

**错误描述**<br>
在@ComponentV2中，@Local、@Param、@Once、@Event、@Provider、@Consume以及@BuilderParam只能装饰成员属性。

**可能原因**<br>
开发者在V2场景下使用@Local、@Param、@Once、@Event、@Provider、@Consume以及@BuilderParam装饰了函数方法等非成员属性导致报错。

**处理步骤**<br>
在V2场景中，避免使用@Local、@Param、@Once、@Event、@Provider、@Consume以及@BuilderParam装饰方法。

## 10905115 @LocalBuilder、@Monitor等装饰器使用校验异常
**错误信息**<br>
\'xxx\' can only decorate method.

**错误描述**<br>
@LocalBuilder、@Monitor等装饰器仅能装饰方法。

**可能原因**<br>
开发者使用@LocalBuilder或@Monitor等装饰器装饰了属性变量、全局函数或者class内的方法等导致报错。

**处理步骤**<br>
正确使用@LocalBuilder、@Monitor等装饰器装饰方法。

## 10905116 @Computed装饰器使用校验异常
**错误信息**<br>
\'@Computed\' can only decorate 'GetAccessor'.

**错误描述**<br>
@Computed只能装饰get方法。

**可能原因**<br>
开发者使用@Computed装饰普通函数方法导致报错。

**处理步骤**<br>
根据@Computed只能装饰正确规范的get方法规则进行修改。

## 10905117 方法装饰器混用校验异常
**错误信息**<br>
A funtion can only be decorated by one of the \'@AnimatedExtend\'，\'@Builder\'，\'@Extend\'，\'@Styles\'，\'@Concurrent\' and \'@Sendable\''.

**错误描述**<br>
两个不同方法装饰器定义在同一个方法上。

**可能原因**<br>
开发者使用了多个方法装饰器定义在同一个方法上导致报错。

**处理步骤**<br>
选择一个合适的方法装饰器来装饰方法即可。

## 10905119 装饰器重复校验异常
**错误信息**<br>
Duplicate \'xxx\' decorators for method are not allowed.

**错误描述**<br>
装饰器重复使用校验。

**可能原因**<br>
开发者在一个方法上重复使用相同的装饰器进行装饰导致报错。

**处理步骤**<br>
避免重复使用装饰器装饰相同方法。

## 10905121 内置装饰器使用校验异常
**错误信息**<br>
The member property or method can not be decorated by multiple built-in decorators.

**错误描述**<br>
成员属性或方法不能被多个内置装饰器装饰。

**可能原因**<br>
开发者使用了多个内置装饰器同时装饰同一个成员属性或方法导致报错。

**处理步骤**<br>
选择一个合适的内置装饰器来装饰成员属性或方法即可。

## 10905348 状态变量类型校验异常
**错误信息**<br>
The type of the \'xxx\' property can not be a class decorated with \'@ObservedV2\'.

**错误描述**<br>
该装饰器装饰属性的类型不能是用@ObservedV2装饰的类。

**可能原因**<br>
开发者使用被@ObservedV2装饰的类作为@Local等装饰器装饰的成员属性的类型导致报错。

**处理步骤**<br>
避免使用该装饰器装饰@ObservedV2装饰的类实例。

## 10905122 @Concurrent装饰器使用校验异常 
**错误信息**<br>  
\'@Concurrent\' can not be used on \'xxx\' function declaration.

**错误描述**<br>
@Concurrent不能装饰特定函数。

**可能原因**<br>
开发者使用@Concurrent装饰特定函数导致报错。

**处理步骤**<br>
避免使用@Concurrent装饰器装饰特定函数即可。

## 10905123 @Concurrent装饰方法校验异常
**错误信息**<br>
\'@Concurrent\' can not be used on method, please use it on function declaration.

**错误描述**<br>
@Concurrent不能装饰方法。

**可能原因**<br>
开发者使用@Concurrent装饰成员方法导致报错。

**处理步骤**<br>
避免使用@Concurrent装饰器装饰方法。

## 10905227 自定义组件命名同内置组件校验异常
**错误信息**<br>
The struct \'xxx\' cannot have the same name as the built-in component \'xxx\'.

**错误描述**<br>
自定义组件名字与内置组件重复。

**可能原因**<br>
开发者给自定义组件命名与内置组件相同导致报错。

**处理步骤**<br>
修改自定义组件名为不同于内置组件名称的合法组件名。

## 10905228 自定义组件命名同内置组件属性方法校验异常
**错误信息**<br>
The struct \'xxx\' cannot have the same name as the built-in attribute \'xxx\'.

**错误描述**<br>
自定义组件名字与内置组件属性方法名重复。

**可能原因**<br>
开发者给自定义组件命名与内置组件属性方法名重复导致报错。

**处理步骤**<br>
修改自定义组件名为不同于内置组件属性方法名的合法组件名。

## 10905229 struct装饰器校验异常
**错误信息**<br>
The struct \'xxx\' can not be decorated with \'@ComponentV2\' and \'@Component\'，\'@Reusable\'，\'@CustomDialog\' at the same time.

**错误描述**<br>
struct不能同时使用 \'@ComponentV2\'、\'@Component\'、\'@Reusable\'和\'@CustomDialog\'一起装饰。

**可能原因**<br>
开发者同时使用\'@ComponentV2\'、\'@Component\'、\'@Reusable\'和\'@CustomDialog\'装饰同一个struct导致报错。

**处理步骤**<br>
避免同时使用\'@ComponentV2\'、\'@Component\'、\'@Reusable\'和\'@CustomDialog\'装饰器同时装饰同一个struct。

## 10905230 子组件调用校验异常
**错误信息**<br>
Decorator \'@Component\'，\'@ComponentV2\'，or \'@CustomDialog\' is missing for struct \'xxx\'.

**错误描述**<br>
子组件未用\'@Component\'、\'@ComponentV2\'或\'@CustomDialog\'进行装饰。

**可能原因**<br>
开发者没有使用\'@Component\'、\'@ComponentV2\'或\'@CustomDialog\'装饰子组件导致报错。

**处理步骤**<br>
需要使用\'@Component\'、\'@ComponentV2\'或\'@CustomDialog\'装饰器来装饰struct。

## 10905402 @Entry装饰器校验异常
**错误信息**<br>
A page configured in \'main_pages.json\' or \'build-profile.json5\' must have one and only one \'@Entry\' decorator.

**错误描述**<br>
主页面缺少@Entry装饰器校验。

**可能原因**<br>
开发者在主页面中没有给任何自定义组件装饰@Entry导致报错。

**处理步骤**<br>
确保主页面中有且仅有一个@Entry装饰器生效。

## 10905231 @Entry装饰器数量校验异常
**错误信息**<br>
A page can't contain more than one \'@Entry\' decorator.

**错误描述**<br>
一个页面不能包含多个@Entry装饰器校验。

**可能原因**<br>
开发者在一个页面中多个自定义组件上都使用了@Entry装饰器进行装饰。

**处理步骤**<br>
删除多余@Entry装饰器，页面最多保留一个@Entry装饰器。

## 10905404 @Preview装饰器数量校验异常
**错误信息**<br>
A page can contain at most 10 \'@Preview\' decorators.

**错误描述**<br>
一个页面最多可以包含10个@Preview装饰器校验。

**可能原因**<br>
开发者在一个页面中使用的@Preview装饰器数量大于10个导致报错。

**处理步骤**<br>
删除多余@Preview装饰器，页面最多保留十个@Preview装饰器。

## 10905232 struct命名校验异常
**错误信息**<br>
A struct must have a name.

**错误描述**<br>
struct必须有名称。

**可能原因**<br>
开发者没有给struct命名导致报错。

**处理步骤**<br>
给struct定义名称即可。

## 10905233 子组件调用校验异常
**错误信息**<br>
Decorator \'@Component\'，\'@ComponentV2\'，or \'@CustomDialog\' is missing for struct \'xxx\'.

**错误描述**<br>
子组件未用\'@Component\'、\'@ComponentV2\'或\'@CustomDialog\'进行装饰而被父组件调用。

**可能原因**<br>
开发者没有使用\'@Component\'、\'@ComponentV2\'或\'@CustomDialog\'装饰子组件导致报错。

**处理步骤**<br>
需要使用\'@Component\'、\'@ComponentV2\'或\'@CustomDialog\'装饰器来装饰子组件后再调用。

## 10905125 成员属性方法装饰器校验异常
**错误信息**<br>
The member property or method can not be decorated by multiple decorators.

**错误描述**<br>
成员属性或方法不能被多个装饰器装饰。

**可能原因**<br>
开发者使用了多个装饰器同时装饰同一个成员属性或方法导致报错。

**处理步骤**<br>
保留合适的装饰器，去掉多余的装饰器即可。

## 10905235 组件命名校验异常
**错误信息**<br>
The module name \'xxx\' can not be the same as the inner component name.

**错误描述**<br>
自定义组件不能使用内部组件的名称。

**可能原因**<br>
开发者给自定义组件命名与内部组件名称重复导致报错。

**处理步骤**<br>
修改自定义组件名称为不同于内部组件名称的合法组件名。

## 10905236 组件使用校验异常
**错误信息**<br>
UI component \'xxx\' cannot be used in this place.

**错误描述**<br>
ArkUI系统组件使用限制。

**可能原因**<br>
开发者未在@Builder方法或build()方法中使用组件不符合使用限制导致报错。

**处理步骤**<br>
在@Builder方法、build()方法或者页面间转场方法中使用ArkUI系统组件。

## 10905237 组件命名校验异常
**错误信息**<br>
The struct name cannot contain reserved tag name: \'xxx\'.

**错误描述**<br>
自定义组件名字与已有组件重复。

**可能原因**<br>
开发者给自定义组件命名与已有组件名称重复导致报错。

**处理步骤**<br>
修改自定义组件名称为不同于已有组件名称的合法组件名。

## 10905127 @Styles声明校验异常
**错误信息**<br>
Should not add return type to the function that is decorated by Styles.

**错误描述**<br>
@Styles装饰的函数不能返回函数类型。

**可能原因**<br>
开发者声明@Styles装饰的函数返回值为函数类型导致报错。

**处理步骤**<br>
避免声明@Styles装饰的函数返回值为函数类型。

## 10905238 struct声明校验异常
**错误信息**<br>
A struct declaration without the \'default\' modifier must have a name.

**错误描述**<br>
没有default修饰符的struct声明必须有一个name。

**可能原因**<br>
开发者声明struct时没有加入default修饰符也没有命名导致报错。

**处理步骤**<br>
为struct正确命名即可。

## 10905128 @Extend声明校验异常
**错误信息**<br>
Should not add return type to the function that is decorated by Extend.

**错误描述**<br>
@Extend装饰的函数不能返回函数类型。

**可能原因**<br>
开发者声明@Extend装饰的函数返回值为函数类型导致报错。

**处理步骤**<br>
避免声明@Extend装饰的函数返回值为函数类型。

## 10905129 @Computed装饰器与!!同时使用校验异常
**错误信息**<br>
A property decorated by \'xxx\' cannot be used with two-bind syntax.

**错误描述**<br>
@Computed装饰器与!!一起使用错误。

**可能原因**<br>
开发者同时使用@Computed装饰器与!!导致报错。

**处理步骤**<br>
避免同时使用@Computed装饰器与!!。

## 10905130 @Computed装饰set方法使用校验异常
**错误信息**<br>
A property decorated by \'xxx\' cannot define a set method.

**错误描述**<br>
@Computed只能装饰get方法校验。

**可能原因**<br>
开发者使用@Computed装饰器装饰了set方法导致报错。

**处理步骤**<br>
按照@Computed规范正确使用，只能装饰get方法。

## 10905358 !!语法校验异常
**错误信息**<br>
When the two-way binding syntax is used, do not assign a value to \'xxx\' variable \'yyy\' because the framework generates the default assignment.

**错误描述**<br>
当使用双向绑定语法!!时不需要给@Event对应函数赋值因为UI框架会自动生成默认值。

**可能原因**<br>
开发者在使用双向绑定语法!!时还给对应的@Event方法传值导致报错。 

**处理步骤**<br>
当使用!!双向绑定语法给子组件传递参数时，给对应的@Event方法传参会编译报错，不要给对应的\$开头的@Event方法传参。

## 10905241 @Reusable和@ReusableV2混用校验异常
**错误信息**<br>
The \'@Reusable\' and \'@ReusableV2\' decorators cannot be applied simultaneously.

**错误描述**<br>
@Reusable不能与@ReusableV2一起装饰组件。

**可能原因**<br>
开发者同时使用@Reusable和@ReusableV2一起装饰组件导致报错。

**处理步骤**<br>
避免同时使用@Reusable和@ReusableV2一起装饰组件。

## 10905242 @ReusableV2使用校验异常
**错误信息**<br>
\'@ReusableV2\' is only applicable to custom components decorated by \'@ComponentV2\'.

**错误描述**<br>
@ReusableV2不能装饰非@ComponentV2装饰的自定义组件。

**可能原因**<br>
开发者使用@ReusableV2装饰@Component等非@ComponentV2装饰器装饰的自定义组件导致报错。

**处理步骤**<br>
用@ReusableV2装饰@ComponentV2装饰的自定义组件即可。

## 10905244 @ReusableV2使用校验异常
**错误信息**<br>
A custom component decorated with \'@Component\' cannot contain child components decorated with \'@ReusableV2\'.

**错误描述**<br>
@Component组件调用的子组件不能是@ReusableV2装饰的组件。

**可能原因**<br>
开发者在@Component装饰的组件中调用了@ReusableV2装饰的组件作为子组件导致报错。

**处理步骤**<br>
避免在V1装饰器@Component装饰的组件中调用@ReusableV2装饰的组件。

## 10905245 @ReusableV2使用校验异常
**错误信息**<br>
A custom component decorated with \'@Reusable\' cannot contain any child components decorated with \'@ReusableV2\'.

**错误描述**<br>
@Reusable组件不能包含@ReusableV2装饰的子组件。

**可能原因**<br>
开发者在@Reusable装饰的组件中调用了@ReusableV2装饰的组件作为子组件导致报错。

**处理步骤**<br>
避免在V1装饰器@Reusable装饰的组件中调用@ReusableV2装饰的组件。

## 10905246 @Reusable使用校验异常
**错误信息**<br>
A custom component decorated with \'@ReusableV2\' cannot contain child components decorated with \'@Reusable\'.

**错误描述**<br>
@ReusableV2组件不能包含@Reusable装饰的子组件。

**可能原因**<br>
开发者在@ReusableV2装饰的组件中调用了@Reusable装饰的组件作为子组件导致报错。

**处理步骤**<br>
避免在V2装饰器@ReusableV2装饰的组件中调用@Reusable装饰的组件。

## 10905359 组件构造初始化校验异常
**错误信息**<br>
Property \'xxx\' must be initialized through the component constructor.

**错误描述**<br>
必须父组件构造初始化校验。

**可能原因**<br>
开发者使用@Require装饰器装饰的变量没有在父组件构造时初始化导致报错。

**处理步骤**<br>
@Require装饰器装饰的变量需要在父组件构造时进行初始化。

## 10905247 @ReusableV2使用校验异常
**错误信息**<br>
The template attribute of the Repeat component cannot contain any custom component decorated with \'@ReusableV2\'.

**错误描述**<br>
Repeat.template不能包含@ReusableV2装饰的自定义组件。

**可能原因**<br>
开发者在使用Repeat时template属性中包含了@ReusableV2装饰的自定义组件导致报错。

**处理步骤**<br>
根据错误描述修改，删除template属性中@ReusableV2装饰的组件即可。

## 10905248 reuse属性使用校验异常
**错误信息**<br>
The reuse attribute is only applicable to custom components decorated with both \'@ComponentV2\' and \'@ReusableV2\'.

**错误描述**<br>
reuse只能用于@ReusableV2装饰的@ComponentV2自定义组件。

**可能原因**<br>
开发者未明确reuse的使用场景，在@ReusableV2装饰的@ComponentV2自定义组件之外使用该属性导致报错。

**处理步骤**<br>
根据错误描述修改，在正确场景下使用reuse属性功能。

## 10905249 reuseId属性使用校验异常
**错误信息**<br>
The reuseId attribute is not applicable to custom components decorated with both \'@ComponentV2\' and \'@ReusableV2\'.

**错误描述**<br>
reuseId属性不能用于@ReusableV2装饰的@ComponentV2自定义组件。

**可能原因**<br>
开发者在@ReusableV2装饰的@ComponentV2自定义组件下使用reuseId属性导致报错。

**处理步骤**<br>
根据错误描述修改，在正确场景下使用reuseId属性功能。