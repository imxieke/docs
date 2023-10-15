## PHP Extensions

### apcu

- apcu.ini

```ini
[apcu]
extension=apcu.so
apc.enabled=1
apc.shm_size=32M
apc.enable_cli=1
```

- opcache.ini
```ini
[Zend Opcache]
zend_extension="opcache.so"
opcache.memory_consumption=128
opcache.interned_strings_buffer=8
opcache.max_accelerated_files=4000
opcache.revalidate_freq=60
opcache.fast_shutdown=1
opcache.enable_cli=1

; for php 8+
opcache.jit = 1255
opcache.jit_buffer_size = 64M
```

- xcache.ini
```ini
[xcache-common]
extension = xcache.so

[xcache.admin]
xcache.admin.enable_auth = On
xcache.admin.user = "dockenv"
;run: echo -n "yourpassword" |md5sum |awk '{print $1}' to get md5 password
xcache.admin.pass = "dockenv"

[xcache]
xcache.shm_scheme =        "mmap"
xcache.size  =               20M
; set to cpu count (cat /proc/cpuinfo |grep -c processor)
xcache.count =                 ${cpu_count}
xcache.slots =                8K
xcache.ttl   =                 0
xcache.gc_interval =           0
xcache.var_size  =            4M
xcache.var_count =             1
xcache.var_slots =            8K
xcache.var_ttl   =             0
xcache.var_maxttl   =          0
xcache.var_gc_interval =     300
xcache.readonly_protection = Off
; for *nix, xcache.mmap_path is a file path, not directory. (auto create/overwrite)
; Use something like "/tmp/xcache" instead of "/dev/*" if you want to turn on ReadonlyProtection
; different process group of php won't share the same /tmp/xcache
xcache.mmap_path =    "/tmp/php-xcache"
xcache.coredump_directory =   ""
xcache.experimental =        Off
xcache.cacher =               On
xcache.stat   =               On
xcache.optimizer =           Off

[xcache.coverager]
; enabling this feature will impact performance
; enable only if xcache.coverager == On && xcache.coveragedump_directory == "non-empty-value"
; enable coverage data collecting and xcache_coverager_start/stop/get/clean() functions
xcache.coverager =          Off
xcache.coveragedump_directory = ""
```