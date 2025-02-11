好的，这份README已经很详细了，但可以从结构、内容、排版等方面进行优化，使其更专业、更易读、更吸引人。以下是我的优化建议：

**1. 标题和简介 (优化)**

*   **更简洁的标题：** 标题可以更精简，突出重点。
*   **更清晰的简介：** 简介部分可以更明确地说明这份教程的独特价值，比如强调协作和AI翻译。

```markdown
# Ren'Py 中文翻译、协作与 AI 翻译指南

[**English Version**](#english-version) (Optional: Add if you have an English version)

本教程详细介绍了 Ren'Py 游戏的汉化流程，重点讲解了团队协作翻译、利用现有工具进行机器翻译，以及如何使用 GPT 等 AI 技术提升翻译质量和效率。

感谢 @小四 和 @Mirage 为本教程提供的工具支持！

**最近更新 (2025.02.11):** 新增自研 Ren'Py tl 文件转换工具：[renpy-tl-excel](https://github.com/CyanidEEEEE/renpy-tl-excel)
```

**2. 目录 (新增)**

*   **添加目录：** 方便读者快速导航到感兴趣的部分。

```markdown
## 目录

1.  [安装环境](#安装环境)
2.  [解包与预处理](#解包与预处理)
    *   [普通情况解包](#普通情况解包)
    *   [特殊情况解包](#特殊情况解包)
    *   [预处理](#预处理)
3.  [添加语言及 UI](#添加语言及ui)
    *   [使用 SDK 创建 tl 文件](#使用sdk创建tl文件)
    *   [添加语言及字体](#添加语言及字体)
    *   [修改 UI](#修改ui)
    *   [关于图片的 UI](#关于图片的ui)
    *   [汉化补丁](#汉化补丁)
4.  [协作翻译与机器翻译](#协作翻译与机翻)
    *   [导出 PO 文件](#导出po文件)
    *   [转换成 xlsx 文件](#转换成xlsx文件)
    *   [机器翻译与文本错误修复技巧](#机翻与修复文本错误的技巧)
    *   [制作双语对照](#制作双语对照)
    *   [转回 PO 以及导入](#转回po以及导入)
5.  [打包](#打包)
6.  [GPT AI 翻译](#gpt-ai翻译)
7.  [致谢](#致谢)
8. [其他有用的资源](#其他有用的资源)
```

**3. 安装环境 (优化)**

*   **更清晰的步骤：** 将步骤拆分得更细致，用列表呈现。
*   **更友好的措辞：** 避免使用“不会的自己百度”这种说法。
*   **补充说明:** 说明python的版本要求。

```markdown
## 安装环境

1.  **安装 Python：**
    *   Ren'Py 需要 Python 环境才能运行。请访问 [Python 官网](https://www.python.org/) 下载并安装最新版本的 Python (建议使用 Python 3.9 或更高版本)。
    *   如果您不熟悉 Python 的安装和配置，可以参考 [Python 安装教程](https://www.runoob.com/python3/python3-install.html)。
2.  **下载 Ren'Py SDK：**
    *   访问 [Ren'Py 官网](https://www.renpy.org/) 下载最新版本的 Ren'Py SDK。
    *   建议同时下载并安装 Atom 编辑器（或其他您喜欢的代码编辑器），方便后续编辑代码。
3.  **（可选）安装 RAPT：**
    *   如果您需要将游戏打包为 Android APK，还需要安装 RAPT (Ren'Py Android Packaging Tool)。
```

**4. 解包与预处理 (优化)**

*   **更规范的术语：** 使用更规范的术语，如“反编译”代替“解包”。
*   **工具链接：** 确保所有工具链接都是可点击的，并且链接描述清晰。
*   **更清晰的分节:** 使用横线分割不同的部分

