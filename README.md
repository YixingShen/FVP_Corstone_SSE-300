# FVP_Corstone_SSE-300
FVP_Corstone_SSE-300

```
FVP_Corstone_SSE-300_Ethos-U55 ^
--parameter mps3_board.DISABLE_GATING=1 ^
--parameter mps3_board.FPGA_SRAM_SIZE=2 ^
--parameter mps3_board.sse300.VM_BANK_SIZE=2048 ^
-a cpu0*="D:/demo/TF-Mv1.6.0/cmakebuild/bin/bl2.axf" ^
--data "D:/demo/TF-Mv1.6.0/cmakebuild/bin/tfm_s_ns_signed.bin"@0x11000000
```

```
//No BL2
FVP_Corstone_SSE-300_Ethos-U55 ^
--parameter mps3_board.DISABLE_GATING=1 ^
--parameter mps3_board.FPGA_SRAM_SIZE=2 ^
--parameter mps3_board.sse300.VM_BANK_SIZE=2048 ^
--parameter mps3_board.uart0.out_file=fvp_uart0_log.txt ^
--parameter cpu0.INITSVTOR=0x11000000 ^
--parameter cpu0.INITNSVTOR=0x01000000 ^
--application cpu0*="cmakebuild/bin/tfm_s.axf" ^
--application cpu0*="cmakebuild/bin/tfm_ns.axf"
```
