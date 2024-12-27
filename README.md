# C-and-C-Pipe
### C and C++ Pipe (reading output from another console application)

Based from this Link https://pubs.opengroup.org/onlinepubs/009695399/functions/popen.html

```C
#include <stdio.h>
//...

int main(){
    FILE *fp;
    int status;
    char path[512];

    // colors.exe is the other application
    fp = popen("colors.exe -r", "r");
    if (fp == NULL)
        /* Handle error */;


    while (fgets(path, 512, fp) != NULL)
        printf("%s", path);


    status = pclose(fp);
    if (status == -1) {
        /* Error reported by pclose() */
       // ...
    } else {
        /* Use macros described under wait() to inspect `status' in order
           to determine success/failure of command executed by popen() */
        //...
    }
}
```
