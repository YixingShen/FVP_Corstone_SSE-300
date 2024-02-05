# FVP_Corstone_SSE-300
FVP_Corstone_SSE-300

```
//FVP Run ARM MPS3 AN552
FVP_Corstone_SSE-300_Ethos-U55 ^
--parameter mps3_board.DISABLE_GATING=1 ^
--parameter mps3_board.FPGA_SRAM_SIZE=2 ^
--parameter mps3_board.sse300.VM_BANK_SIZE=2048 ^
-a cpu0*="cmakebuild/bin/bl2.axf" ^
--data "cmakebuild/bin/tfm_s_ns_signed.bin"@0x11000000
//FVP Run ARM MPS3 AN552, No BL2
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

```
//QEMU Run ARM MPS3 AN521
qemu-system-arm -machine mps2-an521 -cpu cortex-m33 ^
-kernel cmakebuild/bin/bl2.elf ^
-device loader,file="cmakebuild/bin/tfm_s_ns_signed.bin",addr=0x10080000 ^
-serial stdio
//QEMU Run ARM MPS3 AN521, No BL2
qemu-system-arm -machine mps2-an521 -cpu cortex-m33 ^
-device loader,file="cmakebuild/bin/tfm_s.bin",addr=0x00000000 ^
-device loader,file="cmakebuild/bin/tfm_ns.bin",addr=0x10080000
-serial stdio
```

```
//QEMU Run ARM MPS3 AN547
qemu-system-arm -machine mps3-an547 -cpu cortex-m55 ^
-kernel cmakebuild/bin/bl2.elf ^
-device loader,file="cmakebuild/bin/tfm_s_ns_signed.bin",addr=0x11000000 ^
-serial stdio
//QEMU Run ARM MPS3 AN547, No BL2
qemu-system-arm -machine mps3-an547 -cpu cortex-m55 ^
-device loader,file="cmakebuild/bin/tfm_s.bin",addr=0x00000000 ^
-device loader,file="cmakebuild/bin/tfm_s.bin",addr=0x11000000 ^
-device loader,file="cmakebuild/bin/tfm_ns.bin",addr=0x11060000 ^
-serial stdio
```
