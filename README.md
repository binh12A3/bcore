# bcore
core functionalities such as logger, ....


```
/home/btnguyen/Code/btest
├── bcore
|   └── logger
|       ├── logger.cpp
|       └── logger.h
└── btest.cpp
```


```cpp
[btnguyen@hpserver btest]$ ls -ltr
total 4
drwxr-xr-x. 3 root     root      20 Sep 21 09:39 bcore
-rw-rw-r--. 1 btnguyen btnguyen 378 Sep 21 15:08 btest.cpp
[btnguyen@hpserver btest]$ cat btest.cpp
#include "bcore/logger/logger.h"

int main()
{
    Logger::ref().openLogFile("app.log");
    //Logger::ref().setThreadNameForLogging("LOOP");
    //Logger::ref().enableThreadId(true);
    Logger::ref().log("Hello World");
    Logger::ref().log(8080, Logger::ll_info);
    Logger::ref().log(0.1234, Logger::ll_debug);
    Logger::ref().closeLogFile();
    return 0;
}
[btnguyen@hpserver btest]$ g++ -Wall -o btest btest.cpp bcore/logger/logger.cpp
[btnguyen@hpserver btest]$ ./btest
[21/09/2026 15:09:11] [INFO ] [702096|----] Hello World
[21/09/2026 15:09:11] [INFO ] [702096|----] 8080
[21/09/2026 15:09:11] [DEBUG] [702096|----] 0.1234
[btnguyen@hpserver btest]$ ls -ltr
total 40
drwxr-xr-x. 3 root     root        20 Sep 21 09:39 bcore
-rw-rw-r--. 1 btnguyen btnguyen   378 Sep 21 15:08 btest.cpp
-rwxrwxr-x. 1 btnguyen btnguyen 31008 Sep 21 15:09 btest
-rw-rw-r--. 1 btnguyen btnguyen   156 Sep 21 15:09 app.log
[btnguyen@hpserver btest]$ cat app.log
[21/09/2026 15:09:11] [INFO ] [702096|----] Hello World
[21/09/2026 15:09:11] [INFO ] [702096|----] 8080
[21/09/2026 15:09:11] [DEBUG] [702096|----] 0.1234
[btnguyen@hpserver btest]$ 
```
