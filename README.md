# alc/weblio on command-line

英和及び和英の翻訳コマンドです。
command-lineでalcを用いた英和辞典や和英辞典を使用したいというモチベーションで書きました。
alcの検索結果の部分を切り取って表示しています。
画面内に収まって欲しかったので例も切り取っています。
itermなどで半透明にしてhot keyを設定しておくと翻訳や論文を読むのが捗ります。

## 下準備

### w3mをインストール

* macportsを使用する場合

```zsh
$ sudo port selfupdate
$ sudo port install w3m
```

* brewを使用する場合

```zsh
$ brew update
$ brew install w3m
```

### git cloneしPATHを通す

```zsh
$ git clone https://github.com/tocci3/dict.git
$ cd dict
$ prefix=/usr/local
$ cp -p alc $prefix/bin/ # コマンドとして使用可能に
$ cp -p weblio $prefix/bin/ # コマンドとして使用可能に
$ sudo mkdir -pv $prefix/share/zsh/site-functions # fpathの通っている場所へ
$ sudo ln -si _alc $prefix/share/zsh/site-functions/ # 補完が効くように
```

## 使用例

### 標準

```zsh
$ alc git

    【名】
        〈英話〉ばか、間抜｛まぬ｝け、くそったれ（野郎｛やろう｝）
    【発音】gít、【＠】ギットゥ
```

### 熟語は`space`でも`+`でも検索可能

```zsh
$ alc pros+and+cons

    賛否両論｛さんぴりょうろん｝、良い点と悪い点
    ・Let's discuss the pros and cons of the proposal. : その提案のプラス面とマ
    イナス面について話し合おう。
    ・The pros and cons are batted back and forth. : 賛否両論が入り乱れている。
```

### スペルミスをした場合

```zsh
$ alc ggit
failed
```

## オプション

### -h ---> show help

```zsh
$ alc -h
Usage: alc [-h] [-i word] [-o word] [-v]
```

### -i ---> interactive mode

```zsh
$ alc -i git

    【名】
        〈英話〉ばか、間抜｛まぬ｝け、くそったれ（野郎｛やろう｝）
    【発音】gít、【＠】ギットゥ

alc> vim

    【名】
        精力｛せいりょく｝、活力｛かつりょく｝
    【発音】vím、【＠】ヴィム

alc> # ^D(EOF)を入力して終了
```

### -o ---> open browser

```zsh
$ alc -o git
```

### -v ---> check version

```zsh
$ alc -v
1.0.0
```

## ToDo

* -iモードを終了する際にEOFではなくReturnでも終了してしまうbugをどの方向に修正するか
* openの一般化
