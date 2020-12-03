# dde_autotest
```
base pytest for linux ui test
```

# pytest+allure安装

## 安装依赖包
```
sudo pip3 install pytest allure-python-commons allure-pytest
sudo apt install openjdk-8-jdk npm
```
## 安装npm对应版本6.4.1(node 10.15.2)
查询当前版本
```
npm -v 
node -v
```
下载地址：https://docs.deepin.com/d/27c896aeb3/
解压v6.4.1.tar.gz,并进行安装
```
cd cli-6.4.1
sudo make install
```
## 安装allure命令
```
sudo npm install -g allure-commandline --save-dev
```
## 如果默认安装报错，则需要用淘宝镜像源进行注册,再执行上面的安装命令
```
sudo npm install -g less
sudo npm install -g cnpm --registry=https:/registry.npm.taobao.org
sudo npm config set registry https:/registry.npm.taobao.org
```
# 执行生成报告
## 生成pytest_allure报告
```
./pytest_allure_report.sh
```
## 生产pytest_html报告
```
sudo pip3 install pytest-html

./pytest_html_report.sh
```
##  支持中文
```
cd /usr/local/lib/python3.7/dist-packages/_pytest
sudo vim nodes.py
```
修改内容：
```
#self.name = name
self.name = name.encode("utf-8").decode("unicode_escape")
```
# 代码提交规范
## Commit message 规范
```
格式:

类型(影响范围) : 描述 

type(scope) : subject

注意冒号两边加空格
```
## 1.type 类型（必须）
```
type是commit 的类别，只允许使用下面几个标识：

fix: 修复bug

add: 新功能

update: 更新

delete: 删减内容

style: 代码格式改变

test: 增加测试代码，不影响功能，如：print

revert: 撤销上一次的commit

build: 构建工具或构建过程等的变动

refactor: 某个已有功能重构
```
## 2.scope(选填)
```
scope用于说明 commit 影响的范围，推荐用模块(全小写)

urfl (py自定义库, 用到的dbus模块比较多，统一用urfl标识)

dde (uos整个桌面环境) 【适用于robot资源和用例】

desktop (桌面)

dock（任务栏）

launcher（启动器）

kwin (窗口管理器)

dcc (控制中心)

tool(工具、脚本相关)

docs（文档）
```

## 3.subject(必须)
```
subject是对本次提交的简短描述。

不超过50个字符。

结尾不加句号（.或。）

推荐以动词开头，如： 设置、修改、增加、删减、撤销等

merge合并分支代码用默认的,无需修改
```

# 举例（制定了规则，请大家自觉遵守）
```
eg: type(scope) : subject

add(dcc) : 添加个性化测试用例

fix(urfl) : 修改dbus接口的参数类型

update(docs) : 更新README.md，添加dogtail安装步骤

style(dock) : 调整任务栏关键字格式

fix(dde) : 修改鼠标点击的速度

test(tool) : 添加脚本调试代码

add(tool) : 添加自动化环境部署脚本
```
test
