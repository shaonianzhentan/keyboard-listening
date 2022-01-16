# ha-keyboard
键盘监听

## 安装依赖
```bash
pip3 install pyyaml paho-mqtt keyboard
```

```bash
pip install --upgrade setuptools
```

启动
```bash
python3 kb.py
```

开机启动
```bash
sudo nano /etc/systemd/system/ha_keyboard.service

# 启动服务
sudo systemctl start ha_keyboard

sudo systemctl enable ha_keyboard

sudo systemctl restart ha_keyboard

sudo systemctl status ha_keyboard
```

```
[Unit]
Description=ha-keyboard
After=network-online.target

[Service]
Type=simple
ExecStart=/usr/bin/python3 /root/git/ha-keyboard/kb.py
WorkingDirectory=/root/git/ha-keyboard/
RestartSec=15
Restart=always

[Install]
WantedBy=multi-user.target
```

## 日志

```yaml
service: logger.set_level
data:
  homeassistant.components.mqtt: debug
```

```yaml
service: logger.set_level
data:
  homeassistant.components.mqtt: warn
```