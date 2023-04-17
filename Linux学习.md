# Linux学习

---------



# Linux常用基础命令



## 命令解析器

- shell就是命令解释器
- 命令解析器的作用：对用户输入到终端的命令进行解析，调用对应的执行程序

![image-20221020104930674](Linux学习.assets/image-20221020104930674.png)

​	用户在终端输入命令，由shell命令解释器对命令进行解析（按照 $PATH 环境变量搜索命令），解析成内核能够识别的指令，然后由内核执行命令，最后终端显示命令执行的结果。

​	<font color = red>注意：shell在寻找命令的时候是按照$PATH 环境变量去查找的，如果找到了就执行对应的命令，若找不到就报错，执行 echo $PATH 命令可以查看PATH环境变量的值。</font>

![image-20221020110758957](Linux学习.assets/image-20221020110758957.png)

- 常用的命令解析器：

  ```
  shell -- Bourne Shell
  	/bin/sh
  bash -- Bourne Again Shell
  	/bin/bash
  ```

  

- <font face = "楷体" size = 5>当前系统所使用的shell</font>

  ```
  echo $SHELL
  ```

- <font face = "楷体" size = 5>当前系统下有那些shell</font>

  ```
  cat  /etc/shells
  ```
  
  

## Linux下常用快捷键



### tab键的作用

- 补齐功能

  如：在终端输入his然后按下tab键，会补齐history命令；

  如：输入l然后按下tab键，会显示所有以l开头的命令。

- 补齐文件（包括目录和文件）

  例如：如果文件在执行ls或者cd等命令，然后按下tab键， 会显示当前目录下所有的文件。

  <font color = red>使用tab键的优点：减少用户输入，加快输入速度，减少出错机会。</font>



### 主键盘快捷键

- 遍历输入的历史命令

  从当前位置向上遍历：Ctrl + p ( **↑** )

  从当前位置向下遍历：Ctrl + n ( **↓** )

  <font size = 5 color = red>注意：使用history命令可以显示用户输入的所有命令。</font>

- 光标位置移动

  光标左移：Ctrl + b ( **←** )

  光标右移：Ctrl + f  ( → )

  移动到头部：Ctrl + a  ( home )

  移动到尾部：Ctrl + e  ( end )

- 字符删除

  删除光标前边的字符：Ctrl + h  ( Backspace )

  删除光标后边的字符：Ctrl + d

  ​	光标后边的字符即光标覆盖的字符

  ​    ![image-20221020155345335](Linux学习.assets/image-20221020155345335.png)，执行该命令，删除的是字符W

  删除光标前所有的内容：Ctrl + u

  删除光标后的所有内容：Ctrl + k

## Linux下的目录结构





## 文件和目录操作相关命令





## 用户权限、用户、用户组





---



# vim使用





##  vim简单介绍

​	vi是"visual interface"的简称, 它在Linux上的地位就仿佛Windows中的记事本一样. 它可以执行编辑、删除、查找、替换、块操作等众多文本操作, 而且用户可以根据自己的需要对其进行定制. vi是一个文本编辑程序, 没有菜单, 只有命令. 

​	*vim更高级一些, 可以理解是vi的高级版本.*

​	*vim需要自行安装, 在shell中输入vimtutor命令可以查看相关的帮助文档.*



## vim的三种模式

​	<font size = 5 color = skybiue>vi有三种基本工作模式：命令模式、文本输入模式、末行模式。</font>

​	三种模式的切换如图所示，从下图中可以看出编辑模式和末行模式之间不能相互切换，必须经过命令模式。

![image-20221028191335559](Linux学习.assets/image-20221028191335559.png)



## vim的基本操作

### 命令模式下的操作

​	当用户按下esc键，就可以使vim进入命令模式下；当使用vim打开一个新文件开始时也是进入命令模式下。

- **保存退出**

  | <font color = paleyellow>快捷键</font> | <font color = paleyellow>操作</font> |
  | :------------------------------------: | :----------------------------------: |
  |      <font color = red>ZZ</font>       |               保存退出               |

- **代码格式化**

  | <font color = paleyellow>快捷键</font> | <font color = paleyellow><span style="display:inline-block;width: 80px">操作</span></font> |
  | :------------------------------------: | :----------------------------------------------------------: |
  |     <font color = red>gg=G</font>      |                             列名                             |

- **光标移动**

  | <font color = paleyellow>快捷键</font> | <font color = paleyellow>操作</font> |
  | :------------------------------------: | :----------------------------------: |
  |       <font color = red>h</font>       |               光标左移               |
  |       <font color = red>j</font>       |               光标下移               |
  |       <font color = red>k</font>       |               光标上移               |
  |       <font color = red>l</font>       |               光标右移               |
  |       <font color = red>w</font>       |             移动一个单词             |
  |      <font color = red>gg</font>       |          光标移动到文件开头          |
  |       <font color = red>G</font>       |          光标移动到文件末尾          |
  |       <font color = red>0</font>       |            光标移动到行首            |
  |       <font color = red>$</font>       |            光标移动到行尾            |
  |      <font color = red>nG</font>       |     行跳转，例如12G，跳到12行处      |

- **删除命令**

  | <font color = paleyellow>快捷键</font> |             <font color = paleyellow>操作</font>             |
  | :------------------------------------: | :----------------------------------------------------------: |
  |       <font color = red>x</font>       |                删除光标后一个字符，相当于Del                 |
  |       <font color = red>X</font>       |             删除光标前一个字符，相当于Backspace              |
  |      <font color = red>dw</font>       |            删除光标开始位置的字，包含光标所在字符            |
  |      <font color = red>d0</font>       |          删除光标前本行所有内容，不包含光标所在字符          |
  |     <font color = red>D[d$]</font>     |           删除光标后本行所有内容，包含光标所在字符           |
  |      <font color = red>dd</font>       |               删除光标所在行（本质其实是剪切）               |
  |      <font color = red>ndd</font>      |                从光标当前行向下删除指定的行数                |
  |   <font color = red>v/ctrl+v</font>    | 使用h、j、k、l移动选择内容，然后按d删除。（其中ctrl+v是列模式，v为非列模式） |

- **撤销和反撤销**

  | <font color = paleyellow>快捷键</font> | <font color = paleyellow>操作</font> |
  | :------------------------------------: | :----------------------------------: |
  |       <font color = red>u</font>       | 一步一步撤销，相当于word文档的ctrl+z |
  |    <font color = red>ctrl-r</font>     |    反撤销，相当于word文档的ctrl+y    |

- **复制粘贴**

  | <font color = paleyellow>快捷键</font> |             <font color = paleyellow>操作</font>             |
  | :------------------------------------: | :----------------------------------------------------------: |
  |      <font color = red>yy</font>       |                          复制当前行                          |
  |      <font color = red>nyy</font>      |                           复制n行                            |
  |       <font color = red>p</font>       |           在光标所在位置向下新开辟一行，然后再粘贴           |
  |   <font color = red>剪切操作</font>    | 按dd或者ndd删除，将删除的行保存到剪切板中然后按下p就可以粘贴了 |

- 可视模式

  | <font color = paleyellow>快捷键</font> |             <font color = paleyellow>操作</font>             |
  | :------------------------------------: | :----------------------------------------------------------: |
  |   <font color = red>v/ctrl+v</font>    | 使用h、j、k、l移动选择内容：<br />使用d删除<br />使用y复制<br />       使用p粘贴到光标的后面<br />使用P粘贴到光标的前面 |

- 替换操作

  | <font color = paleyellow>快捷键</font> | <font color = paleyellow>操作</font> |
  | :------------------------------------: | :----------------------------------: |
  |       <font color = red>r</font>       |             替换当前字符             |
  |       <font color = red>R</font>       |        替换当前行光标后的字符        |

- 查找命令

  | <font color = paleyellow>快捷键</font> |           <font color = paleyellow>操作</font>            |
  | :------------------------------------: | :-------------------------------------------------------: |
  |       <font color = red>/</font>       | /xxxx, 从光标所在的位置开始搜索, 按n向下搜索, 按N向上搜索 |
  |       <font color = red>?</font>       | ?xxxx, 从光标所在的位置开始搜索, 按n向上搜索, 按N向下搜索 |
  |       <font color = red>#</font>       | 将光标移动到待搜索的字符串上, 然后按n向上搜索,按N向下搜索 |
  |    <font color = red>shift+k</font>    | 在待搜索的字符串上按shift+k或者K, 可以查看相关的帮助文档  |



### 文本输入模式操作

- 从命令模式切换到文本输入模式只需输入如下命令：

  | <font color = paleyellow>快捷键</font> |             <font color = paleyellow>操作</font>             |
  | :------------------------------------: | :----------------------------------------------------------: |
  |       <font color = red>i</font>       |                         在光标前插入                         |
  |       <font color = red>a</font>       |                         在光标后插入                         |
  |       <font color = red>I</font>       |                    在光标所在行的行首插入                    |
  |       <font color = red>A</font>       |                    在光标所在行的行尾插入                    |
  |       <font color = red>o</font>       |           在光标所在的行的下面新创建一行, 行首插入           |
  |       <font color = red>O</font>       |           在光标所在的行的上面新创建一行, 行首插入           |
  |       <font color = red>s</font>       |            删除光标后边的字符, 从光标当前位置插入            |
  |       <font color = red>S</font>       |                删除光标所在当前行, 从行首插入                |
  | <font color = red>按列模式插入</font>  | 先按ctrl+v进入列模式, 按h、j、k、l、移动选定某列,按I或者shift+i向前插入, 然后插入字符, 最后按两次esc. |



### 末行模式下的操作

​	从命令模式切换到末行模式，输入冒号即可。

- 保存退出

  | <font color = paleyellow>快捷键</font> | <font color = paleyellow>操作</font> |
  | :------------------------------------: | :----------------------------------: |
  |       <font color = red>q</font>       |                 退出                 |
  |      <font color = red>q!</font>       |       强制退出，不保存修改内容       |
  |       <font color = red>w</font>       |         保存修改内容，不退出         |
  |      <font color = red>wq</font>       |              保存并退出              |
  |       <font color = red>x</font>       |               相当于wq               |

- 替换操作

   下面表格中old表示原字符串，new表示新字符串

  |  <font color = paleyellow>快捷键</font>   | <font color = paleyellow>操作</font> |
  | :---------------------------------------: | :----------------------------------: |
  |   <font color = red>:s/old/new/</font>    |    光标所在行的第一个old替换为new    |
  |   <font color = red>:s/old/new/g</font>   |     光标所在行的所有old替换为new     |
  | <font color = red>:m, ns/old/new/g</font> | 将第m行至第n行之间的old全部替换成new |
  |  <font color = red>:%s/old/new/g</font>   |      当前文件的所有old替换为new      |
  | <font color = red>:1,$s/old/new/g</font>  |      当前文件的所有old替换为new      |
  |  <font color = red>:%s/old/new/gc</font>  |    同上，但是每次替换需要用户确认    |

- 快速翻屏

  | <font color = paleyellow>快捷键</font> | <font color = paleyellow>操作</font> |
  | :------------------------------------: | :----------------------------------: |
  |   <font color = red>ctrl + u</font>    |     向下翻半屏(up)--光标向上移动     |
  |   <font color = red>ctrl + d</font>    |    向上翻半屏(down)--光标向下移动    |
  |   <font color = red>ctrl + f</font>    |          向上翻一屏(front)           |
  |   <font color = red>ctrl + b</font>    |           向后翻一屏(back)           |

- 分屏操作

  ==> 在打开文件之后分屏

  |       <font color = paleyellow>快捷键</font>        |     <font color = paleyellow>操作</font>     |
  | :-------------------------------------------------: | :------------------------------------------: |
  |             <font color = red>sp</font>             |               当前文件水平分屏               |
  |            <font color = red>vsp</font>             |               当前文件垂直分屏               |
  |         <font color = red>sp 文件名</font>          |         当前文件和另一个文件水平分屏         |
  |         <font color = red>vsp 文件名</font>         |         当前文件和另一个文件垂直分屏         |
  |          <font color = red>ctrl-w-w</font>          |              在多个窗口切换光标              |
  | <font color = red>wall/wqall/xall/qall/qall!</font> | 保存/保存退出/保存退出/退出/强制退出分屏窗口 |

  ==> 在打开文件之前分屏

  ​	分屏: vim -on file1 file2 … 

  ​	垂直分屏: vim -On file1 file2… 

  ​	**注意: n可以省略, 有几个文件就分几屏**

  

- 在末行模式下执行shell命令

  ```shell
  ！shell 命令  // 按下两次esc可以回到命令模式
  ```

- 从末行模式切换回命令模式

  *按两次ESC，退格（backspace）或者回车键。*



### vim的配置文件

- 用户级别配置文件

  ~/.vimrc, 修改用户级别的配置文件只会影响当前用户, 不会影响其他的用户.

  例如: 在用户的家目录下的.vimrc文件中添加

  set tabstop=4 ----设置缩进4个空格

  set nu    ----设置行号

  set shiftwidth=4 ---设置gg=G缩进4个空格, 默认是缩进8个空格

- 系统级别配置文件

  /etc/vim/vimrc, 修改了系统级别的配置文件将影响系统下的所有用户.

  说明: 由于linux是多用户操作系统, 建议只在用户级别的配置文件下进行修改, 不要影响其他用户.

---



# Git



Git 是一个免费的、开源的分布式版本控制系统，可以快速高效地处理从小型到大型的各种项目。

Git易于学习，占地面积小，性能极快。它具有廉价的本地库，方便的暂存区域和多个工作流分支等特性。其性能优于Subversion、CVS、Perforce和 ClearCase等版本控制工具。



## 分布式版本控制

版本控制是一种记录文件内容变化，以便将来查阅特定版本修订情况的系统。
版本控制其实最重要的是可以记录文件修改历史记录，从而让用户能够查看历史版本，方便版本切换。

像Git这种分布式版本控制工具，客户端提取的不是最新版本的文件快照，而是把代码仓库完整地镜像下来（本地库)。这样任何一处协同工作用的文件发生故障，事后都可以用其他客户端的本地仓库进行恢复。因为每个客户端的每一次文件提取操作，实际上都是一次对整个文件仓库的完整备份。
分布式的版本控制系统出现之后,解决了集中式版本控制系统的缺陷:

1.服务器断网的情况下也可以进行开发（因为版本控制是在本地进行的)

2.每个客户端保存的也都是整个完整的项目（包含历史记录，更加安全)



## Git历史

![image-20230309170616436](Linux学习.assets/image-20230309170616436.png)



## Git工作机制

![image-20230309170903697](Linux学习.assets/image-20230309170903697.png)



## Git命令

**注意：**Git首次安装必须设置一下用户签名，否则无法提交代码。

![image-20230309173540928](Linux学习.assets/image-20230309173540928.png)



## Git操作例程

创建一个文件夹GitSpace作为Git的工作空间，进入里面创建一个文件夹git_test作为一个例程，进入该文件夹，执行`git init`命令来初始化本地库，此时工作文件夹下将出现`.git`的配置文件，如下图：

![image-20230309174003187](Linux学习.assets/image-20230309174003187.png)

![image-20230310081240327](Linux学习.assets/image-20230310081240327.png)

执行`git status`来查看本地库的状态

![image-20230309174943044](Linux学习.assets/image-20230309174943044.png)

新增一个`hello.c`文件，作为测试文件，用`git status`命令查看状态检测到未跟踪的文件：

![image-20230310082101883](Linux学习.assets/image-20230310082101883.png)

使用`git add 文件`命令将工作区的文件提交到暂存区：

![image-20230310082616752](Linux学习.assets/image-20230310082616752.png)

使用`git rm --cached 文件`命令可将暂存区的文件给删除，删除后状态显示为尚无提交，未跟踪文件：

![image-20230310082900607](Linux学习.assets/image-20230310082900607.png)

我们可以重新使用`git add 文件`命令，提交到暂存区，使用`git commit -m "日志信息" 文件名`命令，将暂存区的文件提交到本地库：

![image-20230310083521523](Linux学习.assets/image-20230310083521523.png)

修改`hello.c`文件后，检测到工作区有文件被修改：

![image-20230310083745043](Linux学习.assets/image-20230310083745043.png)

将修改后的文件再次提交到暂存区，然后提交到本地库：

![image-20230310084209292](Linux学习.assets/image-20230310084209292.png)

`git reflog`    查看版本信息

![image-20230310084741025](Linux学习.assets/image-20230310084741025.png)

`git log`          查看版本详细信息

![image-20230310084509820](Linux学习.assets/image-20230310084509820.png)

`git reset --hard 版本号`     切换到其他版本

首先使用`git reflog`查看当前的历史记录，可以看到当前是在eed1cbc版本：

![image-20230310085058938](Linux学习.assets/image-20230310085058938.png) 

`git reset --hard 31a2a9b`切换到31a2a9b版本，也是我们第一次提交的版本：

![image-20230310085521634](Linux学习.assets/image-20230310085521634.png)

`git reflog`查看历史记录：

![image-20230310085751341](Linux学习.assets/image-20230310085751341.png)



## Git分支

在版本控制过程中，同时推进多个任务，为每个任务，我们就可以创建每个任务的单独分支。使用分支意味着程序员可以把自己的工作从开发主线上分离开来，开发自己分支的时候，不会影响主线分支的运行。对于初学者而言，分支可以简单理解为副本，一个分支就是一个单独的副本。(分支底层其实是指针的引用)

**分支优点：**同时并行推进多个功能开发，提高开发效率。
各个分支在开发过程中，如果某一个分支开发失败，不会对其他分支有任何影响。失败的分支删除重新开始即可。

**分支操作：**

![image-20230310090151884](Linux学习.assets/image-20230310090151884.png)



`git branch -v`   查看分支：

![image-20230310113845184](Linux学习.assets/image-20230310113845184.png)

![image-20230310114002905](Linux学习.assets/image-20230310114002905.png)

`git branch 分支名`   创建分支，把主分支的内容复制了一份：

![image-20230310114542205](Linux学习.assets/image-20230310114542205.png)

![image-20230310114616403](Linux学习.assets/image-20230310114616403.png)



修改主分支master上文件内容如下，并提交到本地库：

![image-20230310115511652](Linux学习.assets/image-20230310115511652.png)



`git checkout 分支名`   可切换到相应分支：

![image-20230310115944128](Linux学习.assets/image-20230310115944128.png)

查看当前的`hello.c`文件，发现没有被修改，可修改后提交到本地库：

![image-20230310120306588](Linux学习.assets/image-20230310120306588.png)



`git merge 分支名`   把指定分支合并到当前分支上来

此时可能会产生冲突：

![image-20230310134653027](Linux学习.assets/image-20230310134653027.png)

**冲突产生原因：**

合并分支时，两个分支在同一个文件的同一个位置有两套完全不同的修改。Git无法替我们决定使用哪一个。必须人为决定新代码内容。



查看当前文件状态：

![image-20230310134845757](Linux学习.assets/image-20230310134845757.png)



**解决冲突：**

编辑有冲突的文件，删除特殊符号，决定要使用的内容

此时冲突文件代码为：

![image-20230310135439532](Linux学习.assets/image-20230310135439532.png)

人为修改代码

![image-20230310135728537](Linux学习.assets/image-20230310135728537.png)

添加到暂存区，提交到本地库

**注意：**此时本地库的提交不能带文件名进行部分提交

![image-20230310140147974](Linux学习.assets/image-20230310140147974.png)

`git reflog`  查看历史记录

![image-20230310140432331](Linux学习.assets/image-20230310140432331.png)





## Git远程仓库

git以GitHub作为远程代码托管中心



**远程仓库操作**

![image-20230310140623754](Linux学习.assets/image-20230310140623754.png)



**GitHub创建仓库**

![image-20230310141748335](Linux学习.assets/image-20230310141748335.png)



`git remote -v`                             查看当前所有远程地址别名

`git remote add 别名 远程地址`    给一个远程地址创建别名

![image-20230310142519465](Linux学习.assets/image-20230310142519465.png)



**推送本地分支到远程仓库**

`git push 别名 分支`

![image-20230310142817409](Linux学习.assets/image-20230310142817409.png)

![image-20230310142854754](Linux学习.assets/image-20230310142854754.png)





**克隆远程仓库到本地**



`git clone 远程地址`

创建一个新文件夹来克隆

![image-20230310145052926](Linux学习.assets/image-20230310145052926.png)



clone会做三个操作：

- 拉取代码
- 初始化本地仓库
- 创建别名

![image-20230310145252940](Linux学习.assets/image-20230310145252940.png)



## 解决GitHub无法加载图片问题

通过修改hosts文件来解决

hosts文件所在路径地址

```
Mac /etc/hosts
Linux /etc/hosts
Windows C:\Windows\System32\drivers\etc\hosts
```

在hosts文件末尾追加以下信息：

```
# GitHub Start

192.30.253.112 Build software better, together
192.30.253.119 gist.github.com
151.101.184.133 assets-cdn.github.com
151.101.184.133 raw.githubusercontent.com
151.101.184.133 gist.githubusercontent.com
151.101.184.133 cloud.githubusercontent.com
151.101.184.133 camo.githubusercontent.com
151.101.184.133 avatars0.githubusercontent.com
151.101.184.133 avatars1.githubusercontent.com
151.101.184.133 avatars2.githubusercontent.com
151.101.184.133 avatars3.githubusercontent.com
151.101.184.133 avatars4.githubusercontent.com
151.101.184.133 avatars5.githubusercontent.com
151.101.184.133 avatars6.githubusercontent.com
151.101.184.133 avatars7.githubusercontent.com
151.101.184.133 avatars8.githubusercontent.com

# GitHub End
```



如果由于权限出现修改 hosts 文件无法保存问题，可以先把 hosts 文件复制到另一个地方，修改后替换原 hosts 文件。





---



# gcc编译器介绍

​	**gcc命令** 使用GNU推出的基于 `C/C++` 的编译器，是开放源代码领域应用最广泛的编译器，具有功能强大，编译代码支持性能优化等特点。现在很多程序员都应用 `GCC`，怎样才能更好的应用 `GCC`。目前，`GCC` 可以用来编译 `C/C++`、`FORTRAN`、`JAVA`、`OBJC`、`ADA`等语言的程序，可根据需要选择安装支持的语言。

