# 沉浸光感功耗优化
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @H-xinwei-->
<!--Designer: @zhanghaibo0-->
<!--Tester: @lxl007-->
<!--Adviser: @Brilliantry_Rui-->

沉浸式系统材质由材质滤镜、折射、高光、阴影等多层效果叠加而成，渲染时需要消耗GPU（Graphics Processing Unit，图形处理器）资源，不合理的使用会显著增加功耗。

总体优化原则：沉浸式系统材质作为一种"稀缺"视觉资源使用——控制面积与层数、不应固定显示在视频动图动画等变化的内容之上。遵循以下功耗优化建议，即可在获得高品质观感的同时将性能与功耗影响降到最低。

## 控制材质使用面积

沉浸式系统材质影响的区域越大，需要处理的像素越多，功耗越高。应避免在单个超大尺寸区域上使用沉浸式系统材质，也应避免在大量小区域上重复使用沉浸式系统材质；推荐在顶部标题栏和底部tabs区域中少量使用，优先将沉浸式系统材质限定在需要凸显的局部区域中。

```ts
// 正例：仅在需要凸显的局部容器上使用沉浸式系统材质
Stack() {
  // ...整页内容
  Column() {
    Text('卡片')
  }
  .width(328)
  .height(120)
  .borderRadius(24)
  .systemMaterial(new uiMaterial.ImmersiveMaterial({
    style: uiMaterial.ImmersiveStyle.REGULAR,
  }))
}

// 反例：整页背景均设置沉浸式系统材质，区域过大
Column() {
  // ...整页内容
}
.width('100%')
.height('100%')
.systemMaterial(new uiMaterial.ImmersiveMaterial({
  style: uiMaterial.ImmersiveStyle.REGULAR,
}))
```

## 减少材质嵌套与层叠

材质层叠会导致效果被重复计算，既增加功耗，视觉上又相互干扰。同一子树中只需在最外层设置一次沉浸式系统材质，内层节点不应再设置。

```ts
// 正例：仅在最外层设置一次沉浸式系统材质
Column() {
  Column() {
    Text('内容')
  }
}
.systemMaterial(new uiMaterial.ImmersiveMaterial({
  style: uiMaterial.ImmersiveStyle.REGULAR,
}))

// 反例：外层和内层都设置了沉浸式系统材质，相互嵌套
Column() {
  Column() {
    Text('内容')
  }
  .systemMaterial(new uiMaterial.ImmersiveMaterial({
    style: uiMaterial.ImmersiveStyle.THIN,
  }))
}
.systemMaterial(new uiMaterial.ImmersiveMaterial({
  style: uiMaterial.ImmersiveStyle.REGULAR,
}))
```

## 避免与模糊效果叠加

沉浸式系统材质自带的材质滤镜（materialFilter）已包含背景模糊效果，再叠加backgroundBlurStyle、backgroundEffect等模糊属性属于重复处理，会增加额外的功耗开销。

```ts
// 正例：仅使用沉浸式系统材质，由其提供模糊效果
Column() {
  Text('内容')
}
.systemMaterial(new uiMaterial.ImmersiveMaterial({
  style: uiMaterial.ImmersiveStyle.THICK,
}))

// 反例：同时设置沉浸式系统材质与背景模糊，重复处理
Column() {
  Text('内容')
}
.systemMaterial(new uiMaterial.ImmersiveMaterial({
  style: uiMaterial.ImmersiveStyle.THICK,
}))
.backgroundBlurStyle(BlurStyle.COMPONENT_THICK)
```

## 控制弹窗尺寸

