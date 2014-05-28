<!---
    Licensed to the Apache Software Foundation (ASF) under one
    or more contributor license agreements.  See the NOTICE file
    distributed with this work for additional information
    regarding copyright ownership.  The ASF licenses this file
    to you under the Apache License, Version 2.0 (the
    "License"); you may not use this file except in compliance
    with the License.  You may obtain a copy of the License at

      http://www.apache.org/licenses/LICENSE-2.0

    Unless required by applicable law or agreed to in writing,
    software distributed under the License is distributed on an
    "AS IS" BASIS, WITHOUT WARRANTIES OR CONDITIONS OF ANY
    KIND, either express or implied.  See the License for the
    specific language governing permissions and limitations
    under the License.
-->

# org.apache.cordova.inappbrowser

这个插件提供了一个 web 浏览器视图，显示时调用 `window.open()` ，或当打开链接形成的作为`<a target="_blank">`.

    var ref = window.open('http://apache.org', '_blank', 'location=yes');
    

**NOTE**： InAppBrowser 窗口的行为表现像一个标准的 web 浏览器，并且无法访问Cordova APIs。

## 安装

    cordova plugin add org.apache.cordova.inappbrowser
    

### 火狐浏览器操作系统

在[清单文件][1]中所述创建**www/manifest.webapp** 。添加相关权限。

 [1]: https://developer.mozilla.org/en-US/Apps/Developing/Manifest

    "permissions": {
        "browser": {}
    }
    

## window.open

在一个新的中打开 URL `InAppBrowser` 实例，当前的浏览器实例或系统浏览器。

    var ref = window.open (url、 目标、 选项） ；
    

*   **ref**： 参考 `InAppBrowser` 窗口。*(InAppBrowser)*

*   **url**： 要加载*(String)*的 URL。如果 URL 包含 Unicode 字符则在此调用 `encodeURI()` 。

*   **target**：在其中加载的 URL的目标，默认值为 `_self`的可选参数 。*(String)*
    
    *   `_self`： 如果 URL 是在白名单中则在Cordova web 视图中打开，否则它在`InAppBrowser`中打开.
    *   `_blank`： 在`InAppBrowser`中打开.
    *   `_system`： 在该系统的 web 浏览器中打开。

*   **options**： 选项为 `InAppBrowser` 。可选，默认值为： `location=yes` 。*(String)*
    
    `options`字符串必须不包含任何空白的空间，并且每个功能的名称/值对必须用逗号分隔。 功能名称区分大小写。 所有平台都支持下面的值：
    
    *   **location**： 设置为 `yes` 或 `no` ，打开 `InAppBrowser` 的位置栏开或关。
    
    仅仅Android 系统支持一下属性：
    
    *   **closebuttoncaption**: 设置为一个字符串，以用作**Done**按钮的标题。
    *   **hidden**： 将设置为 `yes` ，创建浏览器和加载页面，但不是显示它。 加载完成时，将触发 loadstop 事件。 省略或设置为 `no` （默认值），浏览器打开并且加载正常。
    *   **clearcache**： 将设置为 `yes` ，打开新窗口之前浏览器的 cookie 清除缓存
    *   **clearsessioncache**： 将设置为 `yes` ，打开新窗口之前清除会话cookie 缓存
    
    如下只有 iOS支持：
    
    *   **closebuttoncaption**: 设置为一个字符串，以用作**Donw**按钮的标题。请注意您需要你自己对此值进行本地化。
    *   **disallowoverscroll**： 将设置为 `yes` 或 `no` （默认值是 `no` ）。打开/关闭的 UIWebViewBounce 属性。
    *   **隐藏**： 将设置为 `yes` ，创建浏览器和加载页面，但不是显示它。 加载完成时，将触发 loadstop 事件。 省略或设置为 `no` （默认值），有的浏览器打开，然后以正常方式加载。
    *   **clearcache**： 将设置为 `yes` 有浏览器的 cookie 清除缓存之前打开新窗口
    *   **clearsessioncache**： 将设置为 `yes` 有会话 cookie 缓存清除之前打开新窗口
    *   **工具栏**： 设置为 `yes` 或 `no` ，为 InAppBrowser （默认为打开或关闭工具栏`yes`)
    *   **enableViewportScale**： 将设置为 `yes` 或 `no` ，防止通过 meta 标记 （默认为缩放的视区`no`).
    *   **mediaPlaybackRequiresUserAction**： 将设置为 `yes` 或 `no` ，防止 HTML5 音频或视频从 autoplaying （默认为`no`).
    *   **allowInlineMediaPlayback**： 将设置为 `yes` 或 `no` ，让线在 HTML5 播放媒体，在浏览器窗口中，而不是特定于设备播放界面内显示。 HTML 的 `video` 元素还必须包括 `webkit-playsinline` 属性 （默认为`no`)
    *   **keyboardDisplayRequiresUserAction**： 将设置为 `yes` 或 `no` 时，要打开键盘窗体元素接收焦点通过 JavaScript 的 `focus()` 调用 （默认为`yes`).
    *   **suppressesIncrementalRendering**： 将设置为 `yes` 或 `no` 等待，直到所有新查看的内容正在呈现 （默认为前收到`no`).
    *   **presentationstyle**： 将设置为 `pagesheet` ， `formsheet` 或 `fullscreen` 来设置[演示文稿样式][2](默认为`fullscreen`).
    *   **transitionstyle**： 将设置为 `fliphorizontal` ， `crossdissolve` 或 `coververtical` 设置[过渡样式][3](默认为`coververtical`).
    *   **toolbarposition**： 将设置为 `top` 或 `bottom` （默认值是 `bottom` ）。使工具栏，则在顶部或底部的窗口。

 [2]: http://developer.apple.com/library/ios/documentation/UIKit/Reference/UIViewController_Class/Reference/Reference.html#//apple_ref/occ/instp/UIViewController/modalPresentationStyle
 [3]: http://developer.apple.com/library/ios/#documentation/UIKit/Reference/UIViewController_Class/Reference/Reference.html#//apple_ref/occ/instp/UIViewController/modalTransitionStyle