## gcc的工作流程

​	gcc编译器将C源文件到生成一个可执行程序，中间一共经历了四个步骤：

![img](Linux学习.assets/clip_image002.gif)

四个步骤并不是gcc独立完成的，而是在内部调用了其他工具，从而完成了整个工作流程，其中编译最耗时，因为要逐行检查语法。

![image-20220916155236559](Linux学习.assets/image-20220916155236559-1666254787436.png)

- **预处理**

​	cpp预处理器、去掉注释、展开头文件、宏替换

​	**注意：**在此步骤，没有进行语法检查

```shell
gcc -E test.c -o test.i
```

- **编译**

​	gcc，将源代码文件编译成汇编语言代码

​	**注意：**在此步骤，进行了语法检查

```shell
gcc -S test.i -o test.s
```

- **汇编**

​	as，将汇编语言代码编译成二进制文件

```shell
gcc -c test.s -o test.o
```

- **链接**

​	ld，链接test.c代码中调用的库函数

```shell
gcc test.o -o test
```

​	一步生成最终的可执行程序:

```shell
gcc test.c -o test
```



## gcc常用参数介绍

```
-v: 查看gcc版本号, --version也可以
-o：指定生成的输出文件；
-E：仅执行编译预处理；
-S：将C代码转换为汇编代码；
-wall：显示警告信息；
-c：仅执行编译操作，不进行连接操作。
-l：用来指定程序要链接的库，-l参数紧接着就是库名
-I：寻找头文件的目录
-L: 指定库文件所在的路径
-g: 包含调试信息, 使用gdb调试需要添加-g参数
```

<font face = "楷体" size = 5>详细介绍可以参考下列网站：</font>

```html
https://wangchujiang.com/linux-command/c/gcc.html
```





---------



# 静态库和共享（动态）库的制作



## 库的介绍

库是二进制文件, 是源代码文件的另一种表现形式, 是加了密的源代码; 是一些功能相近或者是相似的函数的集合体。

- 使用库的优势

​	:eyes:==>提高代码的可重用性，而且还可以提高程序的健壮性；

​	:eyes:==>可以减少开发者的代码开发量，缩短开发周期。

- 库制作完成后，如何给用户使用？

  ==>头文件--包含了库函数的声明

  ==>库文件--包含了库函数的代码实现

  <font color = red>注意：库不能单独使用，只能作为其他执行程序的一部分完成某些功能，也就是说只能被其他程序调用才能使用。</font>



## 静态库（static library）

静态库可以认为是一些目标代码的集合, 是在可执行程序运行前就已经加入到执行代码中, 成为执行程序的一部分. 按照习惯, 一般以.a做为文件后缀名。

静态库的命名一般分为三个部分：

​	<font face = "楷体" size = 5 color = green>==> 前缀：lib</font>

​	<font face = "楷体" size = 5 color = green>==> 库名称：自定义即可，如test</font>

​	<font face = "楷体" size = 5 color = green>==> 后缀：.a</font>

​	<font color = skyblue>结合上述命名的规定，可以得出最终的静态库的名称为：libtest.a</font>



### 静态库的制作

下面以func1.c , func2.c和head.h三个文件为例讲述静态库的制作和使用, 其中head.h文件中有函数的声明,  fun1.c和fun2.c中有函数的实现.

```c
// head.h
#include <stdio.h>
void func1();
void func2();
```



```c
// func1.c
#include "head.h"
void func1()
{
	printf("This is func1!\n");
}
```



```c
// func2.c
#include "head.h"
void func2()
{
	printf("This is func2!\n");
}
```



**步骤一：**将库函数c源文件生成对应的.o文件

```bash
gcc -c func1.c func2.c -I ./include
```



**步骤二：**使用打包工具ar将准备好的.o文件打包为.a文件

- 在使用ar工具时候需要添加参数rcs----r更新、c创建、s建立索引
- ar rcs 静态库名 .o文件

​     例如如下指令：

```bash
ar rcs libtest.a func1.o func2.o
```

![image-20230309093413223](Linux学习.assets/image-20230309093413223.png)





### 静态库的使用

静态库制作完成之后, 需要将.a文件和头文件一起发布给用户。

假设测试文件为main.c, 静态库文件为libtest.a, 头文件为head.h

用到的参数：

- -L：指定要连接的库的所在目录

- -l：指定链接时需要的静态库, 去掉前缀和后缀

- -I: 指定main.c文件用到的头文件head.h所在的路径

使用如下指令：

```bash
gcc -o main main.c -L ./ -ltest -I ./include
```





### 静态库的优缺点

**优点：**函数库最终被打包到应用程序中，实现是函数本地化，寻址方便、速度快（库函数调用效率==自定义函数使用效率），程序在运行时与函数库再无瓜葛，移植方便。

**缺点：**消耗系统资源较大, 每个进程使用静态库都要复制一份, 无端浪费内存。静态库会给程序的更新、部署和发布带来麻烦。如果静态库libxxx.a更新了，所有使用它的应用程序都需要重新编译、发布给用户（对于玩家来说，可能是一个很小的改动，却导致整个程序重新下载）。

![image-20230309100521103](Linux学习.assets/image-20230309100521103.png)







## 共享库（shared library）/ 动态库

共享库在程序编译时并不会被连接到目标代码中, 而是在程序运行是才被载入. 不同的应用程序如果调用相同的库, 那么在内存里只需要有一份该共享库的拷贝, 规避了空间浪费问题.动态库在程序运行时才被载入, 也解决了静态库对程序的更新、部署和发布会带来麻烦. 用户只需要更新动态库即可, 增量更新. 为什么需要动态库, 其实也是静态库的特点导致. 

按照习惯, 一般以“.so”做为文件后缀名. 共享库的命名一般分为三个部分：

- 前缀：lib

- 库名称：自己定义即可, 如test

- 后缀：.so

所以最终的静态库的名字应该为：libtest.so

![image-20230310171543344](Linux学习.assets/image-20230310171543344.png)



### 共享库的制作

1. 生成目标文件.o, 此时要加编译选项：-fPIC（fpic）

​     `gcc -fpic -c func1.c func2.c -I ./include`

  **参数：**-fpic创建与地址无关的编译程序(pic, position independent code), 目的就是为了能够在多个应用程序间共享.

2. 生成共享库, 此时要加链接器选项: -shared（指定生成动态链接库**）**

​	`gcc -shared func1.o func2.o -o libtest.so`

![image-20230310192203632](Linux学习.assets/image-20230310192203632.png)



引用动态库编译成可执行文件（和静态库方式一样）：

用到的参数：

- -L：指定要连接的库的所在目录

- -l：指定链接时需要的动态库, 去掉前缀和后缀

- -I: 指定main.c文件用到的头文件head.h所在的路径

使用如下指令：

```bash
gcc -o main main.c -L ./ -ltest -I ./include
```



**注意：**若执行main指令报错，可参考下面步骤：

分析为什么在执行的时候找不到libtest.so库

当系统加载可执行代码时候，能够知道其所依赖的库的名字，但是还需要知道所依赖的库的绝对路径，此时就需要系统动态载入器；

ldd命令可以查看可执行文件依赖的库文件，执行ldd main，可以发现libtest2.so找不到

对于**elf**格式的可执行程序，是由ld-linux.so来完成的, 它先后搜索elf文件的 DT_RPATH段 — 环境变量LD_LIBRARY_PATH — /etc/ld.so.cache文件列表 — /lib/, /usr/lib目录找到库文件后将其载入内存。

使用**file**命令可以查看文件的类型: `file main`



**如何让系统找到共享库**

1. 拷贝自己制作的共享库到~/lib或者/lib下

2. 把`export LD_LIBRARY_PATH=$LD_LIBRARY_PATH:库路径`, 设置到∼/.bashrc文件中, 然后在执行下列三种办法之一:

- 执行. ~/.bashrc使配置文件生效(第一个.后面有一个空格)

- 执行source ~/.bashrc配置文件生效

- 退出当前终端, 然后再次登陆也可以使配置文件生效



### 共享库特点

- 动态库把对一些库函数的链接载入推迟到程序运行的时期。

- 可以实现进程之间的资源共享。（因此动态库也称为共享库）

- 将一些程序升级变得简单。

- 甚至可以真正做到链接载入完全由程序员在程序代码中控制（显示调用）



## 静态库和动态库的优缺点

**静态库的优点:**

​    1 执行速度快, 是因为静态库已经编译到可执行文件内部了

​    2 移植方便, 不依赖域其他的库文件

 **缺点:** 

​    1 耗费内存, 是由于每一个静态库的可执行程序都会加载一次

​    2 部署更新麻烦, 因为静态库修改以后所有的调用到这个静态库的可执行文件都需要重新编译

 

 **动态库的优点:**

​    1 节省内存

​    2 部署升级更新方便, 只需替换动态库即可, 然后再重启服务.

 **缺点:** 

​    1 加载速度比静态库慢

​    2 移植性差, 需要把所有用到的动态库都移植.由于由静态库生成的可执行文件是把静态库加载到了其内部, 所以静态库生成的可执行文件一般会比动态库大.











---------





# makefile文件编写



## 何为makefile

​	makefile文件中定义了一系列的规则来指定, 哪些文件需要先编译, 哪些文件需要后编译, 哪些文件需要重新编译, 甚至于进行更复杂的功能操作, 因为makefile就像一个Shell脚本一样, 其中也可以执行操作系统的命令. makefile带来的好处就是——“自动化编译”, 一旦写好, 只需要一个make命令, 整个工程完全自动编译, 极大的提高了软件开发的效率.

​	make是一个命令工具, 是一个解释makefile中指令的命令工具, 一般来说, 大多数的IDE都有这个命令, 比如：Visual C++的nmake, Linux下GNU的make. 可见, makefile都成为了一种在工程方面的编译方法.

​	makefile文件中会使用gcc编译器对源代码进行编译, 最终生成可执行文件或者是库文件.

​	makefile文件的命名：Makefile



## makefile的基本规则

makefile由一组规则组成，规则如下：

```
目标：依赖
（tab）命令
```

makefile基本规则三要素：

- *目标：要生成的目标文件*

- *依赖：目标文件由哪些文件生成*

- *命令：通过执行该命令能够由依赖文件生成目标文件*

  

下面以一个具体例子来讲解：

​	当前目录下有main.c fun1.c fun2.c sum.c, 根据这个基本规则编写一个简单的makefile文件, 生成可执行文件main.

<font face = "楷体" size = 5 color = pink>第一个版本的makefile：</font>

```makefile
main:main.c fun1.c fun2.c sum.c
	gcc -o main main.c fun1.c fun2.c sum.c -I ./
```

- *缺点：效率低, 修改一个文件, 所有的文件会全部重新编译.*



## makefile工作原理

<font face = "楷体" size = 5 color = pink>基本原则：</font>

:fire:若想生成目标, 检查规则中的所有的依赖文件是否都存在:

- <font color = red>如果有的依赖文件不存在,</font>则向下搜索规则, 看是否有生成该依赖文件的规则:

  如果有规则用来生成该依赖文件, 则执行规则中的命令生成依赖文件;如果没有规则用来生成该依赖文件, 则报错。

  ![image-20221023090549970](Linux学习.assets/image-20221023090549970.png)

  

  - <font color = red>如果所有依赖都存在, </font>检查规则中的目标是否需要更新, 必须先检查它的所有依赖,依赖中有任何一个被更新, 则目标必须更新.(检查的规则是哪个时间大哪个最新)

  ![image-20221023091146792](Linux学习.assets/image-20221023091146792.png)

  <font face = "楷体" size = 5 color = red>总结：</font>

   ➤分析各个目标和依赖之间的关系

   ➤根据依赖关系自底向上执行命令

   ➤根据依赖文件的时间和目标文件的时间确定是否需要更新

   ➤如果目标不依赖任何条件，则执行对应命令。以示更新（如：伪目标）

  

  <font face = "楷体" size = 5 color = pink>第二个版本的makefile:</font>

  ```makefile
  main : main.o fun1.o fun2.o sum.o
  	gcc -o main main.o fun1.o fun2.o sum.o
  
  main.o : main.c
  	gcc -o main.o -c main.c -I ./
  	
  fun1.o : fun1.c
  	gcc -o fun1.o -c fun1.c -I ./
  	
  fun2.o : fun2.c
  	gcc -o fun2.o -c fun2.c -I ./
  
  sum.o : sum.c
  	gcc -o sum.o -c sum.c -I ./
  ```

  - *缺点：冗余，若.c文件数量很多，编写起来比较麻烦*



## makefile中的变量

在makefile中使用变量有点类似于C语言中的宏定义, 使用该变量相当于内容替换, 使用变量可以使makefile易于维护, 修改起来变得简单。

*makefile有三种类型的变量:*

​		 ➤普通变量

​		 ➤自带变量

​		 ➤自动变量

<font color = poolblue>普通变量</font>

 ➤变量定义直接使用   `=`

​     使用变量值用 $(变量名)

```makefile
#如:下面是变量的定义和使用
foo = abc			#定义变量并赋值
bar = $(foo)		#使用变量, $(变量名)
```

定义了两个变量: foo、bar, 其中bar的值是foo变量值的引用。

➤更改变量代表的意义使用  `:=`

➤追加这个变量代表的意义使用 `+=`

```makefile
obj = main.o kbd.o commond.o 
obj:= main.o kbd.o commond.o insert.o
obj+= files.o utils.o   
#此时obj = main.o kbd.o commond.o insert.o files.o utils.o
```



除了使用用户自定义变量, makefile中也提供了一些变量（变量名大写）供用户直接使用, 我们可以直接对其进行赋值：

```
CC = gcc #arm-linux-gcc
CPPFLAGS : C预处理的选项 -I
CFLAGS:   C编译器的选项 -Wall -g -c
LDFLAGS :  链接器选项 -L  -l
```



<font color = poolblue>自动变量</font>

 ➤	$@:	表示规则中的目标

 ➤	$<:	表示规则中的第一个条件

 ➤	$^:	表示规则中的所有条件，组成一个列表，以空格隔开，如果这个列表中有重复的项则消除重复项。

<font face = "kaiti" size = 5 color = red>特别注意：自动变量只能在规则的命令中使用</font>

<font face = "楷体" size = 5 color = poolblue>模式规则</font>

至少在规则的目标定义中要包含'%','%'表示一个或多个, 在依赖条件中同样可以用'%', 依赖条件中的'%'的取值取决于其目标:

比如: main.o:main.c fun1.o: fun1.c fun2.o:fun2.c, 说的简单点就是: xxx.o:xxx.c

<font face = "楷体" size = 5 color = pink>第三个版本的makefile：</font>

```makefile
target = main
object = main.o fun1.o fun2.o sum.o
CC = gcc

$(target):$(object)
	$(CC) $^ -o $@

%.o:%.c
	$(CC) -o $@ -c $< -I ./
```



## makefile函数

makefile中的函数有很多，下面选两个最常用的介绍：

```
1.	wildcard – 查找指定目录下的指定类型的文件
	src=$(wildcard *.c)  //找到当前目录下所有后缀为.c的文件,赋值给src
2.	patsubst – 匹配替换
	obj=$(patsubst %.c,%.o, $(src)) //把src变量里所有后缀为.c的文件替换成.o
```

在makefile中所有的函数都是有返回值的。当前目录下有main.c fun1.c fun2.c sum.c

```
src=$(wildcard *.c) 等价于src=main.c fun1.c fun2.c sum.c
obj=$(patsubst %.c,%.o, $(src))等价于obj=main.o fun1.o fun2.o sum.o
```

<font face = "楷体" size = 5 color = pink>第四个版本的makefile：</font>

```makefile
target = main
src = $(wildcard ./*.c)
object = $(patsubst %.c, %.o, $(src))
CC = gcc

$(target):$(object)
	$(CC) $^ -o $@

%.o:%.c
	$(CC) -o $@ -c $< -I ./
```

- *缺点: 每次重新编译都需要手工清理中间.o文件和最终目标文件*



## makefile的清理条件

用途: 清除编译生成的中间.o文件和最终目标文件

make clean 如果当前目录下有同名clean文件,则不执行clean对应的命令, 解决方案：

​	➤伪目标声明：

​	<font color = orange>.PHONY : clean</font>

​	<font color = orange>▲声明目标为伪目标之后, makefile将不会检查该目标是否存在或者该目标是否需要更新</font>

- clean命令中的特殊符号：

  ➤  **"-"**  此命令如果出错，make也会继续执行后续的命令。如:"-rm main.o"

  rm -f：强制执行，比如若要删除的文件不存在使用-f也不会报错

- 其他

  ➤make默认执行第一个出现的目标，可通过make dest指定要执行的目标

  ➤make -f ：-f 执行第一个makefile文件名称，使用make执行指定的makefile ：

  ```shell
  make -f mainmake clean //执行mainmake中的clean
  ```

  

<font color = pink>第五个版本的makefile：</font>

```makefile
target = main
src = $(wildcard ./*.c)
object = $(patsubst %.c, %.o, $(src))
CC = gcc

$(target):$(object)
	$(CC) $^ -o $@

%.o:%.c
	$(CC) -o $@ -c $< -I ./

.PHONY:clean
clean:
	-rm -f $(object)
```

​	<font color = skyblue>在makefile的第5个版本中, 综合使用了变量, 函数, 模式规则和清理命令, 是一个比较完善的版本.</font>





---------





# GDB调试



## gdb介绍

GDB（GNU Debugger）是GCC的调试工具。其功能强大, 现描述如下：

GDB主要帮忙你完成下面四个方面的功能：

- 启动程序, 可以按照你的自定义的要求随心所欲的运行程序。

- 可让被调试的程序在你所指定的断点处停住。（断点可以是条件表达式）

- 当程序被停住时, 可以检查此时你的程序中所发生的事。

- 动态的改变你程序的执行环境。



## 生成调试信息

一般来说GDB主要调试的是C/C++的程序。要调试C/C++的程序, 首先在编译时, 我们必须要把调试信息加到可执行文件中。使用编译器（cc/gcc/g++）的 `-g` 参数可以做到这一点。如：

`gcc -g -o hello hello.c`

如果没有`-g`, 你将看不见程序的函数名、变量名, 所代替的全是运行时的内存地址。





## 启动gdb

启动gdb：`gdb program`

program 也就是你的执行文件, 一般在当前目录下。

设置运行参数

- `set args` 可指定运行时参数。（如：set args 10 20 30 40 50 ）

- `show args` 命令可以查看设置好的运行参数。

启动程序

- `run`：程序开始执行, 如果有断点, 停在第一个断点处

- `start`：程序向下执行一行。(在第一条语句处停止)



## 显示源代码

GDB 可以打印出所调试程序的源代码, 当然, 在程序编译时一定要加上`-g`的参数, 把源程序信息编译到执行文件中。不然就看不到源程序了。当程序停下来以后, GDB会报告程序停在了那个文件的第几行上。你可以用`list`命令来打印程序的源代码, 默认打印10行, list命令的用法如下所示:

- `list linenum`：打印第linenum行的上下文内容.

- `list function`：显示函数名为function的函数的源程序。

- `list`： 显示当前行后面的源程序。

- `list -`：显示当前文件开始处的源程序。

- `list file:linenum`: 显示file文件下第n行

- `list file:function`: 显示file文件的函数名为function的函数的源程序

一般是打印当前行的上5行和下5行, 如果显示函数是是上2行下8行, 默认是10行, 当然, 你也可以定制显示的范围, 使用下面命令可以设置一次显示源程序的行数。

- `set listsize count`：设置一次显示源代码的行数。     

- `show listsize`：  查看当前listsize的设置。



## 例程

工作文件夹如下：

![image-20230315113633495](Linux学习.assets/image-20230315113633495.png)

Makefile文件如下：

```makefile
target = main
src = $(wildcard ./*.c)
object = $(patsubst %.c, %.o, $(src))
CC = gcc

$(target):$(object)
	$(CC) $^ -o $@

%.o:%.c
	$(CC) -g -o $@ -c $< -I ./include  # 需要加-g

.PHONY:clean
clean:
	-rm -f $(object)
```

执行Makefile文件

![image-20230315114257876](Linux学习.assets/image-20230315114257876.png)

启动gdb，`gdb ./main`

![image-20230315114446708](Linux学习.assets/image-20230315114446708.png)

执行`run`

![image-20230315114536195](Linux学习.assets/image-20230315114536195.png)

`list`命令

![image-20230315115641660](Linux学习.assets/image-20230315115641660.png)



## 断点操作



**在当前文件设置断点**

- `break `设置断点, 可以简写为`b`
- `b 5` 在源程序第5行设置断点
- `b func` 在func函数入口处设置断点

![image-20230315141323018](Linux学习.assets/image-20230315141323018.png)



**多文件设置断点**

在进入指定函数时停住:

- `b filename:linenum` --在源文件filename的linenum行处停住

- `b filename:function` --在源文件filename的function函数的入口处停住

![image-20230315142025226](Linux学习.assets/image-20230315142025226.png)



**查询所有断点**

- `info b` == `info break` == `i break` == `i b`

![image-20230315142059610](Linux学习.assets/image-20230315142059610.png)



**条件断点**

一般来说, 为断点设置一个条件, 我们使用if关键词, 后面跟其断点条件。设置一个条件断点：

`b test.c:8 if intValue == 5`



**维护断点**

`delete [range...]` 删除指定的断点, 其简写命令为d。

如果不指定断点号, 则表示删除所有的断点。range表示断点号的范围。

- 删除某个断点: `delete num`

- 删除多个断点: `delete num1 num2 ...`

- 删除连续的多个断点: `delete m-n`

- 删除所有断点: `delete`



比删除更好的一种方法是disable停止点, disable了的停止点, GDB不会删除, 当你还需要时, enable即可, 就好像回收站一样。

`disable [range...] `使指定断点无效, 简写命令是dis。

