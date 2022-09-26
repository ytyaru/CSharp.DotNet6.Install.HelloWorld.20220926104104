# ラズパイにdotnet6をインストールしHelloWorldする

　15分くらいでできた。

<!-- more -->

# 成果物

* [リポジトリ][]

[リポジトリ]:https://github.com/ytyaru/CSharp.DotNet6.Install.HelloWorld.20220926104104

# 目次

1. [インストールする](#install)
	1. [ダウンロードする](#download)
	2. [展開する](#expand)
	3. [パスを通す](#path)
2. [動作確認する](#check)
	1. [バージョン確認する](#version)
	2. [ヘルプ確認する](#help)
	3. [プロジェクト種別を確認する](#new-list)
3. [HelloWorldする](#hello-world)
	1. [プロジェクトを作る](#new-project)
	2. [コードを書く](#code)
	3. [実行する](#run)

<a id="install"></a>

# [インストールする](#install)

<a id="download"></a>

## [ダウンロードする](#download)

　[dotnet6][]の`バイナリ`から`Arm32`のリンクをクリックする。執筆時点では`6.0.401`だった。以下コマンドでも取得できる。

```sh
wget https://download.visualstudio.microsoft.com/download/pr/451f282f-dd26-4acd-9395-36cc3a9758e4/f5399d2ebced2ad9640db6283aa9d714/dotnet-sdk-6.0.401-linux-arm.tar.gz
```

<a id="expand"></a>

## [展開する](#expand)

　これを展開する。コマンドは以下。

```sh
NAME=dotnet-sdk-6.0.401-linux-arm.tar.gz
tar -zxvf $NAME
```

　出力先を指定するなら`-C`オプションをつける。

```sh
NAME=dotnet-sdk-6.0.401-linux-arm.tar.gz
OUT=$HOME/some/.NETCore/6.0.401
tar -zxvf $NAME -C $OUT
```

<a id="path"></a>

## [パスを通す](#path)

　環境変数`PATH`に.NET6のルートディレクトリをセットする。

```sh
export PATH=$PATH:$HOME/some/.NETCore/6.0.401
```

　もしbashを起動するたび自動でパスを通したいなら`/home/ユーザ名/.bashrc`ファイルに上記コードを追記すること。

<a id="check"></a>

# [動作確認する](#check)

<a id="version"></a>

## [バージョン確認する](#version)

```sh
$ dotnet --version
6.0.401
```

<a id="help"></a>

## [ヘルプ確認する](#help)

```sh
$ dotnet --help
使用法: dotnet [runtime-options] [path-to-application] [arguments]

.NET アプリケーションを実行します。

runtime-options:
  --additionalprobingpath <path>   調査ポリシーと調査対象アセンブリを含むパス。
  --additional-deps <path>         追加の deps.json ファイルへのパス。
  --depsfile                       <application>.deps.json ファイルへのパス。
  --fx-version <version>           アプリケーションを実行するために使用するインストール済み Shared Framework のバージョン。
  --roll-forward <setting>         フレームワーク バージョン (LatestPatch、Minor、LatestMinor、Major、LatestMajor、Disable) にロールフォワードします。
  --runtimeconfig                  <application>.runtimeconfig.json ファイルへのパス。

path-to-application:
  実行するアプリケーション .dll ファイルへのパス。

使用法: dotnet [sdk-options] [command] [command-options] [arguments]

.NET SDK コマンドを実行します。

sdk-options:
  -d|--diagnostics  診断出力を有効にします。
  -h|--help         コマンド ラインのヘルプを表示します。
  --info            .NET 情報を表示します。
  --list-runtimes   インストール済みランタイムを表示します。
  --list-sdks       インストール済み SDK を表示します。
  --version         使用中の .NET SDK バージョンを表示します。

SDK コマンド:
  add               .NET プロジェクトにパッケージまたは参照を追加します。
  build             .NET プロジェクトをビルドします。
  build-server      ビルドによって開始されたサーバーとやり取りします。
  clean             .NET プロジェクトのビルド出力をクリーンします。
  format            プロジェクトやソリューションにスタイルのユーザー設定を適用します。
  help              コマンド ラインのヘルプを表示します。
  list              .NET プロジェクトのプロジェクト参照を一覧表示します。
  msbuild           Microsoft Build Engine (MSBuild) コマンドを実行します。
  new               新しい .NET プロジェクトまたはファイルを作成します。
  nuget             追加の NuGet コマンドを提供します。
  pack              NuGet パッケージを作成します。
  publish           .NET プロジェクトを配置のために公開します。
  remove            .NET プロジェクトからパッケージまたは参照を削除します。
  restore           .NET プロジェクトに指定されている依存関係を復元します。
  run               .NET プロジェクトの出力をビルドして実行します。
  sdk               .NET SDK のインストールを管理します。
  sln               Visual Studio ソリューション ファイルを変更します。
  store             指定されたアセンブリをランタイム パッケージ ストアに格納します。
  test              .NET プロジェクトに指定されているテスト ランナーを使用して、単体テストを実行します。
  tool              .NET のエクスペリエンスを向上するツールをインストールまたは管理します。
  vstest            Microsoft Test Engine (VSTest) コマンドを実行します。
  workload          オプションのワークロードを管理します。

バンドルされたツールからの追加コマンド:
  dev-certs         開発証明書を作成し、管理します。
  fsi               F# Interactive を開始するか、F# スクリプトを実行します。
  sql-cache         SQL Server cache command-line tools.
  user-secrets      開発ユーザーのシークレットを管理します。
  watch             ファイルが変更されたときにコマンドを実行するファイル ウォッチャーを起動します。

コマンドに関する詳細情報については、'dotnet [command] --help' を実行します。
```

<a id="new-list"></a>

## [プロジェクト種別を確認する](#new-list)

```sh
$ dotnet new --list
これらのテンプレートは、入力:  と一致しました

テンプレート名                                短い名前        言語        タグ                      
--------------------------------------------  --------------  ----------  --------------------------
ASP.NET Core Empty                            web             [C#],F#     Web/Empty                 
ASP.NET Core gRPC Service                     grpc            [C#]        Web/gRPC                  
ASP.NET Core Web API                          webapi          [C#],F#     Web/WebAPI                
ASP.NET Core Web App                          webapp,razor    [C#]        Web/MVC/Razor Pages       
ASP.NET Core Web App (Model-View-Controller)  mvc             [C#],F#     Web/MVC                   
ASP.NET Core with Angular                     angular         [C#]        Web/MVC/SPA               
ASP.NET Core with React.js                    react           [C#]        Web/MVC/SPA               
Blazor Server App                             blazorserver    [C#]        Web/Blazor                
Blazor WebAssembly App                        blazorwasm      [C#]        Web/Blazor/WebAssembly/PWA
dotnet gitignore ファイル                     gitignore                   Config                    
dotnet ローカル ツール マニフェスト ファイル  tool-manifest               Config                    
EditorConfig ファイル                         editorconfig                Config                    
global.json ファイル                          globaljson                  Config                    
MSTest Test Project                           mstest          [C#],F#,VB  Test/MSTest               
MVC ViewImports                               viewimports     [C#]        Web/ASP.NET               
MVC ViewStart                                 viewstart       [C#]        Web/ASP.NET               
NuGet Config                                  nugetconfig                 Config                    
NUnit 3 Test Item                             nunit-test      [C#],F#,VB  Test/NUnit                
NUnit 3 Test Project                          nunit           [C#],F#,VB  Test/NUnit                
Protocol Buffer File                          proto                       Web/gRPC                  
Razor Class Library                           razorclasslib   [C#]        Web/Razor/Library         
Razor Component                               razorcomponent  [C#]        Web/ASP.NET               
Razor Page                                    page            [C#]        Web/ASP.NET               
Web 構成                                      webconfig                   Config                    
Worker Service                                worker          [C#],F#     Common/Worker/Web         
xUnit Test Project                            xunit           [C#],F#,VB  Test/xUnit                
クラス ライブラリ                             classlib        [C#],F#,VB  Common/Library            
コンソール アプリ                             console         [C#],F#,VB  Common/Console            
ソリューション ファイル                       sln,solution                Solution                  
```

　`dotnet`コマンドが作成できるプロジェクト形式一覧。

　素人には何がなんだかさっぱりわからない。

　今回は単純な`console`アプリを作成したい。

<a id="hello-world"></a>

# [HelloWorldする](#hello-world)

* [.NET チュートリアル - 5 分でできる Hello World][]

<a id="new-project"></a>

## [プロジェクトを作る](#new-project)

```sh
dotnet new console -o MyApp -f net6.0
```

　カレントディレクトリ直下に`MyApp`ディレクトリが作成される。

```sh
cd MyApp
```
```sh
$ tree
.
├── MyApp.csproj
├── Program.cs
└── obj
    ├── MyApp.csproj.nuget.dgspec.json
    ├── MyApp.csproj.nuget.g.props
    ├── MyApp.csproj.nuget.g.targets
    ├── project.assets.json
    └── project.nuget.cache
```

<a id="code"></a>

## [コードを書く](#code)

　`Program.cs`がエントリポイントとなる。

```sh
vim Program.cs
```

　すでに以下のようにコードが書かれていた。

```csharp
// See https://aka.ms/new-console-template for more information
Console.WriteLine("Hello, World!");
```

<a id="run"></a>

## [実行する](#run)

```sh
$ dotnet run
Hello, World!
```

　時間をはかると20秒くらいかかった。昔.NET3や5は50秒くらいかかってた気がするのでだいぶ速くなった。

```sh
$ time dotnet run
Hello, World!

real	0m22.328s
user	0m18.891s
sys	0m1.402s
```

# 情報源

* [dotnet6][]
* [.NET チュートリアル - 5 分でできる Hello World][]

[dotnet6]:https://dotnet.microsoft.com/ja-jp/download/dotnet/6.0
[.NET チュートリアル - 5 分でできる Hello World]:https://dotnet.microsoft.com/ja-jp/learn/dotnet/hello-world-tutorial/intro

