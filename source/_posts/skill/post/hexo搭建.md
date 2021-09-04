---
title: mac上搭建基于hexo的博客,主题是shoka

tag: 教程

cover: cover.jpg
categories:
- [技能, post]
---



# 配置环境

## mac安装node

### 安装npm



```shell
git clone https://gitee.com/mirrors/nvm.git ~/.nvm && cd ~/.nvm && git checkout `git describe --abbrev=0 --tags`	
```
> https://www.shangmayuan.com/a/f8cac747ffb4419fa95382bf.html

### 为npm配置环境变量



```shell
vim ~/.zshrc
# 打开文件：将下面的代码帖到光标处
export NVM_DIR="$([ -z "${XDG_CONFIG_HOME-}" ] && printf %s "${HOME}/.nvm" || printf %s "${XDG_CONFIG_HOME}/nvm")"
[ -s "$NVM_DIR/nvm.sh" ] && \. "$NVM_DIR/nvm.sh"
```
> https://www.cnblogs.com/jiduoduo/p/14096774.html


### 安装node

```shell
nvm install node	
```

+++info 问题

;;;id1 镜像问题

https://blog.csdn.net/u010741112/article/details/108991629

;;;

;;;id1 版本问题

https://www.cnblogs.com/judeyq/p/12124985.html

https://blog.csdn.net/Fabulous1111/article/details/84983869

;;;

+++

## Win安装node

[NodeJS、NPM安装配置步骤及环境变量详解](https://blog.csdn.net/shenggaofei/article/details/80361627)


## 安装hexo

```shell
npm install -g hexo-cli
npm install hexo-deployer-git --save
```



:::info 慢

https://blog.csdn.net/f6619082/article/details/109193251

:::

## 运行hexo

```shell
# mac:清理，编译，搜索，推送，推送develop远程服务器，启动hexo五步走
hexo clean && hexo g && hexo a && hexo d && hexo s
```
```shell
# win
hexo clean ; hexo g ; hexo a ; hexo d ; hexo s
```
# 主题美化

[hexo官网主题](https://hexo.io/themes/)

[Hexo-Theme-Yun](https://www.yunyoujun.cn)

[next主题问题](https://blog.csdn.net/qq_39898645/article/details/109181736)

[shoka主题问题](https://blog.csdn.net/yu826103408/article/details/106619696/)




参考链接

> https://dylan-get.github.io/2021/08/13/blog搭建-hexo/