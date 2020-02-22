---
title: 二-Hexo+Github Page搭建技术博客教程
tags: Hexo+Github,博客教程
slug:  storywriter/tutorial
---

==**安装 Hexo**==
如果以上环境准备好了就可以使用 npm 开始安装 Hexo 了。也可查看 Hexo 的详细文档。
在命令行输入执行以下命令：

``` avrasm
npm install -g hexo-cli
```

安装 Hexo 完成后，再执行下列命令，Hexo 将会在指定文件夹中新建所需要的文件。

``` bash
hexo init myBlog
cd myBlog
npm install
```

新建完成后，指定文件夹的目录如下：

.
├── _config.yml # 网站的配置信息，您可以在此配置大部分的参数。 
├── package.json
├── scaffolds # 模版文件夹
├── source  # 资源文件夹，除 _posts 文件，其他以下划线_开头的文件或者文件夹不会被编译打包到public文件夹
|   ├── _drafts # 草稿文件
|   └── _posts # 文章Markdowm文件 
└── themes  # 主题文件夹
好了，如果上面的命令都没报错的话，就恭喜了，运行 hexo s 命令，其中 s 是 server 的缩写，在浏览器中输入 http://localhost:4000 回车就可以预览效果了。

hexo s

==**注册 Github**==
省略……
配置 SSH key
要使用 git 工具首先要配置一下SSH key，为部署本地博客到 Github 做准备。

打开命令行输入 cd ~/.ssh 如果没报错或者提示什么的说明就是以前生成过的，直接使用 cat ~/.ssh/id_rsa.pub 命令就是可以查看本机上的 SSH key 了。

``` matlab
cat ~/.ssh/id_rsa.pub
```

如果之前没有创建，则执行以下命令全局配置一下本地账户：

``` verilog
git config --global user.name "用户名"
git config --global user.email "邮箱地址"
```

然后开始生成密钥 SSH key

``` mathematica
ssh-keygen -t rsa -C '上面的邮箱'
```

按照提示完成三次回车，即可生成 ssh key。通过查看 ~/.ssh/id_rsa.pub 文件内容，获取到你的 SSH key


首次使用还需要确认并添加主机到本机SSH可信列表。若返回 Hi xxx! You've successfully authenticated, but GitHub does not provide shell access. 内容，则证明添加成功。

``` css
ssh -T git@github.com
```

==**部署到 Github**==
此时，本地和Github的工作做得差不了，是时候把它们两个连接起来了。你也可以查看官网的部署教程。
先不着急，部署之前还需要修改配置和安装部署插件。
第一：打开项目根目录下的 _config.yml 配置文件配置参数。拉到文件末尾，填上如下配置（也可同时部署到多个仓库，后面再说）：


第二：要安装一个部署插件 hexo-deployer-git。

``` sql
npm install hexo-deployer-git --save
```

最后执行以下命令就可以部署上传啦，以下 g 是 generate 缩写，d 是 deploy 缩写：

``` bash
hexo g -d
```

稍等一会，在浏览器访问网址： https://你的用户名.github.io 就会看到你的博客啦！！

参考教程：[超详细教程感谢原作者](https://segmentfault.com/a/1190000017986794)