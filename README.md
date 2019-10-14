This project reproduce lldb (lldb-1100.0.28.19 ) issue with
macOS (Catalina 10.15)
(present in older version of macOS and lldb)
 Clion

Problem:
1. lldb inside clion doesn't work

```
Process finished with exit code 1
```
2. lldb from terminal works well


lldb from terminal works ok
To run fuzzy tests on macOS

Install llvm
```bash
> brew install llvm
```

Set compiller to llvm clang
Clion > Preferences -> Build Execution -> Toolchains
set "c compiler" to
```bash
/usr/local/opt/llvm/bin/clang
```


