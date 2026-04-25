# DelphiMTKClient Feature Matrix

This document summarizes the major DelphiMTKClient development areas for buyers, developers and research teams.

DelphiMTKClient is sold as a source code project. Feature availability depends on chipset, boot mode, Download Agent support, storage type, firmware package and device security state.

## Protocol Support

| Area | Description |
| --- | --- |
| LEGACY protocol | Classic DA-based MediaTek workflow for supported devices. |
| XFLASH protocol | Modern DA flow with native partition and flash operations where supported. |
| XML protocol | MTK V6 / XML command workflow for supported devices and packages. |
| BROM flow | Handshake, device info and boot preparation logic. |
| Preloader flow | Preloader communication paths where supported. |
| DA stage flow | Stage-1 / Stage-2 upload and initialization logic. |
| EMI flow | EMI selection and sending paths where supported. |

## Device Information

| Feature | Description |
| --- | --- |
| Hardware code read | Reads hardware code and device identification values where available. |
| Hardware sub-code read | Parses hardware sub-code for supported devices. |
| Software version read | Parses BROM / Preloader software version data. |
| Security flags | Reads selected security capability flags where supported. |
| MEID / SOCID | Reads MEID and SOCID where supported by device mode. |
| Storage info | Detects EMMC, UFS, NAND, NOR and SDMMC paths where supported. |

## Flash and Firmware

| Feature | Description |
| --- | --- |
| Scatter workflow | Scatter-based firmware handling. |
| XML workflow | XML firmware package workflow for supported MTK V6 devices. |
| Flash by name | Partition-name based flash path where supported. |
| Raw flash | Address-based read / write path. |
| Preloader read | Read preloader partition / data where supported. |
| Preloader write | Write preloader data where supported by mode and DA. |
| Progress reporting | UI progress and log callback integration. |

## Partition Management

| Feature | Description |
| --- | --- |
| GPT read | Reads and parses partition layout. |
| Partition browser | Displays partition names, regions, sectors and sizes. |
| Read partition | Dumps selected partition data. |
| Write partition | Writes selected partition data where supported. |
| Erase partition | Erases selected partitions where supported. |
| Full flash read | Full storage dump path where supported. |
| Partition lookup | Helper logic for partition name and sector mapping. |

## File Management

| Feature | Description |
| --- | --- |
| Boot device | Initializes the device for file management workflows. |
| Browse partitions | Browses supported readable partitions from the UI. |
| EXT4 support | EXT4 stream reader and related file operations. |
| Super partition | Logical partition metadata handling. |
| Dynamic partitions | Opens supported partitions inside Android `super`. |
| EROFS detection | Detects / reads EROFS where implemented. |
| F2FS detection | Detects / reads F2FS where implemented. |
| File extraction | Extract files and directories where supported. |
| Android info | Reads Android information such as `build.prop` where supported. |

## NV / IMEI / Keys

| Feature | Description |
| --- | --- |
| NV backup | Reads selected NV partitions and files where supported. |
| NV write | Writes selected NV paths where supported. |
| NV erase | Erase / format related NV paths where supported. |
| Decode NV items | Decodes supported NV item data. |
| LD0B / nvdata | IMEI-related development paths for supported targets. |
| IMEI workflow | IMEI read / repair module areas for selected brands and modes. |
| Key read paths | Hardware key read paths where supported by mode and chipset. |
| DXCC integration | Crypto-related helper paths where available. |

## RPMB

| Feature | Description |
| --- | --- |
| RPMB read | Reads RPMB data where supported. |
| RPMB write | Writes RPMB data where supported. |
| RPMB erase | Erases RPMB where supported. |
| RPMB key path | RPMB key read / related path where supported. |

## Security and Research Paths

| Feature | Description |
| --- | --- |
| SLA / DAA handling | Security authorization related paths where supported. |
| Kamakiri-style path | Payload workflow for supported targets. |
| HeapBait path | HeapBait protocol development path where supported. |
| Carbonara path | Stage authentication path where supported. |
| Bootloader unlock | Unlock logic where supported. |
| Bootloader relock | Relock logic where supported. |
| Permanent unlock | Permanent unlock development path for supported targets. |
| FRP / format | Format and FRP-related workflows. |
| Vbmeta / dm-verity | Patch logic where supported. |
| Brand patches | Model / brand specific patch workflow examples. |

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

## Notes

Some features are protocol-dependent and device-dependent. A feature being part of the codebase does not mean it is universally available on every MediaTek device. MTK behavior varies by chipset, firmware, DA, boot mode and security configuration.
