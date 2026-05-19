# Kill-appium-script-macOS
```
cat << 'EOF' > ~/kill_appium.sh
#!/bin/bash

PORT=4723

# Находим PID процесса на порту 4723
PID=$(lsof -t -i:$PORT)

if [ -z "$PID" ]; then
    echo " На порту $PORT ничего не запущено."
else
    echo " Найдена запущенная node/appium (PID: $PID). Убиваю..."
    kill -9 $PID
    echo " Done! Порт $PORT свободен."
fi
EOF
```

```
chmod +x ~/kill_appium.sh
```

Make alias:
```
echo "alias kill-appium='~/kill_appium.sh'" >> ~/.zshrc
source ~/.zshrc
```
