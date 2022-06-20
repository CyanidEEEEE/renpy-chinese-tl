# Renpy汉化、机翻与协作教程
renpy游戏翻译的教程、团队协作拓展
Renpy引擎目前在众多VN中得到使用，其对多语言翻译的支持也十分友善，只需要在Sdk下生成tl文件一般即可进行翻译工作，但是鉴于汉化活动一般都是基于一个爱好者组织来进行的，rpy文件对于协作的支持十分有限，因此本文将大致讲一下汉化的流程以及重点描述协作汉化、机翻自己玩的流程。

本文提到的工具均会给出详细链接，尤其感谢@小四，@Mirage两位朋友为我们编写了便利的工具！

## 安装环境

安装好python环境，这一步不会的自己百度！

去renpy官网下载sdk，建议把atom也下了，如果想打包安卓apk的还要下rapt；


## 解包与预处理


### 普通情况解包

Renpy的解包一般都是基于https://github.com/Lattyware/unrpa
详细的使用方法请自行阅读文档，但是基于使用的便利性考虑，分享一个更便利的软件：https://iwanplays.itch.io/rpaex
只需要将rpa直接拖拽到该软件即可解包，解包后将rpa文件删除。


### 特殊情况解包

（1）如果发现游戏目录里只有rpyc，表示作者删除了rpy，算是做了加密处理，不过使用https://github.com/CensoredUsername/unrpyc
将其放入game目录下，运行游戏，即可得到rpy；

（2）apk解包，renpy游戏的apk中，其实就是把所有文件加了X-，只需要解压apk，将其批量重命名即可，这里推荐使用这个工具https://github.com/DrDRR/RenPy-UnAPK


### 预处理

大部分Renpy游戏其实不需要预处理，需要预处理的情况主要是游戏存在大量为按照renpy文档撰写多语言支持的变量的情况（点名RPG），这里推荐使用该工具处理https://github.com/DrDRR/RenPy-TransVariables


## 添加语言及UI


### 使用Sdk创建tl文件

将解包的文件夹放在你设定的目录中，然后在renpy sdk中点击生成翻译文件，起一个你喜欢的名字，即可生成对应的翻译文件，即tl/XXX中的各种rpy，如果你不想使用太复杂的方式翻译，直接修改rpy即可进行翻译工作，注意，当游戏更新，大部分情况下你只需要把tl文件夹转移过去，再生成一次，renpy sdk会自动修补。


### 添加语言及字体

个人认为应在尽量不破坏原文件的基础上进行改动，因此这里可以使用renpy的特性，我们在tl/none中创建一个rpy，rpy名为你想要更改的原rpy名，比如我想更改screen.rpy添加语言选项，我就在该文件夹中创建一个，然后将原本文件中的部分或者全部内容复制过来，注意部分复制必须复制一个完整的框架，例如某个screen框架，在这里修改，游戏会优先使用这边的代码，因此即可达到不修改原文件并添加语言。

添加语言选项直接模仿原文件中的对应句式即可，这里给出PW中的语言选项代码：

    textbutton "{font=975GothicSC-Regular.ttf}简体中文{font}" action Language("cchinese")

font为指定这个文本使用特定字体，字体目录默认为game文件夹下，字体推荐去https://www.maoken.com/all-fonts
选用免费字体，​Language里则表示使用tl/XXX下的翻译文件，使用你前一步创建的名称即可；


### 修改UI

由于不同文字之间的情况不同，调整UI尤为重要，因此一般都需要修改UI的参数，这一步的所有参数都需要去原文件中，例如gui、screen中找，找到参数之后才可以定义修改，我们可以在tl/none中随意创建一个rpy，例如UI.rpy，然后在里面指定特定语言使用的UI参数，例如，我要指定cchinese的UI参数：

    translate cchinese python:
        gui.default_font = "975GothicSC-Regular.ttf"
        gui.name_font = "975GothicSC-Regular.ttf"
        gui.interface_font = "975GothicSC-Regular.ttf"
        gui.button_text_font = "975GothicSC-Regular.ttf"
        gui.choice_button_text_font = "975GothicSC-Regular.ttf"
        gui.label_text_size = 20
        gui.button_text_size = 23
        gui.text_size = 23
        gui.text_ypos = 26

        if renpy.variant("touch"):
            gui.text_size = 31
            gui.name_text_size = 34
            gui.text_width = 1200
            gui.text_xpos = 38
            gui.text_ypos = 47
            gui.name_xpos = 57
            gui.name_ypos = 0
            gui.button_text_size = 30

这里包含了普通UI与手机UI两种参数，仅针对cchinese语言，UI调试过程比较玄学，请大家自己多尝试，推荐在该rpy前面加 define config.developer = "True"，开启renpy调试模式，使用Shift+R即可重载文件，Shift+D进入开发者菜单，调试完成后删除或改为False；


### 关于图片的UI

修改图片UI的方法其实是大多数引擎的相同特性，优先调用外头的文件，因此只需要按照game文件夹下的目录结构，使用完全相同的目录和文件名，放到tl/XXX文件夹下，即可对应该语言调用指定图片；


### 汉化补丁

这一步其实没什么好说的，如果你按照我的教程只修改了tl文件，那么只需要打包tl文件夹和你自己加入的字体文件，按照目录放好，随意写个说明文档，即可（对我就是那么懒），当然如果你打包成exe也不是不行；


