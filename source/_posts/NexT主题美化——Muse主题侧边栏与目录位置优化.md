---
title: NexT主题美化——Muse主题侧边栏与目录位置优化
date: 2019-12-13 08:23:14
top: 1
tags:
- Hexo
- NexT
- 主题优化
categories: 
- code
---

### NexT 主题优化——Muse

**Hexo version: v4.1.0**

**NexT version: v5.1.4**

> Hexo博客支持很多主题风格，其中[NexT](https://github.com/theme-next/hexo-theme-next)主题是Github上Star最多的主题，其一直在更新维护，支持非常多的外部插件和功能选项。我目前使用的是Next6.0版本，下面我会介绍基于NexT主题中Muse主题的界面美化手法。

### 前言

**未优化**

![Muse](/img/Muse.png)

可以看到未优化的Muse主题的侧边栏默认在右边，而且_config.yml中`sidebar position`字段是无法修改Muse主题的侧边栏位置的

`# Sidebar Display, available value (only for Muse | Mist):`

同时博客标题和目录的布局都是相对布局，只要鼠标一滚动就会随着博文消失（讲道理这绝对是NexT开发者的锅），使用体验比较差，因此对其进行优化乃是大势所趋。话不多说，咱先开始。

<!-- more -->

### 优化

#### 侧边栏

侧边栏的位置其实各取所需就好，喜欢放在右边的话可以直接跳过这一段。

##### 修改motion.js

首先调整侧边栏的动画效果，让他从左边伸出来

打开 `<your blog>/theme/next/source/js/src` ，找到 `motion.js` 并打开

`Ctrl + F` 查找 `paddingRight` 将其改为 `paddingLeft`

```javascript
$(document)
        .on('sidebar.isShowing', function () {
          NexT.utils.isDesktop() && $('body').velocity('stop').velocity(
            {paddingLeft: SIDEBAR_WIDTH},			
            SIDEBAR_DISPLAY_DURATION
          );
        })
        .on('sidebar.isHiding', function () {
   		});
```

```javascript
hideSidebar: function () {
      NexT.utils.isDesktop() && $('body').velocity('stop').velocity({paddingLeft: 0});
      this.sidebarEl.find('.motion-element').velocity('stop').css('display', 'none');
      this.sidebarEl.velocity('stop').velocity({width: 0}, {display: 'none'});

      sidebarToggleLines.init();

      this.sidebarEl.removeClass('sidebar-active');
      this.sidebarEl.trigger('sidebar.isHiding');

      // Prevent adding TOC to Overview if Overview was selected when close & open sidebar.
      if (!!$('.post-toc-wrap')) {
        if ($('.site-overview-wrap').css('display') === 'block') {
          $('.post-toc-wrap').removeClass('motion-element');
        } else {
          $('.post-toc-wrap').addClass('motion-element');
        }
      }
    }
```

##### 调整CSS样式表

找到 `<your blog>/theme/next/source/css/_common/components/sidebar/sidebar-toggle.styl`

修改类 `.sidebar-toggle`

```css
.sidebar-toggle {
  position: fixed;
  left: 10%;
  bottom: 45px;
  width: 14px;
  height: 14px;
  padding: 5px;
  background: $black-deep;
  line-height: 0;
  z-index: $zindex-5;
  cursor: pointer;
  -webkit-transform: translateZ(0);

  +tablet() {
    fixbutton() if hexo-config('sidebar.onmobile');
    hide() if not hexo-config('sidebar.onmobile');
  }
  +mobile() {
    fixbutton() if hexo-config('sidebar.onmobile');
    hide() if not hexo-config('sidebar.onmobile');
  }
}
```

CSS样式建议根据自己实际情况修改

不懂CSS的话只需要将 `right` 字段删除，然后添加 `letf: xxpx;` 或者`left: xx%;`，分号一定要加

`xx`是数字，`px`是像素的意思，可以直观体现出距离位置

##### 修改箭头动画

还是刚才的`motion.js`文件

```javascript
var sidebarToggleLine1st = new SidebarToggleLine({
  el: '.sidebar-toggle-line-first',
  status: {
    arrow: {width: '60%', rotateZ: '45deg', top: '2px', left: '50%'},
    close: {width: '100%', rotateZ: '-45deg', top: '5px'}
  }
});
var sidebarToggleLine2nd = new SidebarToggleLine({
  el: '.sidebar-toggle-line-middle',
  status: {
    arrow: {width: '90%'},
    close: {opacity: 0}
  }
});
var sidebarToggleLine3rd = new SidebarToggleLine({
  el: '.sidebar-toggle-line-last',
  status: {
    arrow: {width: '60%', rotateZ: '-45deg', top: '-2px', left: '50%'},
    close: {width: '100%', rotateZ: '45deg', top: '-5px'}
  }
});
```

**侧边栏的工作就大功告成了**



#### 目录

刚开始我是打算把目录放在界面上端设置一个绝对位置让他停留在界面上的，但是由于要搭配背景的关系最终决定放在右面

更改目录位置只需要修改一个文件

`<your blog>/theme/next/source/css/_schemes/Muse/sidebar/_menu.styl`

```css
.site-nav {
  +mobile() {
    position: absolute;
    left: 0;
    top: 52px;
    margin: 0;
    width: 100%;
    padding: 0;
    background: white;
    border-bottom: 1px solid $gray-lighter;
    z-index: $zindex-5;
  }
  /*以下为新增内容*/
  position: fixed;
  right: 10%;
  top: 15%;
  margin: 0;
  padding: 0;
  border-left: 1px solid $gray-lighter;
  z-index: $zindex-5;
}

.menu {
  +mobile() { text-align: left; }
  /*以下为新增内容*/
  display: flex;
  flex-direction: column;
}
```



#### 社交链接

默认的社交链接是 `inhert-block`行内块元素，因此它默认先填满一行再换行显示，观感不是太好，我们也可以靠修改css使他达到换行的效果

打开 `<your blog>/theme/next/source/css/_common/components/sidebar-author-links.styl`

修改 `.links-of-author`类

```css
.links-of-author {
  margin-top: 20px;
  margin-left: 25%;
  text-align: left;
  padding: 0px 0px 0px 0px;
}
```

这样就大功告成了

#### 成品

![Muse](/img/Muse_u.png)

