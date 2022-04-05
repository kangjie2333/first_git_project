# Git

author:刘强

## Git发展

**diff&patch ===》RCS（本地）===》CVS&SVN（集中式版本控制工具）===》Git（分布式版本控制工具）**

//集中式版本控制

CVS，产于1985年，实现协同工作，不支持原子操作，网络传输效率低。

SVN，目的是替代CVS，实现原子提交，局域网外查看日志、提交数据等操作存在延迟。

缺点：提交排队，不能同时修改，提交缺乏质量控制；缺乏代码门禁；单点故障；黑客攻击

//分布式版本控制

Git，产于2005年，快照流。不适合word等二进制文档的版本控制，不能将读授权精细到目录级别。

## Git安装

略

## Git使用

### 三种工程区域状态

1、版本库（Repository），在隐藏目录.git下，这个目录就是git的版本库，存放了git用来管理该工程的所有版本数据，又称为本地仓库

2、工作区（Working Directory），本地PC桌面上的工程文件，就是日常工作的代码文件或者文档所在的文件夹

3、暂存区（Stage），也叫索引，存放在工程根目录.git/index中

### 三种文件状态

1、已提交（committed），文件已经被安全的放在本地数据库

2、已修改（modified），修改了某文件，还没有提交保存

3、已暂存（staged），把已修改的文件放在下次要提交保存的清单中

### 常用命令

![image-20220405131510154](C:\Users\KJ\AppData\Roaming\Typora\typora-user-images\image-20220405131510154.png)

### Git操作演示