如果什么都不指定, 表示disable所有的停止点。

- 使一个断点无效/有效: `disable num`

- 使多个断点无效有效: `disable num1 num2 ...`

- 使多个连续的断点无效有效:`disable m-n`

- 使所有断点无效有效: `disable`



`enable [range...] `使无效断点生效, 简写命令是ena。

如果什么都不指定, 表示enable所有的停止点。

- 使一个断点无效/有效: `enable num`

- 使多个断点无效有效: `enable num1 num2 ...`

- 使多个连续的断点无效有效:`enable m-n`

- 使所有断点无效有效: `disable/enable`



## 调试代码

- `run` 运行程序, 可简写为r

- `next` 单步跟踪, 函数调用当作一条简单语句执行, 可简写为n

- `step` 单步跟踪, 函数调进入被调用函数体内, 可简写为s

- `finish` 退出进入的函数, 如果出不去, 看一下函数体中的循环中是否有断点，如果有删掉，或者设置无效

- `until` 在一个循环体内单步跟踪时, 这个命令可以运行程序直到退出循环体,可简写为u, 如果出不去, 看一下函数体中的循环中是否有断点，如果有删掉，或者设置无效

- `continue` 继续运行程序, 可简写为c(若有断点则跳到下一个断点处)



## 查看变量的值



**查看运行时变量的值**

print 打印变量、字符串、表达式等的值, 可简写为p

`p count `-----打印count的值



**自动显示变量的值**

你可以设置一些自动显示的变量, 当程序停住时, 或是在你单步跟踪时, 这些变量会自动显示。相关的GDB命令是display。

- `display 变量名`

- `info display` -- 查看display设置的自动显示的信息。

- `undisplay num`（info display时显示的编号）

- `delete display dnums… `-- 删除自动显示, dnums意为所设置好了的自动显式的编号。如果要同时删除几个, 编号可以用空格分隔, 如果要删除一个范围内的编号, 可以用减号表示（如：2-5）

  - 删除某个自动显示: `undisplay num` 或者`delete display num`

  - 删除多个: `delete display num1 num2`

  - 删除一个范围: `delete display m-n`

- `disable display dnums...`

  - 使一个自动显示无效: `disable display num`

  - 使多个自动显示无效: `delete display num1 num2`

  - 使一个范围的自动显示无效: `delete display m-n`

- `enable display dnums...`

  - 使一个自动显示有效: `enable display num`

  - 使多个自动显示有效: `enable display num1 num2`

  - 使一个范围的自动显示有效: `enable display m-n`

- disable和enalbe不删除自动显示的设置, 而只是让其失效和恢复。



**查看修改变量的值**

- `ptype width` --查看变量width的类型

​    

- `p width` --打印变量width 的值

​     

可以使用set var命令来告诉GDB, width不是GDB的参数, 而是程序的变量名, 如：

​     set var width=47 // 将变量var值设置为47

<font color =red>在改变程序变量取值时, 最好都使用set var格式的GDB命令。</font>



## 安装GDB插件gef

```
下载网址：https://github.com/hugsy/gef
```

![image-20230415101856910](F:\Documents\Typora_file\Linux学习.assets\image-20230415101856910.png)

下载后的目录如下：

![image-20230415102104883](F:\Documents\Typora_file\Linux学习.assets\image-20230415102104883.png)

对目录下的`gef.py`进行操作，执行下面命令：

`echo "source ~/GdbPlugins/gef-dev/gef.py" > ~/.gdbinit`

启动gdb

![image-20230415102326400](F:\Documents\Typora_file\Linux学习.assets\image-20230415102326400.png)

run起来后可以看到内存信息

![image-20230415102433624](F:\Documents\Typora_file\Linux学习.assets\image-20230415102433624.png)



<font color=red>注意：</font>该gef插件调试嵌入式设备的时候可能出现bug这时可以切换到原始gdb中去调试，所以我写了一个脚本，用来切换gdb模式。

创建目录及说明文件

![image-20230415110816800](F:\Documents\Typora_file\Linux学习.assets\image-20230415110816800.png)

其中`README.md`文件内容如下：

```markdown
如果想把GDB切换到原始模式，执行下面命令
./gdb_switch gdb
 
如果想把GDB切换到gef模式，执行下面命令
./gdb_switch gef
```

`gdb_switch.sh`脚本文件内容如下：

```shell
#!/bin/bash
str1=$1
str2="gdb"
str3="gef"
if [ "$str1" = "$str2" ] #注意这里的空格不能少！
then echo "" > ~/.gdbinit
elif [ "$str1" = "$str3" ]
then echo "source ~/GdbPlugins/gef-dev/gef.py" > ~/.gdbinit
else
	echo "Incoming parameter error"
fi
```

执行`./gdb_switch gdb`切换GDB到原始版本

![image-20230415111450760](F:\Documents\Typora_file\Linux学习.assets\image-20230415111450760.png)

调试程序，发现已经切换到GDB原始模式：

![image-20230415111538218](F:\Documents\Typora_file\Linux学习.assets\image-20230415111538218.png)

执行`./gdb_switch gef`切换到gef模式

![image-20230415111635796](F:\Documents\Typora_file\Linux学习.assets\image-20230415111635796.png)

调试程序，发现已经切换到gef模式：

![image-20230415111727074](F:\Documents\Typora_file\Linux学习.assets\image-20230415111727074.png)





## 多进程调试

**确定gdb中的进程跟踪模式**

- `follow-fork-mode`
`show follow-fork-mode`查看当前调试的fork进程的模式
如果此时调试的是父进程 返回`parent`
如果此时调试的是子进程 返回`child`
`set follow-fork-mode [parent|child]`
	- `parent`：gdb默认调试的是父进程，如果参数是parent则fork之后继续调试父进程，子进程不受影响
	- `child`：如果想调试子进程，则修改参数为child，set follow-fork-mode child之后调试子进程，父进程不受影响。


- `detach-on-fork`
`show detach-on-fork` 查看detach-on-fork模式,返回`on`或者`off`,gdb将每一个被调试进程的执行状态记录在一个名为inferior的结构中。一般情况下一个inferior对应一个进程，每个不同的inferior有不同的地址空间。inferior有时候会在进程没有启动的时候就存在。
`set detach-on-fork [on|off]`
	- on：断开调试follow-fork-mode调试的指定进程
	- off：gdb将控制父进程和子进程。follow-fork-mode指定的进程将被调试，另一个进程置于暂停（suspended）状态。

**两者具体关系如下表：**

| show follow-fork-mode | show detach-on-fork |                                        |
| :-------------------: | :-----------------: | -------------------------------------- |
|        parent         |         on          | 只调试父进程，子进程正常运行           |
|         child         |         on          | 只调试子进程，父进程正常运行           |
|        parent         |         off         | 同时调试两个进程，子进程暂停在fork位置 |
|         child         |         off         | 同时调试两个进程，父进程暂停在fork位置 |

- `info inferiors`
查询正在调试的进程,gdb会为他们分配唯一的Num号，其中前面带'*'号的就是正在调试的进程

- `inferior <inferior num>`
切换调试的进程为inferior num的进程处

- ` add-inferior [-copies n] [-exec executable] `
添加n个新的调试进程，可以用file executable来分配给inferior可执行文件。如果不指定n，则只增加一个inferior；如果不指定executable，则执行程序留空，增加后可使用file命令重新指定执行程序；这时候创建的inferior其关联的进程并没启动。

- `clone-inferior [-copies n] [infno]`
复制n个编号是infno的inferior。如果不指定n的话，就只复制一个inferior；如果不指定infno，则就复制正在调试的inferior

- `detach inferior infno`
断开(detach)掉编号是infno的inferior。值得注意的是这个inferior还存在，可以再次用run命令执行它。

- `kill inferior infno`
kill掉infno号inferior。值得注意的是这个inferior仍然存在，可以再次用run等命令执行它。

- `remove-inferior infno`
删除一个infno号的inferior。删除前需要先kill或者detach这个inferior，因为当一个inferior正在运行时不能被删除.



## 多线程调试
- `info threads`
显示当前可调试的所有线程。每个线程会有gdb为其分配的ID，后面的操作会用到这个ID。前面带'*'号的是当前正在调试的线程。

- `thread ID`
切换当前调试的线程为指定ID的线程

- `thread apply ID1 ID2 command `
让一个或者多个线程执行gdb命令command

- `thread apply all command`
让所有被调试线程执行gdb命令command

- `set scheduler-locking [off|on|step]`
值得注意的是，在使用step或者continue命令调试当前被调试线程的时候，其他线程也是同时执行的，怎么只让被调试程序执行呢？通过这个命令就可以实现这个需求。

  `off`：不锁定任何线程，也就是所有线程都执行，这是默认值。

  `on`：只有当前被调试程序会执行。 

  `step`：在单步的时候，除了next过一个函数的情况(熟悉情况的人可能知道，这其实是一个设置断点然后continue的行为)以外，只有当前线程会执行。

- `show scheduler-locking`
查看当前锁定线程的模式
















---







# 文件IO

<font color = pink>Linux下文件IO操作可见下列网站博主文章：</font>

```
https://blog.csdn.net/qq_43469158/article/details/118437075	// Linux文件IO详解

https://blog.csdn.net/rong09_13/article/details/79233956  // Linux下七种文件类型、文件属性及其查看方法

https://blog.csdn.net/yushuaigee/article/details/107883964	// 彻底弄懂 Linux 下的文件描述符（fd）
```



## 文件描述符

一个进程启动之后，默认打开三个文件描述符：

```c
#define  STDIN_FILENO     		0
#define  STDOUT_FILENO    	    1
#define  STDERR_FILENO    	    2
```



新打开文件返回文件描述符表中未使用的最小文件描述符,调用`open`函数可以打开或创建一个文件, 得到一个文件描述符.



## open函数

- 函数描述: 打开或者新建一个文件

- 函数原型: 

​     `int open(const char *pathname, int flags)`

​     ` int open(const char *pathname, int flags, mode_t mode)`

- 函数参数：

​     :elephant: `​pathname`参数是要打开或创建的文件名,和`fopen`一样, `pathname   `既可以是相对路径也可以是绝对路径。 

​     :eagle: `flags`参数有一系列常数值可供选择, 可以同时选择多个常数用按位或运算符连接起来, 所以这些常数的宏定义都以`O_`开头,表示`or`。

```
必选项:以下三个常数中必须指定一个, 且仅允许指定一个
O_RDONLY 只读打开
O_WRONLY 只写打开
O_RDWR 可读可写打开
```

```
可选项:可以同时指定0个或多个, 和必选项按位或起来作为flags参数。可选项有很多, 这里只介绍几个常用选项：

O_APPEND 表示追加。如果文件已有内容, 这次打开文件所写的数据附加到文件的末尾而不覆盖原来的内容。

O_CREAT 若此文件不存在则创建它。使用此选项时需要提供第三个参数mode, 表示该文件的访问权限。文件最终权限：mode & ~umask

O_EXCL 如果同时指定了O_CREAT,并且文件已存在,则出错返回。

O_TRUNC 如果文件已存在, 将其长度截断为为0字节。

O_NONBLOCK 对于设备文件, 以O_NONBLOCK方式打开可以做非阻塞I/O(NonblockI/O),非阻塞I/O。
```



- 函数返回值

​    成功: 返回一个最小且未被占用的文件描述符

​    失败: 返回-1, 并设置errno值.



## close函数

- 函数描述: 关闭文件

- 函数原型: `int close(int fd)`

- 函数参数:  fd文件描述符

- 函数返回值:

​      成功返回0

​      失败返回-1, 并设置errno值.

 

当一个进程终止时, 内核对该进程所有尚未关闭的文件描述符调用close关闭,所以即使用户程序不调用close, 在终止时内核也会自动关闭它打开的所有文件。但是对于一个长年累月运行的程序(比如网络服务器), 打开的文件描述符一定要记得关闭, 否则随着打开的文件越来越多, 会占用大量文件描述符和系统资源。



## read函数

- 函数描述: 从打开的设备或文件中读取数据

- 函数原型: `ssize_t read(int fd, void *buf, size_t count)`

- 函数参数:

​     `fd`: 文件描述符

​     `buf`: 读上来的数据保存在缓冲区buf中

​     `count`: buf缓冲区存放的最大字节数

- 函数返回值:

​      `返回值 > 0`：读取到的字节数

​      `返回值 = 0`：文件读取完毕

​      `返回值 = -1`： 出错，并设置errno



## write函数

- 函数描述: 向打开的设备或文件中写数据

- 函数原型: `ssize_t write(int fd, const void *buf, size_t count)`

- 函数参数： 

​     `fd`：文件描述符

​     `buf`：缓冲区，要写入文件或设备的数据

​     `count`：buf中数据的长度

- 函数返回值:

​     成功：返回写入的字节数

​     错误：返回-1并设置errno



## perror 和 errno

errno是一个全局变量, 当系统调用后若出错会将errno进行设置, perror可以将errno对应的描述信息打印出来.

如:perror("open"); 如果报错的话打印: open:(空格)错误信息



## 文件读写操作

<font color = pink>文件读写操作代码如下：</font>

```c
// IO函数测试 实现文件的读写操作
#include <stdio.h>
#include <stdlib.h>
#include <string.h>
#include <sys/types.h>
#include <sys/stat.h>
#include <fcntl.h>
#include <unistd.h>
int main()
{
	// 打开文件
	// int open(const char *pathname, int flags, mode_t mode);
	int fd = open("./test.txt", O_RDWR | O_CREAT, 0777);
	if(fd < 0)
	{
		perror("Open Error");
		return -1;
	}
	
	// 写文件
	// ssize_t write(int fd, const void *buf, size_t count);
	write(fd, "Hello World", strlen("Hello World"));
    
	// 移动文件指针到开始处
	// off_t lseek(int fd, off_t offset, int whence);
	lseek(fd, 0, SEEK_SET);

	// 读文件
	// ssize_t read(int fd, void *buf, size_t count);
	char buf[1024];
	memset(buf, 0x00, sizeof(buf));
	int n = read(fd, buf, sizeof(buf));
	printf("n = [%d], buf = [%s]\n", n, buf);

	// 关闭文件
	close(fd);
	return 0;
}
```





## lseek函数

所有打开的文件都有一个**当前文件偏移量(current file offset)**,以下简称为cfo. cfo通常是一个非负整数, 用于表明文件开始处到文件当前位置的字节数. 读写操作通常开始于 cfo, 并且使 cfo 增大, 增量为读写的字节数. 文件被打开时, cfo 会被初始化为 0, 除非使用了 O_APPEND.

使用 lseek 函数可以改变文件的 cfo.

- 函数描述: 移动文件指针

- 函数原型: `off_t lseek(int fd, off_t offset, int whence)`

- 函数参数：

​     `fd`：文件描述符

:cat: 参数 `offset` 的含义取决于参数 `whence`：

如果 `whence` 是 `SEEK_SET`，文件偏移量将设置为 `offset`。

如果 `whence` 是 `SEEK_CUR`，文件偏移量将被设置为 `cfo` 加上 `offset`，`offset` 可以为正也可以为负。

如果 `whence` 是 `SEEK_END`，文件偏移量将被设置为文件长度加上 `offset`，`offset` 可以为正也可以为负。

- 函数返回值: 若lseek成功执行, 则返回新的偏移量。



lseek函数常用操作

- 文件指针移动到头部     `lseek(fd, 0, SEEK_SET)`

- 获取文件指针当前位置  `int len = lseek(fd, 0, SEEK_CUR)`

- 获取文件长度                `int len = lseek(fd, 0, SEEK_END)`





## lseek应用

<font face = "kaiti" size = 5 color = pink>lseek函数应用代码如下：</font>

```c
// 利用lseek函数获取文件大小
#include <stdio.h>
#include <stdlib.h>
#include <string.h>
#include <sys/types.h>
#include <sys/stat.h>
#include <fcntl.h>
#include <unistd.h>
int main()
{
	// 打开文件
	// int open(const char *pathname, int flags, mode_t mode);
	int fd = open("./test.txt",O_RDWR | O_CREAT, 0777);
	if(fd < 0)
	{
		perror("Open Error");
		return -1;
	}
	// 写文件
	write(fd, "hello world", sizeof("hello world"));

	// 获取文件大小
	int file_size = lseek(fd, 0, SEEK_END);
	printf("file of size is %d\n", file_size);	

	// 关闭文件
	close(fd);
	return 0;
}
```

```c
// 利用lseek来实现文件的扩展
#include <stdio.h>
#include <stdlib.h>
#include <string.h>
#include <sys/types.h>
#include <sys/stat.h>
#include <fcntl.h>
#include <unistd.h>
int main()
{
	// 打开文件
	// int open(const char *pathname, int flags, mode_t mode);
	int fd = open("./test.txt",O_RDWR | O_CREAT, 0777);
	if(fd < 0)
	{
		perror("Open Error");
		return -1;
	}
	// 写文件
	write(fd, "hello world", strlen("hello world"));

	// 打印文件大小
	int len1 = lseek(fd, 0, SEEK_END);
	printf("修改之前file of size is %d\n", len1);	
	
	// 用lseek实现指针移动到开始后的100字节处
	lseek(fd, 100, SEEK_SET);
	// 写一次
	write(fd, "H", strlen("H"));
	// 修改之后文件的大小
	int len2 = lseek(fd, 0, SEEK_END);
	printf("修改之后file of size is %d\n", len2);	

	// 关闭文件
	close(fd);
	return 0;
}

```





## dup函数

- 函数描述: 复制文件描述符

- 函数原型: `int dup(int oldfd)`

- 函数参数: `oldfd` -要复制的文件描述符

- 函数返回值:

​     成功: 返回最小且没被占用的文件描述符

​     失败: 返回-1, 设置`errno`值



## dup2函数

- 函数描述: 复制文件描述符

- 函数原型: `int dup2(int oldfd, int newfd)`

- 函数参数: 
    - `oldfd`-原来的文件描述符
    - `newfd`-复制成的新的文件描述符

- 函数返回值:

    - 成功: 将oldfd复制给newfd, 两个文件描述符指向同一个文件

    - 失败: 返回-1, 设置errno值

- 假设newfd已经指向了一个文件，首先close原来打开的文件，然后newfd指向oldfd指向的文件.若newfd没有被占用，newfd指向oldfd指向的文件.



## fcntl函数

- 函数描述: 改变已经打开的文件的属性

- 函数原型: `int fcntl(int fd, int cmd, ... /* arg */ )`
    - 若cmd为`F_DUPFD`, 复制文件描述符, 与dup相同
    - 若cmd为`F_GETFL`, 获取文件描述符的flag属性值
    - 若cmd为 `F_SETFL`, 设置文件描述符的flag属性

- 函数返回值:返回值取决于cmd
    - 成功

         若cmd为`F_DUPFD`, 返回一个新的文件描述符

         若cmd为`F_GETFL`, 返回文件描述符的flags值

         若cmd为`F_SETFL`, 返回0

    - 失败返回-1, 并设置errno值.

fcntl函数常用的操作:

1 复制一个新的文件描述符:

   `int newfd = fcntl(fd, F_DUPFD, 0)`

2 获取文件的属性标志

   `int flag = fcntl(fd, F_GETFL, 0)`

3 设置文件状态标志

   `flag = flag | O_APPEND`

   `fcntl(fd, F_SETFL, flag)`

4 常用的属性标志

   `O_APPEND`------- 设置文件打开为末尾添加

   `O_NONBLOCK`-----设置打开的文件描述符为非阻塞





![image-20230401094651599](F:\Documents\Typora_file\Linux学习.assets\image-20230401094651599.png)







## dup系函数使用

<font face = "kaiti" size = 5 color = pink>dup函数和dup2函数应用代码如下：</font>

```c
// 利用dup函数复制文件描述符
#include <stdio.h>
#include <stdlib.h>
#include <string.h>
#include <sys/types.h>
#include <sys/stat.h>
#include <fcntl.h>
#include <unistd.h>
int main(int argc, char *argv[])
{
	// 打开文件
	int fd = open(argv[1], O_RDWR);
	// 判断文件是否打开
	if(fd < 0)
	{
		perror("open error");
		return -1;
	}
	
	// 用dup函数复制文件描述符
	int newfd = dup(fd);
	printf("fd = %d, newfd = %d\n", fd, newfd);
	
	// 写文件
	write(fd, "hello world", strlen("hello world"));
	// 移动文件指针到开始处
	lseek(fd, 0, SEEK_SET);

	// 用newfd读文件
	char buf[64];
	memset(buf, 0x00, sizeof(buf));
	int n = read(fd, buf, sizeof(buf));
	printf("n = %d, buf = [%s]\n", n, buf);

	// 关闭文件
	close(fd);
	close(newfd);
}
```

```c
// 利用dup2函数复制文件描述符
#include <stdio.h>
#include <stdlib.h>
#include <string.h>
#include <sys/types.h>
#include <sys/stat.h>
#include <fcntl.h>
#include <unistd.h>

int main(int argc, char *argv[])
{
	// 打开oldfd文件
	int oldfd = open(argv[1], O_RDWR | O_CREAT);
	// 判断文件是否打开
	if(oldfd < 0)
	{
		perror("open error");
		return -1;
	}
	
	// 打开newfd文件
	int newfd = open(argv[2], O_RDWR | O_CREAT);
	// 判断文件是否打开
	if(newfd < 0)
	{
		perror("open error");
		return -1;
	}

	// 用dup2函数复制文件描述符
	dup2(oldfd, newfd);
	printf("oldfd = %d, newfd = %d\n", oldfd, newfd);
	
	// 用newfd写文件
	write(newfd, "hello world", strlen("hello world"));
	// 移动文件指针到开始处
	lseek(newfd, 0, SEEK_SET);

	// 用oldfd读文件
	char buf[64];
	memset(buf, 0x00, sizeof(buf));
	int n = read(oldfd, buf, sizeof(buf));
	printf("n = %d, buf = [%s]\n", n, buf);

	// 关闭文件
	close(oldfd);
	close(newfd);
}
```

