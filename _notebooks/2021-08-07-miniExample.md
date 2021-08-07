---
jupyter:
  jupytext:
    formats: ipynb,md
    text_representation:
      extension: .md
      format_name: markdown
      format_version: '1.3'
      jupytext_version: 1.10.1
  kernelspec:
    display_name: python37
    language: python
    name: python37
---

# 最小示例

从头开始创建 nbdev 项目的最小端到端示例

本节假设您已通过[教程](https://nbdev.fast.ai/tutorial.html)。以下是从零开始创建 nbdev 项目的最小示例，其中有一些评论说明了为什么某些事情会以他们的方式工作。

例如，我们将使用[艾伦唐尼的优秀书，想想Python2](https://github.com/AllenDowney/ThinkPython2)的代码，特别是[卡](https://github.com/AllenDowney/ThinkPython2/blob/master/code/Card.py)模块。我们不会涵盖所有功能，因为我们专注于为您提供足够的信息，使之富有成效。我们建议您在完成此示例后阅读[文档的](https://nbdev.fast.ai/)其余部分。`nbdev`

## 第 1 步： 设置您的 nbdev Github[](https://nbdev.fast.ai/example.html#Step-1:-Setup-your-nbdev-GitHub-Repo)[](https://nbdev.fast.ai/example.html#Step-1:-Setup-your-nbdev-GitHub-Repo)

根据[教程中的](https://nbdev.fast.ai/tutorial.html)说明，我们将使用[模板](https://github.com/fastai/nbdev_template)制作一个新的存储库。在这种情况下，我们制作一个名为["deck\_of\_cards：](https://github.com/fastai/deck_of_cards)

**注：**如果您计划编写可安装的 Python 模块，我们强烈建议以您的 Python 模块命名您的回购。

![图像.png](https://nbdev.fast.ai/images/att_00010.png)

在此之后，您将有一个具有必要文件的回购开始。您还应[设置 nbdev，](https://nbdev.fast.ai/tutorial.html#Set-up-Your-Jupyter-Server)并根据[教程](https://nbdev.fast.ai/tutorial.html)中的说明[安装吉图克](https://nbdev.fast.ai/tutorial.html#Install-git-hooks)。

## 第 2 步：修改配置文件[](https://nbdev.fast.ai/example.html#Step-2:-Modify-Configuration-Files)[](https://nbdev.fast.ai/example.html#Step-2:-Modify-Configuration-Files)

### 编辑设置.ini[](#Edit-settings.ini)[](#Edit-settings.ini)

[编辑设置.ini](https://nbdev.fast.ai/tutorial.html#Edit-settings.ini)需要nbdev才能正常工作。这些设置用于填充所需的信息，供您在[GitHub 页面](https://nbdev.fast.ai/tutorial.html#Github-pages)上托管文档，以及[将模块作为包发布到 pypi](https://nbdev.fast.ai/tutorial.html#Upload-to-pypi)。

这些是我们在设置中更改的字段[.ini：](https://github.com/fastai/deck_of_cards/blob/master/settings.ini)

lib\_name \= deck\_of\_cards
description \= "A minimal example of nbdev using code from Allen Downey's Think Python 2nd Ed"
keywords \= nbdev
author \= Hamel Husain
author\_email \= hamel@example.com
copyright \= Hamel, inc.
user \= fastai

**注意：**此示例中用户的价值实际上并没有更改，但您必须将其更改为 GitHub 存储库（通常是您的用户名）对应的组织。

设置.ini文件中的值会自动传到各种系统，这有助于最大限度地减少样板和学习复杂的配置文件。例如

*   setup.py[阅读巨](https://github.com/fastai/deck_of_cards/blob/master/setup.py)蛇包装的字段和字段。`author``author_email`
*   [setup.py](https://github.com/fastai/deck_of_cards/blob/master/setup.py)和[Jekyll](https://jekyllrb.com/)的配置文件[（\_config.yaml）](https://github.com/fastai/deck_of_cards/blob/master/docs/_config.yml)都使用该文件，以确保渲染文档在 GitHub 页面上正确配置。`lib_name`

## 第 3 步：编写代码（或将代码复制/粘贴到笔记本中）[](https://nbdev.fast.ai/example.html#Step-3:-Write-Code-(Or-Copy/Paste-Into-A-Notebook))[](https://nbdev.fast.ai/example.html#Step-3:-Write-Code-(Or-Copy/Paste-Into-A-Notebook))

接下来，我们从[ThinkPython2回购中取出卡模块](https://github.com/AllenDowney/ThinkPython2/blob/master/code/Card.py#L17)，并将其写入nbdev。

第一步是将课程从[Card.py](https://github.com/AllenDowney/ThinkPython2/blob/master/code/Card.py)复制并粘贴到一个新的Jupyter笔记本中，我们将其命名为[00\_card.ipynb。](https://github.com/fastai/deck_of_cards/blob/master/00_card.ipynb)复制和粘贴来自巨蛇文件的代码是将现有巨蛇脚本转换为 Jupyter 笔记本的合理方法。将大块代码复制到笔记本中的一个有用的技巧是将整个文件复制到单个单元格中，并用于将代码拆分为单独的单元格。`Card``ctrl-shift-minus`

如果您尝试将现有的巨蛇项目转换为，我们建议逐步将特定文件转换为随着时间的推移。具体来说，我们建议选择一个巨蛇文件开始喜欢下面的例子。`nbdev``nbdev``card.py`

**注：**不需要文件名开头的号码：这是一个约定，我们用来保持笔记本在一个理想的顺序，当他们由文件系统排序。

在笔记本的第一个单元格[中](https://github.com/fastai/deck_of_cards/blob/master/00_card.ipynb)，写一个类似这样的评论（这是不需要的，但我们在这里做，以突出nbdev的一个重要功能）：

\# default\_exp card

在这种情况下，参数指定从本笔记本导出的代码将默认放置在目的地。您可以在这里阅读更多关于如何从笔记本创建巨蛇模块[。](https://nbdev.fast.ai/export.html)安排笔记本的合理方式是这样的：`card``card.py`

![图像.png](https://nbdev.fast.ai/images/att_00011.png)

### 标志[](#Flags)[](#Flags)

nbdev 使用特殊注释或标记作为加价语言，允许您控制文档的各个方面以及代码如何导出到模块，以及代码如何测试。此外，本笔记本中还附有以下其他标志：`default_exp`

`#hide`

**注：**此评论指示 nbdev 在生成文档时隐藏此单元格。

`#export`

**注：**此评论指示 nbdev 将此单元格导出到适当的巨蛇文件。当没有提供[`输出`](https://nbdev.fast.ai/export.html)参数时，此默认为上述所指明的模块。`default_exp`

### 魔法发生的地方：编写文档和测试[](https://nbdev.fast.ai/example.html#Where-The-Magic-Happens:-Write-Documentation-And-Tests)[](https://nbdev.fast.ai/example.html#Where-The-Magic-Happens:-Write-Documentation-And-Tests)

在原始代码基座中，卡测试是分开的，位于[Card\_test.py。](https://github.com/AllenDowney/ThinkPython2/blob/master/code/Card_test.py)此外，文档主要位于 Allen 回购[的图书文件夹](https://github.com/AllenDowney/ThinkPython2/tree/master/book)以及文档中的某些文档中。虽然这是 Python 项目的典型安排，但我们相信，通过将文档、测试和源代码组织到单个上下文中，可以简化您的工作流程。我们相信，这允许开发人员编写更高质量的文档和代码，并鼓励进行更多的测试。`Card``nbdev`

以下是卡的文档+代码外观：

![图像.png](https://nbdev.fast.ai/images/att_00012.png)

这些评论和测试由文档系统提供，该文档系统在后一节中讨论。此外，断言语句自动成为由[GitHub 存储库中默认的 nbdev 中连续集成系统设置](https://nbdev.fast.ai/tutorial.html#CI)运行的测试。

**注：**nbdev 编程环境为您设置了[连续集成 （CI）](https://nbdev.fast.ai/tutorial.html#CI)系统。您不必为启用它而做任何额外的事情，并且它立即开始工作。这对没有 CI 经验的人来说尤其伟大：这是一个温柔的方式开始使用它。

**重要：**Fastcore[的测试公用设施提供测试公用设施，这些公用设施](https://fastcore.fast.ai/test.html)提供环绕常见类型的断言语句的包装，并提供更好的默认错误消息。使用这些是可选的，但建议。

### 编辑索引.ipynb[](#Edit-index.ipynb)[](#Edit-index.ipynb)

`nbdev` 存储库需要一个命名的笔记本，当您使用模板时，该笔记本包含在您的存储库中。 有两个目的：`index.ipynb``index.ipynb`

1.  它成为您的回购的阅读（此笔记本已转换为`README.md`)
2.  它成为您的文档的主页（）。`index.html`

您将注意到以下样板：`index.ipynb`

from your\_lib.core import \*

您应该删除此代码行或将其评论出来，因为它会导致语法错误。稍后，当您完成创建模块时，您可以用适当的导入语句替换此模块。我们故意将这条线路留在此处，以便您体验持续集成系统（上面讨论）如何警告您错误。

## 第 4 步：将笔记本转换为 Python 模块和文档[](https://nbdev.fast.ai/example.html#Step-4:--Convert-Notebooks-To-Python-Modules-&-Docs)[](https://nbdev.fast.ai/example.html#Step-4:--Convert-Notebooks-To-Python-Modules-&-Docs)

从回购的根部**运行命令[`nbdev_build_lib。`](https://nbdev.fast.ai/export2html.html#nbdev_build_lib)** 此出口标记为适当的巨蛇模块的笔记本单元。例如，笔记本[00\_cards.ipynb](https://github.com/fastai/deck_of_cards/blob/master/00_card.ipynb)被转换为[card.py。](https://github.com/fastai/deck_of_cards/blob/master/deck_of_cards/card.py)`#export`

**运行命令[`nbdev_test_nbs`](https://nbdev.fast.ai/test.html#nbdev_test_nbs)**运行代码和测试的所有笔记本。此命令还由[nbdev 为您设置的连续集成系统](https://nbdev.fast.ai/tutorial.html#CI)运行，但本地运行这些测试以获得即时反馈是有用的。

**注意：**有一种方法可以选择性地跳过某些运行时间长或速度慢的测试，方法是使用[此处描述](https://nbdev.fast.ai/test.html)的特殊标签

### 预览文档[](#Preview-The-Docs)[](#Preview-The-Docs)

要预览文档，请从回购的根部运行命令。此命令在幕后为您运行 CLI 命令[`nbdev_build_docs，`](https://nbdev.fast.ai/export2html.html#nbdev_build_docs)该命令从笔记本生成文档站点。运行此命令后，您将在终端中看到一个 URL，指示文档已在本地托管的位置。对于我们用于此示例的[快车/deck\_of\_cards](https://github.com/fastai/deck_of_cards/)存储库，网址是`make docs_serve``http://127.0.0.1:4000/deck_of_cards/`

如果您浏览到卡片页面，您将看到我们刚刚编写的文档，我们已注释以供进一步解释：`http://127.0.0.1:4000/deck_of_cards/card.html`

![图像.png](https://nbdev.fast.ai/images/att_00016.png)

#### 注释说明：[](https://nbdev.fast.ai/example.html#Explanation-of-annotations:)[](https://nbdev.fast.ai/example.html#Explanation-of-annotations:)

1.  标题**卡**对应于笔记本中的第一个标题，并附有注释块*API 详细信息*作为摘要。`H1`

2.  `nbdev` 自动为您呈现内容表。

3.  `nbdev` 自动呈现您的类的签名或作为标题的功能。

4.  `nbdev` 自动在 GitHub 上添加指向相应源代码（这是一个纯文本巨蛇文件）的链接。请记住，将 Jupyter 笔记本转换为具有命令[`nbdev_build_lib`](https://nbdev.fast.ai/export2html.html#nbdev_build_lib)的源代码。`nbdev`

5.  文档的这一部分从文档串中自动呈现。

6.  笔记本的其余部分通过将减价转换为 HTML、显示每个单元格的输入和输出（包括图表和图像）等进行渲染。您可以使用[此页面上描述的标记](https://nbdev.fast.ai/export2html.html)隐藏整个单元格，仅隐藏单元格输入或仅隐藏输出。

7.  nbdev 支持在文档中呈现为彩色框的特殊块报价。你可以[在这里](https://nbdev.fast.ai/export2html.html#add_jekyll_notes)阅读更多关于他们。在此特定示例中，我们使用块报价。`Note`

8.  在背板中环绕的单词将在适当情况下自动超链接到相关文档。这是一个微不足道的情况，即类立即定义在上面，但是这跨页面和模块工作。我们将在以后的步骤中看到另一个例子。`Card`

### show\_doc[](#show_doc)[](#show_doc)

[`show_doc`](https://nbdev.fast.ai/showdoc.html#show_doc)允许您控制文档在文档上显示的。您可以控制文档呈现的位置、顺序、标题和其他详细信息。你可以[在这里阅读更多关于它](https://nbdev.fast.ai/showdoc.html#show_doc)。例如，这是如何使用[`show_doc`](https://nbdev.fast.ai/showdoc.html#show_doc)来渲染文档的方法（注意测试如何自然地包含在文档下面）：`__eq__``Card`

![图像.png](https://nbdev.fast.ai/images/att_00017.png)

#### 关于[`show_doc`](https://nbdev.fast.ai/showdoc.html#show_doc)的重要说明：[](https://nbdev.fast.ai/example.html#Important-Notes-about-show_doc:)[](https://nbdev.fast.ai/example.html#Important-Notes-about-show_doc:)

*   **对于函数和类，默认[`情况下，在`](https://nbdev.fast.ai/showdoc.html#show_doc)**定义函数或类的同一位置自动调用show\_doc。这就是为什么您在上面的文档示例中看到类的标题，即使从未明确调用[`show_doc。`](https://nbdev.fast.ai/showdoc.html#show_doc) `Cards`
    *   您可以通过在所需的位置明确调用[`show_doc`](https://nbdev.fast.ai/showdoc.html#show_doc)来覆盖此默认值。
*   **对于方法，您必须调用[`show_doc，`](https://nbdev.fast.ai/showdoc.html#show_doc)**以便出现文档，如上图所示。这是根据设计进行的，因为与函数不同，您通常会在单个连续代码块中定义类的所有方法。因此[`，show_doc`](https://nbdev.fast.ai/showdoc.html#show_doc)允许您控制文档标题的顺序和放置，以便您编写散文和测试在适当标题下组织的每种方法的方法。`Card.__eq__`
*   我们建议通过编辑笔记本和重新渲染文档（如下所述）来尝试[`show_doc，`](https://nbdev.fast.ai/showdoc.html#show_doc)以查看不同场景中发生的情况。

### 刷新文档[](#Refresh-the-docs)[](#Refresh-the-docs)

如果您要编辑文档，可以更改相应的笔记本（s），然后运行[`nbdev_build_docs`](https://nbdev.fast.ai/export2html.html#nbdev_build_docs)然后在浏览器中[硬刷新](https://www.getfilecloud.com/blog/2015/03/tech-tip-how-to-do-hard-refresh-in-browsers/#.X52j8lNKjng)以重新呈现文档。

## 第 5 步：将文件推送至 GitHub 并查看托管文档[](https://nbdev.fast.ai/example.html#Step-5:-Push-Files-To-GitHub-And-View-Hosted-Docs)[](https://nbdev.fast.ai/example.html#Step-5:-Push-Files-To-GitHub-And-View-Hosted-Docs)

此步骤假设您已[启用 GitHub 页面](https://nbdev.fast.ai/tutorial.html#Github-pages)。

此时，我们准备将您的第一个文件推送至 GitHub。如果您[已按照教程说明安装了 git 钩](https://nbdev.fast.ai/#Avoiding-and-handling-git-conflicts)，将自动清除笔记本中不必要的元数据，以避免冲突和过于冗长的差异。在第一次将文件推至 GitHub 之前，我们建议运行命令，以便您可以查看为您生成的所有文件。您会注意到创建了以下文件：`nbdev``git status``nbdev`

*   `.py` 文件对应于您创建的笔记本，在文件夹中对应于库名称，在这种情况下，这称为[deck\_of\_cards。](https://github.com/fastai/deck_of_cards/tree/master/deck_of_cards)例如，文件会自动创建在适当的目录中，以便组织一个巨蛇模块。`__init__.py`
*   文件文件为您的文档网站在文件夹中。此目录包含用于在 GitHub 页面托管文档网站的 HTML、CSS 和其他文件。`docs/`

在推送 GitHub 之前，请确保将所有这些文件添加到您的提交中，因为它们都是正常工作所需的一切。`git add`

将文件推至 GitHub 将[自动触发使用 GitHub 操作的连续集成 （CI）。](https://nbdev.fast.ai/#Using-nbdev-as-part-of-your-CI)CI 将自动执行[此处概述](https://nbdev.fast.ai/tutorial.html#CI)的多项检查。您可以通过导航到 GitHub 回购中的"操作"选项卡，在 GitHub 操作中查看 CI 进程。

推档后，GitHub 将自动重建文档。您可以通过转到存储库设置并在选项下查找 GitHub 页面部分来查看文档生成的状态。当 GitHub 正在构建页面时，它看起来像这样：

![图像.png](https://nbdev.fast.ai/images/att_00018.png)

页面构建完成后，颜色和状态消息将更改为：

![图像.png](https://nbdev.fast.ai/images/att_00019.png)

此外，假设您已经[启用了 GitHub 页面](https://nbdev.fast.ai/tutorial.html#Github-pages)，则可以随时查看您的 Github 页面部署状态。如果添加到存储库的 GitHub URL，您将看到部署仪表板。例如，下面是推新文件后[立即 https://github.com/fastai/deck\_of\_cards/deployments](https://github.com/fastai/deck_of_cards/deployments)屏幕截图：`/deployments`

![图像.png](https://nbdev.fast.ai/images/att_00021.png)

## 第 6 步：添加更多代码[](https://nbdev.fast.ai/example.html#Step-6:-Add-More-Code)[](https://nbdev.fast.ai/example.html#Step-6:-Add-More-Code)

恭喜你，你用nbdev编写了你的第一个代码！但是，要全面掌握 nbdev 的工作原理，在导入您之前编写的代码的新笔记本中添加附加代码是值得的。接下来，我们将在名为[01\_deck.ipynb](https://github.com/fastai/deck_of_cards/blob/master/01_deck.ipynb)的新笔记本[中添加甲板类表单](https://github.com/AllenDowney/ThinkPython2/blob/master/code/Card.py#L55)cards.py。此笔记本导入以前创建的类并创建一个，这是卡的集合：`Card``Deck`

![图像.png](https://nbdev.fast.ai/images/att_00022.png)

与前一个笔记本类似，第一个单元格具有 nbdev 标志，这意味着标有代码块的代码块将默认导到文件中。您可以看到我们导入对象并将该代码导出到以下代码单元格：`# default_exp deck``#export``deck.py``Card``deck.py`

#export
from deck\_of\_cards.card import Card

这工作，因为cli命令[`，nbdev_build_lib`](https://nbdev.fast.ai/export2html.html#nbdev_build_lib)转换为，我们已经进口在这里。`00_card.ipynb``card.py`

### 测试[](#Tests)[](#Tests)

唐尼的代码包含一个测试类在一个单独的文件称为[Card\_test.py。](https://github.com/AllenDowney/ThinkPython2/blob/master/code/Card_test.py)此文件是一个很好的例子，突出了 . 的优势.此文件的内容如下：`Deck``nbdev`

"""This file contains code for use with "Think Stats",
by Allen B. Downey, available from greenteapress.com
Copyright 2014 Allen B. Downey
License: GNU GPLv3 http://www.gnu.org/licenses/gpl.html
"""

from \_\_future\_\_ import print\_function, division

import unittest
from Card import Card, Deck

class Test(unittest.TestCase):

    def testDeckRemove(self):
        deck \= Deck()
        card23 \= Card(2, 3)
        deck.remove\_card(card23)

if \_\_name\_\_ \== "\_\_main\_\_":
    unittest.main()

上述代码存在问题，原因如下：

*   目前尚不清楚测试的目的是什么。
*   测试位于与实现分开的文件中，因此您必须打开多个窗口和/或切换上下文才能理解测试。
*   测试使用 api，如果你想写测试，你必须学习和思考。`unittest`
*   测试与文档和任何与解释类所做的事情相关的散文是分开的。`Deck`

所有这些问题都是在 nbdev 中处理的，因为您可以在相同的上下文中编写代码、文档和测试。以下是[01\_deck.ipynb](https://github.com/fastai/deck_of_cards/blob/master/01_deck.ipynb)相关部分的屏幕截图，该部分以更可读、更表达的方式表示代码和此测试：

![图像.png](https://nbdev.fast.ai/images/att_00023.png)

上述代码表示相同的单元测试，但也集成了文档与甲板的原始实施。您可以[在](https://github.com/fastai/deck_of_cards/blob/master/01_deck.ipynb)此处查看 GitHub 上的笔记本。本笔记本中显示的另外一个工具是[`show_doc`](https://nbdev.fast.ai/showdoc.html#show_doc)功能，它可以控制文档的位置。在此示例中，将在文档中创建具有适当标题的部分。`nbdev``showdoc(Deck.remove_card)`

如果您运行 CLI 命令，则可以预览这些文档在本地的外观。以下是此外观的注释屏幕截图：`make docs_serve`

![图像.png](https://nbdev.fast.ai/images/att_00024.png)

#### 注释说明：[](https://nbdev.fast.ai/example.html#Explanation-of-annotations:)[](https://nbdev.fast.ai/example.html#Explanation-of-annotations:)

1.  在编写这些文档时，我们只是用背板封闭。 自动将其转换为与文档的相应页面的超链接。`Card``nbdev``Card`

2.  这个标题的方法是由[`show_doc`](https://nbdev.fast.ai/showdoc.html#show_doc)创建的。`Deck.remove_card`

3.  `nbdev` 旨在鼓励您编写测试，作为此处所示文档的一部分。

你可以看到这个页面直播[在 https://fastai.github.io/deck\_of\_cards/deck.html。](https://fastai.github.io/deck_of_cards/deck.html)

完成后，请确保在向 GitHub 推之前运行以下 cli 命令。

*   [`nbdev_build_lib：`](https://nbdev.fast.ai/export2html.html#nbdev_build_lib)这会将笔记本转换为模块。
*   [`nbdev_build_docs：`](https://nbdev.fast.ai/export2html.html#nbdev_build_docs)这将生成您的文档站点。
*   [`nbdev_test_nbs：`](https://nbdev.fast.ai/test.html#nbdev_test_nbs)这运行你所有的测试（这是一个好主意，这样你就可以赶上错误）。
*   `git status` 查看哪些文件已更改，这是一个很好的练习，当第一次开始了解哪些文件是自动生成的。`nbdev`

## 第 7 步：将 Python 模块发布到 Pypi[](https://nbdev.fast.ai/example.html#Step-7:-Publish-Python-Module-to-Pypi)[](https://nbdev.fast.ai/example.html#Step-7:-Publish-Python-Module-to-Pypi)

您可以按照[这些说明](https://nbdev.fast.ai/tutorial.html#Upload-to-pypi)将模块发布到 pypi。

## 引用[](#References)[](#References)

此示例的所有代码均可在 GitHub 回购[快泰国/deck\_of\_cards](https://github.com/fastai/deck_of_cards)上找到。

### 实时演示[](#Live-Demo)[](#Live-Demo)

下面的视频显示了此示例的实时演示，结尾有问答部分。

![公司徽标](https://nbdev.fast.ai/assets/images/company_logo.png)

```python

```
