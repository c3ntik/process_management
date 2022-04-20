# process_management
Управление процессами 

реализовать 2 конкурирующих процесса по IO. пробовать запустить с разными ionice
Результат ДЗ - скрипт запускающий 2 процесса с разными ionice, замеряющий время выполнения и лог консоли

# Запускаем одновременно 2 команды с разным приоритетом

`time nice -n -20 su -c "dd if=/dev/zero of=/tmp/test.img bs=2000 count=1M" &  time nice -n 19 su -c "dd if=/dev/zero of=/tmp/test2.img bs=2000 count=1M" &`

# Результат

```
[1] 3761
[2] 3762
[root@nfss ~]# 1048576+0 records in
1048576+0 records out
2097152000 bytes (2.1 GB) copied, 4.42383 s, 474 MB/s

real    0m4.452s
user    0m0.316s
sys     0m2.712s
1048576+0 records in
1048576+0 records out
2097152000 bytes (2.1 GB) copied, 7.15771 s, 293 MB/s

real    0m7.850s
user    0m0.340s
sys     0m2.545s
^C
[1]-  Done                    time nice -n -20 su -c "dd if=/dev/zero of=/tmp/test.img bs=2000 count=1M"
[2]+  Done                    time nice -n 19 su -c "dd if=/dev/zero of=/tmp/test2.img bs=2000 count=1M"
```
