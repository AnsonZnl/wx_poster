# wx_poster

> 用于海报生成，希望能帮助那些不经常开发小程序开发者。

## 问答

**为什么没有二维码功能及一维码。**

> 这个问题在于我们这个是合成海报功能，不是生成二维码和一维码工具。完全可以使用第三方的生成二维码或者一维码。

**为什么有小程序码这个方法了（）**

> 我们工具在于帮助那么接触少的小程序开发者少走弯路（希望大家读读源码，大佬请绕路）。原因在于后台传给我们的无法做圆形的大小，那么我这里进行帮你绘制好了。

**为什么不直接使用 canvas画布画好的了，还要设置showPoster为true了？**

> 最终合成图片的好处：

1. 如果你是想设置rpx单位的话，那么可以拿着图片，将 view标签设置背景图，这样可以进行缩放比例
2. 如果你拿着图片，在保存那块，能够快速进行保存下来。
3. 如果你设置长按进行保存，也是能做到的。


## 使用步骤：

### 第一步：下载或者克隆

> （下载方式，不懂自行百度），下载好后，找到 components 目录中 wx_poster 文件夹，进行拷贝放入到自己项目中。比如我放入在 components 文件夹下面。

### 第二步：引入组件

> 找到自己想要引入的页面 .json文件。然后将 usingComponents 里面进行添加上 wx_poster 。比如如下（注意组件路径）：

```json
{
  "usingComponents": {
    "wx_poster": "/components/wx_poster/wx_poster"
  }
}
```

### 第三步：在 .wxss 文件中使用

```html
<wx_poster id="wx_poster" ></wx_poster>
```

### 第四步：在 .js 中使用

> 此处是重点啊。咱们必须在 onReady 中调用初始化

```js
// pages/demo/index.js
Page({
    /**
     * 页面的初始数据
     */
    data: {
    },
    /**
     * 生命周期函数--监听页面加载
     */
    onLoad: function (options) {
    },

    /**
     * 生命周期函数--监听页面初次渲染完成
     */
    onReady: function () {
        var wx_poster = this.selectComponent('#wx_poster')
        wx_poster.inits(function (){ // 初始化完成
            console.log('初始化完成')
            wx_poster.addImg('https://www.baidu.com/img/baidu_jgylogo3.gif',(img) => {
                console.log(img)
            })
        })
    },

    /**
     * 生命周期函数--监听页面显示
     */
})
```


