# FDL Compiler

This Python module helps compile and decomplie flash device label (FDL) blobs used to configure the 
[Hilscher netX90](https://www.hilscher.com/products/product-groups/network-controller/asics/netx-90/). 
This allows the configuration to be edited in a convienent text format (YAML) and then compiled into 
a blob that can be flashed to the netX.

This project includes the fdl_compiler module, which can compile or decompile files, as well as a schema for the YAML
configuration file for easier editing.

If using Visual Studio Code, the included settings can help configure validation using the YAML plugin (must be
installed separately).

# Usage
```Shell
python -m netx_fdl_compiler compile {source}.yaml {destination}.fdl
```
```Shell
python -m netx_fdl_compiler decompile {source}.fdl {destination}.yaml
```

For more information about the contents of a flash device label, please refer to the [documentation from Hilscher](https://kb.hilscher.com/display/NETX/FDL+-+Flash+Device+Label)

An example of a YAML FDL description is below:
```YAML
Device:
  Manufacturer: 1
  Class: NETX90
  Device Number: 7833000
  Serial Number: 20000
  Hardware Compatibility: 1
  Hardware Revision: 3
  Production Date: 2017-W43
MAC Addresses:
- 02:00:00:1e:99:00
- 02:00:00:1e:99:01
- 02:00:00:1e:99:02
- 02:00:00:1e:99:03
APP MAC Addresses: []
OEM Identification:
  Options:
    SerialNumber: false
    OrderNumber: true
    HWRevision: false
    ProductionDate: false
  Serial Number: ''
  Order Number: TEST
  Hardware Revision: ''
  Production Date: ''
  Custom Data: null
Flash Layout:
- Type: HWCONFIG
  Start: 1048576
  Size: 8192
  Chip: INTFLASH0
  Name: HWConfig
  Access: O_RDONLY
- Type: FDL
  Start: 1056768
  Size: 4096
  Chip: INTFLASH0
  Name: FDL
  Access: O_RDONLY
- Type: FW
  Start: 1060864
  Size: 512000
  Chip: INTFLASH0
  Name: FW
  Access: O_RDONLY
- Type: FWUPDATE
  Start: 1572864
  Size: 389120
  Chip: INTFLASH1
  Name: FWUpdate
  Access: O_RDWR
- Type: MFW_HWCONFIG
  Start: 1961984
  Size: 8192
  Chip: INTFLASH1
  Name: MFW_HWConfig
  Access: O_RDONLY
- Type: MFW
  Start: 1970176
  Size: 86016
  Chip: INTFLASH1
  Name: Maintenance
  Access: O_RDONLY
- Type: REMANENT
  Start: 2056192
  Size: 32768
  Chip: INTFLASH1
  Name: Remanent
  Access: O_RDWR
- Type: MANAGEMENT
  Start: 2088960
  Size: 8192
  Chip: INTFLASH1
  Name: Management
  Access: O_RDWR
- Type: NONE
  Start: 0
  Size: 0
  Chip: INTFLASH0
  Name: ''
  Access: O_RDONLY
- Type: NONE
  Start: 0
  Size: 0
  Chip: INTFLASH0
  Name: ''
  Access: O_RDONLY
Chip Table:
- Chip: INTFLASH0
  Driver: ''
  Block: 4096
  Size: 524288
  Cycles: 10000
- Chip: INTFLASH1
  Driver: ''
  Block: 4096
  Size: 524288
  Cycles: 10000
```