# Kill-appium-script-macOS
```
cat << 'EOF' > ~/kill_appium.sh
#!/bin/bash

PORT=4723

# Find PID of the process running on port 4723
PID=$(lsof -t -i:$PORT)

if [ -z "$PID" ]; then
    echo " No process found running on port $PORT."
else
    echo " Found process running on port $PORT (PID: $PID). Killing..."
    kill -9 $PID
    echo " Done! Port $PORT is now free."
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
