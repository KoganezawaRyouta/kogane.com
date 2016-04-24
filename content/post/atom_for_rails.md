+++
date = "2016-04-25T00:32:22+09:00"
draft = false
title = "atom_for_rails"

+++

# Tips Atom editer for rails

## linter

### install
```
$ rbenv exec gem install rubocop
$ rbenv exec gem install haml-lint
$ apm install linter-rubocop
$ apm install linter-haml
$ apm install linter-ruby
```

### Settings
```~/.atom/config.cson
'linter-rubocop':
  'executablePath': rubocopのパス（rbenv which rubocop）
'linter-haml':
  'copyRubocopYml': true
  'hamlLintExecutablePath': haml-lintのパス（rbenv which haml-lint）
```

### yamlのloadでinvalid byte sequenceになる場合
下記を追加

```~/.atom/packages/linter-rubocop/index.coffee
process.env.LANG = 'ja_JP.UTF-8'
```

## rubocop-auto-correct(rubocop -aの自動化)

### install
```
$ apm install rubocop-auto-correct
```

## Haml Syntax highlighting

### install
```
$ apm install language-haml
```
