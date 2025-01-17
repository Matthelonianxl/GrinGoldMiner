# GGM - open-source Grin GPU miner

**Update: GGM3 is compatible with Cuckarood29 PoW activated in 7/2019**

Miner supports all AMD and NVIDIA 6GB+ cards for both Linux and Winows (MacOS untested). Up to 60% faster compared to GGM2.

GGM releases collect 1% fee for the Grin Development Fund and 1% fee for further miner development.

If you disable fees or profit from the code in some way, consider donating to:

BTC 37WJeFqsvSSdC9BbJUW96oCqzSe4TeESnF

## How to build

Miner is written entirely in C# using new open-source .NET implementation called Dotnet Core.

Instal dotnet core 2.2 SDK (Linux/Windows/Mac) from https://dotnet.microsoft.com/download

Clone the repository and go to _build forder.

Run `build_win.bat` (Windows) or `build_linux.sh` (Linux). Alternatively, run `build_[OS]_API.bat` to build a miner with remote API support.
API version can be used with our dashboard project to manage multiple rigs.

Run `run_miner_win.bat` or `run_miner_linux.sh` to start the miner.

*If you wish to build CUDA .ptx intermediate code yourself, install CUDA SDK with compatible compiler and compile the project in Cudacka folder.
Pre-generated PTX file is already included in the repository so there is no need to pre-compile it yourself.*

## How to run binary releases

Both Winows and Linux builds are self-contained and come with all needed dotnet core libraries, there is no need to install any additional SW.

## Configuration

GPUs should be auto-detected on first launch. Once `config.xml` is created you can edit is to access hidden options:

### Define log level

```xml
    <FileMinimumLogLevel>INFO</FileMinimumLogLevel>
    <ConsoleMinimumLogLevel>DEBUG</ConsoleMinimumLogLevel>
```

If you want to see all the details that are happening in the background, change the configration as above. Possible log level options are DEBUG, INFO, WARNING, ERROR.

### Change CPU load

Locate this line in the config

```xml
  <CPUOffloadValue>
    0
  </CPUOffloadValue>
```

If you wish to reduce CPU load use small numbers (1..10), if you have a powerful multi-core CPU then you can try higher values like 50..100. Value 0 mean auto-balancer. Automatic setting may not work optimally with either very weak CPUs and/or many fast GPUs on the PC (8 and more Vegas for example).