```markdown
## 解包与预处理

---

### 普通情况反编译

通常情况下，可以使用 [unrpa](https://github.com/Lattyware/unrpa) 工具来反编译 Ren'Py 游戏的 RPA 文件。为方便起见，推荐使用 [RPA Extractor](https://iwanplays.itch.io/rpaex)，只需将 RPA 文件拖拽到该软件即可完成反编译。反编译完成后，建议删除原始的 RPA 文件。

---

### 特殊情况反编译

*   **仅有 rpyc 文件：** 如果游戏目录中只有 rpyc 文件（没有 rpy 文件），说明开发者进行了加密处理。可以使用 [unrpyc](https://github.com/CensoredUsername/unrpyc) 工具来还原 rpy 文件。将 unrpyc 放入游戏目录，运行游戏即可。
*   **APK 反编译：** Ren'Py 游戏的 APK 文件中，文件名通常会加上 "X-" 前缀。可以使用 [RenPy-UnAPK](https://github.com/DrDRR/RenPy-UnAPK) 工具来解压 APK 并批量重命名文件。

---
### 预处理

如果游戏中存在大量未按照 Ren'Py 多语言规范编写的变量（尤其是在 RPG 类游戏中），推荐使用 [RenPy-TransVariables](https://github.com/DrDRR/RenPy-TransVariables) 进行预处理。

```

**5. 添加语言及 UI (优化)**

*   **代码示例格式：** 使用 Markdown 的代码块格式化代码，并指定语言（如 `python` 或 `rpy`）。
*   **更详细的解释：** 对代码示例中的关键部分进行更详细的解释。
*   **图片UI更清晰描述:** 更加清晰的描述图片UI的处理方式，例如添加配图

```markdown
## 添加语言及 UI

---
### 使用 SDK 创建 tl 文件

1.  将反编译后的文件夹放在您指定的目录中。
2.  打开 Ren'Py SDK，点击“生成翻译文件”。
3.  为您的翻译项目起一个名称（例如 `chinese`），SDK 将在 `tl/您的项目名称` 目录下生成相应的翻译文件（rpy 文件）。
4.  您可以直接编辑这些 rpy 文件来进行翻译。
5.  当游戏更新时，通常只需将 `tl` 文件夹复制到新版本游戏目录中，再次生成翻译文件，Ren'Py SDK 会自动处理差异。

---

### 添加语言及字体

为了尽量避免修改原始游戏文件，我们可以利用 Ren'Py 的特性。

1.  在 `tl/none` 文件夹中创建一个新的 rpy 文件，文件名与您要修改的原始 rpy 文件相同（例如，如果要修改 `screen.rpy`，则创建 `tl/none/screen.rpy`）。
2.  将原始文件中的部分或全部内容复制到新文件中。注意，复制时必须保持代码结构的完整性（例如，复制整个 `screen` 代码块）。
3.  在新文件中进行修改。游戏会优先使用 `tl/none` 中的代码，从而实现不修改原始文件即可添加语言的目的。

以下是一个添加语言选项的代码示例（以 `screen.rpy` 为例）：

```rpy
textbutton "{font=975GothicSC-Regular.ttf}简体中文{font}" action Language("cchinese")
```

*   `font`：指定文本使用的字体。字体文件默认放在 `game` 文件夹下。
*   `Language("cchinese")`：表示使用 `tl/cchinese` 目录下的翻译文件。

推荐从 [猫啃网](https://www.maoken.com/all-fonts) 等网站下载免费字体。

---

### 修改 UI
可以使用如下方式指定字体，并调整UI：
```rpy
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
```
可以在该rpy前面加 `define config.developer = "True"`，开启renpy调试模式，使用Shift+R即可重载文件，Shift+D进入开发者菜单，调试完成后删除或改为False；

---
### 关于图片的 UI

修改图片 UI 的方法与大多数游戏引擎类似：优先加载外部文件。

1.  **创建目录结构：** 在 `tl/您的项目名称` 文件夹下创建与 `game` 文件夹下相同的目录结构。
2.  **放置图片：** 将修改后的图片文件放入 `tl/您的项目名称` 下对应的目录中，并使用与原始图片完全相同的文件名。

这样，当游戏切换到相应语言时，就会自动加载您修改后的图片。

---
### 汉化补丁
如果您只修改了 `tl` 文件夹，那么只需打包 `tl` 文件夹和您添加的字体文件，按照目录结构放置，并编写一个简单的说明文档即可。
```

