# bash脚本的基本使用

## if结构

```bash
if [ "$NODE_VERSION_MAJOR" -gt "$NODE_VERSION_MAX" ]; then \
    echo "Your node version $NODE_VERSION is too high. Try to use version 10."; \
    nvm use $NODE_VERSION_MAX; \
fi;\
```