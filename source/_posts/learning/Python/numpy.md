---
title: numpy
date: 2021-08-26 11:48:49
tags: Python
categories:
- [学习, Python]
---

[numpy中的复制（copy）](https://blog.csdn.net/qq_34995963/article/details/100178252)

一些返回值注意

| 函数   | 返回值  | 示例                                                         |
| ------ | ------- | ------------------------------------------------------------ |
| hstack | array   | o = np.hstack((o, fea[i * 10 + j].reshape((32, 32)).T))      |
| resize | inplace | O.resize(320, 320) <br />io.imsave(os.path.join(dir, "faces.png"), O) |
|        |         |                                                              |