```c
// 利用dup2函数进行文件重定向操作
#include <stdio.h>
#include <stdlib.h>
#include <string.h>
#include <sys/types.h>
#include <sys/stat.h>
#include <fcntl.h>
#include <unistd.h>
int main(int argc, char *argv[])
{
	// 打开oldfd文件
	int oldfd = open(argv[1], O_RDWR | O_CREAT, 0777);
	// 判断文件是否打开
	if(oldfd < 0)
	{
		perror("open error");
		return -1;
	}
	
	dup2(oldfd, STDOUT_FILENO);
	printf("hello world");

	// 关闭文件
	close(oldfd);
	close(STDOUT_FILENO);
	return 0;
}
```







## stat/lstat函数



- 函数描述: 获取文件属性
- 函数原型: 
 `int stat(const char *pathname, struct stat *buf)`

   `int lstat(const char *pathname, struct stat *buf)`

- 函数返回值： 

    - 成功返回 0

    - 失败返回 -1

```c
struct stat 
{
	dev_t    st_dev;   //文件的设备编号
	ino_t    st_ino;   //节点
	mode_t   st_mode;  //文件的类型和存取的权限
	nlink_t  st_nlink; //连到该文件的硬连接数目，刚建立的文件值为1
    uid_t    st_uid;   //用户ID
	gid_t    st_gid;   //组ID
	dev_t    st_rdev;  //(设备类型)若此文件为设备文件，则为其设备编号
	off_t    st_size;  //文件字节数(文件大小)
	blksize_t  st_blksize; //块大小(文件系统的I/O 缓冲区大小)
	blkcnt_t   st_blocks;  //块数
	time_t     st_atime;   //最后一次访问时间
	time_t     st_mtime;   //最后一次修改时间
	time_t     st_ctime;   //最后一次改变时间(指属性)
};

```



**stat函数和lstat函数的区别：**

- 对于普通文件, 这两个函数没有区别, 是一样的.

- 对于连接文件,调用lstat函数获取的是链接文件本身的属性信息;而stat函数获取的是链接文件指向的文件的属性信息.





<font face = "kaiti" size = 5 color = pink>使用st_mode判断文件属性</font>

```c
// 使用st_mode判断文件属性
#include <sys/types.h>
#include <sys/stat.h>
#include <unistd.h>
#include <stdio.h>
#include <stdlib.h>
#include <string.h>

int main(int argc, char *argv[])
{
	// int stat(const char *pathname, struct stat *statbuf);
	struct stat sb;

	stat(argv[1], &sb);

	if ((sb.st_mode & S_IFMT) == S_IFREG) {
		/* Handle regular file */
		printf("这是一个普通文件\n");
	}

	else if((sb.st_mode & S_IFMT) == S_IFSOCK)
	{
		printf("这是一个socket文件\n");
	}
	else if((sb.st_mode & S_IFMT) == S_IFLNK)
	{
		printf("这是一个链接文件\n");
	}
	else if((sb.st_mode & S_IFMT) == S_IFDIR)
	{
		printf("这是一个目录\n");
	}

	// 判断文件权限
	if(sb.st_mode & S_IROTH)
	{
		printf("该文件具有读权限\n");
	}
	if(sb.st_mode & S_IWOTH)
	{
		printf("该文件具有写权限\n");
	}
	if(sb.st_mode & S_IXOTH)
	{
		printf("该文件具有执行权限\n");
	}


	return 0;
}

```





## opendir函数

- 函数描述:打开一个目录 

- 函数原型: `DIR *opendir(const char *name)`

- 函数返回值: 指向目录的指针

- 函数参数: 要遍历的目录(相对路径或者绝对路径)



## readdir函数

- 函数描述: 读取目录内容--目录项

- 函数原型: `struct dirent *readdir(DIR *dirp)`

- 函数返回值: 读取的目录项指针

- 函数参数: `opendir`函数的返回值

```c
struct dirent

{
	ino_t d_ino;       // 此目录进入点的inode
	off_t d_off;       // 目录文件开头至此目录进入点的位移
	signed short int d_reclen;  // d_name 的长度, 不包含NULL 字符
	unsigned char d_type;   // d_name 所指的文件类型 
	char d_name[256];       // 文件名

};
```



 **结构体中`d_type`的取值:** 

- `DT_BLK` - 块设备

- `DT_CHR` - 字符设备 

- `DT_DIR` - 目录 

- `DT_LNK` - 软连接 
- `DT_FIFO` - 管道
- `DT_REG` - 普通文件
- `DT_SOCK` - 套接字

- `DT_UNKNOWN` - 未知 

![image-20230401083925399](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20230401083925399.png)



## closedir函数

- 函数描述: 关闭目录

- 函数原型: `int closedir(DIR *dirp)`

- 函数返回值: 成功返回0, 失败返回-1

- 函数参数: opendir函数的返回值



## 读取目录内容的一般步骤

1 `DIR *pDir = opendir(“dir”)` //打开目录

2 `while((p=readdir(pDir))!=NULL){}` //循环读取文件

3 `closedir(pDir)`//关闭目录





## 目录函数代码

<font face = "kaiti" size = 5 color = pink>目录函数操作代码如下：</font>

```c
// 目录测试 opendir readdir closedir
#include <sys/types.h>
#include <dirent.h>
#include <stdio.h>
#include <stdlib.h>
#include <string.h>

int main(int argc, char *argv[])
{
	// 打开目录
	// DIR *opendir(const char *name);
	DIR *odr = opendir(argv[1]);
	if(odr == NULL)
	{
		perror("opendir error");
		return -1;
	}
	// 循环读取目录
	// struct dirent *readdir(DIR *dirp);
	struct dirent *pdir = NULL;
	while((pdir = readdir(odr)) != NULL)
	{
		if(strcmp(pdir->d_name, ".") == 0 || strcmp(pdir->d_name, "..") == 0)
		{
			continue;
		}
		// 文件名字
		printf("文件名：%s", pdir->d_name);
		// Inode number
		printf("===");
		printf("Inode number:%ld", pdir->d_ino);
		// 文件类型
		printf(" ===>> ");
		switch(pdir->d_type)
		{
			case DT_BLK:
				printf("This is a block device.");
				break;
			case DT_CHR:
				printf("This is a character device.");
				break;
			case DT_DIR:
				printf("This is a directory.");
				break;
			case DT_LNK:
				printf("This is a symbolic link.");
				break;
			case DT_REG:
				printf("This is a regular file.");
				break;
			default:
				printf("未知文件！");
		}
		printf("\n");
	}
	// 关闭目录
	closedir(odr);
	return 0;
}

```



---



# 进程控制



## 进程相关概念

### 程序和进程

- <font size = 5 color = pink>**程序**，</font>是指编译好的二进制文件，在磁盘上，占用磁盘空间，是一个静态的概念。

- <font size = 5 color = pink>**进程**，</font>一个启动的程序，进程占用的是系统资源，如：物理内存，CPU，终端等，是一个动态的概念

  

### 并行和并发

- <font size = 5 color = pink>**并发**，</font>在一个时间段内，是在同一个CPU上，同时运行多个程序。

  如：若将CPU的1S的时间分成1000个时间片，每个进程执行完一个时间片必须无条件让出CPU的使用权，这样1S中就可以执行1000个进程。

![image-20221023180501569](Linux学习.assets/image-20221023180501569.png)

![image-20221023180522256](Linux学习.assets/image-20221023180522256.png)

![image-20221023180531127](Linux学习.assets/image-20221023180531127.png)

![image-20221023180538625](Linux学习.assets/image-20221023180538625.png)

- <font size = 5 color = pink>**并行性**</font>指两个或两个以上的程序在同一时刻发生。

![image-20221023180749761](Linux学习.assets/image-20221023180749761.png)

![image-20221023180756519](Linux学习.assets/image-20221023180756519.png)



## PCB进程控制块

每个进程在内核中都有一个**进程控制块（PCB）**来维护进程相关的信息，Linux内核的进程控制块是task_struct结构体。	 

`/usr/src/linux-headers-4.4.0-96/include/linux/sched.h`文件可以查看`struct task_struct` 结构体定义。其内部成员有很多，重点掌握以下部分即可：

:icecream:	<font color = skyblue>进程id。系统中每个进程有唯一的id，在C语言中用pid_t类型表示，其实就是一个非负整数。</font>

:icecream:	<font color = skyblue>进程的状态，有就绪、运行、挂起、停止等状态。</font>

:icecream:	进程切换时需要保存和恢复的一些CPU寄存器。

:icecream:	描述虚拟地址空间的信息。

:icecream:	描述控制终端的信息。

:icecream:	当前工作目录。

:icecream:	umask掩码。

:icecream:	文件描述符表，包含很多指向file结构体的指针。

:icecream:	和信号相关信息。

:icecream:	用户id和组id。

:icecream:	会话和进程组。

:icecream:	进程可以使用的资源上限（Resource Limit）。		

```shell
ulimit -a
```



## 进程状态(面试常考)

- 进程基本的状态有5种。分别为**初始态，就绪态，运行态，挂起态与终止态**。其中初始态为进程准备阶段，常与就绪态结合来看。

![image-20221023182650445](Linux学习.assets/image-20221023182650445.png)



## 创建进程

<font color = pink>fork函数介绍：</font>

```fork函数介绍
函数作用：创建子进程
原型：pid_t fork(void)
函数参数：无
返回值:调用成功==>父进程返回子进程的PID，子进程返回0；
      调用失败==>返回-1，设置errno值。

```

<font color = pink>fork函数代码示例：</font>

```c
#include <stdio.h>
#include <stdlib.h>
#include <string.h>
#include <sys/types.h>
#include <unistd.h>
int main()
{
	// 获取当前进程即父进程的pid
    printf("before fork pid = %d\n", getpid());

    // pid_t fork(void);
    // 创建子进程
    pid_t pid = fork();
    printf("fork函数返回的pid = %d\n", pid);
    if(pid < 0)
    {
        perror("fork error");
        return -1;
    }
    else if(pid == 0)
    {
        printf("我是child进程: pid = %d, ppid = %d\n", getpid(), getppid());
    }
    else
    {
        printf("我是farther进程: pid = %d, ppid = %d\n", getpid(), getppid());
        sleep(1);
    }
    printf("当前进程pid = %d\n", getpid());
    return 0;
}
```

<font color = pink>执行结果如下：</font>

![image-20221104144005500](Linux学习.assets/image-20221104144005500.png)

<font color = pink>调用fork函数的内核实现原理：</font>

![image-20221104144129531](Linux学习.assets/image-20221104144129531.png)

<font color = pink>fork函数总结</font>

```fork函数总结
==>fork函数的返回值？
	父进程返回子进程的PID，是一个大于0的数；
	子进程返回0；
	特别注意的是：不是fork函数在一个进程中返回两个值，而是在父子进程中各自返回一个值，例如上述例子中的pid = 3501和pid = 0.
	
==>子进程创建成功后，代码的执行位置？
	父进程执行到什么位置，子进程就从哪里执行
==>如何区分父子进程
	通过fork函数的返回值
==>父子进程的执行顺序
	顺序是不确定的，哪个进程先抢到CPU，哪个进程就先执行
```



## 父子进程能否共享全局变量

当利用fork函数创建出一个子进程之后，子进程会复制父进程的**虚拟**地址空间，也就是说子进程会复制父进程的数据段。那么接下来我们就要验证子进程与父进程能否共享全局变量。

**验证代码如下：**

```c
// 全局变量读的时候共享  写的时候就在物理内存中新建了一个
#include <stdio.h>
#include <stdlib.h>
#include <string.h>
#include <sys/types.h>
#include <unistd.h>

int g_x = 99; // 全局变量
int main()
{
	printf("父子进程都未修改全局变量前地址为：%p\n", &g_x);
	// pid_t fork(void);
	// 创建子进程
	pid_t pid = fork();
	if(pid < 0)
	{
		perror("fork error");
		return -1;
	}
	else if(pid == 0)
	{
		sleep(1);
		printf("child: pid = %d, ppid = %d\n", getpid(), getppid());
		printf("父进程修改，子进程未修改前全局变量的地址：%p\n", &g_x);
		printf("父进程修改，子进程未修改前全局变量的值：%d\n", g_x);
		g_x--;
		printf("子进程修改后全局变量的地址：%p\n", &g_x);
		printf("子进程修改后全局变量的值：%d\n", g_x);
	}
	else
	{
		printf("farther: pid = %d, ppid = %d\n", getpid(), getppid());
		// 修改全局变量
		g_x++;
		printf("子进程未修改，父进程修改后全局变量的值：%d\n", g_x);
		printf("子进程未修改，父进程修改后全局变量地址：%p\n", &g_x);
		sleep(5);
		printf("子进程修改，父进程中全局变量的值：%d\n", g_x);
		printf("子进程修改，父进程中全局变量的地址：%p\n", &g_x);
	}
	return 0;
}

```



执行结果如下：

![image-20230403090910755](F:\Documents\Typora_file\Linux学习.assets\image-20230403090910755.png)

从执行结果可以看出当在父进程中修改全局变量的值时，子进程中的全局变量没有改变，同时子进程修改，父进程中也没有改变。那么父子进程之间到底共享全局变量吗？

可以看到父子进程打印的地址都是一样的，那么为啥同样的地址上存储的值却不同呢？其实我们代码中显示的内存地址是虚拟内存的地址，每一个虚拟内存都映射一个物理内存，又因为子进程是复制了父进程的虚拟空间的，所以两者虚拟地址是相同的。当在一个进程中对全局变量的值进行修改，实际上是在物理内存中给全局变量创建了一个副本，修改操作是在副本上面做的，操作如下图所示：

![image-20230403092300689](F:\Documents\Typora_file\Linux学习.assets\image-20230403092300689.png)



**结论：**

- 父子进程不能共享全局变量
- 如果父子进程只是对全局变量做读操作，则父子进程在内存共享同一份全局变量
- 如果父子进程中的任何一个对变量做修改操作，会在内存中拷贝一份副本，然后在这个副本上进行修改，修改完成后再通过MMU（内存管理单元）映射回去







## ps命令和kill命令

<font color = pink>ps命令介绍：</font>

```ps命令介绍
ps aux | grep "xxx"
ps ajx | grep "xxx"
	-a：(all)当前系统所有用户的进程
	-u：查看进程所有者及其他一些信息
	-x：显示没有控制终端的进程--不能与用户进行交互的进程【输入、输出】
	-j：列出与作业控制相关的信息
具体介绍可见下列网站：
	https://wangchujiang.com/linux-command/c/cp.html#!kw=open
```

<font color = pink>kill命令介绍</font>

```kill命令介绍
kill -l 查看系统有那些信号
kill -9 pid 杀死某个进程
```



## exec函数族

<font color = pink>exec函数作用</font>

有的时候需要在一个进程里面执行其他的命令或者是用户自定义的应用程序，此时就用到了exec函数族当中的函数。

使用方法一般都是在父进程里面调用fork创建处子进程，然后在子进程里面调用exec函数。

<font color = pink>exec函数介绍</font>

```execl函数介绍
头文件：#include <unistd.h>
函数原型：int execl(const char *pathname, const char *arg, ...  /* (char  *) NULL */);
参数介绍：
	path：要执行的程序的绝对路径
	变参arg：要执行的程序的需要参数
	arg：占位，通常写应用程序的名字
	arg后面的：命令的参数
	参数写完之后：NULL
返回值：若是成功，则不返回，不会再执行exec函数后面的代码；若是失败，会执行execl后面的代码，可以用perror打印错误原因。execl函数一般执行自己写的程序。
```

<font color = pink>execl函数测试实例</font>

```c
// 测试execl
#include <stdio.h>
#include <stdlib.h>
#include <string.h>
#include <sys/types.h>
#include <unistd.h>
int main()
{
	// pid_t fork(void);
    // 创建子进程
    pid_t pid = fork();
    if(pid < 0)
    {
        perror("fork error");
        return -1;
    }
    else if(pid == 0) // 子进程
    {
        printf("child: pid = %d, ppid = %d\n", getpid(), getppid());
        // 相当于调用当前文件夹下的test程序 并且给它传参数
        execl("./test","test", "hello","world","hah","Hah", NULL);
        perror("execl error");
    }
    else  // 父进程
    {
        sleep(1);
        printf("farther: pid = %d, ppid = %d\n", getpid(), getppid());
        // sleep(1);
    }
    return 0;
}

// test函数代码实现
#include <stdio.h>
#include <stdlib.h>
#include <string.h>
#include <unistd.h>
int main(int argc, char* argv[])
{
    for(int i = 0; i < argc; ++i)
    {
        printf("[%d]==>[%s]\n", i, argv[i]);
    }
    // 相当于执行 ls -a -l命令
    execl("/usr/bin/ls", "-a", "-l", NULL);
    return 0;
}
```

<font color = pink>运行结果如下</font>

![image-20221104161631438](Linux学习.assets/image-20221104161631438.png)

<font color = pink>execlp函数</font>

```execlp函数介绍
函数原型: int execlp(const char *file, const char *arg, .../* (char  *) NULL */);
参数介绍：
	file: 执行命令的名字, 根据PATH环境变量来搜索该命令
	arg:占位
	arg后面的: 命令的参数
	参数写完之后: NULL
返回值：若是成功，则不返回，不会再执行exec函数后面的代码；若是失败，会执行exec后面的代码，可以用perror打印错误原因。
execlp函数一般是执行系统自带的程序或者是命令.
```

<font color = pink>exec函数族原理介绍</font>

exec函数族实现原理图：

​	如：execlp("ls", "ls", "-l", NULL);

![image-20221104162434552](Linux学习.assets/image-20221104162434552.png)

<font color = pink>总结:</font>

exec函数是用一个新程序替换了当前进程的代码段、数据段、堆和栈；原有的进程空间没有发生变化，并没有创建新的进程，进程PID没有发生变化。



## 进程回收

### 进程回收的目的

当一个进程退出之后，进程能够回收自己的用户区的资源，但是不能回收内核空间的PCB资源，必须由它的父进程调用`wait`或者`waitpid`函数完成对子进程的回收，避免造成系统资源的浪费。

### 孤儿进程

<font color = pink>孤儿进程的概念：</font>

若子进程的父进程已经死掉，而子进程还存活着，这个进程就成了孤儿进程。为了保证每个进程都有一个父进程，孤儿进程会被`init`进程领养，init进程成为了孤儿进程的养父进程，当孤儿进程退出之后，由init进程完成对孤儿进程的回收。

<font color = pink>模拟孤儿进程案例代码：</font>

```c
// 孤儿进程实例
#include <stdio.h>
#include <stdlib.h>
#include <string.h>
#include <sys/types.h>
#include <unistd.h>

int main()
{
    // pid_t fork(void);
    // 创建子进程
    pid_t pid = fork();
    if(pid < 0)
    {
        perror("fork error");
        return -1;
    }
    else if(pid == 0)
    {
        // 阻塞20s，父进程先被回收，子进程就成为孤儿进程
        sleep(20);
        printf("child: pid = %d, ppid = %d\n", getpid(), getppid());
    }
    else
    {
        printf("farther: pid = %d, ppid = %d\n", getpid(), getppid());
        // sleep(1);
    }
    return 0;
}
```

执行结果如下图所示：

![image-20221104165449283](Linux学习.assets/image-20221104165449283.png)



### 僵尸进程

<font color = pink>僵尸进程的概念：</font>

若子进程死了，父进程还活着， 但是父进程没有调用`wait`或`waitpid`函数完成对子进程的回收，则该子进程就成了僵尸进程。

<font color = pink>如何解决僵尸进程？</font>

==>由于僵尸进程是一个已经死亡的进程，所以不能使用`kill`命令将其杀死

==>通过杀死其父进程的方法可以消除僵尸进程。杀死其父进程后，这个僵尸进程会被init进程领养，由init进程完成对僵尸进程的回收。

<font color = pink>模拟僵尸进程</font>

```c
// 僵尸进程实例
#include <stdio.h>
#include <stdlib.h>
#include <string.h>
#include <sys/types.h>
#include <unistd.h>

int main()
{
    // pid_t fork(void);
    // 创建子进程
    pid_t pid = fork();
    if(pid < 0)
    {
        perror("fork error");
        return -1;
    }
    else if(pid == 0)
    {
        printf("child: pid = %d, ppid = %d\n", getpid(), getppid());

    }
    else
    {
        // 阻塞200s使得父进程无法对子进程进行回收，这样子进程死后就成为僵尸进程了
        sleep(200);
        printf("farther: pid = %d, ppid = %d\n", getpid(), getppid());
    }
    return 0;
}
```

代码执行结果：

![image-20221104170726399](Linux学习.assets/image-20221104170726399.png)

![image-20221104170838660](Linux学习.assets/image-20221104170838660.png)

然后杀死父进程，执行下列代码：

```shell
kill -9 4224  // 杀死子进程的父进程 让init来回收子进程
```

结果如下：

![image-20221104171124670](Linux学习.assets/image-20221104171124670.png)



### 进程回收函数

<font color = pink>wait函数介绍</font>

```wait函数介绍
头文件: #include <sys/types.h>
       #include <sys/wait.h>
函数原型：pid_t wait(int *status);
函数作用：
	1，阻塞并等待子进程退出；
	2，回收子进程残留资源；
	3，获取子进程结束状态（退出原因）；
返回值：
	成功：清理掉的子进程ID；
	失败：-1（没有子进程）；
status参数：子进程的退出状态--传出参数
	WIFEXITED(status)：为非0   ==> 进程正常结束
	WEXITSTATUS(status)：获取进程退出状态
	WIFSIGNALED(status)：为非0  ==> 进程异常终止
	WTERMSIG(status)：取得进程终止的信号编号
```

<font color = pink>wait函数代码示例：</font>

