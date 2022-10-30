# Only Tengine
Auto install tengine in termius following https://medium.com/@agungsijawir/tengine-download-compile-install-5b7f4fddb941

nginx.service have been replaced by tengine.service

## Snippet code
`apt-get update && apt-get dist-upgrade -y && apt-get install sudo git -y`  
`sudo apt-get install build-essential libpcre3 libpcre3-dev libssl-dev libjemalloc-dev libatomic-ops-dev zlib1g-dev curl -y`  
`git clone --branch master https://github.com/alibaba/tengine /tengine/tengine/`  
`cd /tengine/tengine/`  
`./configure --with-jemalloc --with-libatomic`  
`make`  
`sudo make install`  
`sudo touch /etc/systemd/system/nginx.service`  
`sudo chmod 655 /etc/systemd/system/nginx.service`  
`sudo curl -L -o /etc/systemd/system/tengine.service https://raw.githubusercontent.com/MrMathias154/Snippet_termius_auto/main/tengine/tengine.service`  
`sed -i "s+#pid+pid+g" /usr/local/nginx/conf/nginx.conf`  
`sed -i "s+logs/nginx.pid+/run/nginx.pid+g" /usr/local/nginx/conf/nginx.conf`  
`sudo systemctl daemon-reload`  
`sudo systemctl start tengine.service && sudo systemctl enable tengine.service`  
`curl -I 127.0.0.1`  
`echo "Tengine Installed"`  

## Thanks :D
