[en](./README.md)

# DotNet6.Install.HelloWorld

　ラズパイにdotnet6をインストールしHelloWorldする。

<!--

# デモ

* [demo](https://ytyaru.github.io/CSharp.DotNet6.Install.HelloWorld.20220926104104/)

![img](https://github.com/ytyaru/CSharp.DotNet6.Install.HelloWorld.20220926104104/blob/master/doc/0.png?raw=true)

# 特徴

* セールスポイント

-->

# 開発環境

* <time datetime="2022-09-26T10:40:35+0900">2022-09-26</time>
* [Raspbierry Pi](https://ja.wikipedia.org/wiki/Raspberry_Pi) 4 Model B Rev 1.2
* [Raspberry Pi OS](https://ja.wikipedia.org/wiki/Raspbian) buster 10.0 2020-08-20 <small>[setup](http://ytyaru.hatenablog.com/entry/2020/10/06/111111)</small>
* bash 5.0.3(1)-release
* [dotnet 6][]
    * [dotnet 6.0.401][]

[dotnet 6]:https://dotnet.microsoft.com/ja-jp/download/dotnet/6.0
[dotnet 6.0.401]:https://download.visualstudio.microsoft.com/download/pr/451f282f-dd26-4acd-9395-36cc3a9758e4/f5399d2ebced2ad9640db6283aa9d714/dotnet-sdk-6.0.401-linux-arm.tar.gz


```sh
$ uname -a
Linux raspberrypi 5.10.103-v7l+ #1529 SMP Tue Mar 8 12:24:00 GMT 2022 armv7l GNU/Linux
```

# インストール

　[dotnet 6][]から最新版を取得する。執筆時点での最新版は[dotnet 6.0.401][]であり以下のコマンドで取得できる。

```sh
NAME=dotnet-sdk-6.0.401-linux-arm.tar.gz
wget https://download.visualstudio.microsoft.com/download/pr/451f282f-dd26-4acd-9395-36cc3a9758e4/f5399d2ebced2ad9640db6283aa9d714/$NAME
tar -zxvf $NAME
```

~/.bashrc
```sh
export PATH=$PATH:$HOME/some/.NETCore/6.0.401
```

　または以下でもよい。

```bash
git clone https://github.com/ytyaru/CSharp.DotNet6.Install.HelloWorld.20220926104104
cd CSharp.DotNet6.Install.HelloWorld.20220926104104
./install.sh
```

# 使い方

```bash
git clone https://github.com/ytyaru/CSharp.DotNet6.Install.HelloWorld.20220926104104
cd CSharp.DotNet6.Install.HelloWorld.20220926104104
./info.sh
./run.sh
```

# 著者

　ytyaru

* [![github](http://www.google.com/s2/favicons?domain=github.com)](https://github.com/ytyaru "github")
* [![hatena](http://www.google.com/s2/favicons?domain=www.hatena.ne.jp)](http://ytyaru.hatenablog.com/ytyaru "hatena")
* [![twitter](http://www.google.com/s2/favicons?domain=twitter.com)](https://twitter.com/ytyaru1 "twitter")
* [![mastodon](http://www.google.com/s2/favicons?domain=mstdn.jp)](https://mstdn.jp/web/accounts/233143 "mastdon")

# ライセンス

　このソフトウェアはCC0ライセンスである。

[![CC0](http://i.creativecommons.org/p/zero/1.0/88x31.png "CC0")](http://creativecommons.org/publicdomain/zero/1.0/deed.ja)

