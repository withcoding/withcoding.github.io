.. title: 数学学习笔记——概率论基本公式1
.. slug: shu-xue-xue-xi-bi-ji-gai-lu-lun-ji-ben-gong-shi-1
.. date: 2018-11-05 23:11:37 UTC+08:00
.. tags: 
.. category: 
.. link: 
.. description: 
.. type: text
.. has_math: true


1.  | 任意一个事件发生的概率 :math:`P(E \cup F) = P(E)+P(F)-P(EF)`


2.  | 条件概率公式 :math:`P(E|F) = \frac{P(EF)}{P(F)}`


3.  | 如果 :math:`P(EF)=P(E)P(F)`，那么两个事件E和F称为独立的。


4.  | 设E和F是事件，我们可以将E表示为 :math:`E=EF \cup EF^c`，
    | 所以我们有 :math:`P(E)=P(EF)+P(EF^c)=P(E|F)P(F)+P(E|F^c)(1-P(F))`


5.  | 贝叶斯公式 :math:`P(F_j|E)= \frac{P(EF_j)}{P(E)} = \frac{P(E|F_j)P(F_j)} {\sum_{i=1}^{n}P(E|F_i)P(F_i)}`