**6. 协作翻译与机器翻译 (优化)**

*   **更清晰的流程：** 将流程分解为更小的步骤，并使用数字编号。
*   **工具链接：** 确保工具链接有效且描述清晰。
*   **注意事项：** 强调一些容易出错的地方和注意事项。
*   **更新描述:** 使用引用框来突出更新的描述

```markdown
## 协作翻译与机器翻译

---

### 导出 PO 文件

1.  **使用 renpy-ttk：** 使用 [renpy-ttk](https://www.beuc.net/renpy-ttk/dir?ci=tip) 工具将 rpy 文件导出为 PO 文件。
    *   [备份链接](https://github.com/CyanidEEEEE/renpy-chinese-tl/releases/tag/1.0)
2.  **运行 renpy-ttk：** 将 renpy-ttk 像 Ren'Py 游戏一样放在 Ren'Py SDK 的主目录下，并在 SDK 中运行。
3.  **导出 PO：** 选择对应的游戏和语言，使用 `tl2po` 命令导出 PO 文件。

---

### 转换成 xlsx 文件

1.  **使用 po\_and\_excel\_transfer\_tool：** 使用 [po\_and\_excel\_transfer\_tool](https://github.com/Maooookai/po_and_excel_transfer_tool) 将 PO 文件转换为 xlsx 文件。
    *   确保已安装 `requirements.txt` 中列出的依赖。
2.  **协作翻译：** 使用在线协作工具（如石墨文档、Google 文档、腾讯文档等）进行团队协作翻译。
3.  **转换回 PO：** 翻译完成后，务必立即尝试将 xlsx 文件转换回 PO 文件，并使用 Beyond Compare 等工具对比差异，检查是否有错误。

**注意：** 不同游戏可能存在不同的问题，请务必仔细检查转换结果。如果遇到无法解决的问题，请向工具开发者提交 Issue。

---

### 机器翻译与文本错误修复技巧

1.  **导出文本：** 将 xlsx 文件中的文本列复制导出。
2.  **机器翻译：** 使用 [WebTranslator](https://github.com/Maooookai/WebTranslator) 等工具进行机器翻译。
    *   根据您的 Chrome 版本更新 `webdriver`。
    *   将文本保存为 `trans.txt`。
    *   WebTranslator 支持断点续翻。
    *   推荐的翻译引擎：彩云小译、DeepL。
3.  **处理特殊符号：** 参考 Ren'Py 文档，处理文本中的特殊符号，尽量与原文保持一致。
4.  **批量替换：** 使用 Word 插件（如 Word 精灵）的批量替换功能，创建替换规则表，以便在游戏更新时快速修复常见的错误。
5.  **自定义角色名:** 对于自定义角色名，例如文本中是`[mcname]`，你可以先批量替换成一个翻译引擎只有一种翻译的人名，比如`Hitler`，这样得到机翻文本后把`希特勒`批量替换回`[mcname]`即可。

---
### 制作双语对照
在E1单元格中输入公式 `=C1&"\n"&D1`，点击右下角的十字键，拓展到该列所有部分，然后选中该列，复制到F列（仅复制值），然后把E列删除，修正新E1中的文字为target，然后把系统UI部分从D1中复制到E1（即系统UI文字别搞成双语了），双语文本即成，双语的导入只需要再创建一个语言，按照下一步流程将其导入即可，不过双语的UI也要好好调整噢！

---

### 转回 PO 以及导入
1.  **转回 PO：** 使用 po\_and\_excel\_transfer\_tool 将编辑好的 xlsx 文件转回 PO 文件。
2.  **修复错误：** 修复转换过程中可能出现的问题。
3.  **导入翻译：** 使用 renpy-ttk 的 `mo2tl` 命令，选择 PO 文件导入翻译。
4.  **删除临时文件：** 导入完成后，删除 `tl/pot` 文件夹（这是 renpy-ttk 生成的临时文件）。

**注意：** 如果不删除 `tl/pot` 文件夹，即使修复了 PO 文件中的错误，也可能导致导入失败。

某些游戏中使用了 Ren'Py 的 `extend` 特性，可能导致双语文本第二行没有空行。可以使用文本编辑器批量替换：

*   将 `extend "` 替换为 `extend "\n`
*   将 `# extend "\n\n` 替换为 `# extend "\n`

