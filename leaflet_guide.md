翻译规范
=======

非常感谢你的关注，为了提高翻译质量和协同效率，特约定些文档。在参与翻译前，请仔细阅读此文档。

## 质量保证机制

* 使用互相 Review 机制，修改后发 Pull Request（小修改除外），Collaborator 看到后，如果有问题回复指出；如果没有问题，简单回复一下并 Accept 即可；
* 每半个月定期与原文对照，并同步更新。

## 翻译约定

* 不译的英文名词复数改为单数，因为中文没有复数的概念；
* 专有名词保持大写：HTML, HAML, SASS, REST... 等等；
* 英文和数字与中文之间要留空格。中文标点符号和中文之间不需要留空格；
* 使用中文的标点符号。句号是 `。` 不是 `.`，破折号是 `——` 不是 `-`；
* 英文有斜体、中文没有，可用强调取代 `**强调**`；
* 译文和原文行数应保持一致，以便于后期同步更新；
* 代码缩进使用两个空格，禁止使用 Tab；
* 按照语义把英文逗号改为中文顿号；
* 译完自己读一次，看看像不像中文；
* 遇到不确定的翻译很正常，请在 Pull Request 里指出，大家一起解决。

## 约定翻译的名词

为了免除误解，这些词第一次出现时可以用 `（）` 来显示原文。

英文         | 中文
------------ | -------------
plain object | 普通对象
manage  | 管理
compose | 组合
action creator | action 创建函数
dispatch | 发起
note | 注意/须知
hold | 维持
state shape | state 结构
handle | 处理
boilerplate | 样板代码
normalized | 范式化
function | 函数？
composition | 合成
helper utility | 辅助工具
this won’t work | 这样做行不通
this will work | 这样做行得通
tips | 小贴士
create | 创建
flag | 标记位
package | 库
hook | 钩子
component | 组件
lifecycle | 生命周期
constant | 常量

## 保留不译的名词

前端开发常用的专有名词，在不造成读者理解困难的情况下，尽量保持原汁原味。

英文  | 说明
----- | ------
action | 动作
reducer | -
store | -
middleware | 中间件
dispatcher | 分发器
state | 状态
state tree | 状态树
props | 属性
UI | 用户界面
monkey patch | -
currying | 柯里化

## 加入翻译

欢迎加入我们一起为 React 在中文推广出一份力，对于有能力且积极的同学会被邀请加入我们 Group。

开始翻译前，你可以通过以下方式认领，确保没有重复工作。

## 认领制度

对于未被翻译的章节，你应该在翻译之前进行翻译认领来保证没有人和你重复工作。
很简单，请从 repo 的 issue 列表中认领，如果没有对应章节的 issue，自己创建一个即可。
认领成功后就代表你已经成功占到一个坑，你可以开始慢慢翻译自己的文章了。
如果占坑太久你的占位可能被取消，尽量在两周内完成。

对于已经翻译的章节，欢迎做校验工作，校验不需要认领，fork 后修改并发 Pull Request 即可。

## 翻译流程

一、fork 要翻译的 repo

二、如果是新翻译章节，应参照对应的原文进行翻译；如果是校对则直接修改

建议使用 Sublime Text、Mou 等支持 Markdown 类编辑器编辑，同时开启横向双列模式。

三、翻译时启动 watch 来实时看结果
```
npm run watch
```
打开：[localhost:4000](http://localhost:4000)

四、翻译结束，提交 Pull Request

五、fork 后的 repo 如何同步本 repo？

```
// 添加 upstream 源，只需执行一次
git remote add upstream git@github.com:react-group/***.git
// 拉取远程代码
git pull upstream master
// 更新 fork 仓库
git push origin master
```

更多参考：https://help.github.com/articles/syncing-a-fork/

## 与原文同步机制

To Be Determined

## Collaborator 协作规范

成为 Collaborator 说明自己的能力和贡献被肯定，是很光荣的事情。有直接操作代码库和 Accept 别人 Pull Request 的权限，为了避免错误的操作，因此需要一些规范来约束自己。

* Collaborator 应该是活跃的，遇到 Pull Request 主动 Review，主动参与和发起讨论。
* 自己发的 Pull Request 虽有合并权限，但需要至少其它一人 Reivew 后才能合并

## 小贴士

* [Bing 词典](http://cn.bing.com/dict/) 可以查询相关的翻译

## 建议与反馈

欢迎任何建议！直接开一个 github issues 就可以了。

## License

Creative Commons Zero v1.0 Universal
