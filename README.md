# Leaflet - 中文文档  <img src='http://leafletjs.cn/docs/images/logo.png' height='30'>


> Leaflet一个开源并且对移动端友好的交互式地图JavaScript库。本项目目的在于为国内使用`Leaflet`的小伙伴们提供一份内容完善、准确度相对较高并且更新及时的中文文档，希望能够给大家在学习或开发过程中带来一定的便利。
> 
> Leaflet 中文站点：http://leafletjs.cn/
> Leaflet 官方站点：http://leafletjs.com/

### 加入翻译

由于本人精力有限，希望更多的小伙伴可以加入我们，一起参与翻译，共同来帮助更多人。如果你完全没接触过翻译工作也不用担心，我们将会为你准备完善的[翻译规范](https://github.com/NICEXAI/leaflet_zh/blob/master/leaflet_guide.md)和操作说明。

<img src='http://leafletjs.cn/docs/images/QQ.png' height='300'>

开始翻译前，你可以先加入我们的交流群，然后在群里通过以下方式认领，确保没有重复工作。

#### 认领制度

对于未被翻译的章节，你应该在翻译之前进行翻译认领来保证没有人和你重复工作。
很简单，请从 repo 的 issue 列表中认领，如果没有对应章节的 issue，自己创建一个即可。
认领成功后就代表你已经成功占到一个坑，你可以开始慢慢翻译自己的文章了。
如果占坑太久你的占位可能被取消，尽量在两周内完成。

对于已经翻译的章节，欢迎做校验工作，校验不需要认领，fork 后修改并发 Pull Request 即可。

#### 翻译流程

1、fork 要翻译的 repo

2、如果是新翻译章节，应参照对应的原文进行翻译；如果是校对则直接修改

建议使用 Sublime Text、Vscode 等支持 Markdown 类编辑器编辑，同时开启横向双列模式。

3、安装[jekyll](https://jekyllcn.com/), 翻译时启动 watch 来实时看结果（`jekyll`[官方安装文档](http://jekyllcn.com/docs/installation/)）

```
jekyll serve
```
打开：[127.0.0.1:4000](http://127.0.0.1:4000/)

4、翻译结束，提交 Pull Request

5、fork 后的 repo 如何同步本 repo？

```
// 添加 upstream 源，只需执行一次
git remote add upstream https://github.com/NICEXAI/leaflet_zh.git
// 拉取远程代码
git pull upstream master
// 更新 fork 仓库
git push origin master
```

更多参考：https://help.github.com/articles/syncing-a-fork/


#### 其它事项

```
C:\User>gem install jekyll
Temporarily enhancing PATH for MSYS/MINGW...
Building native extensions. This could take a while...
ERROR:  Error installing jekyll:
    ERROR: Failed to build gem native extension.

    current directory: C:/Ruby25-x64/lib/ruby/gems/2.5.0/gems/http_parser.rb-0.6.0/ext/ruby_http_parser
C:/Ruby25-x64/bin/ruby.exe -r ./siteconf20180308-3672-ueo7ea.rb extconf.rb
creating Makefile

current directory: C:/Ruby25-x64/lib/ruby/gems/2.5.0/gems/http_parser.rb-0.6.0/ext/ruby_http_parser
 make "DESTDIR=" clean
```
如果安装`jekyll`过程中遇到上面问题或者安装`msys2`过程中报错，可以参考以下文章进行解决:
* [在Windows上安装Jekyll](https://www.jianshu.com/p/58e2c5ea3103)
* [mysys2使用记录](https://www.jianshu.com/p/2a3ff0d4f53a)



### 参与贡献人员名单

> 定期更新，谢谢各位辛勤贡献

- [待定](https://blog.h5base.cn/)

**只要文档符合 [翻译规范](https://github.com/NICEXAI/leaflet_zh/blob/master/leaflet_guide.md)，欢迎你来一起完善**
