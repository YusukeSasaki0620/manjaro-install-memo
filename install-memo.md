初期構築手順を備忘がてらメモ
# 環境
- core i7 3930k
- メモリ
- ssh
- manjaro i3 21.0

# インストール
- USBメディア作成
- UGIでポチポチインストール
  - パーティション全削除新規

(省略)

# パッケージ系初期設定
## JPサーバ見るように
```sh
sudo pacman-mirrors --geoip
```

## パッケージ更新
```sh
sudo pacman -Syu
```

## ググれないと何もできないのでブラウザ入れる
### firefox
```
sudo pacman -S firefox
```
### vivaldi
```
sudo pacman -S vivaldi
```

## 日本語化
### mozc入れる
```
sudo pacman -S fcitx-im
```

### 設定入れる
~/.xprofileに以下を記述
```
export LANG="ja_JP.UTF-8"
export XMODIFIERS="@im=fcitx"
export XMODIFIER="@im=fcitx"
export GTK_IM_MODULE=fcitx
export QT_IM_MODULE=fcitx
export DefaultIMModule=fcitx
```

~/.i3/configに以下を記述
```
#Autostart applications
exec --no-startup-id fcitx
```
再起動


## メモ用VScodeいれる

```
yay -S visual-studio-code-bin
```


## デフォルトシェルをzshに変更
```
chsh -s $(which zsh)
```
ログオフ->ログオン


## キーボードカスタマイズ
操作性が死にすぎて発狂しそうなので早々に
### 日本語・英語切り替え
```
fcitx-configtool
```
GUIが入ってないと言われるのでいれる

```
yay -S fcitx-configtool
```

日本語が化けるので日本語フォント入れる
```
yay -S adobe-source-han-sans-jp-fonts
```
再起動

mozcツール->設定ツール
一般->キー設定->キー設定の選択->編集
Henkan/Muhenkan
=>
IME有効/IME無効


## 日本語

$ sudo pacman -S xdg-user-dirs-gtk
$ LANG=C xdg-user-dirs-gtk-update#＃

$ yay google-chrome-stable
