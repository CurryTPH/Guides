# Display Adapter Registry Keys Documentation

## Overview
This documentation provides details on all registry keys located under:

```
HKLM\System\CurrentControlSet\Control\Class\{4d36e968-e325-11ce-bfc1-08002be10318}\0000\
```

These registry keys are used to configure and manage the display adapter at boot.

## Registry Keys

### EnableGpuFirmware
Description: (No information available)

### EnableRmTestOnlyCode
Description: (No information available)

### EncSessionStatsReportingState
**Type:** DWORD  
**Description:** Allows changing the state of NVENC session stats reporting. Currently only used for Grid.
- `0x00000000` - Disable NVENC session stats reporting.
- `0x00000001` - Enable NVENC session stats reporting.

### EPC_HWSLOW_FC7E081B
**Type:** DWORD  
**Description:** If set to non-zero, overrides AC/DC state of GPIO_FUNC_EXT_PERF_CONTROL_HWSLOW with MMIO `0xFC7E081B`.

### GridLicensedFeatures
**Type:** DWORD  
**Description:** Specifies supported GRID licensed features.
- `0x00000000` - Disabled
- `0x00000001` - Quadro Enabled
- `0x00000001` - vGPU Enabled
- `0x00000001` - GeForce Enabled
- `0x00000001` - Compute Enabled

### L40GCompatibilityMode
Description: (No information available)

### PeerMappingOverride
**Type:** DWORD  
**Description:** Enables/disables the workaround for bug 1630288 where third-party peer mappings are disabled.
- Default: Disabled

### RMBifMnocOverride
Description: (No information available)

### RMFermiMinGpmFifoDepth
**Type:** DWORD  
**Description:** Specifies the minimum GPM FIFO depth.

### RMHotPlugI2cDisplays
**Type:** DWORD  
**Description:** Sets the device map for which hardware I2C will monitor and report.

### RmMClkSwitchOnFbflcn
**Type:** DWORD  
**Description:** Controls MCLK switch on FB Falcon.
- `0x00000000` - Disabled (Default)
- `0x00000001` - Enabled

### RMOverrideSmSpeedSelect
**Type:** DWORD  
**Description:** Allows setting the `SM_SPEED_SELECT` through registry keys (used in verification builds only).

### RMPcieFLRPolicy
**Type:** DWORD  
**Description:** Forces the disablement of Function Level Reset (FLR).
- `0` - Default Policy
- `1` - Force Disable FLR

### RMSkip2d3dBundleInit
**Type:** DWORD  
**Description:** Controls initialization behavior for 2D/3D bundle.
- `0x00000000` - Full bundle init
- `0x00000001` - Skip 2D/3D bundle init

### RMSlcg
**Type:** DWORD  
**Description:** Used to disable Second Level Clock Gating (SLCG) settings.
- `0` - Enable SLCG (Default)
- `1` - Disable SLCG

### RMSwdxDirectCtxswSkip
**Type:** DWORD  
**Description:** Controls whether RM tells the microcode to skip `swdx direct context switch`.
- `0x00000000` - Allow swdx direct ctxsw
- `0x00000001` - Skip swdx direct ctxsw

### RmWatchDogInterval
**Type:** DWORD  
**Description:** Sets watchdog interval.
- `0x00000007` - Low
- `0x0000000C` - High

### TestAnalogLoadAlways
**Type:** DWORD  
**Description:** Controls whether an analog load test is always run when detecting CRT or FP devices.

### EnableGpuFirmwareLogs
Description: (No information available)

### RMDisableHdcp22
**Type:** DWORD  
**Description:** Disables HDCP22 feature.
- `0x00000000` - Enabled
- `0x00000001` - Disabled

### RMDisableRamchainScrub
**Type:** DWORD  
**Description:** Controls whether RM tells the microcode to disable RAM chain scrub.
- `0x00000000` - Not disabled
- `0x00000001` - Disabled

## Contributing
If you have additional information about any of these registry keys or new registry keys to document, please submit a pull request.

## License
This documentation is provided under the MIT License.
