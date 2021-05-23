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

### chrome
```
yay google-chrome-stable

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

### TODO
手間なのでファイル書き出しして読み込めるようにしたい
## デュアルディスプレイ対応
### GPUドライバインストール
```
sudo mhwd -a pci nonfree 0300
```
OSインストール時にnonfreeでやたので導入済み
### 設定
sudo nvidia-settings
UGIで設定変更
設定ファイル保存
設定反映
```
ln -s /etc/X11/xorg.conf /etc/X11/xorg.conf.d/80-screen.conf
```
ログオフ->ログオン


## パッケージインストールが遅いので最適化
/etc/makepkg.conf
### 圧縮マルチコア化
```
COMPRESSXZ=(xz -c -z - --threads=0)
```
### コンパイルオプション
```
% grep -m1 -A3 "vendor_id" /proc/cpuinfo
vendor_id	: GenuineIntel
cpu family	: 6
model		: 45
model name	: Intel(R) Core(TM) i7-3930K CPU @ 3.20GHz
```
https://wiki.gentoo.org/wiki/Safe_CFLAGS#Intel
=>
MAKEFLAGSのオプションを-march=sandybridge


はやくなってる、、、か？

## ホーム配下サブディレクトリ英語化
```
yay -S xdg-user-dirs-gtk
LANG=C xdg-user-dirs-gtk-update
```
再起動

できてない、、、
