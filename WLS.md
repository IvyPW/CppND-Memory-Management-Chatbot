# Using WSL and Visual Studio Code on Windows

## Install WSL
https://docs.microsoft.com/en-us/windows/wsl/install

## Config for cplusplus developing env
```
sudo apt install gcc build-essential cmake
```
## Problems
### 1. The x11 app is not able to be launched on windows

* Windows 11

    https://docs.microsoft.com/en-us/windows/wsl/tutorials/gui-apps

* Windows 10 or early Windows11

    XServer on windows should be installed:

    https://sourceforge.net/projects/vcxsrv/

* WSL Ubuntu

    Add below to ~/.bashrc and relaunch terminal

    ```
    export DISPLAY=:0
    ```
