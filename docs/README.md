# 这是啥?

这是一款扩展了 layui 功能的插件, 能让你的输入框可以变成一个 `图标选择器`, 这意味着你现在可以很轻松的给某个东西附加一格图标的能力了, 譬如: 管理后台某个功能模块加个图标, 嗯! 就是这样!

![场景配图](./imgs/example.png)

---

# 怎么使用?

1. 下载源代码, 通常情况下, 你可以在 [Releases](https://gitee.com/layui-exts/icon-selected/releases) 这里找到所有已经发布的版本.
2. 将下载好的文件, 通常是压缩包, 解压到你项目的扩展目录里去, 譬如: `libs/layui_exts`
3. 确认项目的 `layui.config` 和 `layui.base` 配置是否正确, 可参考 [示例文件](./example.html)
4. 使用 `layui.use` 来引入扩展! 可参考 [示例文件](./example.html)

---

# 代码片段

> 仅供学习参考, 请勿无脑复制粘贴照搬照抄.

## 配置扩展

```javascript
layui
    .config({
        base: "./libs/layui_exts/",
    })
    .extend({
        iconSelected: "iconSelected/js/index",
    });
```

## 引入扩展并使用

### HTML 部分

```html
<div class="layui-form">
    <div class="layui-form-item">
        <div class="layui-form-label">选择图标</div>
        <div class="layui-input-block">
            <!-- 给输入框附加一个ID -->
            <input type="text" name="icon" value="layui-icon layui-icon-username" placeholder="请选择" maxlength="16" autocomplete="off" class="layui-input" id="icon" />
        </div>
    </div>
</div>
```

### Javascript 部分

```javascript
// 引入扩展
layui.use(["iconSelected"], function () {
    var iconSelected = layui.iconSelected;

    iconSelected.init("#icon");
});
```

---

# 可配置项

!> 本扩展骑士配置项很少, 几乎都是写死的设定一般不需要修改. 当然我会告诉你有哪些配置项!

## 使用配置项

```javascript
layui.use(["iconSelected"], function () {
    var iconSelected = layui.iconSelected;

    // 第二个参数用于接收配置项
    iconSelected.init("#icon", {});
});
```

## 可用配置项

-   width

    -   弹窗的宽度
    -   默认: 300

-   offsetX

    -   弹窗 X 轴偏移量
    -   默认: 30
    -   不建议修改

-   offsetY

    -   弹窗 Y 轴偏移量
    -   默认: 10
    -   不建议修改

-   icons

    -   图标列表
    -   默认: layui 默认图标
    -   参考: [https://www.layui.com/doc/element/icon.html](https://www.layui.com/doc/element/icon.html)

-   placeholder

    -   输入框提示文字
    -   默认: 请选择

-   value

    -   当前选中值
    -   默认: 输入框的值
    -   注意! 理论上该值一定是字体图标的样式名, 如: `layui-icon layui-icon-username`

-   zIndex
    -   zIndex 值
    -   默认: 999
    -   别告诉我你不知道 zIndex 啥意思!

---

# 事件

本扩展就一个事件, 同样是写在 `event` 下面, 该事件为 `select` 事件, 即选中某个图标时触发, 参考代码如下!

```javascript
layui.use(["numberInput", "layer", "iconSelected", "form"], function () {
    var iconSelected = layui.iconSelected;

    iconSelected.init("#icon", {
        event: {
            select(event, data) {
                console.log("选中的图标数据", { event, data });
            },
        },
    });
});
```

---

# API

!> 如果你想使用 API 服务, 那么请确保扩展版本高于等于 `v1.0.1.20210609`, API 的调用方式为: `iconSelected.xxx`, 譬如: `iconSelected.icons` 即可获取默认图标列表

!> 添加图标操作都是支持链式写法的, 即 `iconSelected.addIcon().addIcon()......init()` 这样, 但是请注意! 因为渲染顺序问题, 如果要添加图标确保 初始化 API 在最后面!

## init

-   初始化
-   这就没啥好说的了
-   如果需要添加图标请保证该 API 在最后面调用!

## icons

-   取出默认的图标数据
-   即 layui 官方图标清单

## addIcon(name,classList)

-   添加一个图标(在尾部)
-   参数分别为:
    -   显示的名字
    -   图标的样式

## addIcons(icons)

-   批量添加图标(在尾部)
-   参数为数组
-   你需要自行维护数组内部的键值对, 确保键值对符合规范格式
-   即: name=名字, classList=图标

## addIconBefore(name,classList)

-   添加一个图标(在头部)
-   其他的就跟 addIcon 一样了

## addIconsBefore(icons)

-   批量添加图标(在头部)
-   其它的就跟 addIcons 一样了

# 支持作者

最简单的粗暴的方式就是直接使用 **钞能力**, 当然这是您自愿的! **点击可直接查看大图**

## 钞能力通道

<img src="./imgs/zhifubao.jpg" height="200px" title="支付宝">
<img src="./imgs/weixin.png" height="200px" title="微信">
<img src="./imgs/qq.png" height="200px" title="QQ">

当然, 如果客观条件不允许, 主观上不愿意, 也无伤大雅嘛! 谁的钱都是自己幸苦挣来的. 除了使用 **钞能力**, 你还可以通过以下方式支持作者!

## 打工人通道

1. 给项目点个 Star, 让更多的小伙伴知道这个扩展!
2. 积极测试, 反馈 BUG, 如果发现代码中有不合理的地方积极反馈!
3. 加入粉丝群, 看看有多少志同道合的小伙伴! <a target="_blank" href="https://qm.qq.com/cgi-bin/qm/qr?k=SykXsUtejaedB0TSs6a0_S-SseGByzdU&jump_from=webapi"><img border="0" src="//pub.idqqimg.com/wpa/images/group.png" alt="码云 Layui Exts 交流群" title="码云 Layui Exts 交流群"></a>

```

```
