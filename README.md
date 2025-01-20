# hostloc_getPoints
HOSTLOC 每日获取积分脚本

## 前置条件
本地需要有`python3`运行环境

## 1. 安装
### 1.1 克隆项目
(可能需要代理软件才能正常访问，请自行搜索git代理方案)
```
git clone https://github.com/seemygesture/hostloc_getPoints.git
```

### 1.2 在虚拟环境venv中安装依赖模块
(可能需要代理软件或者更换pip源才能正常访问，请自行搜索方案)
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

## 2. 填写配置信息
示例配置文件为`config.example.yaml`，复制它，并重命名为`config.yaml`

修改`config.yaml`文件，注意需要保持`yaml`配置文件中相关行的**缩进一致**！

以下为2个账号，并设置代理为socks5h本地代理`127.0.0.1:8080`的参考配置。

注意，如果配置使用：`socks5://127.0.0.1:8080`，则会启用本地的8080端口上的socks5代理，但是DNS解析域名仍可能被污染。
如果配置使用：`socks5h://127.0.0.1:8080`，则会启用本地的8080端口上的socks5代理，并负责域名的DNS解析。

```
usercredentials:
  - [hostloc_username1, password1]
  - [hostloc_username2, password2]

proxyaddress: "socks5h://127.0.0.1:8080"
```
`usercredentials`下，可以按照相同格式添加多个账户信息（注意缩进）。
`proxyaddress`为可选项，不需要代理访问的话，可以删除此行，或者在此行开头添加`#`注释掉此行使其无效。

## 3. 运行
### 3.1 虚拟环境下运行（方式一）
因为安装的所有依赖模块都在虚拟环境中，因此此处注意需要在**虚拟环境下运行**

(在 `hostloc_getPoints`目录下，执行了 `.\.venv\Scripts\Activate.ps1`之后)
```
# 已经执行过：.\.venv\Scripts\Activate.ps1 进入venv虚拟环境
python -m hostlocautogetpoints
```
#### 3.1.1（可选）退出虚拟环境
如果需要退出**虚拟环境**，在 `hostloc_getPoints`目录下，执行过`.\.venv\Scripts\Activate.ps1`之后，请使用下述命令。
```
deactivate
```

### 3.2 单文件直接运行（方式二）
单python文件+`config.yaml`配置文件运行，需要安装所需依赖模块，`config.yml`需要放置在当前目录下
```
# 以 Windows11 的 powershell，使用venv虚拟环境为例

# 进入项目的主文件夹下
cd hostloc_getPoints

# 如果不使用虚拟环境，需要安装requests、curl_cffi等模块。所需模块详见requirements.txt
# 确保当前目录下已放置`config.yml`
python .\hostlocautogetpoints\hostloc_auto_get_points.py
```

## 4. 任务列表
检验当前代码是否能绕过可能存在的CC机制