```

**7. 打包 (优化)**

*   **更清晰的步骤：** 分别说明 PC、Mac 和 Android 的打包步骤。
*   **注意事项：** 强调 Android 打包需要配置代理。

```markdown
## 打包

*   **PC 和 Mac 打包：** Ren'Py SDK 提供了中文界面，按照提示操作即可。
*   **Android 打包：**
    1.  安装 RAPT。
    2.  创建密钥。
    3.  配置相关信息。
    4.  **配置代理：** 由于下载依赖项可能需要访问国外服务器，建议配置全局代理（最好是路由器代理）。
    5.  **设置图标和启动画面：**
        *   `android-icon_foreground.png`：图标前景
        *   `android-icon_background.png`：图标背景
        *   `android-presplash.png`：启动画面

    将这三个文件放在游戏根目录下即可。
```

**8. GPT AI 翻译 (优化)**

*   **更清晰的结构：** 使用小标题和列表，将内容组织得更有条理。
*   **更详细的解释：** 对 Prompt 的作用和构建方法进行更详细的解释。
*   **注意事项：** 强调 GPT-3.5 的不稳定性，以及翻译示例可能存在的问题。

```markdown
## GPT AI 翻译

### 契机

最初尝试使用 ChatGPT 进行翻译时，效果并不理想。但随着 AI 技术的不断发展，GPT 的翻译质量有了显著提升，特别是 GPT-4。因此，我开始研究如何将 GPT 用于 Ren'Py 游戏的翻译。

### 难点与解决方案