高算力设备上，沉浸光感强度设置为强和均衡，Dialog、Menu组件默认附带形变、流光等沉浸式空间动效（参见[沉浸式空间动效](arkts-immersive-light-sense-overview.md#沉浸式空间动效)相关说明）。弹窗面积越大，动效的绘制开销越高，应避免接近全屏的超大面积Dialog或Menu，保持弹窗尺寸在合理范围。

## 避免在动态内容上方使用沉浸式系统材质

沉浸式系统材质的折射、模糊效果需要实时采样其背后的内容。当背景是视频、动画图片等持续变化的内容时，材质层需要重新采样与计算，功耗显著上升。应避免在视频、动图等动态内容上方叠加沉浸式系统材质。

```ts
// 反例：在视频上方叠加沉浸式系统材质，视频在播放时沉浸式系统材质会重新绘制
Stack() {
  Column() {
    // 视频
  }
    .width('100%')
    .height('100%')
  Column() {
    Text('浮层')
  }
  .systemMaterial(new uiMaterial.ImmersiveMaterial({
    style: uiMaterial.ImmersiveStyle.THIN,
  }))
}
```

## 减少对材质区域的动画

对设置了沉浸式系统材质的区域持续做属性动画（如反复改变尺寸、位置、透明度等），会让材质效果在每一帧重新计算，长时间运行会持续占用GPU。材质区域应尽量保持稳定；如确需动画，应缩短时长并避免无限循环。

```ts
// 正例：材质区域保持稳定，不对其做长时间动画
// 如确需动画，缩短时长且不使用无限循环

// 反例：对材质区域做长时间、无限循环的尺寸动画
animateTo({ duration: 3000, iterations: -1 }, () => {
  this.boxWidth = 400
})
```

## 控制自动反色的作用范围

自动反色（colorInvert）会对材质子树中通过资源接口设置的颜色逐个计算反色。子树越大、参与反色的组件越多，计算量越高。应控制反色的作用范围，避免在包含大量文本、图标的大范围内整体开启反色。

```ts
// 正例：缩小反色范围，仅对需要保证可读性的局部区域开启
Column() {
  // ...多数内容不开启反色
  Column() {
    Text('标题').fontColor($r('app.color.text'))
  }
  .systemMaterial(new uiMaterial.ImmersiveMaterial({
    style: uiMaterial.ImmersiveStyle.THIN,
    colorInvert: true,
  }))
}

// 反例：在包含大量子项的列表外层开启反色，所有子项颜色都参与计算
Column() {
  ForEach(this.largeList, (item: string) => {
    Text(item).fontColor($r('app.color.text'))
  })
}
.systemMaterial(new uiMaterial.ImmersiveMaterial({
  style: uiMaterial.ImmersiveStyle.THIN,
  colorInvert: true,
}))
```

## 避免在滚动列表项中逐项使用沉浸式系统材质

当给每个ListItem都设置沉浸式系统材质时，滚动过程中每个材质项背后的内容都在持续变化，沉浸式系统材质会重新绘制造成开销。因此不建议在每个ListItem上设置沉浸式系统材质；如需列表整体具备材质质感，建议在外层容器上设置沉浸式系统材质，更为稳定。

```ts
// 正例：不在逐项上设置沉浸式系统材质，滚动时无额外材质采样开销
List() {
  ForEach(this.largeList, (item: string) => {
    ListItem() {
      Text(item)
    }
  })
}

// 反例：每个ListItem都设置沉浸式系统材质，滚动时逐帧重算
List() {
  ForEach(this.largeList, (item: string) => {
    ListItem() {
      Text(item)
    }
    .systemMaterial(new uiMaterial.ImmersiveMaterial({
      style: uiMaterial.ImmersiveStyle.THIN,
    }))
  })
}
```

## 保持材质参数与材质区域稳定

频繁修改style、materialColor等材质参数，或在材质区域内频繁增删子节点，都会触发材质效果重新计算。建议一次性确定材质参数并保持稳定，材质区域内部的子树结构也应尽量稳定。

```ts
// 正例：材质参数一次性设置并保持稳定
new uiMaterial.ImmersiveMaterial({
  style: uiMaterial.ImmersiveStyle.THIN,
  materialColor: '#80FF0000',
})

// 反例：在定时器中频繁修改材质颜色，反复触发材质重算
setInterval(() => {
  this.materialColor = this.nextColor()
}, 100)
```

## 避免重复叠加阴影

沉浸式系统材质默认已通过applyShadow提供阴影，再额外设置通用shadow属性既与材质效果冲突，又造成重复绘制开销。如需自定义阴影，应将applyShadow置为false后再使用shadow，避免两套效果同时生效。

```ts
// 正例：如需自定义阴影，先关闭沉浸式系统材质自带阴影（applyShadow:false）
Column() {
  Text('内容')
}
.systemMaterial(new uiMaterial.ImmersiveMaterial({
  style: uiMaterial.ImmersiveStyle.REGULAR,
  applyShadow: false,
}))
.shadow({ radius: 20, color: Color.Black })

// 反例：沉浸式系统材质（默认applyShadow为true）与自定义阴影同时存在，重复且冲突
Column() {
  Text('内容')
}
.systemMaterial(new uiMaterial.ImmersiveMaterial({
  style: uiMaterial.ImmersiveStyle.REGULAR,
}))
.shadow({ radius: 20, color: Color.Black })
```
