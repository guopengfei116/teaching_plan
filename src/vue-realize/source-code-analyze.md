# SourceCodeInterpretation

在github上搜索vue仓库进行Fork，`https://github.com/vuejs/vue`，然后clone源码到本地，分析源码目标结构。

## flow

因为Vue使用了flow静态类型语言，定义了很多数据类型，所以我们先从flow目录开始，方便理解和查阅源码里的数据类型。



## src

因为源代码处在src目录，所以这里从src目录开始分析，下面是src目录下的内容。

- compiler: 编译相关
- core：核心代码
- platforms：跨平台支持
- server：服务端渲染
- sfc：vue文件解析
- shared：共享代码

知道了大概的目录结构后，准备抄袭代码，如果抄袭过程中遇到晦涩难懂逻辑复杂的地方，先搁浅，等后续对整个代码结构和执行过程有宏观的了解后再研究会更好理解。另外抄袭源代码时，一定要屡出一条主线，主线屡完再补充分支，尽量广度优先，逐渐向深度靠近，避免走火入魔。

### shared

实际上整个过程还得根据具体情况做调整，但是主体方向按照这个思路走，逐步摸清代码逻辑。

按照常理讲，我们应该从入口文件开始，一点一点抄袭源代码，并根据自己的理解做注释。但是我们做一个调整，
shared目录的内容属于共享的，它又不依赖与其他目录，所以先从这里开始分析，这样其他地方使用时更容易理解目的。






