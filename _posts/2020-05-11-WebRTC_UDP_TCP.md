---
title: WebRTC -- TCP Or UDP
---

> 记录和学习一些基本的音视频知识。

作为音视频底层传输协议是TCP还是UDP？目前来看是UDP比较合理，因为目前TCP超时重传的机制保障了数据绝对不会丢，但是数据到达时间不可控。音视频场景下仅需要尽量到达以及数据实时性，并不需要绝对不能丢。TCP追求的数据完整性这里并不适用。


