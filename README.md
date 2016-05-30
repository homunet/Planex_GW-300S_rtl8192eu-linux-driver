#GW-300S Katana用拡張

Mange(Magnus Bergmark)さんのLinux最新カーネル用ドライバをGW-300S用に修正を加えました。
各ドングルで共通であるコードををGW-300S用に書き換えているので、Masterとは互換性がありません。

公式とMangeさんの変更の詳細は元のレポジトリを参照してください。
https://github.com/Mange/rtl8192eu-linux-driver

# Raspbery Piでのインストール方法

詳細はInterface本誌をご参照願います(夏頃刊行予定)。

```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get install build-essential git bc

git clone https://github.com/homunet/Planex_GW-300S_rtl8192eu-linux-driver.git
cd Planex_GW-300S_rtl8192eu-linux-driver/

wget https://raw.githubusercontent.com/notro/rpi-source/master/rpi-source 
chmod +x rpi-source 
sudo mv rpi-source   /usr/bin/
sudo rpi-source -q --tag-update
sudo rpi-source --skip-gcc

sudo make ARCH=arm
sudo make ARCH=arm install
sudo bash -c 'echo "options 8192eu rtw_power_mgnt=0 rtw_enusbss=0" > /etc/modprobe.d/8192eu.conf'
sudo modprobe 8192eu
```

# hostapdとの連携

公式バイナリでは動きませんでしたので、realtek版のバイナリと差し替えてください。

