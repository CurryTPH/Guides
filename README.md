Display Adapter Registry Keys Documentation

All registry keys listed below are located in:

HKLM\System\CurrentControlSet\Control\Class\{4d36e968-e325-11ce-bfc1-08002be10318}\0000\

EnableGpuFirmware

No additional information provided.

EnableRmTestOnlyCode

No additional information provided.

EncSessionStatsReportingState

Type: DWORDThis registry key controls NVENC session stats reporting. Currently, it is used only for GRID.

0x00000000 - Disable NVENC session stats reporting.

0x00000001 - Enable NVENC session stats reporting.

#define NV_REG_STR_RM_NVENC_SESSION_STATS_REPORTING_STATE "EncSessionStatsReportingState"
#define NV_REG_STR_RM_NVENC_SESSION_STATS_REPORTING_STATE_DISABLED 0x00000000
#define NV_REG_STR_RM_NVENC_SESSION_STATS_REPORTING_STATE_ENABLED 0x00000001

EPC_HWSLOW_FC7E081B

Type: DWORDIf set to a non-zero value, overrides AC/DC state of GPIO_FUNC_EXT_PERF_CONTROL_HWSLOW with MMIO 0xFC7E081B.

#define NV_REG_STR_RM_EPC_HWSLOW_FC7E081B "EPC_HWSLOW_FC7E081B"

GridLicensedFeatures

Type: DWORDSet to supported GRID licensed features:

0x00000000 - Disabled

0x00000001 - Enabled for specific features

Supported feature definitions:

#define NV_REG_STR_RM_GRID_LICENSED_FEATURES "GridLicensedFeatures"
#define NV_REG_STR_RM_GRID_LICENSED_FEATURES_QUADRO 0:0
#define NV_REG_STR_RM_GRID_LICENSED_FEATURES_VGPU 1:1
#define NV_REG_STR_RM_GRID_LICENSED_FEATURES_GEFORCE 2:2
#define NV_REG_STR_RM_GRID_LICENSED_FEATURES_COMPUTE 3:3

L40GCompatibilityMode

No additional information provided.

PeerMappingOverride

Type: DWORDEnables/Disables the workaround for bug 1630288, which disables third-party peer mappings. Disabled by default.

#define NV_REG_STR_PEERMAPPING_OVERRIDE "PeerMappingOverride"
#define NV_REG_STR_PEERMAPPING_OVERRIDE_DEFAULT 0

RMBifMnocOverride

No additional information provided.

RMFermiMinGpmFifoDepth

Type: DWORDNumeric value encoding FIFO depth.

#define NV_REG_STR_FERMI_MIN_GPM_FIFO_DEPTH "RMFermiMinGpmFifoDepth"

RMHotPlugI2cDisplays

Type: DWORDSet of device maps for which HW I2C will monitor and report.

#define NV_REG_STR_HOTPLUG_I2C_DISPLAYS "RMHotPlugI2cDisplays"

RmMClkSwitchOnFbflcn

Type: DWORD (Boolean)Enable MCLK switch on FB falcon, offloading execution from RM to FB falcon.

0x00000000 - Disabled

0x00000001 - Enabled

#define NV_REG_STR_RM_MCLK_SWITCH_ON_FBFLCN "RmMClkSwitchOnFbflcn"
#define NV_REG_STR_RM_MCLK_SWITCH_ON_FBFLCN_DISABLE (0x00000000)
#define NV_REG_STR_RM_MCLK_SWITCH_ON_FBFLCN_ENABLE (0x00000001)

RMOverrideSmSpeedSelect

Type: DWORDAllows setting SM_SPEED_SELECT via registry keys. Takes effect in verification builds only.