![img](https://images2015.cnblogs.com/blog/809218/201606/809218-20160604213832164-1203726937.png)

![img](https://images2015.cnblogs.com/blog/809218/201606/809218-20160604213850274-1309981476.jpg)

#### ====================================================

**打开Git Bash，快捷键是Shift+F10，然后按s，再按Enter**

#### 1、查看用户信息

```C++ 
git config user.name
git config user.email
```

![image-20220405143837293](C:\Users\KJ\AppData\Roaming\Typora\typora-user-images\image-20220405143837293.png)

#### 2、修改用户信息

```c++
git config --global user.name  "xxxx"
git config --global user.email  "xxxx"
```

====================================================

#### 3、新建仓库，并初始化

```C++
git init "xxxx"
```

在本地目录中新建first_git_project项目仓库

![image-20220405140955715](C:\Users\KJ\AppData\Roaming\Typora\typora-user-images\image-20220405140955715.png)

其中ls -al表示-a, -al # 列出目录中所有文件，包括以“.”开头的文件。

![image-20220405141302230](C:\Users\KJ\AppData\Roaming\Typora\typora-user-images\image-20220405141302230.png)

#### 4、添加文件

**进入项目**

![image-20220405141816609](C:\Users\KJ\AppData\Roaming\Typora\typora-user-images\image-20220405141816609.png)

**新建文件**

![image-20220405141905589](C:\Users\KJ\AppData\Roaming\Typora\typora-user-images\image-20220405141905589.png)

**添加内容**

![image-20220405142108661](C:\Users\KJ\AppData\Roaming\Typora\typora-user-images\image-20220405142108661.png)

vim常用操作：英文输入法下，i为输入数据，ESC为退出输入，：wq为保存退出

#### 5、查看文件状态

```C++
git status
```

![image-20220405142307803](C:\Users\KJ\AppData\Roaming\Typora\typora-user-images\image-20220405142307803.png)

**提示我有未追踪的文件，让我用git add命令。**

#### 6、添加到暂存区

```
git add
```

![image-20220405142731485](C:\Users\KJ\AppData\Roaming\Typora\typora-user-images\image-20220405142731485.png)

![image-20220405143007333](C:\Users\KJ\AppData\Roaming\Typora\typora-user-images\image-20220405143007333.png)

**提示我文件已经在暂存区了，可以提交了，也可以从暂存区删除**

#### 7、提交修改

```C++
git commit -m "xxxx"
```

**将文件提交到repository里。提交信息用英文的双引号括起来**

![image-20220405143254760](C:\Users\KJ\AppData\Roaming\Typora\typora-user-images\image-20220405143254760.png)

提示我一个文件改变，插入一行内容

![image-20220405143623604](C:\Users\KJ\AppData\Roaming\Typora\typora-user-images\image-20220405143623604.png)

#### 8、查看日志

```C++
git log
```

![image-20220405143657287](C:\Users\KJ\AppData\Roaming\Typora\typora-user-images\image-20220405143657287.png)

**查看到刚才提交的commit，显示作者信息，时间信息等**

**`HEAD` 指向的就是当前分支：在master分支上，HEAD指向master，而master指向的是最近的一次提交**

![img](https://img-blog.csdn.net/20141230143856975?watermark/2/text/aHR0cDovL2Jsb2cuY3Nkbi5uZXQvYmRzczU4/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70/gravity/Center)

#### ====================================================

#### 9、修改文件

![image-20220405144512141](C:\Users\KJ\AppData\Roaming\Typora\typora-user-images\image-20220405144512141.png)

**显示未提交的更改**

#### 10、比较差异

```
git diff
```

![image-20220405144731024](C:\Users\KJ\AppData\Roaming\Typora\typora-user-images\image-20220405144731024.png)

**默认跟最新的一个commit进行比较，-表示删除，+表示增加**

#### 11、撤销工作区修改（未暂存的更改）

![image-20220405145327307](C:\Users\KJ\AppData\Roaming\Typora\typora-user-images\image-20220405145327307.png)

![image-20220405145431141](C:\Users\KJ\AppData\Roaming\Typora\typora-user-images\image-20220405145431141.png)

#### 12、版本回退

**当前文件状态**

![image-20220405145809678](C:\Users\KJ\AppData\Roaming\Typora\typora-user-images\image-20220405145809678.png)

**有两个commit节点，两行黄色部分是以 `commit` 开头的，后面接着一串字符。这一串字符是16进制的数，是一串哈希值。我们叫它版本号就行了**

```c++
git reset --hard "xxxx"
```

![image-20220405150136933](C:\Users\KJ\AppData\Roaming\Typora\typora-user-images\image-20220405150136933.png)

**取版本号前7位就可以了，然后显示已经回退到想要的commit节点处，并显示那个节点的注释信息。此时桌面文件中的内容已经被回退**

![image-20220405150404098](C:\Users\KJ\AppData\Roaming\Typora\typora-user-images\image-20220405150404098.png)

**新版本的commit记录不见了！这就是 reset --hard 的力量，很好很强硬！**

#### 13、回退后，回到最新版本

![image-20220405150535378](C:\Users\KJ\AppData\Roaming\Typora\typora-user-images\image-20220405150535378.png)

**可以看到HEAD的变化情况。**
 **第1行表示当前HEAD所在的版本号，而之所以在这个版本号，是由于我们执行了reset命令。**
 **看第3行，它告诉我们，这个HEAD所在的版本号，这个版本号是在执行commit之后形成的。**

![image-20220405150811560](C:\Users\KJ\AppData\Roaming\Typora\typora-user-images\image-20220405150811560.png)

![image-20220405150828969](C:\Users\KJ\AppData\Roaming\Typora\typora-user-images\image-20220405150828969.png)

**又回去了**

#### 14、清楚未追踪的文件

```
git clean -xf
```

![image-20220405151518631](C:\Users\KJ\AppData\Roaming\Typora\typora-user-images\image-20220405151518631.png)

#### 15、git连接github

**略，参考git安装**

#### 16、创建远程仓库并与本地关联

**step1：创建远程仓库**

![image-20220405151859738](C:\Users\KJ\AppData\Roaming\Typora\typora-user-images\image-20220405151859738.png)

**两个地方都可以新建远程仓库**

![image-20220405152057094](C:\Users\KJ\AppData\Roaming\Typora\typora-user-images\image-20220405152057094.png)



复制项目地址![image-20220405152225330](C:\Users\KJ\AppData\Roaming\Typora\typora-user-images\image-20220405152225330.png)

![image-20220405152551993](C:\Users\KJ\AppData\Roaming\Typora\typora-user-images\image-20220405152551993.png)

![image-20220405152749149](C:\Users\KJ\AppData\Roaming\Typora\typora-user-images\image-20220405152749149.png)

**加了参数-u后，以后即可直接用git push 代替git push origin master**

![image-20220405152610662](C:\Users\KJ\AppData\Roaming\Typora\typora-user-images\image-20220405152610662.png)

#### 17、上传到远程仓库

```C++
git push origin "xxxx"
```

#### ====================================================

#### 18、更新本地仓库（git pull）

**在远程仓库新增了readme文件，此时本地push报错**

![image-20220405153627893](C:\Users\KJ\AppData\Roaming\Typora\typora-user-images\image-20220405153627893.png)

![image-20220405153712634](C:\Users\KJ\AppData\Roaming\Typora\typora-user-images\image-20220405153712634.png)

**提示应该git pull**

```
git pull
```

**git pull 命令用于从远程获取代码并合并本地的版本。** 

**git pull 其实就是 git fetch 和 git merge FETCH_HEAD 的简写。**

![image-20220405153841813](C:\Users\KJ\AppData\Roaming\Typora\typora-user-images\image-20220405153841813.png)

![image-20220405154152349](C:\Users\KJ\AppData\Roaming\Typora\typora-user-images\image-20220405154152349.png)

![image-20220405154205064](C:\Users\KJ\AppData\Roaming\Typora\typora-user-images\image-20220405154205064.png)

![image-20220405154321039](C:\Users\KJ\AppData\Roaming\Typora\typora-user-images\image-20220405154321039.png)

![image-20220405154448033](C:\Users\KJ\AppData\Roaming\Typora\typora-user-images\image-20220405154448033.png)

**再次查看，此时都是最新的了**

#### 19、更新本地仓库，解决冲突（git fetch，get merge）

![image-20220405155449480](C:\Users\KJ\AppData\Roaming\Typora\typora-user-images\image-20220405155449480.png)

![image-20220405155508133](C:\Users\KJ\AppData\Roaming\Typora\typora-user-images\image-20220405155508133.png)

#### ====================================================

#### 20、下载远程项目

```C++
git clone "xxxx"
```

![image-20220405160243430](C:\Users\KJ\AppData\Roaming\Typora\typora-user-images\image-20220405160243430.png)

![image-20220405160252717](C:\Users\KJ\AppData\Roaming\Typora\typora-user-images\image-20220405160252717.png)

![image-20220405160305950](C:\Users\KJ\AppData\Roaming\Typora\typora-user-images\image-20220405160305950.png)

#### 21、新建分支

```C++
git checkout -b "xxxx"
```

新建一个分支，并切换

![image-20220405160508935](C:\Users\KJ\AppData\Roaming\Typora\typora-user-images\image-20220405160508935.png)

![image-20220405160636040](C:\Users\KJ\AppData\Roaming\Typora\typora-user-images\image-20220405160636040.png)

#### 22、查看分支

```
git branch
```

![image-20220405161029203](C:\Users\KJ\AppData\Roaming\Typora\typora-user-images\image-20220405161029203.png)

#### 23、分支合并

```
git merge
```

![image-20220405161249102](C:\Users\KJ\AppData\Roaming\Typora\typora-user-images\image-20220405161249102.png)

#### 24、节点合并

**同一仓库节点合并**

![image-20220405162449994](C:\Users\KJ\AppData\Roaming\Typora\typora-user-images\image-20220405162449994.png)

![image-20220405162505032](C:\Users\KJ\AppData\Roaming\Typora\typora-user-images\image-20220405162505032.png)

```C++
git cherry-pick "xxxx"
```

![image-20220405162939503](C:\Users\KJ\AppData\Roaming\Typora\typora-user-images\image-20220405162939503.png)

![image-20220405162955831](C:\Users\KJ\AppData\Roaming\Typora\typora-user-images\image-20220405162955831.png)

![image-20220405162912276](C:\Users\KJ\AppData\Roaming\Typora\typora-user-images\image-20220405162912276.png)

**不同仓库节点合并**

![image-20220405163839697](C:\Users\KJ\AppData\Roaming\Typora\typora-user-images\image-20220405163839697.png)

![image-20220405163912772](C:\Users\KJ\AppData\Roaming\Typora\typora-user-images\image-20220405163912772.png)

![image-20220405163924834](C:\Users\KJ\AppData\Roaming\Typora\typora-user-images\image-20220405163924834.png)

![image-20220405163936248](C:\Users\KJ\AppData\Roaming\Typora\typora-user-images\image-20220405163936248.png)

![image-20220405163949325](C:\Users\KJ\AppData\Roaming\Typora\typora-user-images\image-20220405163949325.png)

![image-20220405164003207](C:\Users\KJ\AppData\Roaming\Typora\typora-user-images\image-20220405164003207.png)

#### 25、删除分支

![image-20220405164141011](C:\Users\KJ\AppData\Roaming\Typora\typora-user-images\image-20220405164141011.png)

```C++
git branch -d "xxxx"
```

![image-20220405164151561](C:\Users\KJ\AppData\Roaming\Typora\typora-user-images\image-20220405164151561.png)

#### 26、切换分支

```C++
git checkout "xxxx"
```

