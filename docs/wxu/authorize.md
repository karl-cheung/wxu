<a name="authorize"></a>

# Authorize(options)
授权流程

参数 | 说明 | 类型 | 可选值 | 默认值
--- | --- | --- | --- | ---
scope | 需要获取权限的 scope | Array |
success | 授权完成的回调函数 | Function


## 说明
Authorize 方法在 onShow 生命周期函数中执行。success 回调函数在授权列表全部完成后触发且默认只触发一次，即授权列表全部完成后再次触发 onShow 生命周期函数，success 回调函数将不再执行。 
 
若希望总是执行，请在 onLoad 生命周期函数中执行 `Authorize()`。


**Example**

```js
// 请注意无 AppID 关联下，此页面功能是受限的
import { Authorize } from '../../wxu/wxu'

Page({
  onLoad() {
    // Authorize()
  },
  onShow() {
    Authorize({
      scope: ['scope.userInfo', 'scope.userLocation'],
      success: () => {
        this.init()
      }
    })
  },
  init() {
    this.setData({
      success: '授权完成，执行 init 函数。'
    })
  }
})
```