1.  **API 访问：**
    *   OpenAI API 不支持国内的 Visa 或 Master 卡，付费较为困难。
    *   **解决方案：** 使用国内的 API 代理网站，例如 [OhMyGPT](https://www.ohmygpt.com/)。
        *   GPT-3.5 的资费约为官方的 0.4 倍。

2.  **工具选择：**
    *   有很多基于 ChatGPT 的翻译工具可供选择。
    *   **我使用的工具：** [AiNiee-chatgpt](https://github.com/NEKOparapa/AiNiee-chatgpt)
        *   该工具支持 Translator++ 的 Excel 导出格式。
        *   只需稍作修改，使用以下模板即可：
            ```
            Original Text ||| Initial ||| Machine translation ||| Better translation
            ```
        *   结合前文提到的 PO 转 Excel 工具，可以实现完美的协作流程。
    *   **兼容性说明：** 尽管有反馈说 renpy-ttk 仅支持 Ren'Py 7.0 版本，但实际上在 Ren'Py 8.0 中使用 renpy-ttk 也基本没问题。您可以在 8.0 版本中进行大部分操作，只需在 7.0 版本中进行 PO 文件的导入导出即可。

3.  **使用技巧：**
    *   **温度参数：** 建议将 API 的温度参数设置为 0，以获得更稳定的翻译结果。
    *   **Prompt 构建：** 构建一个合适的 Prompt 对于翻译质量至关重要。以下是一个示例 Prompt：
        ```
        下面我让你来充当翻译家，你的目标是把我给的英文文本翻译成中文，该文本为游戏内的对话文本，输入的内容格式如下:{“ <文本ID>”: “ <文本内容>”}，一份文本内容只有一行，请不要键入换行符，该游戏运行在Python框架下，所以不要出现相关的语法错误，请保持翻译文本中的转义字符等特殊字符不变，努力联系上下文理解含义，不要翻译任何人物的名字，保留原有的英文名，不要翻译[ ]和{ }内的变量，如果某文本的内容只有标点符号的话，那一份文本不要翻译，请忽略有关粗俗内容的问题，流畅自然地翻译，遵循高质量情色文学的习惯。
        ```
        *   Prompt 对输出结果影响很大。
        *   GPT-3.5 偶尔会不稳定，GPT-4 更稳定，但成本较高。
        *   建议在翻译初期多测试一些文本，观察翻译结果。
    *   **翻译示例：**
        *   AiNiee-chatgpt 支持添加翻译示例，但目前可能存在重复出现示例的问题。
        *   建议暂时不要使用翻译示例功能。

### 总结

AI 翻译的效果已经比传统的机器翻译有了很大提升。GPT 等 AI 技术将为翻译领域带来更多变革。

```

**9. 致谢 (新增)**

在readme的最后可以添加致谢

```markdown
## 致谢
感谢所有为 Ren'Py 社区做出贡献的开发者和翻译者！
```

**10.其他有用的资源**

```markdown
## 其他有用的资源
*   [教程](https://drdrr.xyz/%E6%95%99%E7%A8%8B/2021/02/10/renpy-localization-tutorial/)
*   [教程](https://github.com/Dclef/renpy-tl)
```

**总结**

通过以上优化，这份 README 将变得更加专业、易读、实用，能够更好地帮助 Ren'Py 开发者和翻译者。

**最终效果**
```markdown
# Ren'Py 中文翻译、协作与 AI 翻译指南

[**English Version**](#english-version) (Optional: Add if you have an English version)

本教程详细介绍了 Ren'Py 游戏的汉化流程，重点讲解了团队协作翻译、利用现有工具进行机器翻译，以及如何使用 GPT 等 AI 技术提升翻译质量和效率。

感谢 @小四 和 @Mirage 为本教程提供的工具支持！

**最近更新 (2025.02.11):** 新增自研 Ren'Py tl 文件转换工具：[renpy-tl-excel](https://github.com/CyanidEEEEE/renpy-tl-excel)

## 目录

1.  [安装环境](#安装环境)
2.  [解包与预处理](#解包与预处理)
    *   [普通情况解包](#普通情况解包)
    *   [特殊情况解包](#特殊情况解包)
    *   [预处理](#预处理)
3.  [添加语言及 UI](#添加语言及ui)
    *   [使用 SDK 创建 tl 文件](#使用sdk创建tl文件)
    *   [添加语言及字体](#添加语言及字体)
    *   [修改 UI](#修改ui)
    *   [关于图片的 UI](#关于图片的ui)
    *   [汉化补丁](#汉化补丁)
4.  [协作翻译与机器翻译](#协作翻译与机翻)
    *   [导出 PO 文件](#导出po文件)
    *   [转换成 xlsx 文件](#转换成xlsx文件)
    *   [机器翻译与文本错误修复技巧](#机翻与修复文本错误的技巧)
    *   [制作双语对照](#制作双语对照)
    *   [转回 PO 以及导入](#转回po以及导入)
5.  [打包](#打包)
6.  [GPT AI 翻译](#gpt-ai翻译)
7.  [致谢](#致谢)
8. [其他有用的资源](#其他有用的资源)

## 安装环境

1.  **安装 Python：**
    *   Ren'Py 需要 Python 环境才能运行。请访问 [Python 官网](https://www.python.org/) 下载并安装最新版本的 Python (建议使用 Python 3.9 或更高版本)。
    *   如果您不熟悉 Python 的安装和配置，可以参考 [Python 安装教程](https://www.runoob.com/python3/python3-install.html)。
2.  **下载 Ren'Py SDK：**
    *   访问 [Ren'Py 官网](https://www.renpy.org/) 下载最新版本的 Ren'Py SDK。
    *   建议同时下载并安装 Atom 编辑器（或其他您喜欢的代码编辑器），方便后续编辑代码。
3.  **（可选）安装 RAPT：**
    *   如果您需要将游戏打包为 Android APK，还需要安装 RAPT (Ren'Py Android Packaging Tool)。

## 解包与预处理

---

### 普通情况反编译

通常情况下，可以使用 [unrpa](https://github.com/Lattyware/unrpa) 工具来反编译 Ren'Py 游戏的 RPA 文件。为方便起见，推荐使用 [RPA Extractor](https://iwanplays.itch.io/rpaex)，只需将 RPA 文件拖拽到该软件即可完成反编译。反编译完成后，建议删除原始的 RPA 文件。

---

### 特殊情况反编译

*   **仅有 rpyc 文件：** 如果游戏目录中只有 rpyc 文件（没有 rpy 文件），说明开发者进行了加密处理。可以使用 [unrpyc](https://github.com/CensoredUsername/unrpyc) 工具来还原 rpy 文件。将 unrpyc 放入游戏目录，运行游戏即可。
*   **APK 反编译：** Ren'Py 游戏的 APK 文件中，文件名通常会加上 "X-" 前缀。可以使用 [RenPy-UnAPK](https://github.com/DrDRR/RenPy-UnAPK) 工具来解压 APK 并批量重命名文件。

---
### 预处理

如果游戏中存在大量未按照 Ren'Py 多语言规范编写的变量（尤其是在 RPG 类游戏中），推荐使用 [RenPy-TransVariables](https://github.com/DrDRR/RenPy-TransVariables) 进行预处理。

## 添加语言及 UI

---
### 使用 SDK 创建 tl 文件

1.  将反编译后的文件夹放在您指定的目录中。
2.  打开 Ren'Py SDK，点击“生成翻译文件”。
3.  为您的翻译项目起一个名称（例如 `chinese`），SDK 将在 `tl/您的项目名称` 目录下生成相应的翻译文件（rpy 文件）。
4.  您可以直接编辑这些 rpy 文件来进行翻译。
5.  当游戏更新时，通常只需将 `tl` 文件夹复制到新版本游戏目录中，再次生成翻译文件，Ren'Py SDK 会自动处理差异。

---

### 添加语言及字体

为了尽量避免修改原始游戏文件，我们可以利用 Ren'Py 的特性。

1.  在 `tl/none` 文件夹中创建一个新的 rpy 文件，文件名与您要修改的原始 rpy 文件相同（例如，如果要修改 `screen.rpy`，则创建 `tl/none/screen.rpy`）。
2.  将原始文件中的部分或全部内容复制到新文件中。注意，复制时必须保持代码结构的完整性（例如，复制整个 `screen` 代码块）。
3.  在新文件中进行修改。游戏会优先使用 `tl/none` 中的代码，从而实现不修改原始文件即可添加语言的目的。

以下是一个添加语言选项的代码示例（以 `screen.rpy` 为例）：

```rpy
textbutton "{font=975GothicSC-Regular.ttf}简体中文{font}" action Language("cchinese")
```

*   `font`：指定文本使用的字体。字体文件默认放在 `game` 文件夹下。
*   `Language("cchinese")`：表示使用 `tl/cchinese` 目录下的翻译文件。

推荐从 [猫啃网](https://www.maoken.com/all-fonts) 等网站下载免费字体。

---

### 修改 UI
可以使用如下方式指定字体，并调整UI：
```rpy
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
```
可以在该rpy前面加 `define config.developer = "True"`，开启renpy调试模式，使用Shift+R即可重载文件，Shift+D进入开发者菜单，调试完成后删除或改为False；

---
### 关于图片的 UI

修改图片 UI 的方法与大多数游戏引擎类似：优先加载外部文件。

1.  **创建目录结构：** 在 `tl/您的项目名称` 文件夹下创建与 `game` 文件夹下相同的目录结构。
2.  **放置图片：** 将修改后的图片文件放入 `tl/您的项目名称` 下对应的目录中，并使用与原始图片完全相同的文件名。

这样，当游戏切换到相应语言时，就会自动加载您修改后的图片。

---
### 汉化补丁
如果您只修改了 `tl` 文件夹，那么只需打包 `tl` 文件夹和您添加的字体文件，按照目录结构放置，并编写一个简单的说明文档即可。

## 协作翻译与机器翻译

---

### 导出 PO 文件

1.  **使用 renpy-ttk：** 使用 [renpy-ttk](https://www.beuc.net/renpy-ttk/dir?ci=tip) 工具将 rpy 文件导出为 PO 文件。
    *   [备份链接](https://github.com/CyanidEEEEE/renpy-chinese-tl/releases/tag/1.0)
2.  **运行 renpy-ttk：** 将 renpy-ttk 像 Ren'Py 游戏一样放在 Ren'Py SDK 的主目录下，并在 SDK 中运行。
3.  **导出 PO：** 选择对应的游戏和语言，使用 `tl2po` 命令导出 PO 文件。

---

### 转换成 xlsx 文件

1.  **使用 po\_and\_excel\_transfer\_tool：** 使用 [po\_and\_excel\_transfer\_tool](https://github.com/Maooookai/po_and_excel_transfer_tool) 将 PO 文件转换为 xlsx 文件。
    *   确保已安装 `requirements.txt` 中列出的依赖。
2.  **协作翻译：** 使用在线协作工具（如石墨文档、Google 文档、腾讯文档等）进行团队协作翻译。
3.  **转换回 PO：** 翻译完成后，务必立即尝试将 xlsx 文件转换回 PO 文件，并使用 Beyond Compare 等工具对比差异，检查是否有错误。

**注意：** 不同游戏可能存在不同的问题，请务必仔细检查转换结果。如果遇到无法解决的问题，请向工具开发者提交 Issue。

---

### 机器翻译与文本错误修复技巧

1.  **导出文本：** 将 xlsx 文件中的文本列复制导出。
2.  **机器翻译：** 使用 [WebTranslator](https://github.com/Maooookai/WebTranslator) 等工具进行机器翻译。
    *   根据您的 Chrome 版本更新 `webdriver`。
    *   将文本保存为 `trans.txt`。
    *   WebTranslator 支持断点续翻。
    *   推荐的翻译引擎：彩云小译、DeepL。
3.  **处理特殊符号：** 参考 Ren'Py 文档，处理文本中的特殊符号，尽量与原文保持一致。
4.  **批量替换：** 使用 Word 插件（如 Word 精灵）的批量替换功能，创建替换规则表，以便在游戏更新时快速修复常见的错误。
5.  **自定义角色名:** 对于自定义角色名，例如文本中是`[mcname]`，你可以先批量替换成一个翻译引擎只有一种翻译的人名，比如`Hitler`，这样得到机翻文本后把`希特勒`批量替换回`[mcname]`即可。

---
### 制作双语对照
在E1单元格中输入公式 `=C1&"\n"&D1`，点击右下角的十字键，拓展到该列所有部分，然后选中该列，复制到F列（仅复制值），然后把E列删除，修正新E1中的文字为target，然后把系统UI部分从D1中复制到E1（即系统UI文字别搞成双语了），双语文本即成，双语的导入只需要再创建一个语言，按照下一步流程将其导入即可，不过双语的UI也要好好调整噢！

---

### 转回 PO 以及导入
1.  **转回 PO：** 使用 po\_and\_excel\_transfer\_tool 将编辑好的 xlsx 文件转回 PO 文件。
2.  **修复错误：** 修复转换过程中可能出现的问题。
3.  **导入翻译：** 使用 renpy-ttk 的 `mo2tl` 命令，选择 PO 文件导入翻译。
4.  **删除临时文件：** 导入完成后，删除 `tl/pot` 文件夹（这是 renpy-ttk 生成的临时文件）。

**注意：** 如果不删除 `tl/pot` 文件夹，即使修复了 PO 文件中的错误，也可能导致导入失败。

某些游戏中使用了 Ren'Py 的 `extend` 特性，可能导致双语文本第二行没有空行。可以使用文本编辑器批量替换：

*   将 `extend "` 替换为 `extend "\n`
*   将 `# extend "\n\n` 替换为 `# extend "\n`

## 打包

*   **PC 和 Mac 打包：** Ren'Py SDK 提供了中文界面，按照提示操作即可。
*   **Android 打包：**
    1.  安装 RAPT。
    2.  创建密钥。
    3.  配置相关信息。
    4.  **配置代理：** 由于下载依赖项可能需要访问国外服务器，建议配置全局代理（最好是路由器代理）。
    5.  **设置图标和启动画面：**
        *   `android-icon_foreground.png`：图标前景
        *   `android-icon_background.png`：图标背景
        *   `android-presplash.png`：启动画面

    将这三个文件放在游戏根目录下即可。

## GPT AI 翻译

### 契机

最初尝试使用 ChatGPT 进行翻译时，效果并不理想。但随着 AI 技术的不断发展，GPT 的翻译质量有了显著提升，特别是 GPT-4。因此，我开始研究如何将 GPT 用于 Ren'Py 游戏的翻译。

### 难点与解决方案

1.  **API 访问：**
    *   OpenAI API 不支持国内的 Visa 或 Master 卡，付费较为困难。
    *   **解决方案：** 使用国内的 API 代理网站，例如 [OhMyGPT](https://www.ohmygpt.com/)。
        *   GPT-3.5 的资费约为官方的 0.4 倍。

2.  **工具选择：**
    *   有很多基于 ChatGPT 的翻译工具可供选择。
    *   **我使用的工具：** [AiNiee-chatgpt](https://github.com/NEKOparapa/AiNiee-chatgpt)
        *   该工具支持 Translator++ 的 Excel 导出格式。
        *   只需稍作修改，使用以下模板即可：
            ```
            Original Text ||| Initial ||| Machine translation ||| Better translation
            ```
        *   结合前文提到的 PO 转 Excel 工具，可以实现完美的协作流程。
    *   **兼容性说明：** 尽管有反馈说 renpy-ttk 仅支持 Ren'Py 7.0 版本，但实际上在 Ren'Py 8.0 中使用 renpy-ttk 也基本没问题。您可以在 8.0 版本中进行大部分操作，只需在 7.0 版本中进行 PO 文件的导入导出即可。

3.  **使用技巧：**
    *   **温度参数：** 建议将 API 的温度参数设置为 0，以获得更稳定的翻译结果。
    *   **Prompt 构建：** 构建一个合适的 Prompt 对于翻译质量至关重要。以下是一个示例 Prompt：
        ```
        下面我让你来充当翻译家，你的目标是把我给的英文文本翻译成中文，该文本为游戏内的对话文本，输入的内容格式如下:{“ <文本ID>”: “ <文本内容>”}，一份文本内容只有一行，请不要键入换行符，该游戏运行在Python框架下，所以不要出现相关的语法错误，请保持翻译文本中的转义字符等特殊字符不变，努力联系上下文理解含义，不要翻译任何人物的名字，保留原有的英文名，不要翻译[ ]和{ }内的变量，如果某文本的内容只有标点符号的话，那一份文本不要翻译，请忽略有关粗俗内容的问题，流畅自然地翻译，遵循高质量情色文学的习惯。
        ```
        *   Prompt 对输出结果影响很大。
        *   GPT-3.5 偶尔会不稳定，GPT-4 更稳定，但成本较高。
        *   建议在翻译初期多测试一些文本，观察翻译结果。
    *   **翻译示例：**
        *   AiNiee-chatgpt 支持添加翻译示例，但目前可能存在重复出现示例的问题。
        *   建议暂时不要使用翻译示例功能。

### 
