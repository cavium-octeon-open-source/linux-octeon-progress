git log --oneline master..cavium_OCTEON-SDK-3.Y arch/mips/kernel/octeon_switch.S
---------------------------------------------------------------------------

242d261 MIPS: OCTEON: Fix Automatic provisioning CVMSEG space.
	-#if CONFIG_CAVIUM_OCTEON_CVMSEG_SIZE > 0

ffee00b MIPS: OCTEON: Use correct instruction to read 64-bit COP0 register
	3x mfc0 -> dmfc0

4242acd MIPS: OCTEON: Save and restore CP2 SHA3 state
	lengthy intrusive patch 

b90fdf2 MIPS: OCTEON: Fix FP context save.
	changes two chunks in assembler code, line 31, line 54

8b00f92 MIPS: OCTEON: Save/Restore wider multiply registers in OCTEON III CPUs
	lengthy intrusive patch

f3a0f87 MIPS: OCTEON: Enable use of FPU.
	see comparation

51402c9 MIPS: Octeon: Fast TLS support in octeon_switch.S
	#ifdef CONFIG_FAST_ACCESS_TO_THREAD_POINTER
	with two lines of assembler


git log --oneline cavium_OCTEON-SDK-3.Y..master arch/mips/kernel/octeon_switch.S
---------------------------------------------------------------------------

a36d822 MIPS: OCTEON: Enable use of FPU
	see comparation
	<!> Reintroduces COP2 assembler code in resume() that was removed in 2c952e0
	(see below) among other

8b3c569 MIPS: stack protector: Fix per-task canary switch
	line 73 PTR_L -> PTR_LA
	also see below

1400eb6 MIPS: r4k,octeon,r2300: stack protector: change canary per task
	+#if defined(CONFIG_CC_STACKPROTECTOR) && !defined(CONFIG_SMP)
	+       PTR_L   t8, __stack_chk_guard
	+       LONG_L  t9, TASK_STACK_CANARY(a1)
	+       LONG_S  t9, 0(t8)
	+#endif

	@71

2c952e0 MIPS: Move cop2 save/restore to switch_to()
	here the main difference between "Enable use of FPU" patches 
	(cop2 registers saving from resume()) moved into switch_to()

