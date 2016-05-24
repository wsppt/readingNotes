#VIM TUTOR

---

###第一章

####移动光标

* **`h`**: 向左
* **`j`**: 向下
* **`k`**: 向上
* **`l`**: 向右

####进入和退出

**`q!`**

不保存退出

**`wq`**

保存退出

####文本编辑-删除字符

**`x`**

删除光标所在位置的字符

####文本编辑-插入

**`i`**

在`正常`模式下,可以按下`i`键来插入文本.

**`a`**

当前文字的后面插入

**`A`**

行尾插入

###第二章

####从当前光标删除一个单词到末尾

**`dw`**

从光标处删除至一个单字/单词的末尾.

####从当前光标删除到行末

**`d$`**

从当前光标删除到行末

####删除多个

`[number]` `d` `object` 或者 `d` `[number]` `object`

* number: 代表执行命令的次数
* d:代表删除
* object:代表命令锁需要操作的对象

**object**

* w: 从当前光标当前位置到单字.单词末尾,包括空格.
* e: 从当前光标当前位置到单字,单词末尾,但是`不`包括空格.
* $: 从当前光标当前位置知道当前行末.

####删除正行

**`dd`**

可以删除正行

**`[number]dd`**

删除`[number]`行

####撤销类命令

**`u`(小写)**

撤销最后执行的命令.`undo`

**`U`(大写)**

撤销修正整行,回复到该行的原始状态.

**`CTRL-R`**

`redo`,撤销以前的撤销命令.

###第三章

####置入类命令

**`p`**

输入`p`将最后一次删除的内容置入光标之后.

####替换类命令

**`r`**

输入`r`和一个字符替换光标所在位置的字符.

####更改类命令

**`cw`**

改变一个单字,单词的部分或者全部.会进入文本插入状态.

####使用`C`指令的其他更改类命令

`[number]` `c` `object` 或者 `c` `[number]` `object`

对象参数和删除类命令是一致的. `w`代表单字,单词. `$`代表行末等等.

###第四章

####定位及文件状态

**`CTRL-G(g)`**

显示当前编辑文件中当前光标所在`行位置`以及`文件状态信息`.

**`G`**

输入大写G可以使得当前光标直接跳转到文件最后一行.

`[number](行号)`+`G` 输入行号,然后输入大写`G`,这样就可以直接跳到该行.

**`gg`**

输入`gg`可以是当前光标直接跳转到文件第一行

####搜索类命令

**`/`**

输入`/`加上一个字符串可以用以在当前文件中查找该字符串.要查找同上一次的字符串,只需要按`n`键.要向`相反`方向查找同上一次的字符串,请输入大写`N`即可.

**`?`**

逆向查找用`?`代替`/`

**`CTRL+o`和`CTRL+i`**

按住 `Ctrl` 键不放同时按下字母 `o`,回到之前的位置.重复按可以回退更多步.

`CTRL-I` 会跳转到较新的位置.

####配对括号的查找

**`%`**

输入`%`可以查找配对的括号`)`,`]`,`}`.

用来查找不配对的括号很有用.

####替换命令

**`:s/old/new/g`**

可以替换`old`为`new`.一行内全部替换.

`:s/old/new`只替换光标所在行的第一个匹配.

一些常用匹配:

* `#,#s/old/new/g`: 其中 `#,#` 代表的是替换操作的若干行中首尾两行的行号.
* `%s/old/new/g`: 替换整个文件中的每个匹配串,注意多了一个`%`.
* `%s/old/new/gc`: 会找到整个文件中的每个匹配串,并且对每个匹配串提示是否进行替换,注意多了一个`%`.

###第五章

####在vim内执行外部命令

**`:!`**

		:!ls 当因当前目录

####保存文件的更多信息

**`:w FILENAME`**

将文件的改动保存到文件中.

####一个具有选择性的保存命令

**`v motion :w FILENAME`**

存文件的部分内容.`v`进入可视化模式.

* 按`v`,选择要保存的部分.
* 按`:`,屏幕底部会出现`:'<,'>`
* 输入`:'<,'> w FILENAME`,会保存到该文件中.

####提取和合并文件

**`:r FILENAME`**

向当前文件中插入另外的文件的内容.

**`:r !command`**

读取外部命令的输出.

		:r !ls 可以读取ls命令的输出,并把他放置在光标下面.
		
###第六章

####打开类命令

**`o`和`O`**

* `o`(小写): 在光标的`下方`打开新的一行并进入插入模式.
* `O`(大写): 在光标`上方`打开新的一行.

####附加类命令

**`a`**

在光标之后插入文本.

**`i`**

在光标处插入文本.

####另外一个置换类命令的版本

**`R`**

输入大写的`R`可以连续替换多个字符.

替换模式与插入模式相似,不过每个输入的字符都会删除一个已有的字符.

####复制黏贴文本

**`y`复制文本,`p`黏贴文本**

`yw` 可以用来复制一个单词.

####设置类命令的选项

**`set ic`**

忽略大小写.

**`set noic`**

取消忽略大小写.

**`set hls`**

设置高亮

**`set n hls`或`:nohlsearch`**

取消高亮

**`set is`和`set nois`**

incsearch,`set is`可以设置增量搜索,用`set nois`取消增量搜索.
表示在你输入查找内容的同时,vim就开始对你输入的内容进行匹配.

**总结**

* '`ic`' '`ignorecase`':查找时忽略字母大小写
* '`is`' '`incsearch`':查找短语时显示部分匹配
* '`hls`' '`hlsearch`':高亮显示所有的匹配短语

 选项名可以用完整版本,也可以用缩略版本.
 
 在选项前加上 `no` 可以关闭选项.
 
###第七章

####获取帮助信息

**`:help <回车>`**

输入`CTRL-W CTRL-W`(连按2次)可以在窗口之间跳转.

`:q <回车>`可以关闭帮助窗口.

####创建启动脚本

**`edit ~/.vimrc`**

编辑`vimrc`文件

####补全功能

**`CTRL-D`和`TAB`**

		例如输入 :e
		接着按 CTRL-D 键,Vim 会显示以 e 开始的命令的列表.
		 然后按 <TAB> 键,Vim 会补全命令.

