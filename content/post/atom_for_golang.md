+++
date = "2016-04-25T00:54:22+09:00"
draft = false
title = "atom_for_golang"

+++

# Tips Atom editer for golang

## linter

### install atom packages

```
apm install go-plus
```

このpackagesがかなりすごい。めっちゃオススメです。
go-plusを入れると自動的に下記パッケージも入る。linter, gofmt等はsaveしたタイミングで走る。

```
╰─$ apm list | grep go
├── go-to-line@0.30.0
├── language-go@0.42.0
├── autocomplete-go@1.0.6
├── builder-go@1.0.0
├── go-config@1.1.4
├── go-get@1.0.3
├── go-plus@4.1.0
├── gofmt@1.1.6
├── gometalinter-linter@1.1.0
├── gorename@1.0.2
├── navigator-godef@1.0.3
├── tester-go@1.0.4
```

### Golangの開発支援ツール群（基本go-plusから呼び出される）
go-plusで使ってるライブラリーをインストールする。
入れ忘れてもgo-configのパッケージが検知してgo-getパッケージを使って自動で入れてくれる。

```
$ go get -v github.com/alecthomas/gometalinter
$ go get -v golang.org/x/tools/cmd/gorename
$ go get -v github.com/nsf/gocode
$ go get -v github.com/rogpeppe/godef
$ go get -v golang.org/x/tools/cmd/oracle
```

### Glide: Vendor Package Management for Golang

golangのvendoringにglideを使ってる場合は、gometalinter起動時のパラメータに"--vendor"をつける。
環境変数（GO15VENDOREXPERIMENT）の値を見てvendor配下を参照するようになる。

**注意**

preferencesのsettingsからもgometalinterのパラメータ設定することはできるけど、config.csonが壊れる。
ちゃんと反映されないから自分でconfig.csonををいじる方が無難

```~/.atom/config.cson
"gometalinter-linter": {
  "args": [
    "--vendor"
  ]
}
```
