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