```c
// wait函数的使用
#include <stdio.h>
#include <stdlib.h>
#include <string.h>
#include <sys/types.h>
#include <unistd.h>
#include <sys/wait.h>
int main()
{
	// pid_t fork(void);
	// 创建子进程
	pid_t pid = fork();
	if(pid < 0)
	{
		perror("fork error");
		return -1;
	}
	else if(pid == 0)
	{
		printf("child: pid = %d, ppid = %d\n", getpid(), getppid());
		sleep(2);
		return 5;
	}
	else
	{
		printf("farther: pid = %d, ppid = %d\n", getpid(), getppid());
		int status;
		pid_t wpid = wait(&status);
		printf("wpid = [%d]\n", wpid);
		if(WIFEXITED(status))
		{
			printf("child normal exit [%d]\n", WEXITSTATUS(status));
		}
		else if(WIFSIGNALED(status))
		{
			printf("child killed by signal [%d]\n", WTERMSIG(status));
		}
	}
	return 0;
}

```

执行结果如下：

![image-20221104190129634](Linux学习.assets/image-20221104190129634.png)



<font color = pink>waitpid函数介绍</font>

```waitpid函数介绍
头文件：#include <sys/types.h>
	   #include <sys/wait.h>
函数原型：pid_t waitpid(pid_t pid, int *status, in options);
函数作用：同wait函数
参数介绍：
	pid：
		pid = -1 等待任一子进程，与wait等效；
		pid > 0 等待其进程ID与pid相等的子进程；
		pid = 0 等待进程组ID与目前进程相同的任何子进程，也就是说任何和调用waitpid()函数的进程在同一个进程组的进程；
		pid < -1 等待其组ID等于pid的绝对值的任一子进程（适用于子进程在其他组的情况）；
	status：子进程的退出状态，用法同wiat函数。
	options：设置为WNOHANG，函数非阻塞，设置为0，函数阻塞；
函数返回值：
	>0：返回回收掉的子进程ID
	-1：无子进程
	=0：参3为WNOHANG，且子进程正在运行
```

<font color = pink >waitpid函数执行示例：</font>

```c
// waitpid函数的使用
#include <stdio.h>
#include <stdlib.h>
#include <string.h>
#include <sys/types.h>
#include <unistd.h>
#include <sys/wait.h>

int main()
{
	// pid_t fork(void);
	// 创建子进程
	pid_t pid = fork();
	if(pid < 0)
	{
		perror("fork error");
		return -1;
	}
	else if(pid == 0)
	{
		printf("child: pid = %d, ppid = %d\n", getpid(), getppid());
		sleep(200);
		return 5;
	}
	else
	{
		printf("farther: pid = %d, ppid = %d\n", getpid(), getppid());
		int status;
		// pid_t waitpid(pid_t pid, int *wstatus, int options);
		// pid_t wpid = waitpid(-1,&status,0);
		pid_t wpid = waitped(pid, &status, WNOHANG);
		printf("wpid = [%d]\n", wpid);
		if(WIFEXITED(status))
		{
			printf("child normal exit [%d]\n", WEXITSTATUS(status));
		}
		else if(WIFSIGNALED(status))
		{
			printf("child killed by signal [%d]\n", WTERMSIG(status));
		}
	}
	return 0;
}
```





---------



# 进程间通信

## 进程间通信相关概念

<font color = pink >什么是进程间通信</font>

Linux环境下，进程地址空间相互独立，每个进程各自有不同的用户地址空间。任何一个进程的全局变量在另一个进程中都看不到，所以进程和进程之间不能相互访问，要交换数据必须通过内核，在内核中开辟一块缓冲区，进程1把数据从用户空间拷到内核缓冲区，进程2再从内核缓冲区把数据读走，内核提供的这种机制称为进程间通信（IPC，InterProcess Communication）。

![image-20221107105524511](Linux学习.assets/image-20221107105524511.png)

<font color = pink >进程间通信的方式</font>

在进程间完成数据传递需要借助操作系统提供特殊的方法，如：文件、管道、信号、共享内存、消息队列、套接字、命名管道等。随着计算机的蓬勃发展，一些方法由于自身设计缺陷被淘汰或者弃用。

**现今常用的进程间通信方式有：**

- 管道（使用最简单）
- 信号（开销最小）
- 共享映射区（无血缘关系）
- 本地套接字（最稳定）



## 管道pipe

<font color = pink >管道的概念</font>

管道是一种最基本的IPC机制，也称匿名管道，应用于有血缘关系的进程之间，完成数据传递。调用pipe函数即可创建一个管道。

![image-20221107110022760](Linux学习.assets/image-20221107110022760.png)

<font color = pink >管道有如下性质：</font>

- 管道的本质是一块内核缓冲区；
- 由两个文件描述符引用，一个表示读端，一个表示写端；
- 规定数据从管道的写端流入管道，从读端流出；
- 当两个进程都终结的时候，管道也自动消失；
- 管道的读端和写端默认都是阻塞的。

<font color = pink >管道的原理：</font>

- 管道的实质是内核缓冲区，内部使用环形队列实现；

- 默认缓冲区大小为4K，可以使用`ulimit -a`命令获取大小；

- 实际操作过程中缓冲区会根据数据压力做适当调整；

  

<font color = pink >管道的局限性：</font>

- 数据一旦被读走，便不在管道中存在，不可反复读取；

- 数据只能在一个方向上流动，若要实现双向流动，必须使用两个管道；

- **只能在有血缘关系的进程间使用管道**；

  

<font color = pink >创建管道--pipe函数</font>

```pipe函数
函数作用：
	创建一个管道
函数原型：
	int pipe(int fd[2]);
函数参数：
	若函数调用成功，fd[0]存放管道的读端,fd[1]存放管道的写端；
返回值：
	==>成功返回0；
	==>失败返回-1，并设置errno值；
```

函数调用成功返回读端和写端的文件描述符，其中**fd[0]**是读端，**fd[1]**是写端**，**向管道读写数据是通过使用这两个文件描述符进行的，**读写管道的实质是操作内核缓冲区**。

管道创建成功以后，创建该管道的进程（父进程）同时掌握着管道的读端和写端。



<font color = pink >父子进程使用管道通信</font>

一个进程在由pipe()创建管道后，一般再fork一个子进程，然后通过管道实现父子进程间的通信（因此也不难推出，只要两个进程中存在血缘关系，这里的血缘关系指的是具有共同的祖先，都可以采用管道方式来进行通信）。**父子进程间具有相同的文件描述符，且指向同一个管道pipe**，其他没有关系的进程不能获得`pipe()`产生的两个文件描述符，也就不能利用同一个管道进行通信。

<font color = sandybeige>第一步：父进程创建管道</font>

![image-20221107113459394](Linux学习.assets/image-20221107113459394.png)

<font color = sandybeige>第二步：父进程fork出子进程</font>

![image-20221107113614452](Linux学习.assets/image-20221107113614452.png)

<font color = sandybeige>第三步：父进程关闭fd[0]，子进程关闭fd[1]</font>

![image-20221107113721001](Linux学习.assets/image-20221107113721001.png)

<font color = lightblue>创建管道步骤总结：</font>

	1. 父进程调用pipe函数创建管道，得到两个文件描述符fd[0]和fd[1]，分别指向管道的读端和写端;
	2. 父进程调用fork创建子进程，那么子进程也有两个文件描述符指向同一管;
	3. 父进程关闭管道读端，子进程关闭管道写端。父进程可以向管道中写入数据，子进程将管道中的数据读出，这样就实现了父子进程间通信;

<font color = green>父子间进程通信代码实例：</font>

```c
#include <stdio.h>
#include <stdlib.h>
#include <string.h>
#include <sys/types.h>
#include <sys/wait.h>
#include <unistd.h>
int main()
{
	// 创建管道
	int fd[2];
	int ret = pipe(fd);
	if(ret < 0)
	{
		perror("pipe error");
		return -1;
	}
	
	// 创建子进程
	pid_t pid = fork();
	if(pid < 0)
	{
		printf("fork error");
		return -1;
	}
	else if(pid > 0) // 父进程
	{
		// 关闭读端
		close(fd[0]);
		write(fd[1], "Hello World!", strlen("Hello World!"));
		// 等子进程运行完 回收子进程
		wait(NULL);
	}
	else // 子进程
	{
		// 关闭写端
		close(fd[1]);
		char buf[64];
		memset(buf, 0x00, sizeof(buf));
		int n = read(fd[0], buf, sizeof(buf));
		printf("读出来的数据是：【%s】\n读出来的数据量是：【%d】\n", buf, n);
	}
}
```

<font color = green>代码运行结果如下：</font>

![image-20221107140349778](Linux学习.assets/image-20221107140349778.png)



<font color = green>父子间管道通信高级代码演示：</font>

```c
// 在父子进程间实现 ps -aux | grep bash
#include <stdio.h>
#include <stdlib.h>
#include <string.h>
#include <sys/types.h>
#include <sys/wait.h>
#include <unistd.h>
int main()
{
	// 创建管道
	int fd[2];
	int ret = pipe(fd);
	if(ret < 0)
	{
		perror("pipe error");
		return -1;
	}
	// 创建子进程
	pid_t pid = fork();
	if(pid < 0)
	{
		printf("fork error");
		return -1;
	}
	else if(pid > 0) // 父进程
	{
		// 关闭读端
		close(fd[0]);
		// 在父进程中将标准输出重定向到管道写端
		dup2(fd[1], STDOUT_FILENO);
		// 在父进程中通过execl调用ps -aux;
		execl("/usr/bin/ps", "ps", "aux", NULL);
		wait(NULL);
	}
	else // 子进程
	{
		// 关闭写端
		close(fd[1]);
		// 在父进程中将标准输入重定向到管道读端
		dup2(fd[0], STDIN_FILENO);
		// 在子进程中通过execl调用grep bash
		execl("/usr/bin/grep", "grep", "--color=auto", "bash", NULL);
	}
	return 0;
}
```

<font color = green>代码运行结果如下：</font>

![image-20221107141021689](Linux学习.assets/image-20221107141021689.png)



<font color = pink>管道的读写行为</font>

**读操作**

- 有数据

  read正常读，返回读出的字节数；

- 无数据

  - 写端全部关闭

    read解除阻塞，返回0，相当于读文件读到了尾部；

  - 没有全部关闭

    read阻塞

**写操作**

- 读端全部关闭

  管道破裂，进程终止，内核给当前进程发SIGPIPE信号；

- 读端没有全部关闭

  - 缓冲区写满了

    write阻塞

  - 缓冲区没有满

    继续write



<font color = pink>如何设置管道为非阻塞</font>

默认情况下，管道的读写两端都是阻塞的，若要设置读或者写端为非阻塞，则可参考下列三个步骤进行：

- 第1步： `int flags = fcntl(fd[0], F_GETFL, 0)`

- 第2步： `flag |= O_NONBLOCK`

- 第3步： `fcntl(fd[0], F_SETFL, flags)`

若是读端设置为非阻塞：

  - 写端没有关闭，管道中没有数据可读，则read返回-1；

  - 写端没有关闭，管道中有数据可读，则read返回实际读到的字节数;

  - 写端已经关闭，管道中有数据可读，则read返回实际读到的字节数;

  - 写端已经关闭，管道中没有数据可读，则read返回0;



<font color = pink>如何查看管道缓冲区大小</font>

```c
命令：ulimit -a
函数：
	long fpathconf(int fd, int name);
	printf("pipe size==[%ld]\n", fpathconf(fd[0], _PC_PIPE_BUF));
	printf("pipe size==[%ld]\n", fpathconf(fd[1], _PC_PIPE_BUF));
```







## FIFO

### FIFO介绍

<font color = orange>FIFO常被称为命名管道</font>，以区分管道(pipe)。管道(pipe)只能用于“有血缘关系”的进程间通信。但通过FIFO，不相关的进程也能交换数据。

FIFO是Linux<font color = red>基础文件</font>类型中的一种（**文件类型为p**，可通过ls -l查看文件类型）。但FIFO文件在磁盘上没有数据块，文件大小为0，仅仅用来标识内核中一条通道。进程可以打开这个文件进行read/write，实际上是在读写内核缓冲区，这样就实现了进程间通信。



### 创建管道

- 方式1 使用命令 `mkfifo`

  命令格式：`mkfifo` 管道名

- 方式2 使用函数

  `int mkfifo(const char *pathname, mode_t mode)`

当创建了一个FIFO，就可以使用open函数打开它，常见的文件I/O函数都可用于FIFO。如：close、read、write、unlink等。

**FIFO严格遵循先进先出（first in first out），对FIFO的读总是从开始处返回数据，对它们的写则把数据添加到末尾。它们不支持诸如lseek()等文件定位操作。**

![image-20230403113523579](F:\Documents\Typora_file\Linux学习.assets\image-20230403113523579.png)



### FIFO打开规则

- 如果当前打开操作是为读而打开FIFO时，若已经有相应进程为写而打开该FIFO，则当前打开操作将成功返回；否则，可能阻塞直到有相应进程为写而打开该FIFO（当前打开操作设置了阻塞标志）；或者，成功返回（当前打开操作没有设置阻塞标志）。

- 如果当前打开操作是为写而打开FIFO时，如果已经有相应进程为读而打开该FIFO，则当前打开操作将成功返回；否则，可能阻塞直到有相应进程为读而打开该FIFO（当前打开操作设置了阻塞标志）；或者，返回ENXIO错误（当前打开操作没有设置阻塞标志）。

总之，一旦设置了阻塞标志，调用mkfifo建立好之后，那么管道的两端读写必须分别打开，有任何一方未打开，则在调用open的时候就阻塞。对管道或者FIFO调用lseek，返回ESPIPE错误。




### 使用FIFO完成两个进程通信

<font color = pink>使用FIFO完成两个进程通信的示意图</font>

![image-20221117111733523](Linux学习.assets/image-20221117111733523.png)

**思路**

- 进程A：

  ==> 创建一个fifo文件：myfifo

  ==> 调用open函数打开myfifo文件

  ==> 调用write函数写入一个字符串，如:"hello world"(其实是将数据写入到了内核缓冲区)

  ==> 调用close函数关闭myfifo文件

- 进程B：

  ==> 调用open函数打开myfifo文件

  ==> 调用read函数读取文件内容（其实就是从内核中读取数据）

  ==> 打印显示读取的内容

  ==> 调用close函数关闭myfifo文件

  

<font color = red>注意：不要vim进myfifo文件，不然就会一直阻塞，动不了，可用杀死进程方式退出！杀死进程后还出现了bug！</font>

<font color = pink>FIFO代码实例</font>

```c
// 写
#include <stdio.h>
#include <stdlib.h>
#include <string.h>
#include <sys/types.h>
#include <sys/stat.h>
#include <fcntl.h>
#include <unistd.h>
int main()
{
	// 判断文件是否存在
    // int access(const char *pathname, int mode);
	int ret = access("./myfifo", F_OK);
	if(ret != 0)
	{
        // 不存在就自己创建一个myfifo文件
		ret = mkfifo("./myfifo", 0777);
		if(ret < 0)
		{
			printf("mkfifo error");
			return -1;
		}
	}

	// 打开fifo文件
	int fd = open("./myfifo", O_RDWR, 0777);
	if(fd < 0)
	{
		printf("open error");
		return -1;
	}
	while(1)
	{
		// 写fifo文件
		write(fd, "hello world", strlen("hello world"));
		sleep(1);
	}
	// 延迟20s，让读文件时候fifo文件处于打开状态
	sleep(20);
	close(fd);
	return 0;
}

```

```c
// 读
#include <stdio.h>
#include <stdlib.h>
#include <string.h>
#include <sys/types.h>
#include <sys/stat.h>
#include <fcntl.h>
#include <unistd.h>
int main()
{
	// 判断文件是否存在
    // int access(const char *pathname, int mode);
	int ret = access("./myfifo", F_OK);
	if(ret != 0)
	{
        // 不存在就自己创建一个myfifo文件
		ret = mkfifo("./myfifo", 0777);
		if(ret < 0)
		{
			printf("mkfifo error");
			return -1;
		}
	}
	// 打开fifo文件
	int fd = open("./myfifo", O_RDWR, 0777);
	if(fd < 0)
	{
		printf("open error");
		return -1;
	}

	// 读取fifo文件内容
	char buf[64];
	int i = 1;
	while(1)
	{
		memset(buf, 0x00, sizeof(buf));
		int n = read(fd, buf, sizeof(buf));
		printf("读的第%d条信息为：%s\n信息长度为：%d\n",i, buf, n);
		++i;
	}
	close(fd);
	return 0;
}

```

<font color = pink>代码执行结果如下：</font>

![image-20221128194614869](Linux学习.assets/image-20221128194614869.png)

![image-20221128194658711](Linux学习.assets/image-20221128194658711.png)

写操作一直在阻塞。



## 内存映射区

### 存储映射区介绍

存储映射I/O (Memory-mapped I/O) 使一个磁盘文件与存储空间中的一个缓冲区相映射。从缓冲区中取数据，就相当于读文件中的相应字节；将数据写入缓冲区，则会将数据写入文件。这样，就可在不使用read和write函数的情况下，使用地址（指针）完成I/O操作。

使用存储映射这种方法，首先应通知内核，将一个指定文件映射到存储区域中。这个映射工作可以通过mmap函数来实现。

![image-20221128204124234](Linux学习.assets/image-20221128204124234.png)

### mmap函数

```
函数作用：
	建立存储映射区
函数原型：
	void *mmap(void *addr, size_t length, int prot, int flags, int fd, off_t offset);
函数返回值：
	==>成功：返回创建的映射区首地址；
	==>失败：MAP_FAILED宏
参数：
	==>addr: 指定映射的起始地址, 通常设为NULL, 由系统指定
	==>length: 映射到内存的文件长度
	==>prot: 映射区的保护方式, 最常用的:
		读：PROT_READ
		写：PROT_WRITE
		读写：PROT_READ | PROT_WRITE
	==>flags: 映射区的特性, 可以为下面两个：
		MAP_SHARED: 写入映射区的数据会写回文件, 且允许其他映射该文件的进程共享。
		MAP_PRIVATE: 对映射区的写入操作会产生一个映射区的复制(copy-on-write), 对此区域所做的修改不会写回原文件。
	==>fd: 由open返回的文件描述符，代表要映射的文件。
	==>offest: 以文件开始处的偏移量, 必须是4k的整数倍, 通常为0, 表示从文件头开始映射。
```

<font color = pink>注意事项：</font>

- 创建映射区的过程中，隐含着一次对映射文件的读操作，将文件内容读取到映射区；
- 当MAP_SHARED时，要求：映射区的权限应 <= 文件打开的权限(出于对映射区的保护)。而MAP_PRIVATE则无所谓，因为mmap中的权限是对内存的限制；
- 映射区的释放与文件关闭无关，只要映射建立成功，文件可以立即关闭；
- **特别注意**，当映射文件大小为0时，不能创建映射区。所以，用于映射的文件必须要有实际大小；mmap使用时常常会出现总线错误，通常是由于共享文件存储空间大小引起的。
- 文件偏移量必须为0或者4K的整数倍
- mmap创建映射区出错概率非常高，一定要检查返回值，确保映射区建立成功再进行后续操作。

<font color = pink>mmap函数使用总结：</font>

- 第一个参数写成NULL

- 第二个参数要映射的文件大小 > 0

- 第三个参数：PROT_READ 、PROT_WRITE

- 第四个参数：MAP_SHARED 或者 MAP_PRIVATE

- 第五个参数：打开的文件对应的文件描述符

- 第六个参数：4k的整数倍

  

### munmap函数

```
函数作用：
	释放由mmp函数建立的存储映射区；
函数原型：
	int munmap(void *addr, size_t length);
返回值：
	==>成功：返回0；
	==>失败：返回-1，设置errno值
函数参数：
	==>addr：调用mmap函数成功返回的映射区首地址；
	==>length：映射区大小（mmap函数的第二个参数）。
```

<font color = pink>注意事项：</font>

​	munmap传入的地址一定是mmap的返回地址。坚决杜绝指针++操作。

<font color = pink>代码实例：</font>

```c
// 使用mmap把文件映射到内存缓冲区
#include <stdio.h>
#include <stdlib.h>
#include <string.h>
#include <sys/types.h>
#include <sys/wait.h>
#include <unistd.h>
#include <sys/mman.h>
#include <sys/stat.h>
#include <fcntl.h>
int main()
{
	//打开文件
	int fd = open("./test.log", O_RDWR, 0777);
	if(fd < 0)
	{
		printf("open error");
		return -1;
	}

	// 使用lseek读取文件长度
	int len = lseek(fd, 0, SEEK_END);

	// 使用mmap
	// void *mmap(void *addr, size_t length, int prot, int flags,
    //              int fd, off_t offset);
	void *addr = NULL;
	addr = mmap(NULL, len, PROT_READ | PROT_WRITE, MAP_SHARED, fd, 0);
	if(addr == MAP_FAILED)
	{
		printf("mmap error");
		return -1;
	}
	
	// 创建子进程
	pid_t pid = fork();
	if(pid < 0)
	{
		printf("fork error");
		return -1;
	}
	else if(pid > 0) // 父进程
	{
		// 向内存缓冲区里面写东西
		memcpy(addr, "hello world", strlen("hello world"));
		
		wait(NULL);
	}
	else // 子进程
	{
		// 读内存
		sleep(1);
		char *p = (char*)addr;
		printf("[%s]\n", p);
		
	}
	return 0;
}
```

<font color = pink>代码执行结果：</font>

![image-20221128211406016](Linux学习.assets/image-20221128211406016.png)







---

# 信号



## 信号介绍

**信号概念**

信号是信息的载体，Linux/UNIX 环境下，古老、经典的通信方式， 现下依然是主要的通信手段。

信号在我们的生活中随处可见，例如：

- 古代战争中摔杯为号 

- 现代战争中的信号弹

- 体育比赛中使用的信号枪等等

信号的特点

- 简单

- 不能携带大量信息 

- 满足某个特点条件才会产生 



## 信号的机制

进程A给进程B发送信号，进程B收到信号之前执行自己的代码，收到信号后，不管执行到程序的什么位置，都要暂停运行，去处理信号，处理完毕后再继续执行。与硬件中断类似——异步模式。但信号是软件层面上实现的中断，早期常被称为“软中断”。

**每个进程收到的所有信号，都是由内核负责发送的。**

