# Vim

## 执行系统命令
`!whoami`

## vim 对应按键 似乎不区分大小写
```
C -> Ctrl
S -> Shift
tab 对应 tab 键
<Leader>默认是\
<Space> 对应空格键

alt 键在 iTerm2 需要更改 profiles->keys->left option key 为Esc+
<Alt>          A 
<BS>           Backspace
<Tab>          Tab
<CR>           Enter
<Enter>        Enter
<Return>       Enter
<Esc>          Escape
<Space>        Space
<Up>           Up arrow
<Down>         Down arrow
<Left>         Left arrow
<Right>        Right arrow
<F1> - <F12>   Function keys 1 to 12
#1, #2..#9,#0  Function keys F1 to F9, F10
<Insert>       Insert
<Del>          Delete
<Home>         Home
<End>          End
<PageUp>       Page-Up
<PageDown>     Page-Down
<bar>          the '|' character, which otherwise needs to be escaped '\|'
```

### map映射
```
对于映射可能有以下几种前缀：
nore ：表示非递归（no recursion）
n    ：表示正常模式下生效
v    ：表示可视模式下生效
i    ：表示插入模式下生效
c    ：表示命令模式下生效
```

> noremap表示非递归，递归映射就是 map a b   ；再 map b c , 那么按下 a=c，默认的map就是递归的，加nore，比如noremap 就是非递归的。
unmap后面跟着一个按键组合，表示删除这个映射，同样，unmap可以加各种前缀，表示影响到的模式
mapclear直接清除相关模式下的所有映射。同样，mapclear可以加各种前缀，表示影响到的模式

```
map	noremap	unmap	mapclear
nmap	nnoremap	nunmap	nmapclear
vmap	vnoremap	:vunmap	vmapclear
imap	inoremap	iunmap	imapclear
cmap	cnoremap	cunmap	cmapclear

example
nmap <leader>s  :echo <CR>
表示按下了leader键（我的设置为了\)和s键后，执行:echo命令，<CR>代表了回车

vmap <C-c>  +y
表示在可视模式下，按ctrl+c复制选中的内容
```
### 键表
- <k0> - <k9> 小键盘 0 到 9 
- <S-...> Shift＋键 
- <C-...> Control＋键 
- <M-...> Alt＋键 或 meta＋键 
- <A-...> 同 <M-...> 
- <Esc> Escape 键 
- <Up> 光标上移键 
- <Space> 插入空格 
- <Tab> 插入Tab 
- <CR> 等于<Enter>

## 特殊参数
有些特殊参数必须映射命令的后边，在其他任何参数的前面。
```
<buffer>
<buffer>如果这些映射命令的第一个参数是<buffer>，映射将只局限于当前缓冲区（也就是你此时正编辑的文件）内。比如： 
:map <buffer> ,w /a<CR> 
它的意思时在当前缓冲区里定义键绑定，“,w”将在当前缓冲区里查找字符a。同样你可以在其他缓冲区里定义： 
:map <buffer> ,w /b<CR> 
比如我经常打开多个标签(:tabedit)，想要在各自标签里定义”,w”键绑定，那么你只要在每个标签页里分别定义就可，其作用域也只在各自的标签里。同样要清除这些缓冲区的键绑定也要加上<buffer>参数，比如： 
:unmap <buffer> ,w 
:mapclear <buffer>

<silent>
<silent>是指执行键绑定时不在命令行上回显，比如： 
:map <silent> ,w /abcd<CR> 
你在输入,w查找abcd时，命令行上不会显示/abcd，如果没有<silent>参数就会显示出来。

<special>
<special>一般用于定义特殊键怕有副作用的场合。比如： 
:map <special> <F12> /Header<CR>

<expr>
<expr>. 如果定义新映射的第一个参数是<expr>，那么参数会作为表达式来进行计算，结果使用实际使用的，例如： 
:inoremap <expr> . InsertDot() 
这可以用来检查光标之前的文本并在一定条件下启动全能 (omni) 补全。 

<unique>
<unique>一般用于定义新的键映射或者缩写命令的同时检查是否该键已经被映射，如果该映射或者缩写已经存在，则该命令会失败
```

