# DelphiMTKClient Feature Matrix

This document summarizes the major DelphiMTKClient development areas for buyers, developers and research teams.

DelphiMTKClient is sold as a source code project. Feature availability depends on chipset, boot mode, Download Agent support, storage type, firmware package and device security state.

## Protocol Support

| Area | Description |
| --- | --- |
| LEGACY protocol | Classic MediaTek DA-based workflow for supported devices. |
| XFLASH protocol | Modern DA flow with native partition and flash operations where supported. |
| XML protocol | MTK V6 / XML command workflow for supported devices and firmware packages. |
| BROM flow | Handshake, boot preparation and low-level device communication. |
| Preloader flow | Preloader communication paths where supported. |
| DA stage flow | Stage-1 / Stage-2 Download Agent upload and initialization logic. |
| EMI flow | EMI selection and sending workflow where supported. |
| DA extension flow | DA extension loading and setup paths where supported. |
| SLA / DAA handling | Security authorization related paths where supported. |
| Kamakiri-style path | Payload workflow for supported targets. |
| HeapBait path | HeapBait protocol development path where supported. |
| Carbonara path | Stage authentication path where supported. |

## Device Information

| Feature | Description |
| --- | --- |
| Hardware code read | Reads hardware code and device identification values where available. |
| Hardware sub-code read | Parses hardware sub-code for supported devices. |
| Hardware version read | Reads hardware version data where supported. |
| Software version read | Parses BROM / Preloader software version data. |
| Security flag parsing | Reads secure boot, SLA, DAA, SWJTAG, root cert and memory auth flags where available. |
| MEID read | Reads MEID where supported. |
| SOCID read | Reads SOCID where supported. |
| CPU / chipset detection | Detects chipset family and known MediaTek platform information. |
| Storage info | Detects EMMC, UFS, NAND, NOR and SDMMC paths where supported. |
| Android information read | Reads Android build information from supported filesystems and logical partitions. |

## Flash Tab

### Native Flash

| Feature | Description |
| --- | --- |
| Native firmware selection | Loads supported firmware/scatter items for native flash workflows. |
| Native XFLASH flash path | Uses native XFLASH partition-oriented flash paths where supported. |
| Native XML flash path | Uses XML flash paths for supported MTK V6 packages. |
| Flash by partition name | Writes firmware images by partition name where supported. |
| Download Only mode | Native flash mode for standard image writing. |
| Firmware Upgrade mode | Firmware upgrade style workflow where supported. |
| Format All + Download mode | Format and download style workflow where supported. |
| Progress reporting | Updates progress bar, state label and log output during flash. |

### FlashtoolLib API

| Feature | Description |
| --- | --- |
| Scatter selection | Selects and parses MediaTek scatter firmware packages. |
| Clear scatter list | Clears selected scatter items from the grid. |
| Scatter item grid | Displays scatter partitions and image paths. |
| Scatter flash workflow | Executes selected scatter flash operations. |
| Verified image resolution | Resolves verified image variants where available. |

## RPMB Tab

| Feature | Description |
| --- | --- |
| Read RPMB | Reads RPMB data where supported. |
| Write RPMB | Writes RPMB data where supported. |
| Erase RPMB | Erases RPMB where supported. |
| RPMB key path | RPMB key read / related path where supported. |
| EMMC / UFS RPMB handling | Protocol-specific RPMB integration for supported modes. |

## Keys Tab

| Feature | Description |
| --- | --- |
| Read Keys | Reads supported hardware / device keys where available. |
| PUBKEY read path | Reads public key data where supported. |
| RPMB key read path | Reads RPMB key data where supported. |
| MIRPMB key path | Reads MIRPMB-related key data where supported. |
| MOTO key path | Reads Motorola-related key data where supported. |
| FDE key path | Reads FDE key data where supported. |
| iTrustee key path | Reads iTrustee key data where supported. |
| PROV key path | Reads provisioning key data where supported. |

## Network Tab

### NV Items

