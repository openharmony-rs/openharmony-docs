# SlideRange

定义SlideRange中使用的回调类型。
> **说明：**  
>  
> - 当前仅当min<=from<=to<=max时该接口生效(min和max不依赖于其设置的值，而取决于其实际生效的值)。  
>  
> - 可只设置from或者to，也可以同时设置from和to。  
>  
> - 当接口生效且设置的from处于紧邻的step整数倍的值之间，则from实际取左区间step整数倍的那个值或者min作为修正后的值。  
>  
> - 当接口生效且设置的to处于紧邻的step整数倍的值之间，则to实际取右区间step整数倍的那个值或者MAX作为修正后的值。  
>  
> - 在from和to取修正值后， 当value是undefined或null时，其取值与from一致; 当value是数值型且value &lt;= from，则取from; 当value &gt; to，则取to。

**起始版本：** 12

<!--Device-unnamed-declare interface SlideRange--><!--Device-unnamed-declare interface SlideRange-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## from

```TypeScript
from?: number
```

设置有效滑动区间的开始。

**类型：** number

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-SlideRange-from?: number--><!--Device-SlideRange-from?: number-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## to

```TypeScript
to?: number
```

设置有效滑动区间的结束。

**类型：** number

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-SlideRange-to?: number--><!--Device-SlideRange-to?: number-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