进程A给进程B发送信号示意图：

![image-20230403115027056](F:\Documents\Typora_file\Linux学习.assets\image-20230403115027056.png)

**信号的状态**

信号有三种状态：产生、未决和递达。

- 信号的产生

	- 按键产生，如：Ctrl+c、Ctrl+z、Ctrl+\

	- 系统调用产生，如：kill、raise、abort

	- 软件条件产生，如：定时器alarm

	- 硬件异常产生，如：非法访问内存(段错误)、除0(浮点数例外)、内存对齐出错(总线错误)

	- 命令产生，如：kill命令

- 未决：产生和递达之间的状态。主要由于阻塞(屏蔽)导致该状态。 

- 递达：递送并且到达进程。



**信号的处理方式**

- 执行默认动作 

- 忽略信号(丢弃不处理)

- 捕捉信号(调用用户的自定义的处理函数)



**信号的特质**

信号的实现手段导致信号有很强的延时性，但对于用户来说，时间非常短，不易察觉。

Linux内核的进程控制块PCB是一个结构体，`task_struct`, 除了包含进程id，状态，工作目录，用户id，组id，文件描述符表，还包含了信号相关的信息，主要指**阻塞信号集和未决信号集**。

注:表示PCB的task_struct结构体定义在：

`/usr/src/linux-headers-4.4.0-97/include/linux/sched.h:1390`



**阻塞信号集和未决信号集**

 Linux内核的进程控制块PCB是一个结构体，这个结构体里面包含了信号相关的信息，主要有阻塞信号集和未决信号集。

阻塞信号集中保存的都是被当前进程阻塞的信号。若当前进程收到的是阻塞信号集中的某些信号，这些信号需要暂时被阻塞，不予处理。

信号产生后由于某些原因(主要是阻塞)不能抵达，这类信号的集合称之为未决信号集。在屏蔽解除前，信号一直处于未决状态；若是信号从阻塞信号集中解除阻塞，则该信号会被处理，并从未决信号集中去除。



**信号的四要素**

通过`man 7 signal`可以查看信号相关信息

*1 信号的编号*

使用`kill -l`命令可以查看当前系统有哪些信号，不存在编号为0的信号。其中1-31号信号称之为常规信号（也叫普通信号或标准信号），34-64称之为实时信号，驱动编程与硬件相关。

*2 信号的名称*

*3 产生信号的事件*

*4信号的默认处理动作*

**Term**：终止进程

**Ign**：忽略信号 (默认即时对该种信号忽略操作)

**Core**：终止进程，生成Core文件。(查验死亡原因，用于gdb调试)

**Stop**：停止（暂停）进程

**Cont**：继续运行进程

特别需要注意的是：The signals SIGKILL and SIGSTOP cannot be caught, blocked, or ignored.

几个常用到的信号

`SIGINT、SIGQUIT、SIGKILL、SIGSEGV、SIGUSR1、SIGUSR2、SIGPIPE、SIGALRM、SIGTERM、SIGCHLD、SIGSTOP、SIGCONT`





## signal函数

函数作用：注册信号捕捉函数

头文件：`#include <signal.h>`

函数原型

​     `typedef void (*sighandler_t)(int)`;

​     `sighandler_t signal(int signum, sighandler_t handler)`;

函数参数

- `signum`：信号编号

- `handler`：信号处理函数



## kill函数

描述：给指定进程发送指定信号

头文件：`#include <sys/types.h>`
              `#include <signal.h>`

kill命令：`kill -SIGKILL 进程PID`

kill函数原型：`int kill(pid_t pid, int sig)`;   

函数返回值：

- 成功：0；

- 失败：-1，设置errno

函数参数：

- sig信号参数：不推荐直接使用数字，应使用宏名，因为不同操作系统信号编号可能不同，但名称一致。

- pid参数：

    - pid > 0: 发送信号给指定的进程。

    - pid = 0: 发送信号给与调用kill函数进程属于同一进程组的所有进程。

    - pid < -1: 取|pid|发给对应进程组。

    - pid = -1: 发送给进程有权限发送的系统中所有进程。

进程组：每个进程都属于一个进程组，进程组是一个或多个进程集合，他们相互关联，共同完成一个实体任务，每个进程组都有一个进程组长，默认进程组ID与进程组长ID相同。

相关测试代码如下：

```c
// 调用kill函数杀死子进程
#include <stdio.h>
#include <stdlib.h>
#include <string.h>
#include <sys/types.h>
#include <unistd.h>
#include <signal.h>
#include <errno.h>
int main()
{
	int i;
	for(i = 0; i < 3; ++i)
	{
		pid_t pid = fork();
		if(pid < 0)
		{
			perror("fork error");
			return -1;
		}
		else if(pid == 0) // 子进程
		{
			printf("child: pid = %d, ppid = %d\n", getpid(), getppid());
			break;
		}
		else   // 父进程
		{
			printf("farther: pid = %d, ppid = %d\n", getpid(), getppid());
			sleep(3);
			if(i < 3)
			{
				int ret = kill(pid, SIGKILL);
				if(ret != 0)
				{
					printf("kill error");
					return -1;
				}
				printf("杀死第%d个进程\n", i+1);
			}

		}
	}
	if(i == 0)
	{
		printf("第一个child: [%d]==>[%d]\n", i, getpid());
		sleep(1);
	}
	if(i == 1)
	{
		printf("第二个child: [%d]==>[%d]\n", i, getpid());
		sleep(1);
	}
	if(i == 2)
	{
		printf("第三个child: [%d]==>[%d]\n", i, getpid());
		sleep(1);
	}
	if(i == 3)
	{
		printf("farther: [%d]==>[%d]\n", i, getpid());
		sleep(1);
	}
	return 0;
}

```

执行结果如下：

![image-20230404151633808](F:\Documents\Typora_file\Linux学习.assets\image-20230404151633808.png)







## raise函数

函说描述：给当前进程发送指定信号(自己给自己发) 

头文件：`#include <signal.h>`

函数原型：`int raise(int sig)`;

函数返回值：成功: 0，失败非0值

函数拓展：`raise(signo) == kill(getpid(), signo)`;



## abort函数

函数描述：给自己发送异常终止信号 `6) SIGABRT`，并产生core文件

头文件：`#include <stdlib.h>`

函数原型：`void abort(void)`; 

函数拓展：`abort() == kill(getpid(), SIGABRT)`;



## alarm函数

头文件：`#include <unistd.h>`

函数原型：`unsigned int alarm(unsigned int seconds)`; 

函数描述：设置定时器(闹钟)。在指定seconds后，内核会给当前进程发送`14）SIGALRM`信号。进程收到该信号，默认动作终止。每个进程都有且只有唯一的一个定时器。

函数返回值：返回0或剩余的秒数，无失败。例如：

![image-20230403162234769](F:\Documents\Typora_file\Linux学习.assets\image-20230403162234769.png)

常用操作：取消定时器alarm(0)，返回旧闹钟余下秒数。

alarm使用的是自然定时法，与进程状态无关，就绪、运行、挂起(阻塞、暂停)、终止、僵尸...无论进程处于何种状态，alarm都计时。



相关代码如下：

```c
// 测试定时器的返回值和信号注册函数
#include<stdio.h>
#include<stdlib.h>
#include<string.h>
#include<unistd.h>
#include<signal.h>

void sighandler(int sig)
{
	printf("signal num = %d\n", sig);
}
int main()
{
	signal(SIGALRM, sighandler);
	
	int n;

	// 设置闹钟
	n = alarm(5);   // 此时返回值为0代表开启定时器成功
	printf("第一个闹钟返回值为：%d\n", n);

	sleep(2);
	n = alarm(5);   // 此时返回3代表旧闹钟剩余时间为3
	printf("闹钟的返回值为：%d\n", n);

	n = alarm(1);   // 此时返回5代表就闹钟剩余时间为5
	printf("闹钟的返回值为：%d\n", n);
	sleep(2); // 在这期间，内核给进程发了14号信号
	return 0;	
}
```

执行结果如下：

![image-20230404144218361](F:\Documents\Typora_file\Linux学习.assets\image-20230404144218361.png)





## setitimer函数

函数原型    
`int setitimer(int which, const struct itimerval *new_value, struct itimerval *old_value)`;

函数描述：设置定时器(闹钟)，可代替alarm函数，精度微秒us，可以实现周期定时。

函数返回值：
- 成功：0；
- 失败：-1，设置errno值

函数参数： 
- which：指定定时方式
	- 自然定时：ITIMER_REAL → `14 ）SIGALRM`计算自然时间
	- 虚拟空间计时(用户空间)：ITIMER_VIRTUAL → `26）SIGVTALRM` 只计算进程占用cpu的时间
	- 运行时计时(用户+内核)：ITIMER_PROF →`27）SIGPROF`计算占用cpu及执行系统调用的时间
- new_value：struct itimerval, 负责设定timeout时间。

`itimerval.it_value`: 设定第一次执行function所延迟的秒数 
`itimerval.it_interval`: 设定以后每几秒执行function

```c
struct itimerval{ 
	struct timerval it_interval; // 闹钟触发周期
	struct timerval it_value; // 闹钟触发时间
}; 
struct timeval{ 
	long tv_sec;             // 秒
	long tv_usec;            // 微秒
}    
```

   

- old_value：存放旧的timeout值，一般指定为NULL



代码测试如下：

```c
// 用setitimer来设置定时器
#include<stdio.h>
#include<stdlib.h>
#include<string.h>
#include<unistd.h>
#include<signal.h>
#include <sys/time.h>

void sighandler(int sig)
{
	printf("signal num = %d\n", sig);
}

int main()
{
	// 注册信号SIGALRM来处理信号
	signal(SIGALRM, sighandler);

	// int setitimer(int which, const struct itimerval *new_value,struct itimerval *old_value);
	struct itimerval tm;
	// 设置周期，每一秒触发一次
	tm.it_interval.tv_sec = 1;
	tm.it_interval.tv_usec = 0;
	
	// 设置触发时间 3s后触发
	tm.it_value.tv_sec = 3;
	tm.it_value.tv_usec = 0;

	setitimer(ITIMER_REAL, &tm, NULL);

	while(1)
	{
		sleep(1);
	}
	
	return 0;	
}
```

执行结果如下：

![image-20230404153731637](F:\Documents\Typora_file\Linux学习.assets\image-20230404153731637.png)





## 未决信号集和阻塞信号集的关系

阻塞信号集是当前进程要阻塞的信号的集合，未决信号集是当前进程中还处于未决状态的信号的集合，这两个集合存储在内核的PCB中。

下面以SIGINT为例说明信号未决信号集和阻塞信号集的关系：

当进程收到一个SIGINT信号（信号编号为2），首先这个信号会保存在未决信号集合中，此时对应的2号编号的这个位置上置为1，表示处于未决状态；在这个信号需要被处理之前首先要在阻塞信号集中的编号为2的位置上去检查该值是否为1：

- 如果为1，表示SIGNIT信号被当前进程阻塞了，这个信号暂时不被处理，所以未决信号集上该位置上的值保持为1，表示该信号处于未决状态； 

- 如果为0，表示SIGINT信号没有被当前进程阻塞，这个信号需要被处理，内核会对SIGINT信号进行处理（执行默认动作，忽略或者执行用户自定义的信号处理函数），并将未决信号集中编号为2的位置上将1变为0，表示该信号已经处理了，这个时间非常短暂，用户感知不到。

当SIGINT信号从阻塞信号集中解除阻塞之后，该信号就会被处理。

![image-20230403164700605](F:\Documents\Typora_file\Linux学习.assets\image-20230403164700605.png)





## 信号集相关函数

由于信号集属于内核的一块区域，用户不能直接操作内核空间，为此，内核提供了一些信号集相关的接口函数，使用这些函数用户就可以完成对信号集的相关操作。

信号集是一个能表示多个信号的数据类型，sigset_t set，set即一个信号集。既然是一个集合，就需要对集进行添加、删除等操作。

`sigset_t`类型的定义在`signal.h`文件中的第49行处:

`typedef __sigset_t sigset_t`;

`__sigset_t`的定义在`sigset.h`文件中的26，27行处: 



```c
# define  _SIGSET_NWORDS  (1024 / (8 * sizeof (unsigned long int)))

typedef struct
{
	unsigned long int __val[_SIGSET_NWORDS];
} __sigset_t;
```



上述变量类型的定义的查找有个小窍门： 可以执行gcc的预处理命令：

`gcc -E test.c -o test.i` 这样头文件就会展开，可以直接到test.i文件中看到相关变量类型的定义。



**信号集相关函数**

`int sigemptyset(sigset_t *set)`;

函数说明：将某个信号集清0            

函数返回值：成功：0；失败：-1，设置errno



`int sigfillset(sigset_t *set)`;

函数说明：将某个信号集置1                

函数返回值：成功：0；失败：-1，设置errno



`int sigaddset(sigset_t *set, int signum)`; 

函数说明：将某个信号加入信号集合中

函数返回值：成功：0；失败：-1，设置errno



`int sigdelset(sigset_t *set, int signum)`;      

函数说明：将某信号从信号清出信号集      

函数返回值：成功：0；失败：-1，设置errno



`int sigismember(const sigset_t *set, int signum)`;

函数说明：判断某个信号是否在信号集中

函数返回值：在：1；不在：0；出错：-1，设置errno



**sigprocmask函数**

函数说明：用来屏蔽信号、解除屏蔽也使用该函数。其本质，读取或修改进程控制块中的信号屏蔽字（阻塞信号集）。**特别注意，屏蔽信号只是将信号处理延后执行(延至解除屏蔽)；而忽略表示将信号丢弃处理**。

函数原型：`int sigprocmask(int how, const sigset_t *set, sigset_t *oldset)`;

函数返回值：成功：0；失败：-1，设置errno

函数参数：

- how参数取值：假设当前的信号屏蔽字为mask
	- SIG_BLOCK: 当how设置为此值，set表示需要屏蔽的信号。相当于 mask = mask | set
	- SIG_UNBLOCK: 当how设置为此，set表示需要解除屏蔽的信号。相当于 mask = mask & ~set
	- SIG_SETMASK: 当how设置为此，set表示用于替代原始屏蔽及的新屏蔽集。相当于mask = set，若调用sigprocmask解除了对当前若干个信号的阻塞，则在sigprocmask返回前，至少将其中一个信号递达。
- set：传入参数，是一个自定义信号集合。由参数how来指示如何修改当前信号屏蔽字。
- oldset：传出参数，保存旧的信号屏蔽字。



**sigpending函数**

函数原型：`int sigpending(sigset_t *set)`;      

函数说明：读取当前进程的未决信号集

函数参数：set传出参数

函数返回值：成功：0；失败：-1，设置errno



**信号集相关函数测试：**

```c
// 信号集相关函数测试
#include<stdio.h>
#include<stdlib.h>
#include<string.h>
#include<unistd.h>
#include<signal.h>

void sighandler(int sig)
{
	printf("signal num = %d\n", sig);
}

int main()
{
	// 注册信号
	signal(SIGINT, sighandler);
	signal(SIGQUIT, sighandler);
	
	// 定义信号集变量
	sigset_t myset;
	// 初始化信号集
	sigemptyset(&myset);
	// 向信号集中添加SIGINT, SIGQUIT
	sigaddset(&myset, SIGINT);
	sigaddset(&myset, SIGQUIT);

	// 将myset信号集中的信号添加到阻塞信号集中
	// int sigprocmask(int how, const sigset_t *set, sigset_t *oldset);
	sigprocmask(SIG_BLOCK, &myset, NULL);

	int i = 0;
	int j = 1;
	sigset_t pend;

	while(1)
	{
		// 读取当前未决信号集
		sigemptyset(&pend);
		sigpending(&pend);

		for(i = 1; i <= 32; ++i)
		{
			if(sigismember(&pend, i) == 1)
			{
				printf("1");
			}
			else
			{
				printf("0");
			}
		}
		printf("\n");
		if(j++ % 10 == 0)
		{
			sigprocmask(SIG_UNBLOCK, &myset, NULL);
		}
		else
		{
			sigprocmask(SIG_BLOCK, &myset, NULL);
		}
		sleep(1);
	}

	return 0;	
}
```

执行结果如下：

![image-20230406103128423](F:\Documents\Typora_file\Linux学习.assets\image-20230406103128423.png)







## 信号捕捉函数

signal函数

sigaction函数

函数说明：注册一个信号处理函数

函数原型：

`int sigaction(int signum, const struct sigaction *act, struct sigaction *oldact)`;

函数参数：

- signum：捕捉的信号

- act：  传入参数，新的处理方式。

- oldact： 传出参数，旧的处理方式

 

```c
struct sigaction {
	void (*sa_handler)(int);    // 信号处理函数
	void (*sa_sigaction)(int, siginfo_t *, void *); //信号处理函数
	sigset_t sa_mask; //信号处理函数执行期间需要阻塞的信号
	int   sa_flags; //通常为0，表示使用默认标识
	void   (*sa_restorer)(void);
};
```



**总结：**

- `sa_handler`：指定信号捕捉后的处理函数名(即注册函数)。也可赋值为`SIG_IGN`表忽略 或 `SIG_DFL`表执行默认动作 
- `sa_mask`: 用来指定在信号处理函数执行期间需要被屏蔽的信号，特别是当某个信号被处理时，它自身会被自动放入进程的信号掩码，因此在信号处理函数执行期间这个信号不会再度发生。注意：仅在处理函数被调用期间屏蔽生效，是临时性设置。
- `sa_flags`：通常设置为0，使用默认属性。
- `sa_restorer`：已不再使用



代码测试如下：

```c
// 用sigaction函数来注册一个信号处理函数
#include<stdio.h>
#include<stdlib.h>
#include<string.h>
#include<unistd.h>
#include<signal.h>

void sighandler(int sig)
{
	printf("signal num = %d\n", sig);
	sleep(3);
}

int main()
{
	// int sigaction(int signum, const struct sigaction *act,
    //                 struct sigaction *oldact);
	// 用sigaction注册SIGINT信号
	struct sigaction act;
	act.sa_handler = sighandler; // 指定信号处理函数
	sigemptyset(&act.sa_mask);   // 信号处理函数执行期间需要阻塞的信号归零
	sigaddset(&act.sa_mask, SIGQUIT);   // 信号处理函数执行期间需要阻塞的信号添加SIGQUIT
	act.sa_flags = 0;
	sigaction(SIGINT, &act, NULL);
	signal(SIGQUIT, sighandler);
	while(1)
	{
		sleep(1);
	}
	return 0;	
}
```

执行结果如下：

![image-20230406103036466](F:\Documents\Typora_file\Linux学习.assets\image-20230406103036466.png)





**注意：信号处理不支持排队**

在XXX信号处理函数执行期间, XXX信号是被阻塞的, 如果该信号产生了多次, 在XXX信号处理函数结束之后, 该XXX信号只被处理一次.

在XXX信号处理函数执行期间,如果阻塞了YYY信号, 若YYY信号产生了多次, 当XXX信号处理函数结束后, YYY信号只会被处理一次.



**内核实现信号捕捉的过程**

如果信号的处理动作是用户自定义函数，在信号递达时就调用这个函数，这称为捕捉信号。由于信号处理函数的代码是在用户空间的，处理过程比较复杂，举例如下：

1. 用户程序注册了SIGQUIT信号的处理函数sighandler。

2. 当前正在执行main函数，这时发生中断或异常切换到内核态。

3. 在中断处理完毕后要返回用户态的main函数之前检查到有信号SIGQUIT递达。

4. 内核决定返回用户态后不是恢复main函数的上下文继续执行，而是执行sighandler函数，sighandler和main函数使用不同的堆栈空间，它们之间不存在调用和被调用的关系，是两个独立的控制流程。

5. sighandler函数返回后自动执行特殊的系统调用sigreturn再次进入内核态。

6. 如果没有新的信号要递达，这次再返回用户态就是恢复main函数的上下文继续执行了。

![image-20230403171315092](F:\Documents\Typora_file\Linux学习.assets\image-20230403171315092.png)





## SIGCHLD信号



**产生SIGCHLD信号的条件**

子进程结束的时候

子进程收到SIGSTOP信号

当子进程停止时，收到SIGCONT信号



**SIGCHLD信号的作用**

子进程退出后，内核会给它的父进程发送SIGCHLD信号，父进程收到这个信号后可以对子进程进行回收。

使用SIGCHLD信号完成对子进程的回收可以避免父进程阻塞等待而不能执行其他操作，只有当父进程收到SIGCHLD信号之后才去调用信号捕捉函数完成对子进程的回收，未收到SIGCHLD信号之前可以处理其他操作。



代码测试如下

```c
//父进程使用SIGCHLD信号完成对子进程的回收
#include <stdio.h>
#include <stdlib.h>
#include <string.h>
#include <sys/types.h>
#include <unistd.h>
#include <signal.h>
#include <sys/wait.h>

void waitchild(int signo)
{
	pid_t wpid;

	//回收子进程
	while(1)
	{
		wpid = waitpid(-1, NULL, WNOHANG);
		if(wpid>0)
		{
			printf("child is quit, wpid==[%d]\n", wpid);
		}
		else if(wpid==0)
		{
			printf("child is living, wpid==[%d]\n", wpid);
			break;
		}
		else if(wpid==-1)
		{
			printf("no child is living, wpid==[%d]\n", wpid);
			break;
		}
	}
}

int main()
{
	int i = 0;
	int n = 3;

	//将SIGCHLD信号阻塞
	sigset_t mask;
	sigemptyset(&mask);
	sigaddset(&mask, SIGCHLD);
	sigprocmask(SIG_BLOCK, &mask, NULL);

	for(i=0; i<n; i++)	
	{
		//fork子进程
		pid_t pid = fork();
		if(pid<0) //fork失败的情况
		{
			perror("fork error");
			return -1;
		}
		else if(pid>0) //父进程
		{
			printf("father: fpid==[%d], cpid==[%d]\n", getpid(), pid);
			sleep(1);
		}
		else if(pid==0) //子进程
		{
			printf("child: fpid==[%d], cpid==[%d]\n", getppid(), getpid());
			break;
		}
	}

	//父进程
	if(i==3)
	{
		printf("[%d]:father: fpid==[%d]\n", i, getpid());
		//signal(SIGCHLD, waitchild);
		//注册信号处理函数
		struct sigaction act;
		act.sa_handler = waitchild;
		sigemptyset(&act.sa_mask);
		act.sa_flags = 0;
		sleep(5);
		sigaction(SIGCHLD, &act, NULL);

		//解除对SIGCHLD信号的阻塞
		sigprocmask(SIG_UNBLOCK, &mask, NULL);

		while(1)
		{
			sleep(1);
		}
	}

	//第1个子进程
	if(i==0)
	{
		printf("[%d]:child: cpid==[%d]\n", i, getpid());
		//sleep(1);
	}

	//第2个子进程
	if(i==1)
	{
		printf("[%d]:child: cpid==[%d]\n", i, getpid());
		sleep(1);
	}

	//第3个子进程
	if(i==2)
	{
		printf("[%d]:child: cpid==[%d]\n", i, getpid());
		sleep(1);
	}

	return 0;
}
```