## 协作翻译与机翻

终于到了本文最重要的环节，前面的流程其实有很多可以参考的其他教程，例如：

https://drdrr.xyz/%E6%95%99%E7%A8%8B/2021/02/10/renpy-localization-tutorial/

https://github.com/Dclef/renpy-tl

而本教程最核心的不同即在于因为我个人为了自己玩一些（*#@#）比较具有艺术价值的游戏，研究了机翻流程，因此使用了不同的处理方法，而这种处理方法对于协作翻译也十分有帮助，因此放出来供大家参考：

### 导出PO文件

我们首先用到的工具是https://www.beuc.net/renpy-ttk/dir?ci=tip
相关文件备份在这里https://github.com/CyanidEEEEE/renpy-chinese-tl/releases/tag/1.0
使用这个工具只需要将其像renpy游戏一样放置于设定的renpy主目录，在sdk中运行即可，运行后，选择对应的游戏与语言，使用tl2po，即可将所有rpy导出，成为PO文件，如果只是为了集合到一起方便编辑，直接用Poedit编辑汉化PO之后再使用mo2tl选择PO文件即可导入翻译；


### 转换成xlsx文件

这里我们使用可爱米宝开发的https://github.com/Maooookai/po_and_excel_transfer_tool
记得安装requirement，将PO转为xlsx之后，我们就得到了无论是机翻也好协作也好，最便利的xlsx文件，在线协作流程就自己学习啦，石墨文档和谷歌文档很不错，腾讯文档的话，主要是便利吧？由于这个过程中，不同的游戏有不同的问题，所以请务必马上尝试转回PO文件，使用Beyond Compare对比查看转换回来后的PO有什么错误，之后转回时务必修复，如果遇到无法解决的问题，去写ISSUE吧拜托神奇米宝吧！(bushi)，善用excel的公式与插件，例如方方格子；


### 机翻与修复文本错误的技巧

已经得到xlsx后，机翻只需要将那一整列文本复制导出，机翻后再导入回去即可，机翻的工具推荐使用https://github.com/Maooookai/WebTranslator
里面的webdriver自己根据chrome版本更新，将文本导出保存为trans.txt，然后使用该工具进行翻译，该工具带进度保存，中途程序出问题中断后直接再次运行即可，不过目前有某些BUG，详情请看ISSUE，机翻引擎个人体验下来，最喜欢彩云小译与Deepl，Deepl的翻译米宝还没写，大家想要可以自己去催！记得对照renpy的文档处理一些特殊符号，尽量保持与原文一致，一般来说，同一个游戏由于文本编写的连贯性，因此可以使用一套替换公式，在这里推荐使用word插件——word精灵，使用其批量替换功能，记得每次改一类重复出现的BUG时写一套替换公式表格，这样下次更新的时候只需要批量替换即可修正大多数错误。还有一种思路是从机翻之前入手，比如自定义的角色名，文本中是[mcname]，你可以先批量替换成一个翻译引擎只有一种翻译的人名，比如Hitler，这样得到机翻文本后把希特勒批量替换回[mcname]即可。


### 制作双语对照

这里纯粹是机翻才需要的步骤了，因为机翻大量搞笑的翻译，其实只是为了方便自己玩才制作，因此双语对照是必须制作的，否则根本。看不懂啊！这里只需要利用excel的公式即可简单的制作双语文本：

在E1单元格中输入公式 =C1&"\n"&D1，点击右下角的十字键，拓展到该列所有部分，然后选中该列，复制到F列（仅复制值），然后把E列删除，修正新E1中的文字为target，然后把系统UI部分从D1中复制到E1（即系统UI文字别搞成双语了），双语文本即成，双语的导入只需要再创建一个语言，按照下一步流程将其导入即可，不过双语的UI也要好好调整噢！


### 转回PO以及导入

刚刚的工具中就包含了Xlsx转回PO的工具，把编辑好的Xlsx转回成PO，修复一些转换问题，即可开始导入流程，即使用将Rpy导出成PO的程序中的mo2tl选择PO文件即可导入翻译，无论是导入流程中忘记修复PO导致导入失败，还是最后导入成功，都要记得删除tl/pot文件夹，这是该工具导入产生的临时文件，如果不删除，修复PO之后也还是会导入失败。

某些游戏中使用了Renpy的extend特性，因此双语在第二行文字时会出现没有空行的现象，使用超文本编辑器，将双语文件夹中的所有rpy导入，一键替换：

    extend " 为extend "\n

然后更正一下原文一键替换：

    # extend "\n\n 为 # extend "\n

当然，其实不需要更正原文，因为据我研究，好像根本不靠这个定位原文（XD）；

导入后，可以使用renpy sdk中的检查脚本并分析统计粗略查错，但其实没啥用。


## 打包

至于打包，emm，PC与MAC的打包有手就行，都是中文，相信大家可以自己摸索，安卓打包是在安装sdk时安装rapt，创建秘钥，配置一些信息，即可打包（打包过程需要下载一些不在国内的东西，因此自行配置全局代理，最好是路由器代理），安卓apk的图标与过场载入画面的设置renpy文档有说明，大致讲一下就是在根目录放置三个文件：android-icon_foreground.png（图标）、android-icon_background.png（图标背景）、android-presplash.png（过场图），具体自己实践就知道了。









