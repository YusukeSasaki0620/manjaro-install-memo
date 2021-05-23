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


##　メモ用VScodeいれる

```
yay -S visual-studio-code-bin
```

$ sudo pacman -S xdg-user-dirs-gtk
$ LANG=C xdg-user-dirs-gtk-update#＃

$ yay google-chrome-stable