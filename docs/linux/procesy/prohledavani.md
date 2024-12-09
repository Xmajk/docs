```
ps aux | grep 'node' | grep -- '--processMark=serverBot' | grep -v 'grep' | awk '{print $2}'
```