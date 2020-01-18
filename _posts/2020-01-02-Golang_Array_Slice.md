---
title: Golang -- Array and Slice
---

> 数组和切片是比较容易混淆的概念。


### 一些Tips

> 数组类型的值的长度是固定的，而切片类型的值是可变长的。

换句话说，数组的长度是类型的一部分，[1]string 和 [2]string是不同类型的数组。


> 数组是值类型，切片是引用类型。

Go中，函数参数传递时，仅与类型有关，如果是值类型，则值传递，引用类型则引用传递。

> Slice底层是数组，Slice有长度和容量的概念需要注意。

可以将Slice看作滑动窗口，长度是窗口能看到的大小，容量是真实大小。当对slice进行append等操作时，如果容量不足以存放，容量会进行扩容。底层数组会被完整拷贝到新分配的更大的数组中。

> Slice的capacity是如何增长的。

规则其实不必在意，大概是“合理的比你需要的多一些”。如果你非要知道具体分配细节，可以看runtime/slice.go中的growslice。
```
if len < 1024:  翻倍
if len >= 1024: for 长度*1.25 until Ready for new size
```

其实其他也没什么特别的。