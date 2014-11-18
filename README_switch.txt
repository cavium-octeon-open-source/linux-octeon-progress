[amakarov@turnip linux_upstream]$ git log --oneline @..cavium_OCTEON-SDK-3.Y arch/mips/kernel/octeon_switch.S
242d261 MIPS: OCTEON: Fix Automatic provisioning CVMSEG space.
ffee00b MIPS: OCTEON: Use correct instruction to read 64-bit COP0 register
4242acd MIPS: OCTEON: Save and restore CP2 SHA3 state
b90fdf2 MIPS: OCTEON: Fix FP context save.
8b00f92 MIPS: OCTEON: Save/Restore wider multiply registers in OCTEON III CPUs
f3a0f87 MIPS: OCTEON: Enable use of FPU.
51402c9 MIPS: Octeon: Fast TLS support in octeon_switch.S

[amakarov@turnip linux_upstream]$ git log --oneline cavium_OCTEON-SDK-3.Y..@ arch/mips/kernel/octeon_switch.S
a36d822 MIPS: OCTEON: Enable use of FPU
8b3c569 MIPS: stack protector: Fix per-task canary switch
1400eb6 MIPS: r4k,octeon,r2300: stack protector: change canary per task
2c952e0 MIPS: Move cop2 save/restore to switch_to()

