# 时间转换的问题

如何将String转换成Date，如果使用DateFormat的话，不是标准的时间String能否转换。如果使用正则表达式会不会更好。

我对于时间制作的想法:

1. 解析

2. 逻辑

## 解析

解析可以使用的方法

1. 正则表达式和
2. DateFormat
3. 使用String类切割时间，然后分别对日期和时间做出判断。

每种的好处与坏处:

1. 正则，好像没有什么用，正则是匹配用的，而不是转换用的。

2. DateFormat，不知道

## 问题

1. 2017-10-22的可以解析
2. 2017-11-22 18:22:11可以解析

## 方案

第一种:获取当前时间的日期和具体时间，首先比较日期，如果日期相差超过一天，那么就显示具体日期。如果没有那么就根据时间现实。
第二种:获取当前时间和日期时间之差，然后再相除，进行比较，如果大于48小时，那么就。。

第一种方案的缺点:需要进行多个if{}嵌套，导致逻辑混乱。

# 关于是使用Constant还是枚举，这个问题还是没有分清楚

到时候需要在捋一下，哪个看起来更好，自己感觉使用Constant很蠢

# 任务

完成详情页面

1. 创建刷新和重新加载的RefreshLayout(完成)
2. Header+神评论+回复

(放弃,感觉没什么好做的，以后再补完)

## 分析排行榜页的难点

1. 可弹性滑动的效果是怎么来的
2. 可展开的Adapter是怎么做的。
3. 排行榜的内容其实差不多，没有必要分析，主要是书籍显示的地方需要了解一下
(这个暂时先不了解，准备先去看一下主题书单)

### 分析

1. 弹性滑动的效果

个人想到的是自定义View，并重写。但是如果重写的话是不会出现ScrollBar的。所以认为作者可能是用了某个layout。但是在我的记忆中没有这样的Layout，那么最大的可能就是改造了某个Layout。

2. 展开的Adapter

Adapter的应该是将男生放到了bean中，并设置是否显示的boolean。第二种方式是采用viewType的方法。但是使用viewType，viewType比较繁琐，我觉得我不会使用。
还有就是Adapter中下拉视图的展示。同样觉得可能是这是是否显示的方法，保存了一个RecyclerView吧。感觉这样最方便。

### 作者的方案

1. 重写ScrollView的点击事件，实现弹性滑动

2. 采用ExpandListView，设置含有子View的View。作者用了一个比较巧妙的方式，将最后一个View弄成存在子View的，其实原理是每个item都是一个expandView

### 觉得需要学习的地方

1. ScrollView的重写
2. 作者通过一个取巧的方式，完成了这个事情。


## 主题书单

## 分析
主题书单首先进来就是一个ViewPager，都是布局，没什么难度。略。
唯一有一点难度的，为筛选的制作。

1. 肯定使用的是PopupWindow，并且这个是可以弹性滑动，而没有显示滑动到尾的动画，就感觉应该不是刚才作者自己做的ScrollView。
2. 就是采用什么方法