执行结果如下：

![image-20230406104431397](F:\Documents\Typora_file\Linux学习.assets\image-20230406104431397.png)

**上述代码注意点：**

**问题一：**有可能还未完成信号处理函数的注册三个子进程都退出了。

**解决办法：**可以在fork之前先将SIGCHLD信号阻塞，当完成信号处理函数的注册后在解除阻塞。

**问题二：**当SIGCHLD信号函数处理期间, SIGCHLD信号若再次产生是被阻塞的,而且若产生了多次, 则该信号只会被处理一次, 这样可能会产生僵尸进程。

**解决办法：**可以在信号处理函数里面使用while(1)循环回收, 这样就有可能出现捕获一次SIGCHLD信号但是回收了多个子进程的情况，从而可以避免产生僵尸进程。





---

# 守护进程



**守护进程介绍**

Daemon(精灵)进程，是Linux中的后台服务进程，通常独立于控制终端并且周期性地执行某种任务或等待处理某些发生的事件。一般采用以d结尾的名字，如vsftpd 

Linux后台的一些系统服务进程，没有控制终端，不能直接和用户交互。不受用户登录、注销的影响，一直在运行着，他们都是守护进程。如：预读入缓输出机制的实现；ftp服务器；nfs服务器等。



**总结守护进程的特点：** 
- Linux后台服务进程 
- 独立于控制终端 
- 周期性的执行某种任务 
- 不受用户登陆和注销的影响 
- 一般采用以d结尾的名字



## 进程组和会话

**进程组** 
- 进程组是一个或者多个进程的集合，每个进程都属于一个进程组，引入进程组是为了简化对进程的管理。当父进程创建子进程的时候，默认子进程与父进程属于同一个进程组。 
进程组ID==第一个进程ID（组长进程）。如父进程创建了多个子进程，父进程和多个子进程同属于一个组，而由于父进程是进程组里的第一个进程，所以父进程就是这个组的组长, 组长ID==父进程ID。 
- 可以使用`kill -SIGKILL -进程组ID(负的)`来将整个进程组内的进程全部杀死。 
- 只要进程组中有一个进程存在，进程组就存在，与组长进程是否终止无关。 
- 进程组生存期：从进程组创建到最后一个进程离开 

**会话** 
- 一个会话是一个或多个进程组的集合。 
- **创建会话的进程不能是进程组组长** 
- 创建会话的进程成为一个进程组的组长进程，同时也成为会话的会长。 
- 需要有root权限（ubuntu不需要） 
- 新创建的会话丢弃原有的控制终端 
- 建立新会话时，先调用`fork`, 父进程终止，子进程调用`setsid`函数 

**可以使用`ps ajx`来查看进程组ID和会话ID** 

- 可以fork出几个子进程，然后查看进程组ID和会话ID 

**进程组和会话的关系图** 

![image-20230404172658566](F:\Documents\Typora_file\Linux学习.assets\image-20230404172658566.png)



## 创建守护进程的模型

第1步：fork子进程，父进程退出 

- 子进程继承了父进程的进程组ID, 但具有一个新的进程ID,这样就保证了子进程不是一个进程组的组长ID,这对于下面要做的`setsid`函数的调用是必要的前提条件 

第2步：子进程调用`setsid`函数创建新会话 
     调用这个函数以后 

- 该进程成为新会话的首进程，是会话的会长 
- 成为一个新进程组的组长进程，是进程组组长 
- 不受控制终端的影响 

第3步：改变当前工作目录chdir 

- 如：a.out在U盘上，启动这个程序，这个程序的当前的工作目录就是这个u盘，如果u盘拔掉后进程的当前工作目录将消失，a.out将不能正常工作。 

第4步：重设文件掩码  `mode & ~umask `

- 子进程会继承父进程的掩码 
- 增加子进程程序操作的灵活性 
- `umask(0000)`; 

第5步：关闭文件描述符 

- 守护进程不受控制终端的影响所以可以关闭，以释放资源 
- close(STDIN_FILENO); 

- close(STDOUT_FILENO); 

- close(STDERR_FILENO); 

第6步：执行核心工作 

- 守护进程的核心代码逻辑 



代码示例如下：

```c
// 创建自己的守护进程，实现每隔一秒实时显示当前时间
#include <stdio.h>
#include <stdlib.h>
#include <string.h>
#include <sys/types.h>
#include <sys/stat.h>
#include <fcntl.h>
#include <time.h>
#include <sys/time.h>
#include <unistd.h>
#include <signal.h>

void myfunc()
{
	// 打开文件
	int fd = open("mydaemon.log", O_RDWR | O_CREAT | O_APPEND, 0755);
	if(fd < 0)
	{
		return;
	}

	// 获取当前系统时间
	time_t t;
	time(&t);
	char *p = ctime(&t);

	// 将时间写入文件
	write(fd, p, strlen(p));
	
	close(fd);
	return;
}

int main()
{
	// 父进程fork子进程，然后子进程退出
	pid_t pid = fork();
	if(pid < 0 || pid > 0)
	{
		exit(1);
	}
	
	// 子进程调用setsid函数创建会话
	setsid();

	// 改变当前工作目录
	chdir("/home/xyh/mydaemon/");

	// 改变文件掩码
	umask(0000);

	// 关闭当前标准输入，输出和错误输出的文件描述符
	close(STDIN_FILENO);
	close(STDOUT_FILENO);
	close(STDERR_FILENO);

	// 核心编程
	// 注册信号处理函数
	struct sigaction act;
	act.sa_handler = myfunc;
	act.sa_flags = 0;
	sigemptyset(&act.sa_mask);
	sigaction(SIGALRM, &act, NULL);

	// 设置时钟
	struct itimerval tm;
	tm.it_interval.tv_sec = 1;
	tm.it_interval.tv_usec = 0;
	tm.it_value.tv_sec = 3;
	tm.it_value.tv_usec = 0;
	setitimer(ITIMER_REAL, &tm, NULL);
	
	while(1)
	{
		sleep(1);
	}
}
```

执行结果如下：

![image-20230406111728011](F:\Documents\Typora_file\Linux学习.assets\image-20230406111728011.png)

mydaemon.log文件每隔一秒写入一次当前时间。







---

# 线程

**何为线程？**

- 轻量级的进程（LWP：light weight process），在Linux环境下线程的本质仍是进程。 
- 进程：拥有独立的地址空间，拥有PCB，相当于独居。 

- 线程：有PCB，但没有独立的地址空间，多个线程共享进程空间，相当于合租。 

![image-20230404180225424](F:\Documents\Typora_file\Linux学习.assets\image-20230404180225424.png)



在Linux操作系统下：	 
- 线程：最小的执行单位 
- 进程：最小分配资源单位，可看成是只有一个线程的进程。 

线程的特点 
- 类Unix系统中，早期是没有“线程”概念的，80年代才引入，借助进程机制实现出了线程的概念。因此在这类系统中，进程和线程关系密切。 
- 线程是轻量级进程(light-weight process)，也有PCB，创建线程使用的底层函数和进程一样，都是clone 
- 从内核里看进程和线程是一样的，都有各自不同的PCB. 
- 进程可以蜕变成线程 

- 在linux下，线程最是小的执行单位；进程是最小的分配资源单位 

- 察看指定线程的LWP号：`ps –Lf pid` 

![image-20230404181244284](F:\Documents\Typora_file\Linux学习.assets\image-20230404181244284.png)



实际上，无论是创建进程的fork，还是创建线程的`pthread_create`，底层实现都是调用同一个内核函数 `clone`。 

- 如果复制对方的地址空间，那么就产出一个“进程”； 

- 如果共享对方的地址空间，就产生一个“线程”。 

so：**Linux内核是不区分进程和线程的, 只在用户层面上进行区分**。 

​       **线程操作函数 pthread_* 是库函数，而非系统调用。** 



**线程共享资源**

- 文件描述符表 

- 每种信号的处理方式 
- 当前工作目录 
- 用户ID和组ID 
- 内存地址空间 (.text/.data/.bss/heap/共享库) 

**线程非共享资源**

- 线程id 
- 处理器现场和栈指针(内核栈) 
- 独立的栈空间(用户空间栈) 
- errno变量 
- 信号屏蔽字 

- 调度优先级 

**线程优、缺点** 

- 优点：	 

	- 提高程序并发性	 
	- 开销小	 
	- 数据通信、共享数据方便 

- 缺点：	 

	- 库函数，不稳定	 
	- gdb调试、编写困难	 
	- 对信号支持不好 

优点相对突出，缺点均不是硬伤。Linux下由于实现方法导致进程、线程差别不是很大。 



## pthread_create函数

**函数作用：**创建一个新线程 
**函数原型：**

```c
 int pthread_create(pthread_t *thread, const pthread_attr_t *attr,void *(*start_routine) (void *), void *arg);
```

**返回值** 

- 成功，返回0 
- 失败，返回错误号 

**函数参数：** 

- `pthread_t`：传出参数，保存系统为我们分配好的线程ID 
	- 当前Linux中可理解为：`typedef unsigned long int pthread_t`
- `attr`：通常传NULL，表示使用线程默认属性。若想使用具体属性也可以修改该参数。 
- start_routine：函数指针，指向线程主函数(线程体)，该函数运行结束，则线程结束。 
- arg：线程主函数执行期间所使用的参数。 

**注意点** 

- 由于pthread_create的错误码不保存在errno中，因此不能直接用perror()打印错误信息，可以先用strerror()把错误码转换成错误信息再打印。 
- 如果任意一个线程调用了exit或_exit，则整个进程的所有线程都终止，由于从main函数return也相当于调用exit，为了防止新创建的线程还没有得到执行就终止，我们在main函数return之前延时1秒，这只是一种权宜之计，即使主线程等待1秒，内核也不一定会调度新创建的线程执行，后面会有更好的办法。



代码测试如下：

```c
// 创建线程
#include <stdio.h>
#include <stdlib.h>
#include <string.h>
#include <pthread.h>
#include <unistd.h>
#include <sys/types.h>

void *mythread(int *arg)
{
	printf("传入参数arg = %d\n", *arg);
	printf("son thread pid = [%d], id = [%ld]\n", getpid(), pthread_self()); 
}

int main()
{
	// int pthread_create(pthread_t *thread, const pthread_attr_t *attr,
    //                      void *(*start_routine) (void *), void *arg);
	// 创建子线程
	pthread_t thread;
	int arg = 10;
	int ret = pthread_create(&thread, NULL, mythread, &arg);
	if(ret != 0)
	{
		printf("creat thread error , [%s]\n", strerror(ret));
		return -1;
	}

	printf("main thread pid = [%d], id = [%ld]\n", getpid(), pthread_self()); 

	//目的是为了让子线程能够执行起来
	sleep(1);
	return 0;
}
```

执行结果如下：

![image-20230406144048826](F:\Documents\Typora_file\Linux学习.assets\image-20230406144048826.png)





## pthread_exit函数

在线程中禁止调用`exit`函数，会导致整个进程退出，取而代之的是调用`pthread_exit`函数，这个函数是使一个线程退出，如果主线程调用`pthread_exit`函数也不会使整个进程退出，不影响其他线程的执行。 

**函数描述:** 将单个线程退出 
**函数原型:** `void pthread_exit(void *retval)`;	 
**函数参数:** 传出参数`retval`表示线程退出状态，通常传NULL 

**注意**，pthread_exit或者return返回的指针所指向的内存单元必须是全局的或者是用malloc分配的，不能在线程函数的栈上分配，因为当其它线程得到这个返回指针时线程函数已经退出了，栈空间就会被回收。 



## pthread_join函数

**函数描述：**阻塞等待线程退出，获取线程退出状态。其作用，对应进程中的`waitpid()` 函数。 
**函数原型：**`int pthread_join(pthread_t thread, void **retval)`; 
**函数返回值：** 

- 成功：0; 
- 失败：错误号;

**函数参数：** 

- `thread`：线程ID 
- `retval`：存储线程结束状态，整个指针和`pthread_exit`的参数是同一块内存地址。 



**pthread_exit和pthread_join函数测试代码如下：**

```c
// 实现pthread_exit    pthread_join
#include <stdio.h>
#include <stdlib.h>
#include <string.h>
#include <pthread.h>
#include <unistd.h>
#include <sys/types.h>

typedef struct
{
	char name[64];
	int age;
}__student;

// 全局变量作为退出状态
__student s;

void *mythread(void *arg)
{
	printf("son thread pid = [%d], id = [%ld]\n", getpid(), pthread_self()); 

	// 初始化
	memset(&s, 0x00, sizeof(s));
	s.age = 23;
	strcpy(s.name, "XieYuHang");
	printf("&s = [%p]\n", &s);
	pthread_exit(&s);
}

int main()
{
	// int pthread_create(pthread_t *thread, const pthread_attr_t *attr,
    //                      void *(*start_routine) (void *), void *arg);
	// 创建子线程
	pthread_t thread;
	int ret = pthread_create(&thread, NULL, mythread, NULL);
	if(ret != 0)
	{
		printf("creat thread error , [%s]\n", strerror(ret));
		return -1;
	}

	printf("main thread pid = [%d], id = [%ld]\n", getpid(), pthread_self()); 
	
	// 回收子线程
	void *p = NULL;
	pthread_join(thread, &p);
	__student *stu = (__student *)p;
	printf("child exit status : s.name = [%s], s.age = [%d]\n, &s = [%p]\n", stu->name, stu->age, p);
	
	sleep(1);
	return 0;
}
```



执行结果如下：

![image-20230406153127586](F:\Documents\Typora_file\Linux学习.assets\image-20230406153127586.png)





## pthread_detach函数 

**线程分离状态：**指定该状态，线程主动与主控线程断开关系。线程结束后，其退出状态不由其他线程获取，而直接自己自动释放。网络、多线程服务器常用。 

进程若有该机制，将不会产生僵尸进程。僵尸进程的产生主要由于进程死后，大部分资源被释放，一点残留资源仍存于系统中，导致内核认为该进程仍存在。 也可使用 `pthread_create`函数参2(线程属性)来设置线程分离。`pthread_detach`函数是在创建线程之后调用的。 

**函数描述:**实现线程分离 
**函数原型:** `int pthread_detach(pthread_thread)`;	 
**函数返回值** 

- 成功：0
- 失败：错误号 

一般情况下，线程终止后，其终止状态一直保留到其它线程调用`pthread_join`获取它的状态为止。但是线程也可以被置为detach状态，**这**样的线程一旦终止就立刻回收它占用的所有资源，而不保留终止状态。不能对一个已经处于detach状态的线程调用pthread_join，这样的调用将返回EINVAL错误。也就是说，如果已经对一个线程调用了`pthread_detach`就不能再调用`pthread_join`了。 



代码测试如下：

```c
//设置子线程为分离属性
#include <stdio.h>
#include <stdlib.h>
#include <string.h>
#include <sys/types.h>
#include <unistd.h>
#include <pthread.h>

//线程执行函数
void *mythread(void *arg)
{
	printf("child thread, pid==[%d], id==[%ld]\n", getpid(), pthread_self());
	sleep(10);
}

int main()
{
	//int pthread_create(pthread_t *thread, const pthread_attr_t *attr,
    //                      void *(*start_routine) (void *), void *arg);
	//创建子线程
	pthread_t thread;
	int ret = pthread_create(&thread, NULL, mythread, NULL);
	if(ret!=0)
	{
		printf("pthread_create error, [%s]\n", strerror(ret));
		return -1;
	}
	printf("main thread, pid==[%d], id==[%ld]\n", getpid(), pthread_self());

	//设置线程为分离属性
	pthread_detach(thread);

	//子线程设置分离属性,则pthread_join不再阻塞,立刻返回
	ret = pthread_join(thread, NULL);
	if(ret!=0)
	{
		printf("pthread_join error:[%s]\n", strerror(ret));
	}

	//目的是为了让子线程能够执行起来
	sleep(1);
	return 0;
}
```

执行结果如下：

![image-20230406163737798](F:\Documents\Typora_file\Linux学习.assets\image-20230406163737798.png)







## pthread_cancel函数 

**函数描述** 杀死(取消)线程。其作用，对应进程中 kill() 函数。 
**函数原型**`int pthread_cancel(pthread_t thread)`;	 
**函数返回值:**

- 成功：0； 
- 失败：错误号 

**注意：**线程的取消并不是实时的，而有一定的延时。需要等待线程到达某个取消点(检查点)。类似于玩游戏存档，必须到达指定的场所(存档点，如：客栈、仓库、城里等)才能存储进度。杀死线程也不是立刻就能完成，必须要到达取消点。 

**取消点：**是线程检查是否被取消，并按请求进行动作的一个位置。通常是一些系统调用creat，open，pause，close，read，write..... 执行命令man 7 pthreads可以查看具备这些取消点的系统调用列表。可粗略认为一个系统调用(进入内核)即为一个取消点。还以通过调用`pthread_testcancel`函数设置一个取消点。 该函数原型为`void pthread_testcancel(void)`;

函数测试代码如下：

```c
//创建子线程
#include <stdio.h>
#include <stdlib.h>
#include <string.h>
#include <sys/types.h>
#include <unistd.h>
#include <pthread.h>

//线程执行函数
void *mythread(void *arg)
{
	while(1)
	{
		int a;
		int b;

		//设置取消点
		pthread_testcancel();

		printf("-----\n");
		
	}
}

int main()
{
	//int pthread_create(pthread_t *thread, const pthread_attr_t *attr,
    //                      void *(*start_routine) (void *), void *arg);
	//创建子线程
	pthread_t thread;
	int ret = pthread_create(&thread, NULL, mythread, NULL);
	if(ret!=0)
	{
		printf("pthread_create error, [%s]\n", strerror(ret));
		return -1;
	}
	printf("main thread, pid==[%d], id==[%ld]\n", getpid(), pthread_self());

	//取消子线程
	pthread_cancel(thread);

	pthread_join(thread, NULL);
	return 0;
}
```

若把取消点注释掉：

![image-20230406165043494](F:\Documents\Typora_file\Linux学习.assets\image-20230406165043494.png)

执行结果如下：

![image-20230406165116782](F:\Documents\Typora_file\Linux学习.assets\image-20230406165116782.png)



若不注释取消点：

![image-20230406165150057](F:\Documents\Typora_file\Linux学习.assets\image-20230406165150057.png)

执行结果如下：

![image-20230406165210573](F:\Documents\Typora_file\Linux学习.assets\image-20230406165210573.png)





## pthread_equal函数 

**函数描述：** 比较两个线程ID是否相等。 
**函数原型:** `int pthread_equal(pthread_t t1, pthread_t t2)`; 
**注意：**这个函数是为了以能够扩展使用的， 有可能Linux在未来线程ID pthread_t 类型被修改为结构体实现。



## 进程函数和线程函数比较

|    **进程**       |     **线程**   |
| ---------------- | -------------- |
| **fork**         | pthread_create |
| **exit**         | pthread_exit   |
| **wait/waitpid** | pthread_join   |
| **kill**         | pthread_cancel |
| **getpid**       | pthread_self   |



## 线程属性

linux下线程的属性是可以根据实际项目需要，进行设置，之前讨论的线程都是采用线程的默认属性，默认属性已经可以解决绝大多数开发时遇到的问题，如果对程序的性能提出更高的要求，则需要设置线程属性，本节以设置线程的分离属性为例讲解设置线程属性。 

- 线程的分离状态决定一个线程以什么样的方式来终止自己，有两种状态： 
	- 非分离状态：线程的默认属性是非分离状态，这种情况下，原有的线程等待创建的线程结束。只有当pthread_join()函数返回时，创建的线程才算终止，才能释放自己占用的系统资源。 
	- 分离状态：分离线程没有被其他的线程所等待，自己运行结束了，线程也就终止了，马上释放系统资源。应该根据自己的需要，选择适当的分离状态。 

- 设置线程属性分为以下步骤 

	- **第1步：定义线程属性类型类型的变量** 
      `pthread_attr_t attr`;	 

	- **第2步：对线程属性变量进行初始化** 
      `int pthread_attr_init (pthread_attr_t* attr)`; 

	- **第3步：设置线程为分离属性** 
```c
      int pthread_attr_setdetachstate(pthread_attr_t *attr, int detachstate)
      参数: 
          attr: 线程属性 
          detachstate: 
      		  PTHREAD_CREATE_DETACHED(分离)
              PTHREAD_CREATE_JOINABLE(非分离)
```

==>注意：这一步完成之后调用pthread_create函数创建线程,则创建出来的线程就是分离线程；其实上述三步就是`pthread_create`的第二个参数做准备工作。 

​      **第4步：释放线程属性资源** 
​	  `int pthread_attr_destroy(pthread_attr_t *attr)`; 
​	   参数：线程属性 

测试代码如下：

