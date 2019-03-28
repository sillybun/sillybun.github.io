<head>
    <script src="https://cdn.mathjax.org/mathjax/latest/MathJax.js?config=TeX-AMS-MML_HTMLorMML" type="text/javascript"></script>
    <script type="text/x-mathjax-config">
        MathJax.Hub.Config({
            tex2jax: {
            skipTags: ['script', 'noscript', 'style', 'textarea', 'pre'],
            inlineMath: [['$','$']]
            }
        });
    </script>
</head>

---
layout:     post
title:      Introduction to Word2Vec
subtitle:   NLP 入门
date:       2019-03-27
author:     Eric, Zhang
header-img: img/post-bg-cook.jpg
catalog: true
tags:
    - iOS
---

# Introduction to Word2Vec

## Background
todo
## Model Introduction
在Word2Vec中，Mikolov提出了两个模型 — Continuous Bag-of-Words（CBOW）模型和Skip-gram（SG）模型。两个模型都有三层：输入层，投影层和输出层。对于CBOW模型，输入上下文预测单词；对于SG模型，通过单词预测上下文。目前来看，一般认为SG的效果好于CBOW模型。
### CBOW Model
CBOW包含三层：
1. 输入层，包含了context(w)中的2n个单词：$e(w_{-n}), e(w_{-n+1}), \dots, e(w_n)$
2. 投影层：投影层是输入层的求和，即：$x_w = \sum\limits_{i=-n}^{n}e(w_i)$
3. 输出层：有两种方法：一种是多层的softmax，一种是negative sampling
优化的函数是：
$$
L = \sum\limits_{w\in C}\log \mathrm{P}(w|\mathrm{context}(w))
$$

### Hierarchical Softmax
