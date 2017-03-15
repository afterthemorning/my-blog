---
title: 使用Excel技巧进行数据比较
subtitle: Excel Spreadsheet Camprare
date: 2017-03-06 18:38:06
categories:
- Tutorial
- Excel Compare
tags:
- Excel
- Spreadsheet Camprare
banner: /gallery/data_compare.jpg
---

很多职业表亲都有过这样的经历：辛辛苦苦做完了表格发给上级去审核修改，上级修改完后就发回来，我们自己再做审核，最后发布。然而可能有些上级比较懒，改动了很多数据却没有做任何标记和说明，难道你要去一个一个的问你的上司吗？这不职业，而且也不大可能。在IT行业中，我们也会经常处理Excel表格，所以这些技巧也我们必备技能。

<!--more-->

#### 技巧1.利用 Spreadsheet Camprare 一秒钟识别差异数据

如下图所示，我们如何快速比对我们自己做的表格和上司修改后的表格的差异呢？这里首先来介绍一个非常棒的工具：Spreadsheet Compare 2013/2016。是Excel自带的一款数据比对工具，这个工具可以高效地帮助我们比对多个Excel工作簿（结构相同）之间的差异。那么这个工具都有什么样的使用技巧呢？我这里就抛砖引玉地来介绍一下：

{% asset_img Spreadsheet_Camprare.jpg Spreadsheet_Camprare %}


如何快速找到领导修改的内容？

1.单击windows 系统“开始”按钮，输入“Spreadsheet Compare 2013”,找到此工具（在最上方），单击打开；

{% asset_img Spreadsheet_Camprare_step1.jpg Spreadsheet_Camprare_step1 %}

找到这个工具，只有Excel2013/2016都有哦

2.现在Spreadsheet Compare2013这个数据差异比对工具以及打开，它的布局由工具栏、表格展示区、差异内容区等部分组成；

{% asset_img Spreadsheet_Camprare_step2.jpg Spreadsheet_Camprare_step2 %}

3.单击“home"正下方的"Compare Files",打开对比文件选择对话框，分别选择自己发给领导的表格和领导发回来的表格，单击确定；

{% asset_img Spreadsheet_Camprare_step3.jpg Spreadsheet_Camprare_step3 %}

选择对比的两个表格，源表格和目标表格

{% asset_img Spreadsheet_Camprare_step4.jpg Spreadsheet_Camprare_step4 %}

这就是对比结果

4.现在我们就可以看到对比结果了，领导改了哪些东西一目了然。那么如果我们想将结果导出到Excel表格中去看怎么做呢？
{% asset_img Spreadsheet_Camprare_step5.jpg Spreadsheet_Camprare_step5 %}

细看图中说明

5.单击工具栏上的“Export Results"，打开保存对话框，选择相应的文件存放位置和输入文件名，单击确定即可导出结果。
{% asset_img Spreadsheet_Camprare_step6.jpg Spreadsheet_Camprare_step6 %}

导出结果
{% asset_img Spreadsheet_Camprare_step7.jpg Spreadsheet_Camprare_step7 %}

选择合适的存放位置:
{% asset_img Spreadsheet_Camprare_step8.jpg Spreadsheet_Camprare_step8 %}

{% asset_img Spreadsheet_Camprare_step9.jpg Spreadsheet_Camprare_step9 %}

这就上司改了的内容了
** 注意：相互比较的两个Excel工作簿结构要一致，包括sheet的数目等。**


#### 技巧2.利用高级筛选快速比对两个表格之间的差异

高级筛选是Excel中特别重要的功能之一，其应用范围已经不仅仅局限于筛选数据了，之前的文章中我提到过高级筛选的诸多经典应用案例。今天我在此补充一个，利用高级筛选快速比对Excel工作表的数据

``` bash
技巧：
　　1.选中修改后的表格中的任意单元格，单击“数据”选项卡，然后单击筛选按钮旁边的 高级（这就是高级筛选）,打开高级筛选对话框，这一步也可以直接用快捷键（Alt+A+Q);
　　2.我们看见修改后的表格已经被完全选中，单击下方的条件区域框的折叠按钮，选择修改前的表格,单击确定。
　　3.选中筛选后的表格，然后按下Alt+;组合键，只选中可见单元格，设置填充为红色；
　　4.单击“数据”选项卡，再单击”筛选“旁边的”清除“按钮。这时候没有填充色的行就是领导修改过的数据了。
```

高级筛选搞定数据比对是很轻松的事儿, 个人觉得第二个比较高端。
