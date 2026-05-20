# Kill-appium-script-macOS
```
cat << 'EOF' > ~/kill_appium.sh
#!/bin/bash

PORT=4723

# Find PID of the process running on port 4723
PIDS=$(lsof -t -i:$PORT | xargs)

# Color codes
RED='\033[0;31m'
GREEN='\033[0;32m'
YELLOW='\033[0;33m'
NC='\033[0m'

if [ -z "$PIDS" ]; then
    printf "${RED} No process found running on port %s.${NC}\n" "$PORT"
else
    printf "${YELLOW} Found process(es) on port %s (PID: %s). Killing...${NC}\n" "$PORT" "$PIDS"
    kill -9 $PIDS
    printf "${GREEN} Done! Port %s is now free.${NC}\n" "$PORT"
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
