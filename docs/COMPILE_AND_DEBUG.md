# Compile and Debug Guide

This guide explains the general development requirements and recommended workflow for compiling and debugging the commercial DelphiMTKClient source code package.

This public repository is only a product showcase. The full source code is provided privately to licensed buyers only.

## 1. Development Requirements

Recommended environment:

- Windows 10 or Windows 11, 64-bit.
- Embarcadero RAD Studio / Delphi 12 or newer compatible Delphi version.
- Win32 build target enabled.
- Administrator access for driver installation and USB device testing.
- MediaTek USB / VCOM / Preloader / BROM drivers installed.
- A real MediaTek test device.
- USB cable with stable data connection.
- Required DA, payload, loader and package files provided with the licensed project or selected by the developer.

Optional but recommended:

- Git for source control.
- A clean Windows test machine or VM for build validation.
- A separate physical test PC for USB protocol tests.
- Device logs and firmware packages for target models.

## 2. Project Preparation

After receiving the commercial source code package:

1. Extract the full package to a short local path, for example:

   ```text
   D:\Projects\DelphiMTKClient
   ```

2. Avoid paths with unusual Unicode characters or very long folder names.
3. Keep required runtime folders next to the executable after build, for example:

   ```text
   bin\
   bin\n2\DA\
   bin\payloads\
   db\
   ```

4. Do not remove files from the package unless you understand how they are used.
5. Open the project file in Delphi / RAD Studio.

## 3. Required Runtime Files

Depending on the licensed package and enabled workflows, the application may need files such as:

- Download Agent files.
- DA extension files.
- Payload files.
- Loader-related files.
- Local configuration database.
- Optional auth / cert / preloader files selected by the user.

These files should be placed relative to the executable or selected manually from the UI.

The project is designed to resolve local runtime paths from the executable directory, so it can run on different PCs when the required runtime folders are copied correctly.

## 4. Compile Steps

Typical Delphi build flow:

1. Open the DelphiMTKClient project in RAD Studio.
2. Select the required platform:

   ```text
   Win32
   ```

3. Select configuration:

   ```text
   Debug
   ```

   or:

   ```text
   Release
   ```

4. Build the project.
5. Make sure the generated executable is placed next to the required runtime folders.
6. Run the executable as needed for device testing.

## 5. Command-Line Build Example

If RAD Studio environment variables are available, the project can also be built with MSBuild.

Example:

```bat
call "C:\Program Files (x86)\Embarcadero\Studio\37.0\bin\rsvars.bat"
msbuild "DelphiMTKClient.dproj" /t:Build /p:Config=Debug /p:Platform=Win32
```

Adjust the RAD Studio version path according to the installed Delphi version.

## 6. Driver Preparation

Before testing MTK workflows, install the required USB drivers for the target device and mode.

Common device modes:

- MediaTek BROM mode.
- MediaTek Preloader mode.
- DA / USB download mode.
- USB serial COM mode, depending on workflow.

Recommended checks:

- Open Windows Device Manager.
- Connect the powered-off phone while holding the required boot key.
- Confirm that a MediaTek USB / Preloader / BROM / VCOM device appears.
- Confirm that the COM port is stable and does not rapidly disconnect.
- Use a known-good USB cable and direct motherboard USB port when possible.

## 7. Device Preparation

General device preparation steps:

1. Power off the phone completely.
2. Use the correct boot key combination for the target model.
3. Connect the device to the PC by USB.
4. Confirm that Windows detects the correct MediaTek port.
5. Select the correct DA / preloader / auth / cert files if the workflow requires them.
6. Start the required operation from the application.

Notes:

- Some devices require manual preloader selection.
- Some devices require auth / cert files.
- Some operations depend on chipset, boot mode, security state and selected DA.
- Not all workflows are available on every device.

## 8. Debugging in Delphi

Recommended debug workflow:

1. Use the Debug configuration.
2. Enable breakpoints around the target module.
3. Start the application from Delphi.
4. Connect the device only after the application is ready.
5. Watch the RichLog output and progress state.
6. Inspect exceptions immediately instead of ignoring them.
7. When debugging USB communication, avoid stepping too slowly through timing-sensitive protocol code.

Useful debug areas:

- Device detection and port selection.
- BROM handshake.
- DA selection and upload.
- EMI sending.
- Stage-2 / DA extension flow.
- GPT / partition reading.
- Flash by partition name.
- File Management boot and browse flow.
- NV / IMEI / RPMB workflows.

## 9. Common Build Issues

### Executable Cannot Be Created

If the build fails with an error that the executable cannot be created, close the running application first. The output exe may be locked by Windows.

### Missing Runtime Files

If an operation fails after moving the project to another PC, check that runtime folders such as `bin`, `bin\n2\DA` and `bin\payloads` were copied next to the executable.

### Driver Not Detected

If no MediaTek port appears, reinstall the correct drivers, try another USB port, use another cable or verify the device boot key combination.

### Operation Works on One PC But Not Another

Check:

- Driver installation.
- Runtime folder placement.
- Selected DA / preloader / auth paths.
- Windows permissions.
- USB cable and port.
- Antivirus or endpoint protection blocking USB communication or file access.

## 10. Release Preparation

Before distributing your own compiled product:

- Build in Release mode.
- Test on a clean Windows machine.
- Include required runtime folders.
- Remove debug-only files.
- Add your own branding and licensing where allowed.
- Validate that no private source code is included with the compiled package.

## 11. Support

If you purchased a license and need help compiling, debugging or preparing a device for testing, contact support:

https://t.me/GsmCoder

Product page:

https://alephgsm.com/2026/04/25/delphimtkclient/