### 支持的平台

*   亚马逊火 OS
*   Android 系统
*   黑莓 10
*   iOS
*   Windows Phone 7 和 8

### 示例

    var ref = window.open('http://apache.org', '_blank', 'location=yes');
    var ref2 = window.open(encodeURI('http://ja.m.wikipedia.org/wiki/ハングル'), '_blank', 'location=yes');
    

## InAppBrowser

从调用返回的对象`window.open`.

### 方法

*   addEventListener
*   removeEventListener
*   close
*   show
*   executeScript
*   insertCSS

## addEventListener

> 从该`InAppBrowser`中添加一个事件侦听器.

    ref.addEventListener(eventname, callback);
    

*   **ref**： 参考 `InAppBrowser` 窗口*(InAppBrowser)*

*   **eventname**： 需要监听的事件*(String)*
    
    *   **loadstart**：当`InAppBrowser` 开始加载一个 URL的时候触发事件。
    *   **loadstop**：当 `InAppBrowser` 完成加载一个 URL的时候触发事件。
    *   **loaderror**： 当`InAppBrowser` 加载 URL遇到错误时触发事件。
    *   **exit**： 当`InAppBrowser` 关闭窗口时触发事件。

*   **callback**：触发该事件的时候执行该函数。该函数被通过一个作为参数的`InAppBrowserEvent` 对象。

### InAppBrowserEvent 属性

*   **type**： eventname，或者 `loadstart` ， `loadstop` ， `loaderror` ，或 `exit` 。*(String)*

*   **url**: 已加载的 URL。*(String)*

*   **code**： 仅在`loaderror`情况中的错误代码 。*(Number)*

*   **message**： 该错误消息，只有在`loaderror`的情况下 。*(String)*

### 支持的平台

*   亚马逊火 OS
*   Android 系统
*   iOS
*   Windows Phone 7 和 8

