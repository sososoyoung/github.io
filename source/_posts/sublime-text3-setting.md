---
title: sublime text3 settings
date: 2016-11-10 18:27:40
tags: sublime
categories: sublime
---
## 常用的插件：

1. [Package Control](https://packagecontrol.io/packages/Package%20Control)
    
    功能：安装包管理
    简介：sublime插件控制台，提供添加、删除、禁用、查找插件等功能

    安装方法：
    CTRL+` ，出现控制台
    粘贴以下代码至控制台
    ```
    import urllib.request,os,hashlib; h = 'df21e130d211cfc94d9b0905775a7c0f' + '1e3d39e33b79698005270310898eea76'; pf = 'Package Control.sublime-package'; ipp = sublime.installed_packages_path(); urllib.request.install_opener( urllib.request.build_opener( urllib.request.ProxyHandler()) ); by = urllib.request.urlopen( 'http://packagecontrol.io/' + pf.replace(' ', '%20')).read(); dh = hashlib.sha256(by).hexdigest(); print('Error validating download (got %s instead of %s), please try manual install' % (dh, h)) if dh != h else open(os.path.join( ipp, pf), 'wb' ).write(by)
    ```

2. [Emmet](https://sublime.wbond.net/packages/Emmet)
    
    功能：编码快捷键，前端必备
    简介：Emmet作为zen coding的升级版，对于前端来说，可是必备插件，如果你对它还不太熟悉，可以在其官网（http://docs.emmet.io/）上看下具体的演示视频。

3.  [JSFormat](https://sublime.wbond.net/packages/JsFormat)
    
    简介：指示代码中插入、修改、删除的地方

4.  [LESS](https://sublime.wbond.net/packages/LESS)
    
    LESS高亮插件

5.  [BracketHighlighter](https://github.com/facelessuser/BracketHighlighter)
6.  [git](https://github.com/kemayo/sublime-text-git)
7.  [Doc​Blockr](https://sublime.wbond.net/packages/DocBlockr)
8.  [Color​Picker](https://sublime.wbond.net/packages/ColorPicker)
    
    功能：调色板
    简介：需要输入颜色时，可直接选取颜色
    使用：快捷键Windows: ctrl+shift+c

9. [ConvertToUTF8](https://sublime.wbond.net/packages/ConvertToUTF8)
10. [AutoFileName](https://sublime.wbond.net/packages/AutoFileName)
11. [gitGutter](https://packagecontrol.io/packages/GitGutter)
    
    简介：指示代码中插入、修改、删除的地方
12. [MarkdownEditing](https://github.com/SublimeText-Markdown/MarkdownEditing/issues)

## jsx支持

1. [babel](https://packagecontrol.io/packages/Babel)
    
    支持ES6， React.js, jsx代码高亮，对 JavaScript, jQuery 也有很好的扩展
    配置:

    1. 打开.js, .jsx 后缀的文件;

    2. 打开菜单view， Syntax -> Open all with current extension as... -> Babel -> JavaScript (Babel)，选择babel为默认 javascript 打开syntax

2.  修改 Emmet 兼容jsx 文件
    
    使用方法:
    打开 preferences -> Key bindings - Users，把下面代码复制到[]内部。
    ```
    {
      "keys": [
        "super+e"
      ],
      "args": {
        "action": "expand_abbreviation"
      },
      "command": "run_emmet_action",
      "context": [{
        "key": "emmet_action_enabled.expand_abbreviation"
      }]
    },
    {
      "keys": ["tab"],
      "command": "expand_abbreviation_by_tab",
      "context": [{
        "operand": "source.js",
        "operator": "equal",
        "match_all": true,
        "key": "selector"
      }, {
        "key": "preceding_text",
        "operator": "regex_contains",
        "operand": "(\\b(a\\b|div|span|p\\b|button)(\\.\\w*|>\\w*)?([^}]*?}$)?)",
        "match_all": true
      }, {
        "key": "selection_empty",
        "operator": "equal",
        "operand": true,
        "match_all": true
      }]
    }
    ```

3. JsFormat 格式化 js 代码
    
    使用:
    打开preferences -> Package Settings -> JsFormat -> Setting - Users,输入以下代码：
    ```
    {
      "e4x": true,
      // 保存时自动格式化，看个人需要
      // "format_on_save": true,
    }
    ```