## Vim 的基本模式：

如果想正确操作上面的命令你的先理解Vim的三种模式：

## 普通模式：

进入vim后最初的模式，在这种模式下面你可以输入任何不限于上面的那些编辑命令，在其他模式下只要多按几下ESC键就回到了普通模式

## 插入模式：

在普通模式下输入字符‘i'等插入命令，vim就进入了插入模式，在该模式下面可以插入文本字符。

## 命令行模式：
这个模式用于在编辑器底部执行命令，例如:wq等等，如果从插入模式下面切换到命令行模式或者普通模式呢，用ESC键。
```
 vim 打开 VIM
 vim filename 打开文件 若不存在则创建该文件
 :w 保存
 :q 退出
 :wq 保存后退出 == :x
 :w 强制保存 其他同理

:set filetype=python    #设置默认语言
:set tabstop=4          #设置tab默认为4个空格
:set nu                 #vim窗口左侧显示行号 == :set number
:set ruler              #在vim窗口显示当前光标位置
```
### :nonu 撤销配置 不显示行号  其他同理

CTRL+f：向下翻一页
CTRL+b：向上翻一页
CTRL+d：向下翻半页
CTRL+u：向上翻半页
w：移动到下一个单词的起始处（既然是w，代表的意思就是word，好记吧）
W：移动到下一个单词的起始处
b：移动到前一个单词的起始处
B：移动到前一个单词的起始处（b和B的区别与w和W是同理的）
i/insert 插入
p paste
x 删除当前字符
dd 删除当前行
0（零）：移动到行首
u 撤销操作
$：移动到行未
^：移动到当前行的第一个非空字符处（如果该行首没有空格，那么效果与0是一样的）
g_：移动到当前行的最后一个非空格字符处
i：在当前光标位置插入字符
o：在当前行往下插入新的一空行
O：在当前行往上插入新的一空行
a：在当前光标后追加字符
R：替换当前光标的字符直到推出插入模式（按ESC）
:r filename：把文件名为filename的内容插入当当前行的下一行
:r! command：把command返回的结果插入到当前行的下一行
yw：拷贝当前的一个单词
y0：拷贝的范围是当前光标处到行首
y$：拷贝的范围是当前光标处到行尾
yy：拷贝当前行
nyy：从当前行开始拷贝n行（这里的n是数字）
x：删除当前光标处字符（严格来说x不属于插入，因为你还要按i才能插入）
dw：删除当前光标出一个单词
d0：删除光标处到行首的字符
d$：删除光标处到行尾的字符
dd：删除整行
ndd：删除n行（同样n代表数字）

## Search：
```
:set ignorecase  搜索时忽略大小写
/sting  向下搜索
?string 向上搜索
:set hlsearch
```

## 文件编辑
```
:undo 撤销
:redo 恢复
```

### 复制
1. 将光标移动到要开始的地方
2. 按 `v` 进入 可视化模式
3. 移动光标到复制内容的结束 按 `y` 复制
4. `:1,2 copy 3` 将 1,2 两行复制到第三行 也可以 `1 copy 2 move` 同理

### 移动
1. `:1,2 move 3` 将 1,2 两行移动到第三行

### 粘贴
1. 正常模式下移动到要粘贴的地方 按 `p` 粘贴 行前复制则输入大写P

### 删除
1. `dd` 删除一行
2. `ndd` 删除以当前行开始的n行 如 `3dd` 删除当前及下边共三行

### 删除字符
1. `dw` 删除光标位置的字符(包含单词等连续字符 空格为间隔) 若是空格则会全部删除直到下一个字符位置
2. `ndw` 删除连续 n 个字符


## 位置移动
1. `G` 移动到最后一行 `nvim filename +` 编辑文件添加 `+` 也可以
2. `$` 移动到行尾
3. `:1` 跳转到指定行