# hostloc_getPoints
HOSTLOC 每日获取积分脚本

## 0. 前置条件
本地需要有`python`（python3）运行环境
### 提示
请确认有效的`python`和`pip`可执行命令名称为`python`、`pip`，或者是`python3`、`pip3`。以下以`python`、`pip`为例。

## 1. 安装
### 1.1 克隆项目
(可能需要代理软件才能正常访问，请自行搜索git代理方案)
```
git clone https://github.com/seemygesture/hostloc_getPoints.git
```

### 1.2 安装依赖模块（1.2.a或者1.2.b任选其一即可）
推荐下载本项目后，在项目根文件夹内通过venv虚拟环境安装相应模块，以防和其它python项目产生冲突。
### 1.2.a （推荐）（方式一）在虚拟环境venv中安装依赖模块
```
# 以 Windows11 的 powershell，使用venv虚拟环境为例

# 进入项目的主文件夹下
cd hostloc_getPoints

# 安装虚拟环境至 .venv目录
python -m venv .venv

# 进入虚拟环境
.\.venv\Scripts\Activate.ps1

# 安装依赖模块
pip install -r requirements.txt
```

### 1.2.b （方式二）在系统下安装全局的依赖模块
无需进入虚拟环境，可能和其它python项目产生冲突
```
# 以 Windows11 的 powershell

# 安装全局的依赖模块
pip install pyaes curl_cffi --break-system-packages
```

## 2. 填写配置信息
示例配置文件为`config.example.yaml`，复制它，并重命名为`config.yaml`

修改`config.yaml`文件，注意需要保持`yaml`配置文件中相关行的**缩进一致**！

以下为2个账号，并设置代理为socks5h本地代理`127.0.0.1:8080`的参考配置。

注意，如果配置使用：`socks5://127.0.0.1:8080`，则会启用本地的8080端口上的socks5代理，但是DNS解析域名仍可能被污染。

如果配置使用：`socks5h://127.0.0.1:8080`，则会启用本地的8080端口上的socks5代理，并由socks5代理负责域名的DNS解析。

```
usercredentials:
  - [hostloc_username1, password1]
  - [hostloc_username2, password2]

proxyaddress: "socks5h://127.0.0.1:8080"
```
`usercredentials`下，可以按照相同格式添加多个账户信息。请注意config.yaml文件的缩进。

`proxyaddress`为可选项，不需要代理访问的话，可以删除此行，或者在此行开头添加`#`注释掉此行使其无效。

## 3. 运行
### 3.1 运行说明
### 3.1.a （推荐）（方式一）虚拟环境下运行
根据1.2.a，安装的所有依赖模块都在虚拟环境中，因此此处注意需要在**虚拟环境下运行**。

(在 `hostloc_getPoints`目录下，执行了 `.\.venv\Scripts\Activate.ps1`之后)
```
# 已经执行过：.\.venv\Scripts\Activate.ps1 进入venv虚拟环境
python -m hostlocautogetpoints
```
#### 3.1.a.2（可选）退出虚拟环境
如果需要退出**虚拟环境**，在 `hostloc_getPoints`目录下，执行过`.\.venv\Scripts\Activate.ps1`之后，请使用下述命令。
```
deactivate
```

### 3.1.b （方式二）（全局安装依赖模块）单python文件+config.yaml直接运行
单`python`文件+`config.yaml`配置文件运行，需要安装所需依赖模块，`config.yaml`需要放置在当前目录下。
```
# 进入项目的主文件夹下
cd hostloc_getPoints

# 如果不使用虚拟环境，需要安装相应模块。见步骤1.2.b，具体模块详见requirements.txt文件
# 确保当前工作目录下已放置`config.yaml`
python .\hostlocautogetpoints\hostloc_auto_get_points.py
```

## 4. 任务列表
检验CC机制
