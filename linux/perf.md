perf record -F 99 -p <进程ID> -g -- sleep 30
-F 99：设置采样频率为每秒 99 次。
-p <进程ID>：指定要监控的进程 ID。
-g：启用调用栈收集。
sleep 30：让 perf 在 30 秒内持续采样

监控特定进程：
perf record -p 1234 -g -- sleep 30

监控特定程序：
perf record -g -- ./my_program

监控整个系统：
perf record -a -g -- sleep 10

指定采样频率
perf record -F 99 -g -- ./my_program


监控特定事件:
perf record -e instructions -e cache-references -g -- ./my_program

perf script -i perf.data | ./FlameGraph/stackcollapse-perf.pl | ./FlameGraph/flamegraph.pl > perf.svg
