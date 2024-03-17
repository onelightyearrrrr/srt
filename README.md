# srt
```
apt update
apt upgrade
sudo -i
apt install libinput-dev make cmake tcl openssl zlib1g-dev gcc perl net-tools nano ssh git zip unzip tclsh pkg-config cmake libssl-dev build-essential -y

git clone https://github.com/Haivision/srt.git
cd srt
./configure
make
git checkout v1.4.3 && ./configure && make -j8 && make install
cd ../

git clone https://gitlab.com/mattwb65/srt-live-server.git
cd srt-live-server
make -j8

mv sls.conf sls.bak
pico sls.conf


ufw allow 8181/udp
ufw allow 8181/tcp
ufw allow 8282/udp
ufw allow 8282/tcp
ufw allow 22/tcp
ufw allow 22/udp


cd bin
ldconfig
./sls -c ../sls.conf
```
