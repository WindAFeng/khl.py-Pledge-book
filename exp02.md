## 第二章  认识指令架构

前情回顾，我们在上一篇文章讲到了开发环境以及机器人的 `token`，这一节我们就要学习机器人代码的结构和编写了。

请确保您安装的 khlpy 版本为 0.3.13 或向下兼容的更高版本。0.2 版的 khl.py 并不与 0.3 版兼容。

### 2-1  认识 khl.py 中的机器人代码结构

下面就是机器人代码的大体结构（注：当前代码不可运行）：

```python
from khl import Bot, Message # 导入机器人的运行模块


bot = Bot(token="***********************************") # 这里填写你自己的机器人的token
# bot: 机器人的身份证

@bot.command(name='hello') # .command：机器人的运行模式，指令模式
# name='hello'：这个是召唤机器人所需要的指令
async def func(msg: Message):
    # def func(): ：对于 hello 这个命令来说，主要代码要在这个函数内实现。
    # （注：如果有async他就叫异步方法，如果没有就叫做同步方法，具体的请百度查询）
    # 填写这个命令要实现的内容

bot.run()# 让bot跑起来
```

按照学习编程的惯例，`Hello World!` 是一个很好的入门项目。

### 2-2  新手上路

接下来，我们要着手开始编写机器人了

以下代码可以复制，但要注意token码。

```python
from khl import Bot, Message # 导入机器人的运行模块


bot = Bot(token="***********************************") # 这里填写你自己的机器人的token
# bot: 机器人的身份证

@bot.command(name='hello') # .command：机器人的运行模式，指令模式
# name='hello'：这个是召唤机器人所需要的指令，对应例如 "/hello" 的消息发送。
async def func(msg: Message):
    await msg.reply("Hello, World!")
    # def func(): ：对于 hello 这个命令来说，主要代码要在这个函数内实现。
    # （注：如果有async他就叫异步方法，如果没有就叫做同步方法，具体的请百度查询）
    # 填写这个命令要实现的内容

bot.run()# 让bot跑起来
```

现在，这个 bot 就能跑起来了，但是怎么看见 bot 发送的消息呢？

### 2-3  邀请链接

在上面的代码执行起来后，我们就能在开发者平台-应用中看见 bot 正在运行。接下来我们要获取邀请链接。
找到 “开发者平台-应用-我的应用（找到你的机器人头像，点进去）-机器人-邀请链接“（复制就可以了）。
在浏览器新建一个标签页，打开这个链接把机器人邀请到服务器，就可以啦！

现在，对这个机器人所在的服务器，发送 "/hello" 命令，就可以看见它回复你 "Hello, World!" 啦。

### 2-4 带参数的命令——典型的小项目，账户注册

账户注册指的是，输入例如 `/reg username` 的命令，机器人能够识别这个”username“。

实现这个功能的主要目的是，了解带有参数的消息，如 `/reg 阿风` 如何获取这个参数”阿风“机器人能知道 @ 的是 `阿风`。

这里就需要用到函数的参数了，新增一个 `reg` 命令以及对应的函数：

```python
@bot.command(name = "reg") # reg 命令，通过 "/reg username" 的方式使用。如 "/reg 阿风"
async def register(msg: Message, username): # username 必须是一个字符串，不能是 "@xxx" 的形式；而且必须输入，即通过 "/reg xxx" 的方式调用，形如"/reg"的调用方式是不被允许的。
    await msg.reply("Hello, " + username) # 回复消息，这里用到了字符串拼接。
```

使用例：

- 阿风：/reg 阿风

- bot：Hello, 阿风

### 2-5 消息类型

在世界上，有许多种语言，比如：中文，英文，日文。
当然，在 bot 中也有许多回复你的方式（[khl.py 官方原文章](https://github.com/TWT233/khl.py/tree/main/example/ex04_reply)）。

我们刚才用的就是其中一种，下面我会给大家多演示几种：

```python
# 注：临时消息仅发出命令的人可见，重启kook也会删除该消息
await msg.reply('world for you!')# 这个是回复发消息的人
await msg.reply('world only for you!', is_temp=True)# 发送一个临时消息并回复别人
await msg.ctx.channel.send('world for all!')# 这个是发送消息给全体成员
await msg.ctx.channel.send('world only for you too!', temp_target_id=msg.author.id)# 发送全体消息给某人
```

结语：到目前，我们把 khl.py 的一些普通语法讲完了，接下来就要讲 python 语法了。
