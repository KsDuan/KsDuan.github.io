# 使用hugo和GitHub快速构建并发布博客

> 以下内容参考了博客[氧气计算](http://newoxygen.github.io/post/hugo%E5%BF%AB%E9%80%9F%E5%BB%BA%E7%AB%99/)，非常感谢！

# 1. 安装hugo

hugo是一个快速的静态网站引擎，使用Go语言开发，可以用Markdown格式的文章生成一个完整的静态网站，然后托管到自己的GitHub仓库中。

1. 从[官网](https://github.com/gohugoio/hugo/releases)下载相关版本，比如我是64位Windows系统，需要下载[hugo_extended_0.80.0_Windows-64bit.zip](https://github.com/gohugoio/hugo/releases/download/v0.80.0/hugo_extended_0.80.0_Windows-64bit.zip)；

   > 这里最好下载extended版本的，否则容易在设置主题时报错。

2. 解压缩后，把所在的文件夹添加进系统环境变量PATH，如图所示：

   ![image-20210215215448314](使用hugo和GitHub快速构建并发布博客.assets/20210215231104.png)

   *这里是解压后的软件文件夹*

   ![image-20210215215546599](使用hugo和GitHub快速构建并发布博客.assets/20210215231105.png)

   *你需要将所在文件夹添加PATH*

   3. 测试hugo是否正常使用：打开power shell，输入``` hugo ```，出现以下信息，说明正常：

      ![image-20210215215818210](使用hugo和GitHub快速构建并发布博客.assets/20210215231106.png)

      

# 2. 构建静态网站

在你希望放置网站文件夹的位置打开power shell，键入以下命令：

``` hugo new site Blog ```

进入Blog文件夹，目录结构如下：

```
content/ 
layouts/
layouts/
static/
config.toml
```

## 2.1 新建文章

仍是在Blog文件夹下，键入以下命令，创建about界面：

``` hugo new about.md ```

打开content/about.md，可以看到以下信息：

![image-20210215220604566](https://raw.githubusercontent.com/KsDuan/drawing-bed/master/BlogImg/20210215231107.png)

这几行是文件头信息，之后创建的每篇文章都会包含这些信息。你可以在这个文档中添加关于博客的介绍信息，保存退出。

再创建一篇文章：

``` hugo new post/first.md ```

打开first.md文件，在这里你可以写下你的文章内容，保存退出。

![image-20210215220950619](使用hugo和GitHub快速构建并发布博客.assets/20210215231108.png)

## 2.2 安装主题

hugo有很多主题，你可以在他们的[GitHub主页](https://github.com/gohugoio/hugoThemes)找到自己喜欢的主题，然后在Blog目录下创建themes目录，在该目录中使用git命令下载主题（例如我在这里使用了zen主题）：

``` git clone https://github.com/frjo/hugo-theme-zen.git ```

打开``` config.toml ```文件，添加以下语句以便使用所选主题：

``` theme = "hugo-theme-zen" ```

## 2.3 运行hugo

在Blog根目录下键入以下命令：

``` hugo server -D ```

![image-20210215222200270](使用hugo和GitHub快速构建并发布博客.assets/20210215231109.png)

根据提示访问http://localhost:1313/页面，如无差错页面将显示以下内容：

![image-20210215222521263](使用hugo和GitHub快速构建并发布博客.assets/20210215231110.png)

# 3. 将站点托管至Github

现在我们已经用hugo构建了自己的站点，并可在本地访问，如果希望更多人访问自己的博客，可以用GitHub进行托管。

在GitHub创建一个仓库，名字为``` username.github.io ```（将username替换为你的ID）。

打开``` config.toml ```文件，添加以下语句：

``` baseURL = "https://KsDuan.github.io/" ```

在Blog根目录下键入以下命令：

``` hugo -D ```

这会生成一个public目录用于发布站点

![image-20210215223406975](使用hugo和GitHub快速构建并发布博客.assets/20210215231111.png)

在public目录下打开git bash，把所有文件上传至远程仓库：

``` 
git init
git remote add origin https://github.com/用户名/用户名.github.io.git 
git add .
git commit -m "first commit" 
git push -u origin master
```

上传成功后，在浏览器中输入``` http://用户名.github.io ```就可以访问自己的博客了。