| Feature | Description |
| --- | --- |
| Read NVItems | Backs up selected NV-related partitions and data. |
| Write NVItems | Restores / writes selected NV item backup data where supported. |
| Erase NVItems | Erases / formats selected NV item partitions where supported. |
| Write Oeminfo | Writes selected OEM info / NVRAM-related data where supported. |
| Decrypt NV Items | Decodes / decrypts supported NV item data. |
| Patch Cert | Applies supported certificate patch workflow. |
| NV backup paths | Handles `protect1`, `protect2`, `nvram`, `nvdata`, `sec1`, `tee1`, `tee2`, `seccfg` and related paths where supported. |
| LD0B / nvdata handling | IMEI-related NV data paths where supported. |
| DXCC / crypto integration | Crypto-related helper paths where available. |

### IMEI Read and Write

| Feature | Description |
| --- | --- |
| MTK Generic 4G IMEI workflow | Generic 4G IMEI write path for supported targets. |
| MTK Vivo V1 RPMB IMEI workflow | Vivo RPMB-based IMEI workflow where supported. |
| MTK Vivo V2 4G/5G IMEI workflow | Vivo 4G/5G IMEI workflow where supported. |
| MTK Xiaomi 4G IMEI workflow | Xiaomi 4G IMEI workflow where supported. |
| MTK Oppo 4G IMEI workflow | Oppo 4G IMEI workflow where supported. |
| MTK Infinix / Tecno / Itel IMEI workflow | Brand-specific IMEI workflow for supported targets. |
| IMEI1 / IMEI2 input | Dual IMEI input and validation helper fields. |
| Fix RPMB Bad Sector option | Optional Vivo RPMB bad-sector workaround path where supported. |
| Patch Cert option | Optional certificate patch flag for supported OPPO workflow. |

## Patch [1] Tab

| Feature | Description |
| --- | --- |
| OTA Remove for Oppo / Realme / OnePlus | Super image patch workflow for OTA removal. |
| Xiaomi OTA Remove | Super image patch workflow for Xiaomi OTA removal. |
| MDM + OTA Remove | Super image workflow for combined MDM and OTA removal. |
| MDM / Walock Remove for Walton | Super image workflow for Walton MDM / Walock removal. |
| SIM Lock / MDM Remove for Nothing / CMF | Super image workflow for SIM lock / MDM removal. |
| Modem Patch for Xiaomi Anti-Relock | Modem / NON-HLOS patch workflow for Xiaomi anti-relock cases. |
| Persist Patch | Persist partition patch workflow. |
| Demo Remove | Oeminfo patch workflow for demo removal. |
| Payjoy Remove | Oeminfo patch workflow for Payjoy removal. |
| IT Admin / Network / Payjoy Unlock | Miscdata patch workflow for IT admin, network and Payjoy unlock cases. |
| Restore Vbmeta Security ON | Vbmeta restore workflow for security-on state. |
| Vbmeta Patch V1 Security OFF | Vbmeta patch workflow variant 1. |
| Vbmeta Patch V2 Security OFF | Vbmeta patch workflow variant 2. |
| Vbmeta Patch V3 Security OFF | Vbmeta patch workflow variant 3. |
| Mi Account + Global Cust / OpCust | Cust / opcust patch workflow for Mi Account and global conversion paths. |
| Mi Account Remove + Convert Global V2 | Super image patch workflow for Mi Account removal and global conversion V2. |
| Device partition scan patching | Reads target partitions, scans patch rules and writes patched segments back where supported. |

## Patch Tab

| Feature | Description |
| --- | --- |
| Remove Security Plugin | Device-based security plugin removal workflow. |
| Remove Payjoy | Device-based Payjoy removal workflow. |
| Reset Oppo ID | Oppo ID reset workflow where supported. |
| Fix No Efuse State | LK / related patch workflow for no-efuse state cases. |
| Fix DM Verity Corrupt | DM-Verity / LK string patch workflow where supported. |

## Features Tab

### Bootloader

| Feature | Description |
| --- | --- |
| Unlock Bootloader | Bootloader unlock workflow where supported. |
| Unlock BL Permanent | Permanent bootloader unlock development path for supported targets. |
| Relock Bootloader | Bootloader relock workflow where supported. |

### Bypass

| Feature | Description |
| --- | --- |
| Bypass SLA / DAA / SBC | Security bypass workflow where supported. |
| Crash Preloader | Preloader crash workflow used by supported modes. |
| Bypass FRP | FRP format / bypass workflow. |
| Reset Huawei ID | Huawei ID reset workflow where supported. |

