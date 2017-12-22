## Day 4 - 安裝 k8s

### 本日共賞

* 安裝 VirtualBox
* 安裝 kubectl
* 安裝 minikube

### 希望你知道

* [k8s 安裝須知](https://ithelp.ithome.com.tw/articles/10192448)

<br/>

今天要安裝 k8s 需要的工具包括 [VirtualBox](https://www.virtualbox.org/), [kubectl](https://kubernetes.io/docs/reference/kubectl/overview/) 與 [minikube](https://github.com/kubernetes/minikube) 在 `Linux`, `Mac OS` 與 `Windows` 上。

#### 安裝 VirtualBox

`Linux`：執行下列指令

```bash
$ sudo apt-get install virtualbox
```

<br/>

`Mac OS`：

在 Mac 中安裝 VirtualBox 請到[這裡下載 .dmg 檔](http://download.virtualbox.org/virtualbox/5.1.22/VirtualBox-5.1.22-115126-OSX.dmg)並安裝

> 安裝有問題嗎？
> 
> 可以參考[官方網站建議的安裝方式](https://www.virtualbox.org/wiki/Downloads)

<br/>

`Windows`：下載 [VirtualBox](http://download.virtualbox.org/virtualbox/5.1.22/VirtualBox-5.1.22-115126-Win.exe) 並安裝


<br/>

#### 安裝 kubectl

`Linux`

**步驟一** 下載 kubectl binary

> 這裡利用 `curl` 抓的 `stable.txt` 的內容，即官方發佈的最新穩定版本，如果需要安裝特定版本，請修改這裡。

```bash
$ curl -LO https://storage.googleapis.com/kubernetes-release/release/$(curl -s https://storage.googleapis.com/kubernetes-release/release/stable.txt)/bin/linux/amd64/kubectl
```

>curl
>
>如果系統內沒有 curl，可透過下列指令安裝
>
>```bash
>$ sudo apt-get install curl
>```

**步驟二** 增加 kubectl 可執行權限

```bash
$ chmod +x ./kubectl
```

**步驟三** 將 kubectl 放到可執行位置 (PATH) 下

```bash
$ sudo mv ./kubectl /usr/local/bin/kubectl
```
>請確認 kubectl 被放到可執行位置底下以方便存取

<br/>

`Mac OS`


**步驟一** 下載 kubectl binary

```bash
$ curl -LO https://storage.googleapis.com/kubernetes-release/release/$(curl -s https://storage.googleapis.com/kubernetes-release/release/stable.txt)/bin/darwin/amd64/kubectl
```

> 請注意，雖然看起來很像，但是這裡的下載位置跟 linux 版的不同喔！

**步驟二** 增加 kubectl 可執行權限

```bash
$ chmod +x ./kubectl
```

**步驟三** 將 kubectl 放到可執行位置 (PATH) 下

```bash
$ sudo mv ./kubectl /usr/local/bin/kubectl
```

>請確認 kubectl 被放到可執行位置底下以方便存取

`其他安裝方法`

在 Mac OS 中可以利用 brew 安裝 kubectl，指令如下

```bash
$ brew install kubectl
```

>如需要更詳細的安裝說明可以參考 [官方安裝說明](https://kubernetes.io/docs/tasks/tools/install-kubectl/)

`Windows`：下載 [kubectl.exe](https://storage.googleapis.com/kubernetes-release/release/v1.6.3/bin/windows/amd64/kubectl.exe) 並放到可執行目錄下

<br/>

安裝完成後，可用下列指令確認 kubectl 版本

```bash
$ kubectl version
Client Version: version.Info{Major:"1", Minor:"8", GitVersion:"v1.8.4", GitCommit:"9befc2b8928a9426501d3bf62f72849d5cbcd5a3", GitTreeState:"clean", BuildDate:"2017-11-20T05:28:34Z", GoVersion:"go1.8.3", Compiler:"gc", Platform:"linux/amd64"}
The connection to the server localhost:8080 was refused - did you specify the right host or port?
```

此次鐵人賽使用的 kubectl 版本為 v1.8.4

>由於還沒有設定要連到哪個 k8s 叢集，所以這裡會有 "localhost:8080 was refused ..." 的錯誤訊息，可以先忽略它。

<br/>

#### 安裝 minikube

`Linux`

**步驟一** 下載 minikube

> 這裡示範抓的是 `latest` 版本，即最新版。如果需要指定請修改下載網址，例如下載 v0.24.1，請將 `latest` 換成指定的版本號
> 
> ```bash
> $ curl -Lo minikube https://storage.googleapis.com/minikube/releases/v0.24.1/minikube-linux-amd64 
>


```bash
$ curl -Lo minikube https://storage.googleapis.com/minikube/releases/latest/minikube-linux-amd64
```


>此次鐵人賽使用的 minikube 版本為 v0.24.1
>
>minikube 版本資訊可參考 [minkube 官方說明](https://github.com/kubernetes/minikube/releases)

**步驟二** 增加 minikube 可執行權限

```bash
$ chmod +x ./minikube
```

**步驟三** 將 kubectl 放到可執行位置 (PATH) 下

```bash
$ sudo mv ./minikube /usr/local/bin/minikube
```

`Mac OS`

**步驟一** 下載 minikube

```bash
$ curl -Lo minikube https://storage.googleapis.com/minikube/releases/latest/minikube-darwin-amd64
```

**步驟二** 增加 minikube 可執行權限

```bash
$ chmod +x ./minikube
```

**步驟三** 將 kubectl 放到可執行位置 (PATH) 下

```bash
$ sudo mv ./minikube /usr/local/bin/minikube
```

`Windows`：下載 [minikube](https://storage.googleapis.com/minikube/releases/latest/minikube-windows-amd64.exe) 並放到可執行目錄下。另外，請自行將成稱改成 `minikube.exe`。


<br/>

安裝完成後，用下列指令確認 minikube 版本

```bash
$ minikube version
minikube version: v0.24.1
```

### 小結
今天的內容有點雜亂，以下整理今日重點

* 如何在 Linux 與 Mac OS 中安裝 VirtualBox, kubectl 與 minikube
* 本次鐵人賽使用的 kubectl 版本為 v1.8.4
* 本次鐵人賽使用的 minikube 版本為 v0.24.1

本文同步發表於 [https://jlptf.github.io/ironman2018-day4/](https://jlptf.github.io/ironman2018-day4/)