### 快速的示例

    var ref = window.open('http://apache.org', '_blank', 'location=yes');
    ref.addEventListener('loadstart', function(event) { alert(event.url); });
    

## removeEventListener

> 去除`InAppBrowser`一个事件监听器.

    ref.removeEventListener(eventname, callback);
    

*   **ref**： 参考 `InAppBrowser` 窗口。*(InAppBrowser)*

*   **eventname**： 要停止侦听的事件。*(String)*
    
    *   **loadstart**： 当触发事件 `InAppBrowser` 开始加载一个 URL。
    *   **loadstop**： 当触发事件 `InAppBrowser` 完成加载一个 URL。
    *   **loaderror**： 当`InAppBrowser` 加载 URL遇到错误时触发事件。
    *   **退出**： 当触发事件 `InAppBrowser` 关闭窗口。

*   **回调**: 要在事件触发时执行的函数。该函数通过 `InAppBrowserEvent` 对象。

### 支持的平台

*   亚马逊火 OS
*   Android 系统
*   iOS
*   Windows Phone 7 和 8

### 快速的示例

    var ref = window.open('http://apache.org', '_blank', 'location=yes');
    var myCallback = function(event) { alert(event.url); }
    ref.addEventListener('loadstart', myCallback);
    ref.removeEventListener('loadstart', myCallback);
    

## close

> 关闭 `InAppBrowser` 窗口。

    ref.close() ；
    

*   **ref**： 参考 `InAppBrowser` 窗口*(InAppBrowser)*

### 支持的平台

*   亚马逊火 OS
*   Android 系统
*   iOS
*   Windows Phone 7 和 8

### 快速的示例

    var ref = window.open('http://apache.org', '_blank', 'location=yes');
    ref.close();
    

## show

> 显示打开了隐藏的 InAppBrowser 窗口。如果 InAppBrowser 是已经可见的，调用这个窗口没有任何影响。

    ref.show() ；
    

*   **ref**：参考 InAppBrowser 窗口 (`InAppBrowser`)

### 支持的平台

*   亚马逊火 OS
*   Android 系统
*   iOS

### 快速的示例

    var ref = window.open('http://apache.org', '_blank', 'hidden=yes');
    // some time later...
    ref.show();
    

## executeScript

> 注入 JavaScript 代码到 `InAppBrowser` 窗口

    ref.executeScript(details, callback);
    

*   **ref**： 参考 `InAppBrowser` 窗口。*() InAppBrowser*

*   **injectDetails**: 要运行的脚本的详细信息，指定任意一个`file` 或 `code` 键。*(Object)*
    
    *   **file**： 注入脚本的 URL 。
    *   **code**： 注入脚本的文本。

*   **callback**： 当 JavaScript 代码被注入后执行该函数。
    
    *   如果插入的脚本是`code` 类型，使用单个参数来回调执行，这是该脚本的返回值，包装在 `Array`中。 对于多行脚本，这是最后一条语句或最后计算的表达式的返回值。

### 支持的平台

*   亚马逊火 OS
*   Android 系统
*   iOS

### 快速的示例

    var ref = window.open('http://apache.org', '_blank', 'location=yes');
    ref.addEventListener('loadstop', function() {
        ref.executeScript({file: "myscript.js"});
    });
    

## insertCSS

> 注入CSS代码到 `InAppBrowser` 窗口。

    ref.insertCSS(details, callback);
    

*   **ref**： 参考 `InAppBrowser` 窗口*(InAppBrowser)*

*   **injectDetails**: 要运行的脚本的详细信息或指定 `file` 或 `code` 的关键。*（对象）*
    
    *   **file**：注入样式表的 URL。
    *   **code**： 注入文本样式表。

*   **callback**： 在 CSS 代码被注入后执行该函数。

### 支持的平台

*   亚马逊火 OS
*   Android 系统
*   iOS

### 快速的示例

    var ref = window.open('http://apache.org', '_blank', 'location=yes');
    ref.addEventListener('loadstop', function() {
        ref.insertCSS({file: "mystyles.css"});
    });