```c
//在创建子线程的时候设置分离属性
#include <stdio.h>
#include <stdlib.h>
#include <string.h>
#include <sys/types.h>
#include <unistd.h>
#include <pthread.h>

//线程执行函数
void *mythread(void *arg)
{
	printf("child thread, pid==[%d], id==[%ld]\n", getpid(), pthread_self());
	sleep(2);
}

int main()
{
	//定义pthread_attr_t类型的变量
	pthread_attr_t attr;
	
	//初始化attr变量
	pthread_attr_init(&attr);

	//设置attr为分离属性
	pthread_attr_setdetachstate(&attr, PTHREAD_CREATE_DETACHED);

	//创建子线程
	pthread_t thread;
	int ret = pthread_create(&thread, &attr, mythread, NULL);
	if(ret!=0)
	{
		printf("pthread_create error, [%s]\n", strerror(ret));
		return -1;
	}
	printf("main thread, pid==[%d], id==[%ld]\n", getpid(), pthread_self());

	//释放线程属性
	pthread_attr_destroy(&attr);

	//验证子线程是否为分离属性
	ret = pthread_join(thread, NULL);
	if(ret!=0)
	{
		printf("pthread_join error:[%s]\n", strerror(ret));
	}

	return 0;
}
```

执行结果如下：

![image-20230406170423081](F:\Documents\Typora_file\Linux学习.assets\image-20230406170423081.png)





---

# 线程同步



**线程同步的概念**

线程同步，指一个线程发出某一功能调用时，在没有得到结果之前，该调用不返回。同时其它线程为保证数据一致性，不能调用该功能。 



**线程同步的例子**

创建两个线程，让两个线程共享一个全局变量int number， 然后让每个线程数5000次数，看最后打印出这个number值是多少？ 

线程A代码片段：

![image-20230406170944496](F:\Documents\Typora_file\Linux学习.assets\image-20230406170944496.png)

线程B代码片段：

![image-20230406171021536](F:\Documents\Typora_file\Linux学习.assets\image-20230406171021536.png)

代码片段说明 

- 代码中使用调用usleep是为了让两个子线程能够轮流使用CPU，避免一个子线程在一个时间片内完成5000次数数。 
- 对number执行++操作，使用了中间变量cur是为了尽可能的模拟cpu时间片用完而让出cpu的情况。 

测试结果 
- 经过多次测试最后的结果显示，有可能会出现number值少于5000*2=10000的情况。 

分析原因 
- 假如子线程A执行完了cur++操作，还没有将cur的值赋值给number失去了cpu的执行权，子线程B得到了cpu执行权，而子线程B最后执行完了number=cur，而后失去了cpu的执行权；此时子线程A又重新得到cpu的执行权，并执行number=cur操作，这样会把线程B刚刚写回number的值被覆盖了，造成number值不符合预期的值。 

![image-20230406172115149](F:\Documents\Typora_file\Linux学习.assets\image-20230406172115149.png)

数据混乱的原因 
- 资源共享（独享资源则不会）	 
- 调度随机（线程操作共享资源的先后顺序不确定）	 
- 线程间缺乏必要的同步机制。 

以上3点中，前两点不能改变，欲提高效率，传递数据，资源必须共享。只要共享资源，就一定会出现竞争。只要存在竞争关系，数据就很容易出现混乱。所以只能从第三点着手解决。使多个线程在访问共享资源的时候，出现互斥。 

如何解决问题 
- 原子操作的概念 
原子操作指的是该操作要么不做，要么就完成。 

- 使用互斥锁解决同步问题 
使用互斥锁其实是模拟原子操作。



## 互斥锁

Linux中提供一把互斥锁mutex（也称之为互斥量）。每个线程在对资源操作前都尝试先加锁，成功加锁才能操作，操作结束解锁。 

资源还是共享的，线程间也还是竞争的，但通过“锁”就将资源的访问变成互斥操作，而后与时间有关的错误也不会再产生了。 

![image-20230406172544046](F:\Documents\Typora_file\Linux学习.assets\image-20230406172544046.png)

线程1访问共享资源的时候要先判断锁是否锁着，如果锁着就阻塞等待；若锁是解开的就将这把锁加锁，此时可以访问共享资源，访问完成后释放锁，这样其他线程就有机会获得锁。 

**注意：**图中同一时刻，只能有一个线程持有该锁，只要该线程未完成操作就不释放锁。 

使用互斥锁之后，两个线程由并行操作变成了串行操作，效率降低了，但是数据不一致的问题得到解决了。



## 互斥锁相关函数



### pthread_mutex_init函数 

函数描述： 

- 初始化一个互斥锁(互斥量) ---> 初值可看作1 

函数原型： 
- `int pthread_mutex_init(pthread_mutex_t *restrict mutex, const pthread_mutexattr_t *restrict attr)`; 

```c
pthread_mutex_t 类型 
其本质是一个结构体，为简化理解，应用时可忽略其实现细节，简单当成整数看待。 
pthread_mutex_t mutex; 变量mutex只有两种取值1、0。 
```

函数参数 

- `mutex`：传出参数，调用时应传 `&mutex`	 
- `attr`：互斥锁属性。是一个传入参数，通常传`NULL`，选用默认属性(线程间共享)。 

**restrict关键字**：只用于限制指针，告诉编译器，所有修改该指针指向内存中内容的操作，只能通过本指针完成。不能通过除本指针以外的其他变量或指针修改互斥量mutex的两种初始化方式： 

**静态初始化：**如果互斥锁 mutex 是静态分配的（定义在全局，或加了static关键字修饰），可以直接使用宏进行初始化。 

- `pthead_mutex_t muetx = PTHREAD_MUTEX_INITIALIZER`

**动态初始化：**局部变量应采用动态初始化。 

- `pthread_mutex_init(&mutex, NULL) `



### pthread_mutex_destroy函数 

函数描述 

- 销毁一个互斥锁 

函数原型 
- `int pthread_mutex_destroy(pthread_mutex_t *mutex)`; 

函数参数 
- `mutex`—互斥锁变量 



### pthread_mutex_lock函数 

函数描述 
- 对互斥锁加锁，可理解为将mutex-- 

函数原型 
- `int pthread_mutex_lock(pthread_mutex_t *mutex)`; 

函数参数 
- mutex—互斥锁变量 



### pthread_mutex_unlock函数 

函数描述 

- 对互斥所解锁，可理解为将mutex ++ 

函数原型 
- `int pthread_mutex_unlock(pthread_mutex_t *mutex)`; 



### pthread_mutex_trylock函数 

函数描述 

- 尝试加锁 

函数原型 
- `int pthread_mutex_trylock(pthread_mutex_t *mutex)`; 

函数参数 
- `mutex`—互斥锁变量 



**加锁和解锁**

lock尝试加锁，如果加锁不成功，线程阻塞，阻塞到持有该互斥量的其他线程解锁为止。 

unlock主动解锁函数，同时将阻塞在该锁上的所有线程全部唤醒，至于哪个线程先被唤醒，取决于优先级、调度。默认：先阻塞、先唤醒。 

**总结：**使用互斥锁之后，两个线程由并行变为了串行，效率降低了，但是可以使两个线程同步操作共享资源，从而解决了数据不一致的问题。



## 互斥锁代码示例

```c
#include <stdio.h>
#include <stdlib.h>
#include <string.h>
#include <sys/types.h>
#include <unistd.h>
#include <pthread.h>
#include <time.h>

//定义一把锁
pthread_mutex_t mutex;

void mythread1(void *args)
{
	while(1)
	{
		//加锁
		pthread_mutex_lock(&mutex);

		printf("hello ");
		sleep(rand()%3);
		printf("world\n");
	
		//解锁
		pthread_mutex_unlock(&mutex);
		sleep(rand()%3);
	}

	pthread_exit(NULL);
}


void mythread2(void *args)
{
	while(1)
	{
		//加锁
		pthread_mutex_lock(&mutex);

		printf("HELLO ");
		sleep(rand()%3);
		printf("WORLD\n");

		//解锁
		pthread_mutex_unlock(&mutex);
		sleep(rand()%3);
	}

	pthread_exit(NULL);
}

int main()
{
	int ret;
	pthread_t thread1;
	pthread_t thread2;

	//随机数种子
	srand(time(NULL));
	
	//互斥锁初始化
	pthread_mutex_init(&mutex, NULL);

	ret = pthread_create(&thread1, NULL, mythread1, NULL);
	if(ret!=0)
	{
		printf("pthread_create error, [%s]\n", strerror(ret));
		return -1;
	}

	ret = pthread_create(&thread2, NULL, mythread2, NULL);
	if(ret!=0)
	{
		printf("pthread_create error, [%s]\n", strerror(ret));
		return -1;
	}

	//等待线程结束
	pthread_join(thread1, NULL);
	pthread_join(thread2, NULL);

	//释放互斥锁
	pthread_mutex_destroy(&mutex);
	return 0;
}
```

执行结果如下：

![image-20230407145118458](F:\Documents\Typora_file\Linux学习.assets\image-20230407145118458.png)



## 死锁

死锁并不是linux提供给用户的一种使用方法，而是由于用户使用互斥锁不当引起的一种现象。 

常见的死锁有两种： 

- 第一种：自己锁自己，如下图代码片段 

![image-20230407163406097](F:\Documents\Typora_file\Linux学习.assets\image-20230407163406097.png)

- 第二种 线程A拥有A锁，请求获得B锁；线程B拥有B锁，请求获得A锁，这样造成线程A和线程B都不释放自己的锁，而且还想得到对方的锁，从而产生死锁，如下图所示：

![image-20230407163435647](F:\Documents\Typora_file\Linux学习.assets\image-20230407163435647.png)

**如何解决死锁：**

- 让线程按照一定的顺序去访问共享资源 
- 在访问其他锁的时候，需要先将自己的锁解开 
- 调用`pthread_mutex_trylock`，如果加锁不成功会立刻返回 



## 读写锁

**什么是读写锁？** 

- 读写锁也叫共享-独占锁。当读写锁以读模式锁住时，它是以共享模式锁住的；当它以写模式锁住时，它是以独占模式锁住的。**写独占、读共享。** 

**读写锁使用场合** 

- **读写锁非常适合于对数据结构读的次数远大于写的情况。** 

**读写锁特性**	 

- 读写锁是“写模式加锁”时，解锁前，所有对该锁加锁的线程都会被阻塞。 
- 读写锁是“读模式加锁”时，如果线程以读模式对其加锁会成功；如果线程以写模式加锁会阻塞。 
- 读写锁是“读模式加锁”时， 既有试图以写模式加锁的线程，也有试图以读模式加锁的线程。那么读写锁会阻塞随后的读模式锁请求。优先满足写模式锁。读锁、写锁并行阻塞，写锁优先级高 



**读写锁主要操作函数** 

**定义一把读写锁**

`pthread_rwlock_t rwlock`; 



**初始化读写锁** 

  ```c
  int pthread_rwlock_init(pthread_rwlock_t *restrict rwlock, const pthread_rwlockattr_t *restrict attr);
  ```

函数参数 

- `rwlock`-读写锁 

- `attr`-读写锁属性，传NULL为默认属性 



**销毁读写锁** 

```c
int pthread_rwlock_destroy(pthread_rwlock_t *rwlock); 
```

        

**加读锁** 

```c
int pthread_rwlock_rdlock(pthread_rwlock_t *rwlock);    
```

           

**尝试加读锁** 

```c
int pthread_rwlock_tryrdlock(pthread_rwlock_t *rwlock); 
```



**加写锁** 

```c
int pthread_rwlock_wrlock(pthread_rwlock_t *rwlock); 
```



**尝试加写锁** 

```c
int pthread_rwlock_trywrlock(pthread_rwlock_t *rwlock); 
```



**解锁** 

```c
int pthread_rwlock_unlock(&pthread_rwlock_t *rwlock); 
```



测试代码如下：

```c
//读写锁测试程序
#include <stdio.h>
#include <stdlib.h>
#include <string.h>
#include <sys/types.h>
#include <unistd.h>
#include <pthread.h>

int number = 0;

//定义一把读写锁
pthread_rwlock_t rwlock;

//写线程回调函数
void *thread_write(void *arg)
{
	int i = *(int *)arg;

	int cur;

	while(1)
	{
		//加写锁
		pthread_rwlock_wrlock(&rwlock);

		cur = number;
		cur++;
		number = cur;	
		printf("[%d]-W:[%d]\n", i, cur);

		//解锁
		pthread_rwlock_unlock(&rwlock);
		sleep(rand()%3);
	}
}

//读线程回调函数
void *thread_read(void *arg)
{
	int i = *(int *)arg;
	int cur;

	while(1)
	{
		//加读锁
		pthread_rwlock_rdlock(&rwlock);

		cur = number;
		printf("[%d]-R:[%d]\n", i, cur);

		//解锁
		pthread_rwlock_unlock(&rwlock);
		sleep(rand()%3);
	}	
}

int main()
{
	int n = 8;
	int i = 0;
	int arr[8];
	pthread_t thread[8];

	//读写锁初始化
	pthread_rwlock_init(&rwlock, NULL);

	//创建3个写子线程
	for(i=0; i<3; i++)
	{
		arr[i] = i;
		pthread_create(&thread[i], NULL, thread_write, &arr[i]);
	}

	//创建5个读子线程
	for(i=3; i<n; i++)
	{
		arr[i] = i;
		pthread_create(&thread[i], NULL, thread_read, &arr[i]);
	}

	//回收子线程
	int j = 0;
	for(j=0;j<n; j++)
	{
		pthread_join(thread[j], NULL);
	}

	//释放锁
	pthread_rwlock_destroy(&rwlock);

	return 0;
}
```

执行结果如下：

![image-20230407174350083](F:\Documents\Typora_file\Linux学习.assets\image-20230407174350083.png)



## 条件变量

条件本身不是锁！但它也可以造成线程阻塞。通常与互斥锁配合使用。给多线程提供一个会合的场所。 

- 使用互斥量保护共享数据; 
- 使用条件变量可以使线程阻塞, 等待某个条件的发生, 当条件满足的时候解除阻塞. 

条件变量的两个动作: 
- 条件不满足, 阻塞线程 
- 条件满足, 通知阻塞的线程解除阻塞, 开始工作. 



**条件变量相关函数** 

定义一个条件变量 `pthread_cond_t cond`;



**pthread_cond_init函数**

```c
int pthread_cond_init(pthread_cond_t *restrict cond, const pthread_condattr_t *restrict attr); 
```

函数描述:初始化条件变量 

函数参数: 
- `cond`: 条件变量 
- `attr`: 条件变量属性, 通常传NULL 

函数返回值:成功返回0, 失败返回错误号 



**pthread_cond_destroy函数**

```c
int pthread_cond_destroy(pthread_cond_t *cond); 
```

函数描述: 销毁条件变量 
函数参数: 条件变量 
返回值: 成功返回0, 失败返回错误号 



**pthread_cond_wait函数**

```c
int pthread_cond_wait(pthread_cond_t *restrict cond, pthread_mutex_t *restrict mutex); 
```

函数描述: 条件不满足, 引起线程阻塞并解锁; 

条件满足, 解除线程阻塞, 并加锁 

函数参数: 
- `cond`: 条件变量 
- `mutex`: 互斥锁变量 

函数返回值: 成功返回0, 失败返回错误号 



**pthread_cond_signal函数**

```c
int pthread_cond_signal(pthread_cond_t *cond); 
```

函数描述: 唤醒至少一个阻塞在该条件变量上的线程 
函数参数: 条件变量 
函数返回值: 成功返回0, 失败返回错误号 



代码示例如下

```c
//使用条件变量实现生产者和消费者模型
#include <stdio.h>
#include <stdlib.h>
#include <string.h>
#include <sys/types.h>
#include <unistd.h>
#include <pthread.h>
typedef struct node
{
	int data;
	struct node *next;
}NODE;

NODE *head = NULL;

//定义一把锁
pthread_mutex_t mutex;

//定义条件变量
pthread_cond_t cond;

//生产者线程
void *producer(void *arg)
{
	NODE *pNode = NULL;
	while(1)
	{
		//生产一个节点
		pNode = (NODE *)malloc(sizeof(NODE));
		if(pNode==NULL)
		{
			perror("malloc error");
			exit(-1);
		}
		pNode->data = rand()%1000;
		printf("P:[%d]\n", pNode->data);

		//加锁
		pthread_mutex_lock(&mutex);

		pNode->next = head;
		head = pNode;

		//解锁
		pthread_mutex_unlock(&mutex);

		//通知消费者线程解除阻塞
		pthread_cond_signal(&cond);
		
		sleep(rand()%3);
	}
}


//消费者线程
void *consumer(void *arg)
{
	NODE *pNode = NULL;
	while(1)
	{
		//加锁
        pthread_mutex_lock(&mutex);
		
		if(head==NULL)
		{
			//若条件不满足,需要阻塞等待
			//若条件不满足,则阻塞等待并解锁;
			//若条件满足(被生成者线程调用pthread_cond_signal函数通知),解除阻塞并加锁 
			pthread_cond_wait(&cond, &mutex);
		}

		printf("C:[%d]\n", head->data);	
		pNode = head;
		head = head->next;

		//解锁
		pthread_mutex_unlock(&mutex);

		free(pNode);
		pNode = NULL;

		sleep(rand()%3);
	}
}

int main()
{
	int ret;
	pthread_t thread1;
	pthread_t thread2;

	//初始化互斥锁
	pthread_mutex_init(&mutex, NULL);

	//条件变量初始化
	pthread_cond_init(&cond, NULL);

	//创建生产者线程
	ret = pthread_create(&thread1, NULL, producer, NULL);
	if(ret!=0)
	{
		printf("pthread_create error, [%s]\n", strerror(ret));
		return -1;
	}

	//创建消费者线程
	ret = pthread_create(&thread2, NULL, consumer, NULL);
	if(ret!=0)
	{
		printf("pthread_create error, [%s]\n", strerror(ret));
		return -1;
	}

	//等待线程结束
	pthread_join(thread1, NULL);
	pthread_join(thread2, NULL);

	//释放互斥锁
	pthread_mutex_destroy(&mutex);

	//释放条件变量
	pthread_cond_destroy(&cond);

	return 0;
}
```

执行结果如下

![image-20230409153054748](F:\Documents\Typora_file\Linux学习.assets\image-20230409153054748.png)









## 信号量

**信号量介绍** 

信号量相当于多把锁, 可以理解为是加强版的互斥锁 

**相关函数** 

定义信号量 `sem_t sem`; 



**sem_init函数**

```c
int sem_init(sem_t *sem, int pshared, unsigned int value);
```

函数描述: 初始化信号量 
函数参数: 
- `sem`: 信号量变量 
- `pshared`: 0表示线程同步, 1表示进程同步 
- `value`: 最多有几个线程操作共享数据 

函数返回值:成功返回0, 失败返回-1, 并设置errno值 



**sem_wait函数**

```c
int sem_wait(sem_t *sem); 
```

函数描述: 调用该函数一次, 相当于sem--, 当sem为0的时候, 引起阻塞 
函数参数: 信号量变量 
函数返回值: 成功返回0, 失败返回-1, 并设置errno值 



**sem_post函数**

```c
int sem_post(sem_t *sem);
```

函数描述: 调用一次, 相当于sem++ 
函数参数: 信号量变量 
函数返回值: 成功返回0, 失败返回-1, 并设置errno值 



**sem_trywait函数**

```c
int sem_trywait(sem_t *sem);
```

函数描述: 尝试加锁, 若失败直接返回, 不阻塞 
函数参数: 信号量变量 
函数返回值: 成功返回0, 失败返回-1, 并设置errno值 



**sem_destroy函数**

```c
int sem_destroy(sem_t *sem);
```

函数描述: 销毁信号量 
函数参数: 信号量变量 
函数返回值: 成功返回0, 失败返回-1, 并设置errno值 



示例代码如下

```c
//使用信号量实现生产者和消费者模型
#include <stdio.h>
#include <stdlib.h>
#include <string.h>
#include <sys/types.h>
#include <unistd.h>
#include <pthread.h>
#include <semaphore.h>
typedef struct node
{
	int data;
	struct node *next;
}NODE;

NODE *head = NULL;

//定义信号量
sem_t sem_producer;
sem_t sem_consumer;

//生产者线程
void *producer(void *arg)
{
	NODE *pNode = NULL;
	while(1)
	{
		//生产一个节点
		pNode = (NODE *)malloc(sizeof(NODE));
		if(pNode==NULL)
		{
			perror("malloc error");
			exit(-1);
		}
		pNode->data = rand()%1000;
		printf("P:[%d]\n", pNode->data);

		//加锁
		sem_wait(&sem_producer); //--

		pNode->next = head;
		head = pNode;

		//解锁
		sem_post(&sem_consumer);  //相当于++

		sleep(rand()%3);
	}
}


//消费者线程
void *consumer(void *arg)
{
	NODE *pNode = NULL;
	while(1)
	{
		//加锁
		sem_wait(&sem_consumer); //相当于--
		
		printf("C:[%d]\n", head->data);	
		pNode = head;
		head = head->next;

		//解锁
		sem_post(&sem_producer); //相当于++

		free(pNode);
		pNode = NULL;

		sleep(rand()%3);
	}
}

int main()
{
	int ret;
	pthread_t thread1;
	pthread_t thread2;

	//初始化信号量
	sem_init(&sem_producer, 0, 5);
	sem_init(&sem_consumer, 0, 0);

	//创建生产者线程
	ret = pthread_create(&thread1, NULL, producer, NULL);
	if(ret!=0)
	{
		printf("pthread_create error, [%s]\n", strerror(ret));
		return -1;
	}

	//创建消费者线程
	ret = pthread_create(&thread2, NULL, consumer, NULL);
	if(ret!=0)
	{
		printf("pthread_create error, [%s]\n", strerror(ret));
		return -1;
	}

	//等待线程结束
	pthread_join(thread1, NULL);
	pthread_join(thread2, NULL);

	//释放信号量资源
	sem_destroy(&sem_producer);
	sem_destroy(&sem_consumer);

	return 0;
}
```

执行结果如下：

![image-20230409153302968](F:\Documents\Typora_file\Linux学习.assets\image-20230409153302968.png)











---





# END

