目前編譯 nuttx + NSH ( STM32 VCP 虛擬 USB串口  ) 在板上跑起來了

我的作業系統 :

windows 7 (64 bit)

我的環境及編譯器 :

1.  BASH on Windows
Cygwin ( gcc, g++, make, gdb, perl, flex, bison, python, unix2dos )

http://www.cygwin.com/

2. Pre-built GNU toolchain from ARM Cortex-M & Cortex-R processors (Cortex-M0/M0+/M3/M4, Cortex-[R4](https://code.google.com/p/tmr/source/detail?r=4)/[R5](https://code.google.com/p/tmr/source/detail?r=5))

gcc-arm-none-eabi-4\_7-2013q1-20130313-win32 ( 支援 hard FPU )

https://launchpad.net/gcc-arm-embedded/

3. STM32 虛擬串口驅動 ( 32bit/64bit )

https://docs.google.com/file/d/0B_tVI5sZ9E-CYWJPLVFZMmxDc1E/edit?usp=sharing



把下面內容做成 build\_env.bat 放到 "nuttx" 目錄下, 之後用 cmd 切到這個目錄執行它就可以 make. 當然make 前要先到 nuttx\tools\ 執行"./configure.sh tmrfc/usbnsh"  生成 ".config" 才可以進行 make


```C

@echo off
REM ======================================================
rem Sets path for cygwin, toolchain

set ROOT_DRIVE=C:
set APPSROOT=%ROOT_DRIVE%\apps
set UTILROOT=%ROOT_DRIVE%\utils

set cygwin_=%UTILROOT%\cygwin\bin
set toolchain_=%APPSROOT%\gcc-arm-none-eabi-4_7-2013q1-20130313-win32\bin
rem
rem Path for cygwin, toolchain
rem
set path=.;%cygwin_%;%toolchain_%;%path%
REM ======================================================
bash
```