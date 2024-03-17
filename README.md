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

srt {
    worker_threads 1;
    worker_connections 200;
    http_port 8181;
    cors_header *;
    log_file /dev/stdout;

    server {
        listen 8282;
        latency 2000;
        domain_player play;
        domain_publisher live;
        default_sid live/stream/test1;
        backlog 100;
        idle_streams_timeout 3;

        app {
            app_publisher stream;
            app_player stream;
        }
    }
}

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