### Device Functions

| Feature | Description |
| --- | --- |
| Format device | Formats selected user/device partitions where supported. |
| Factory Reset | Factory reset workflow. |
| Oppo Factory Reset | Oppo / Realme factory reset workflow where supported. |
| Disable Mi Account APK | Mi Account APK disable workflow using supported filesystem paths. |
| Disable Mi Account Hosts | Mi Account hosts patch workflow using supported filesystem paths. |

## Read and Write Tab

| Feature | Description |
| --- | --- |
| Read Raw Firmware | Reads raw firmware / full storage data where supported. |
| Write Raw Firmware | Writes raw firmware data where supported. |
| Read GPT | Reads and saves GPT / partition table data. |
| Write GPT | Writes GPT data where supported. |
| Read Preloader | Reads preloader data where supported. |
| Write Preloader | Writes preloader data where supported. |

## Partition Manage Tab

| Feature | Description |
| --- | --- |
| Read Partition Tables | Reads partition layout and fills the partition grid. |
| Partition selection grid | Displays selectable partition list for read/write/erase operations. |
| Erase selected partitions | Erases checked partitions where supported. |
| Read selected partitions | Reads checked partitions to local backup files. |
| Read full | Performs full flash / full storage read where supported. |
| Write selected partitions | Writes selected partition image files where supported. |
| GPT cache/export support | Saves partition table data during read workflows where supported. |

## File Management Tab

| Feature | Description |
| --- | --- |
| Boot device | Initializes device and loads partition/file-system information for file browsing. |
| Partition browser | Lists readable partitions and supported filesystems. |
| Super partition browser | Opens Android logical `super` partition containers. |
| Dynamic partition browser | Opens supported logical partitions inside `super`. |
| EXT4 browse | Browses EXT4 partitions. |
| EXT4 write-capable operations | Replace, rename and delete paths where supported by the mounted reader. |
| EROFS browse | Browses EROFS partitions in read-only mode where implemented. |
| F2FS browse | Browses F2FS partitions in read-only mode where implemented. |
| Back / Forward navigation | Explorer-style navigation history. |
| Up navigation | Moves to parent directory. |
| Refresh | Refreshes current location. |
| Address display | Shows current filesystem path. |
| Explorer columns | Shows name, size, type, permissions and modified date. |
| Open directory / partition | Opens selected directory or partition. |
| Copy to local | Extracts selected files or directories to local storage. |
| Replace file | Replaces selected file where write support is available. |
| Rename item | Renames selected file/directory where write support is available. |
| Delete item | Deletes selected file/directory where write support is available. |

## Settings and Runtime UI

| Feature | Description |
| --- | --- |
| Universal Device Config | General device configuration mode. |
| Manufacturer select base | Manufacturer/model-based configuration mode. |
| Manual DA selection | Allows selecting a custom Download Agent where needed. |
| Manual preloader selection | Allows selecting a preloader where needed. |
| Auth / cert file selection | Supports optional auth/cert paths where supported. |
| SLA / DAA mode settings | Runtime security handling configuration. |
| Patch DA option | Download Agent patch option where supported. |
| Crash preloader option | Auto crash preloader option where supported. |
| Carbonara option | Enables Carbonara path where supported. |
| HeapBait option | Enables HeapBait path where supported. |
| Skip WDT option | Optional watchdog handling behavior. |
| Debug I/O option | Debug logging for protocol I/O. |
| Stop button | Requests cancellation of active operations where supported. |
| Progress bar / state label | Displays operation progress and transfer status. |
| RichLog output | Rich text operation log with colored status output. |
| Operation history | Stores completed operation history where configured. |

## Customization Areas

The commercial source code can be customized for:

- Private UI branding.
- Licensing and activation systems.
- Custom DA selection logic.
- Model-specific workflows.
- Private service menus.
- Backend API integration.
- Log format changes.
- Workflow restrictions for staff or customers.
- Research instrumentation and protocol logging.
- Custom patch rules and brand-specific modules.
- Custom flash / backup / restore workflows.

## Notes

Some features are protocol-dependent and device-dependent. A feature being part of the codebase does not mean it is universally available on every MediaTek device. MTK behavior varies by chipset, firmware, DA, boot mode and security configuration.
