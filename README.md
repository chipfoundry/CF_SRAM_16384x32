# CF_SRAM_16384x32

This is a 16384x32 SRAM macro that is built using sixteen 1024x32 SRAM macros. It provides a Wishbone compliant slave interface for easy integration into SoC designs.

## Structure

The 16384x32 SRAM macro consists of:

1. **CF_SRAM_16384x32.v** - The main SRAM macro that instantiates sixteen 1024x32 SRAMs with address decoding and data multiplexing
2. **CF_SRAM_16384x32_wb_wrapper.v** - Wishbone compliant wrapper that provides the bus interface
3. **controllers/ram_controller_wb.v** - Wishbone controller that translates bus transactions to SRAM signals

## Features

- **Capacity**: 16384 words × 32 bits = 64KB
- **Address Width**: 14 bits (16384 = 2^14)
- **Data Width**: 32 bits
- **Interface**: Wishbone compliant slave
- **Byte Enable**: Supports byte-level writes using wbs_sel_i[3:0]
- **Scan Chain**: Includes scan chain support for testing

## Address Mapping

The 16384x32 SRAM uses the following address mapping:
- Address bits [13:10]: Select which 1024x32 SRAM macro (0000 through 1111)
- Address bits [9:0]: Word address within each 1024x32 SRAM

## Macro Placement

The macro uses a 2-column × 8-row layout:
- Column 1 (W): sram0, sram2, sram4, sram6, sram8, sram10, sram12, sram14
- Column 2 (E): sram1, sram3, sram5, sram7, sram9, sram11, sram13, sram15

## Dependencies

This macro depends on the CF_SRAM_1024x32 macro, which must be available in your design.

## Installation

Install this IP using IPM

```
pip install cf-ipm
ipm install CF_SRAM_16384x32
```

