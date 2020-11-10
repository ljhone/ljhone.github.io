---
layout: post
title:  "后台开发知识地图"
date:   2020-11-09
categories: work
---


<div class="mermaid">
graph LR;
    A[面试]-->B[语言技能];
    A-->C[算法和数据结构]; 
    A-->E[TCP/IP]
    A-->F[WEBRTC]
    B-->D[C++]
    D-->D1[C语言]
    D-->D2[类]
    D-->D3[STL]
    D-->D4[模版]
    C-->C1[哈希]
    C-->C2[优先级队列]
    C-->C3[字符串处理]
    C-->C4[DFS]
    E-->E1[TCP]
    E-->E2[UDP]
    F-->F1[连接过程梳理]
    F-->F2[STUN与TURN]
</div>

<script src='https://unpkg.com/mermaid@7.1.2/dist/mermaid.min.js'></script>
<script>mermaid.initialize({startOnLoad:true});</script>