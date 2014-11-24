#
# git log --oneline --reverse v3.10.14...HEAD
#
# IMPORTANT: KEEP THE LIST ORDERED
# 
# decision on the patch:
# 	--- -- no actions required
# 	!!! -- not now
# 	??? -- should be investigated
# 	+++ (branch name) -- cherry-picked preparing to upstream
# 	>>> -- related to kvm.  for Andreas
#
# tags:
# 	#SE [N] -- simple executable
#	#MERGE -- merge commits
#	#REVERTS SHA
#	#REVERTED SHA
# 
# branches:
# 
# - octeon_serial.01 -- patch to run on simulator. submitted
#
# - octeon_switch.01 -- bringing the upstream code from upstream
# 	octeon_switch.S in correspondence with OCTEON-SDK-3.Y
#
# - octeon_patches.06 -- pulling patches from cavium linux one by one
# 
# --------------------------------------------------------------------------------

b3366c2a MIPS: OCTEON: Rename Kconfig CAVIUM_OCTEON_REFERENCE_BOARD to CAVIUM_OCTEON_SOC
	--- already in the tree: 9ddebc46e70b434e485060f7c1b53c5b848a6c8c

44bd450 MIPS: Octeon: Fast access thread pointer
4acb845 MIPS: Octeon: CONFIG_FAST_ACCESS_TO_THREAD_POINTER on stackframe
7c7457c MIPS: Octeon: TLB support for FAST_ACCESS_TO_THREAD_POINTER
7741477 MIPS: Octeon: syscall hook for FAST_ACCESS_TO_THREAD_POINTER
51402c9 MIPS: Octeon: Fast TLS support in octeon_switch.S
25dc846 MIPS: Octeon: Kconfig for FAST_ACCESS_TO_THREAD_POINTER
8ea04dd MIPS: Octeon: Fast TLS support in arch/mips/kernel/genex.S
	!!! related to fast tls;  skipping

6bcc665 MIPS: Add CPU identifiers for more OCTEON family members.
	--- already in the three;  71a8b7d86c0dbdd1a278e91afcefc9de4f819ec5

9b09d60 MIPS: Probe for new OCTEON CPU/SoC types.
	--- already in the tree: af04bb8578a47e7a7572cf1c22bb3309ca2380f7

37105af MIPS: Use r4k_wait for OCTEON3 CPUs.
	--- already: 4122af0ab02a4b394e4703a3ac557d556701f4d9

e37fa29 MIPS: Generate OCTEON3 TLB handlers with the same features as OCTEON2.
	--- already: 4723b20a381ae488d845f3e041ef1dd71c6f40f8

877613e MIPS: OCTEON: Set L1 cache parameters for OCTEON3 CPUs.
	--- already: 62597c60816967100243338421782469b831563d

8663a2c MIPS: OCTEON: Remove vestiges of CONFIG_CAVIUM_DECODE_RSL
	--- already: 02a49d5144c58a2b9826946934533a7a9f28c2ec

ca7581b MIPS: OCTEON: Get rid of CONFIG_CAVIUM_OCTEON_HW_FIX_UNALIGNED
	--- already: 0ec315121c8391a14bbeb5eecc146c470dfc00cb

92818288 MIPS: Allow r4k_switch.S to be included by octeon_switch.S
	--- already included in: a36d8225bceba4b7be47ade34d175945f85cffbc

627a134 MIPS: Override assembler ISA for kernel FPU instructions.
	---
	1st chunk: already included in: a36d8225bceba4b7be47ade34d175945f85cffbc
	2nd chunk: eilminated in: dab75dd956522ce19403c108f659ea9b339f2559
	3rd chunk: eliminated in: 3351047f01fe012abbb585b400d1c51b57ed011d
	4th chunk: same
	5th chunk: same

6057b89 MIPS: Declare emulate_load_store_microMIPS as a static function.
	--- already: 74338805ec6869594d583535f941cb478c94dd73

7f46e4c6 MIPS: Don't try to decode microMIPS branch instructions where they cannot exist.
	--- already: fe6d29095d4370bed3a525404c45bbd6aa7c191b

32f863a MIPS: Only set cpu_has_mmips if SYS_SUPPORTS_MICROMIPS
	--- already: 3ddc14add5e6341cf8ef4058c34c67ba7fd15317

63c9556 MIPS: OCTEON: Improve _machine_halt implementation.
	--- already: 38c3c0f6733bec1d1841915a9a82d2c324362686

f3a0f87 MIPS: OCTEON: Enable use of FPU.
	--- already included in: a36d8225bceba4b7be47ade34d175945f85cffbc

f3466d8 MIPS: Define cpu_has_octeon2_isa cpu features.
c809dfb MIPS: Use Octeon2 atomic instructions when cpu_has_octeon2_isa.
	!!! these two are related.  First of them can be cherry picked, 
	the second requires some work.  Skip for now as they are just 
	some optimizations, not necessary 

0e76f59 MIPS: Add ZCB and ZCBT instructions to uasm.
b13153b MIPS: Add Octeon2 optimizations to clear_page.
	!!! These two introduce some optimization for octeon.  At least first 
	patch can not be cherry-picked as is.  Not necessary for now

520b3e0 Add octeon2 build and configuration option
	??? Probably required
	David: Not required

0554e80 MIPS: OCTEON: Select ARCH_REQUIRE_GPIOLIB
9167b5d gpio/MIPS/OCTEON: Add a driver for OCTEON's on-chip GPIO pins.
43320dd gpio/OCTEON: Fix typos and and simplify I/O count determination
	!!! drivers -- skip for now

8d4aca2 MIPS: OCTEON: Add utility helper function octeon_read_ptp_csr()
	!!! drivers (from comment: used by following Ethernet PTP patches)
	probably should be merged with those patches

d7a3ff9 Fix section mismatch in gpio-octeon.c
	!!! drivers -- skip for now

a47c13c i2c: i2c-octeon: broken irqs, high-level controller, retry lost arbitration
8d5ea1a usb: Convert {ohci,ehci}-octeon.c to use device tree.
9dfac39 usb: ehci-octeon/ohci-octeon: Fix for little-endian kernel.
b7dc0ef mmc: Add host driver for OCTEON MMC controller.

e723e8b of: Add prefix parameter to of_modalias_node().
	---
	#REVERTED bbe2ebaf0030f44298e31ab3283ef318562a7e03

fc375c3 spi: Use consistent MODALIAS values.
	---
	#REVERTED 0af834e00fb37e515409c306f73145b9ec168692

8a344d2 eeprom/of: Add device tree bindings to at25.
d33f6e6 netdev/phy: Add driver for Cortina cs4321 quad 10G PHY.
83b3ab9 netdev/staging: octeon-ethernet: Clean up PHY handling.
721cbcb netdev/staging: octeon-ethernet: Only initialize PHYs when a netdevice is open
bea86de MIPS: OCTEON: Add sysfs support for CPU power throttling.
	!!! drivers -- skip for now

a0c4950 MIPS: OCTEON: Add PTP clocksource.
	??? basicly driver, but defines OCTEON_CNF7XXX in 
	arch/mips/include/asm/octeon/octeon-model.h
	that is merged in c415bff
	8d4aca2 MIPS: OCTEON: Add utility helper function octeon_read_ptp_csr()
	(see above), should be merged with it.

08b2dc6 MIPS: Make Cavium as the default configuration.
	--- should not go to upstream at all
	#REVERTED 895f4c49b4b5c3ed4a432b015936a6df09a87d57

02c9ce6 MIPS: Remove unneeded #ifdef __KERNEL__ from asm/processor.h
	+++

# Nov 17

f92a0f2 MIPS: If huge pages are enabled, align STACK_TOP to a huge page boundry.
	+++

37ecc17 MIPS: Implement get_cycles() for CONFIG_CEVT_R4K_LIB
	--- Should not go to upstream because 
	- get_cycles() was rewritten by d617f9e9b80632e5206f0a88b7b25ef39bd2612b
	and d617f9e9b80632e5206f0a88b7b25ef39bd2612b checks the existence of the 
	timer by some much more elaborate means
	- there is no config option CEVT_R4K_LIB in upstream nor cavium kernel

246a50e MIPS: OCTEON: Probe device tree for "cavium,octeon-5750-usbn"
	--- already: included in d617f9e9b80632e5206f0a88b7b25ef39bd2612b

d89de89 MIPS: OCTEON: Re-introduced xkphys_read, xkphys_write sysmips(2) calls
	--- Implements some system calls.  Config options for them were introduced in
	520b3e0 Add octeon2 build and configuration option
	Do not send to upstream.  New system calls probably will not be accepted.

80c2660 MIPS: Octeon: Implement the core-16057 workaround
c3a04f9 MIPS: OCTEON: Don't do acknowledge operations for level triggered irqs.
	+++

2e8d90e MIPS: OCTEON: Print address of passed device tree.
	--- do not send upstream

2944b9d MIPS: OCTEON: Add parameter to disable PCI on command line.
	!!!

4e03dca MIPS: OCTEON: Change load address to waste less memory.
	+++

b1d9a98 MIPS: Change sparsemem physical memory bits from 35 to 38
	--- it has been increased to 48 in c46173183657bbdbe0d54a981c28807581648422
	for Loongson arch
	David: This is problematical.  For now it can be left as is, but I added a patch to our SDK to reduce it based on the sub-architecture.  The large value of 48 causes a 16MB block of .bss to be allocated.  This is a big waste for small memory systems, and takes a very long time to initialize on the simulator. 
	Aleksey: Ok, I saw your next patch and going to pick it later.

	see also cc7b99d (change to 48) 9477842 (revert) 0ecffe9 (change dynamically)

5043204 MIPS: OCTEON: Add ability to used an initrd from a named memory block.
	+++ (with conflicts)

abed31e MIPS: OCTEON: Rearrange CVMSEG slots.
	!!! related to fast tls;  (?) skipping

f3dbda3 MIPS: OCTEON: Add little-endian support to asm/octeon/octeon.h
8f2dd4e MIPS: OCTEON Handle bootloader structures in little-endian mode.
fa86eea MIPS: OCTEON: Add mach-cavium-octeon/mangle-port.h
9734af5 MIPS: OCTEON: Make cvmx-bootmem and packet I/O functions work Little Endian.
	+++
	these basically were merged to make merging the first large S. E. patch easy

fd9bc4f netdev: octeon-ethernet: Add support for Little Endian kernels.
bb9fae7 MIPS: OCTEON: Make PCIe work with Little Endian kernel.
658e2b4 MIPS: OCTEON: Enable little endian kernel.
	!!! related to little-endian and drivers;  not now

f9037af MIPS: OCTEON: Add driver for OCTEON PCI console.
	!!! drivers;  not now

3f9ce70 MIPS: Octeon: Implement DCache errata workaround for all CN6XXX
	+++

5304368 MIPS: OCTEON: Remove unneeded alignment specifiers from struct thread_struct.
	+++ (with conflict resolution)

5048ef6 MIPS: OCTEON: Handle userspace access to CVMSEG
	!!! needs conflict resolution;  not now

4306373 MIPS: Octeon: Quit using all the mailbox bits.
	+++ (with conflict resolution)

87d2ec7 MIPS: Octeon: Add simple Octeon IPI infrastructure
	+++

253087c MIPS: Fix warning spew on CONFIG_PREEMPT_DEBUG and ptrace watch register use.
	!!! some work on conflict resolution required;  not now

61668052 MIPS: Quick debug helper to dump page table for an addres to the console.
	--- do not send to upstream
	#REVERTED 9d189a6

50752c2 MIPS: OCTEON: MSI support for cn68xxP2 and other MSI improvements.
7fb12ef MIPS: Octeon: Correct typos and errors in msi-octeon.c
c1b247e MIPS: OCTEON/MSI: Don't compile unused functions when !CONFIG_SMP
50f5e2c MIPS: OCTEON/MSI: Sign extend irq.
	!!! drivers;  not now

ebf87be MIPS: Align stack top for CONFIG_MIPS_HUGE_TLB_SUPPORT.
	+++

d73afc7 MIPS: Fix compile warning in dump_tlb
	--- fixes a typo introduced in 61668052 (see above) which is not 
	to be sent upstream

cc43ce2 RapidIO: Add interface to memory map rapidio device memory.
f25ef36 MIPS: OCTEON: Add support for SRIO interrupt sources.
	!!!
	David: This patch is a bit of a hack job.  I would recommend deferring most 
	rapidio/SRIO patches for later. 

958bf54 MIPS: Cleanup HUGETLB_PAGE config option
	+++
	But I am not sure about this.  And commit message of this patch should be 
	improved.

fb0ee08 mtd: nand_ids:  Add a couple of device identifiers to the table.
3336254 MIPS/mtd/OCTEON: Add Add NAND flash driver for OCTEON.
	!!! drivers;  not now

9d6af2f Merge branch 'OCTEON-SDK-3.Y' of ssh://cagit1.caveonetworks.com/repo/git/linux/linux-octeon-sdk into OCTEON-SDK-3.Y
	---
	#MERGE

# Nov 19

8093f03 MIPS: OCTEON: Fix command queue unlock memory barriers.
	+++

9b1d01b MIPS: Octeon: Remove reference to cvmx_sysinfo_get()->cpu_clock_hz from cvmx.h
	+++

5d84506 MIPS: Octeon: Increase PCI_CONFIG_SPACE_DELAY
	!!! pci.  not now

3adc612 MIPS: Octeon: Add config option to disable ELF NOTE segments
	??? some workaround for old bootloaders.  Probably is not required upsteram (?)

ce35e6b MIPS: Octeon: Define NR_CPUS_DEFAULT_32 for Cavium Octeon.
	+++

404c2fc MIPS: Octeon: Only enable flash support if CONFIG_MTD is set.
	!!! mtd; not now

8963a8d MIPS: OCTEON: Add /proc/octeon_perf support.
	!!! perf; not now

b0c4419 MIPS: Octeon: Don't restore $ra in SAVE_SOME
	--- outdated by merging the commit 
	e6e44e79 MIPS: Don't save/restore OCTEON wide multiplier state on syscalls.
	(see below).  In upstream it is commit 8dfdd02a4c.  *BUT*

	In cavium the remained lines are:
		#ifdef CONFIG_CPU_CAVIUM_OCTEON
				.set	mips64
				pref	0, 0($28)	/* Prefetch the current pointer */
				pref	0, PT_R31(sp)	/* Prefetch the $31(ra) */
		#endif

	In upstream:
		#ifdef CONFIG_CPU_CAVIUM_OCTEON
				.set    mips64
				pref    0, 0($28)       /* Prefetch the current pointer */
		#endif

	I do not understand why we need to prefetch anything at all?

	David: It is a performance optimization.  I don't know if the prefetches actually help that much, but they don't hurt.
	The idea is that whatever the exception handler will be calling is likely to need to read things from the thread_info, or the PT_REGS, so we prefetch them into the L1 cache. 

	OK, let's leave as it is in upstream

af5f2fb MIPS: Add nudges to writes for bit unlocks.
	+++

d645168 perf: Try to disable detection of python
	--- perf;  not now;  probably never
	#REVERTED 4a73415

37d42aa MIPS: OCTEON: Sync up HOTPLUG_CPU with bootloader structures.
	+++ (with conflicts)

	David: We have made big changes to how HOTPLUG_CPU works, Don't make small adjustments here, just go directly to the current implementation.
	This also effects... (two patches below) watchdog.  Both the HOTPLUG_CPU and watchdog use the NMI facilities of OCTEON.

	For now I am going to just fix and pick this patch.  I will look at what should be done next (probably this patch should be thrown out), 
	but without it the next patches will more likely be rejected

fbb44e9 watchdog: octeon-wdt: Add command-line option to disable.
075df7a watchdog: octeon-wdt: Add support for cn68XX SOCs.
	!!! watchdog: not now

8083a9b MIPS: Octeon: perf_counters for all TADs in available LMC controllers
	!!! perf;  not now
	should have picked: contaminated with c415bff

# Nov 20

239f7af MIPS: OCTEON: Quit using csrc-octeon-ptp.c as a clock source.
	--- see also:
	8d4aca2 MIPS: OCTEON: Add utility helper function octeon_read_ptp_csr()
	a0c4950 MIPS: OCTEON: Add PTP clocksource.
	This patch is basically disables the clock that what was introduced in a0c4950

b427aeb MIPS: Octeon: Core-15169 Workaround and general CVMSEG cleanup.
	+++

979c655 MIPS: Octeon: Remove setting of processor specific CVMCTL icache bits.
	+++

301d177 MIPS: Octeon: Disable probing MDIO for Landbird NIC 10g cards.
	+++

3f9d1da MIPS: OCTEON: Add cvmx-twsi API files.
	--- reverted; see below (9ac3c45)
	#REVERTED 9ac3c45

11f4318 MIPS: OCTEON: netdev/ethernet Fix build error
	!!! ethernet;  not now

9ac3c45 Revert "MIPS: OCTEON: Add cvmx-twsi API files."
	---
	#REVERTS 3f9d1da8bb4d7e74f6647ab8962a11bf9f421be2.

9d189a6 Revert "MIPS: Quick debug helper to dump page table for an addres to the console."
	---
	#REVERTS 61668052fb334c003c2b7ab1e66bcc1fe0256482.

6e028c6 MIPS: OCTEON: Populate kernel memory from cvmx_bootmem named blocks.
	+++ (with conflicts)

293dc19 Merge tag 'v3.10-rc5' into OCTEON-SDK-3.Y
	---
	#MERGE

70a246f MIPS: OCTEON: Add framework for managing and reporting hardware status bit assertions.
4e60836 MIPS: OCTEON: Add table driven handler for SoC error conditions.
	!!! not now

39ae96c i2c: i2c-octeon: Add  octeon_i2c_cvmx2i2c() function.
	!!! not now

# Nov 21

c415bff MIPS: OCTEON: Import new S.E. and adjust things to match.
	+++
	#SE 1
	see also 8083a9b
	see also a0c4950

3333299 MIPS: OCTEON: Build cvmx-appcfg-transport.o and cvmx-fpa-resource.o

de87944 netdev: octeon: Move and update OCTEON network drivers from staging.
436c461 MIPS: OCTEON: Removed unused CAVIUM_DECODE_RSL related files.
4c68051 MIPS/EDAC: Cavium: Fix compilation errors.
f0244a3 MIPS: OCTEON: Add missing octeon-ethernet-user.h

1178699 netdev: octeon-ethernet: Remove incorrect __init annotation.
2e11c90 ata: Use WARN instead of BUG in pata_octeon_cf.
0b78298 usb: Add host driver for cn3XXX and cn5XXX SoCs
3211e1f MIPS: OCTEON: Handle non-cn6xxx in several places.
d23ae68b MIPS/OCTEON: Initialize QLM JTAG.
6c6f0e7 MIPS/OCTEON: Override default address space layout.
c06b1ca MIPS: OCTEON: Add support for running kernel in mapped address space.

4208c04 Fix compile warning in mm/page_alloc.c
	---
	#REVERTED dd62fd0

dd62fd0 Revert "Fix compile warning in mm/page_alloc.c"
	---
	#REVERTS 4208c0486afc7fd29c4419f97482041b05cbc934.

2cdea76 MIPS: OCTEON: Use virt_to_phys() and phys_to_virt() in octeon/setup.c

93257e1 smp.h: Use local_irq_{save,restore}() in !SMP version of on_each_cpu().
	---
	#REVERTED 0e70b19d002c8270ce4a1b7379baf3c30784fab5

0d34967 MIPS: OCTEON: Only use SAA instructions for CONFIG_CAVIUM_OCTEON2
f819600 MIPS: Octeon: Cleanup obsolete CrashKernel memory init in octeon/setup.c
f322e41 MIPS: Octeon: Add /proc/octeon_info support.
c9cbce3 MIPS: Octeon: Allow TLB modify handlers to use scratchpad for temporary register save.
d77ec45 MIPS: Fix typo in CAVIUM_OCTEON_* SYS_SUPPORTS_HOTPLUG_CPU
a417eac MIPS: Octeon: adopt hotplug code to new struct cvmx_coremask
70e3f51 MIPS: Octeon: Rearrange L2 cache locking code
6365c1d MIPS/edac/OCTEON: Hook up Write Buffer parity errors to EDAC.
2f212cb MIPS/edac/OCTEON: Hook up Write Buffer parity errors to EDAC.
c75cc7c MIPS: Add board_mcheck_handler, show process state on machine check exception.

0e70b19 Revert "smp.h: Use local_irq_{save,restore}() in !SMP version of on_each_cpu()."
	---
	#REVERTS 93257e1ad8b2ea0c380d4bc1baef30ee0946b235

8796207 smp.h: Use local_irq_{save,restore}() in !SMP version of on_each_cpu().

f229f51 MIPS/OCTEON: Add OCTEON II TLB parity error handling
2b5588a MIPS: Octeon: Change kuid_t references to __kuid_val()
109d82a MIPS: OCTEON: Add vmlinux* to .gitignore.
70c0681 MIPS: Remove dead code from Makefile.
ae26832 MIPS: Add cpu_has_saa to cpu-features.h
50e56de gpio: gpio-octeon Make Kconfig depend on CAVIUM_OCTEON_SOC
8e0d551 of: Add of_memory_accessor to map device tree node to memory accessor functions.
a86b980 misc/at24: Register memory accessor functions with of_memory_accessor
f6e59de netdev/phy/of: Handle nexus Ethernet PHY devices
3cb6b89 netdev/phy: Add driver for Vitesse vsc848x single, dual and quad 10G phys
34dd2cd MIPS: Octeon: Use cvmx-pcie.c from executive.
e62d7b0 netdev/phy: Fixed mask for active copper cable check.
499b27e MIPS: Octeon: Add /sys/devices/system/cpu/cpuX/cache
b073130 gpio: gpio-octeon: Clean up code.

b201b03 MIPS: OCTEON: Initialize KGDB after serial port is setup.
	---
	#REVERTED f9da4567169b281514c79d2798f2c8da4fe1c051

89b486a mmc: OCTEON: Improve GPIO support.

baa75ab MIPS: OCTEON: Allow for error tree reporting to be enabled per group.
	---
	#REVERTED 43704de

08df64a usb: octeon2-common.c: Enable error reporting.
bf70098 MIPS: Octeon: (Re) Add functions to enable kernel crypto usage.

43704de Revert "MIPS: OCTEON: Allow for error tree reporting to be enabled per group."
	---
	#REVERTS baa75abe3d9a820abbce29640e2b6ce07da3db85.

1d3a172 MIPS: OCTEON: Add module to inject hardware error conditions.
b081635 MIPS: OCTEON: Restore printing of L2 Cache information.
fdad414 MIPS: OCTEON: Add support for CONFIG_CAVIUM_GDB
38d094a MIPS: Don't select SYS_SUPPORTS_HOTPLUG_CPU for CPU_CAVIUM_OCTEON
e4a0810 MIPS: OCTEON: Fix local_flush_icache_range
e97b0a4 MIPS: OCTEON: octeon-lmc bug fixes
5c5fa12 MIPS: Octeon: Move pulsing of MCD0 way earlym, define COP0_MDEBUG
1bf635a MIPS:OCTEON: Sync up cvmx-cmd-queue.h

e6e44e79 MIPS: Don't save/restore OCTEON wide multiplier state on syscalls.
	--- already merged as 8dfdd02a4c
	BUT see comment for the commit b0c4419 above

8b00f92 MIPS: OCTEON: Save/Restore wider multiply registers in OCTEON III CPUs
	+++ (octeon_switch.01)

c4edf70 MIPS: OCTEON: Reword octeon_pci_console messages.

5fc0aff MIPS: OCTEON: Sync up debug stub files.
	---
	#REVERTED 95d5f48

95d5f48 Revert "MIPS: OCTEON: Sync up debug stub files."
	---
	#REVERTS 5fc0affd93a2f8d581ce909eda541742549738b1

a9c987b MIPS:OCTEON: More OCTEONIII support
0a194ae MIPS: OCTEON: Fix model check for setting clock rate.
0c040e0 MIPS: Octeon: Add Octeon3 cache handling
37d27b6 MIPS: OCTEON: Add driver Serial Rapid I/O (sRIO) hardware
b7df9f4 RapidIO: Driver for CN6XXX
b2b04e9 MIPS: Octeon: RapidIO: Use DMA for large memory transfers.
e4941c8 MIPS: Octeon: cleanup defunct 2ND_KERNEL config option
dca43f0 EDAC:OCTEON: Fix reading LMCX_DLL_CTL2 CSR fields.
b01c30c MIPS: Octeon: Merge and cleanup for cavemum-octeon/setup.c
2246fb0 MIPS: OCTEON: Move Simulator command line out of the kernel.
4920cb8 MIPS: OCTEON: Set proper UART clock in internal device trees.
8ee53dc tty/8250_dw: Add support for OCTEON UARTS.
ecbdb44 MIPS: OCTEON: Remove custom serial setup code.

f9da456 Revert "MIPS: OCTEON: Initialize KGDB after serial port is setup."
	---
	#REVERTS b201b0319badc96eae3e9afcbc3ec6e7f17fc675

6a4ec0e MIPS: OCTEON: Add SDK version printout to kernel start messages
46d3f0e netdev: octeon_mgmt: Correct tx IFG workaround.
433d93b netdev: octeon_mgmt: Fix structure layout for little-endian.

0af834e Revert "spi: Use consistent MODALIAS values."
	---
	#REVERTS fc375c3be56e7d4eda123bf912b4b1d05fa765ac.

bbe2eba Revert "of: Add prefix parameter to of_modalias_node()."
	---
	#REVERTS e723e8bf3cc92076b7593a3947d1e950f5c3faef.


fa9a03c MIPS: Octeon: Initialize proper CVMX_SSO_NW_TIM register.
f7e3138 MIPS: Fix arch in assembly for saa instruction.
62a22e9 netdev: octeon-ethernet: Configure the PHY interface type correctly.
b07e85e mips/ftrace: Fix function tracing return address to match

131c3ca2 Merge tag 'v3.10.1' into OCTEON-SDK-3.Y
	---
	#MERGE

1f507be MIPS: Cleanup flags in syscall flags handlers.
9d98053 MIPS: Implement HAVE_CONTEXT_TRACKING.

4a73415 Revert "perf: Try to disable detection of python"
	---
	#REVERTS d645168af1e1c2297fe9512a5db86492826c35bc.

895f4c4 Revert "MIPS: Make Cavium as the default configuration."
	---
	#REVERTS 08b2dc631eb46b3abf809e03733742422c620a2c.

8fcdb8b MIPS: OCTEON: Increase the number of irqs for !PCI case
4d4ab15 serial: 8250_dw: Mask register value in dw8250_serial_outq.
174c9f7 MIPS: Add support for OCTEON III perf events.
6a4845a MIPS: OCTEON: Add semaphore to serialize bootbus accesses.
80ab07c mmc: octeon_mmc: Use octeon_bootbus_sem.
8ea172e MIPS: OCTEON: Protect accesses to bootbus flash with octeon_bootbus_sem.
aab4d33 MIPS: OCTEON: Use device tree to probe for flash chips.
5c6c83e netdev: octeon-ethernet: Fix netif_running/netif_queue_stopped confusion.

1a8bed7 MIPS:OCTEON: Sync up SE files.
	#SE


655ea06 MIPS: OCTEON: Sync up new SE files.
	#SE

f5ac9e9 netdev:octeon-ethernet: Set MAC/PHY mode and 1000x/SGMII mode.

788bfb9 MIPS: OCTEON: Update S.E. files
	#SE

bca8fc5 netdev: octeon-ethernet: Make cvm_oct_pools_lock a mutex
fdde77e MIPS: octeon: Handle cn5xxx USB from builtin device tree

46ac7c6 MIPS: OCTEON: Update S.E. to r86552
	#SE

e80a73d MIPS:OCTEON: Sync up error interrupts from SE.
	#SE

8d3e4ec netdev: octeon-ethernet: Add common module for setting mac address
46d72e6 MIPS: OCTEON: Use current_cpu_type() for CPU model check.
4430d28 MIPS: OCTEON: Fix L1 dacache parity for OCTEON3
5207ed2 MIPS: Move allocate_kscratch to cpu-probe.c and make it public.

a94f89e mips/kvm: Improve code formatting in arch/mips/kvm/kvm_locore.S
66f489d mips/kvm: Cleanup .push/.pop directives in kvm_locore.S
ad32815 mips/kvm: Make kvm_locore.S 64-bit buildable/safe.
3667de3 MIPS: Save and restore K0/K1 when CONFIG_KVM_MIPS_VZ
4333482 mips/kvm: Add casts to avoid pointer width mismatch build failures.
9e1b5e2 mips/kvm: Use generic cache flushing functions.
2b81526 mips/kvm: Rename kvm_vcpu_arch.pc to  kvm_vcpu_arch.epc
c722e3d mips/kvm: Rename VCPU_registername to KVM_VCPU_ARCH_registername
3529105 mips/kvm: Factor trap-and-emulate support into a pluggable implementation.
c3b0b99 mips/kvm: Implement ioctls to get and set FPU registers.
	>>>

cb76a7e MIPS: Rearrange branch.c so it can be used by kvm code.
198e746 MIPS: Add instruction format information for WAIT, MTC0, MFC0, et al.

531ef36 mips/kvm: Add accessors for MIPS VZ registers.
310a57f mips/kvm: Add thread_info flag to indicate operation in MIPS VZ Guest Mode.
339935e mips/kvm: Exception handling to leave and reenter guest mode.
aaa293f mips/kvm: Add exception handler for MIPS VZ Guest exceptions.
0425181 mips/kvm: Add pt_regs slots for BadInstr and BadInstrP
07decd9 mips/kvm: Add host definitions for MIPS VZ based host.
0e008cf mips/kvm: Hook into TLB fault handlers.
0dbcfe4 mips/kvm: Allow set_except_vector() to be used from MIPS VZ code.
4c9e3a5 mips/kvm: Split get_new_mmu_context into two parts.
a72b5e8 mips/kvm: Hook into CP unusable exception handler.
f700bfb mips/kvm: Add thread_struct fields used by MIPS VZ hosts.
0e19c61 mips/kvm: Add some asm-offsets constants used by MIPS VZ.
309ca6e mips/kvm: Split up Kconfig and Makefile definitions in preperation for MIPS VZ.
0e980d8 mips/kvm: Gate the use of kvm_local_flush_tlb_all() by KVM_MIPS_TE
a7eb2d8 mips/kvm: Only use KVM_COALESCED_MMIO_PAGE_OFFSET with KVM_MIPS_TE
2c4189a mips/kvm: Add MIPS VZ support.
40974f1 mips/kvm: Enable MIPS VZ in Kconfig/Makefile
513b8b4 mips/kvm: Allow for upto 8 KVM vcpus per vm.
	>>>

87802a9 MIPS: Discard .eh_frame sections in linker script.
486aac7 MIPS: Move system level config items from CPU_CAVIUM_OCTEON to CAVIUM_OCTEON_SOC
ae9bf7f MIPS: OCTEON: Force L1 Dcache and TLB parity errors for testing.

b7f316e netdev: octeon-ethernet: Common code for changing MTU.
	---
	#REVERTED cca7ab0

cca7ab0 Revert "netdev: octeon-ethernet: Common code for changing MTU."
	---
	#REVERTS b7f316ebcba8199f9f996d6de5eef4f9aae28f7b

b6b38a6 MIPS: OCTEON: Seperate SoC and CPU related config items
e778c04 MIPS: Don't build fast TLB refill handler with 32-bit kernels.
f4c7fff netdev: octeon-ethernet: Remove unused macros.
e4b3856 smp.c: Quit unconditionally enabling irqs in on_each_cpu_mask().

e13672f MIPS: OCTEON: Get rid of special SMP_ICACHE_FLUSH IPI message.
	---
	#REVERTED 6ab7748

69b8f32 Merge branch 'OCTEON-SDK-3.Y' of ssh://cagit1.caveonetworks.com/repo/git/linux/linux-octeon-sdk into OCTEON-SDK-3.Y
	---
	#MERGE

7a9936a netdev: octeon-ethernet: Redo common code for changing MTU.
3795998 netdev: octeon-ethernet: Add AGL support.
eb4df20 MIPS:  Add hypervisor call API for use by MIPS VZ guests.
89088c8 MIPS:  Add mips_cpunum() function.
74368d0 MIPS: Fix !SMP build failures in stackframe.h
3603c70 smp: Quit unconditionally enabling irq in on_each_cpu_mask and on_each_cpu_cond
bcd4fd5 MIPS: move arch/mips/cavium-octeon/cpu.c to arch/mips/kernel/
2f126fc MIPS: OCTEON: Move xkphys_usermem_{read,write} to octeon-cpu.c
638e306 MIPS: OCTEON: Move L2 Cache probing code to setup.c
b9ee220c MIPS: Handle indexed load instructions in emulate_load_store_insn().
d41ea29 MIPS: Add new system 'paravirt'.
d26fba7 MIPS: Add new function local_flush_icache_all()
7b6c459 MIPS: OCTEON:  Add OCTEON specific implemtation of local_flush_icache_all().
f44ecee MIPS: Only flush local ICache in get_new_asid().
29a4adf MIPS: OCTEON: Use correct L2C CSR for cache locking.
2fad0da MIPS/EDAC: Cavium: Updated L2C error checking for OCTEON3.

6ab7748 Revert "MIPS: OCTEON: Get rid of special SMP_ICACHE_FLUSH IPI message."
	--- 
	#REVERTS e13672f

0bf4545 MIPS: OCTEON: Simplify/cleanup octeon_send_ipi_mask.
1841d29 MIPS: Handle OCTEON BBIT instructions in FPU emulator.
57a4c82 MIPS: OCTEON: Handle cn78XX counters in csrc-octeon.c
ab164ed MIPS: OCTEON: Don't write FAU registers for cn78XX
528bc85 MIPS: OCTEON: Use of_irq_init() to initialize interrupt controllers.
4694a47 netdev: octeon-pow-ethernet.c: Don't disable interrrupt in interrupt handler.
12f46a5 MIPS: OCTEON: Fix crash on use of octeon-pci-console.
340f3cb MIPS: OCTEON: Fix section mismatch errors in octeon-irq.c
68d224b MIPS: OCTEON: Fix compilation errors with previous revert.
e1204ad MIPS: OCTEON: Move call to register_smp_ops() to smp.c...
368c758 MIPS: OCTEON: Remove unused octeon_smp_ops declaration.
0983404 MIPS: OCTEON: Disable perf_counters.c for cn78XX
efdc172 MIPS: OCTEON: Add initial CIU3 support for cn78XX.
bbb32ce MIPS: OCTEON: Add SMP support for cn78XX.
11dde5e MIPS: OCTEON: Fix section missmatch warnings in smp.c
1e9cfb8 MIPS: Octeon: Fix new coremask, hotplug CPU

a037ffd MIPS: OCTEON: Sync S.E. files to r87484
	#SE

a5f2746 MIPS: OCTEON: Sync S.E. files to r87487
	#SE

e2e9755 MIPS: Improve support for OCTEON III interrupt controller.
3d2d3de MIPS: OCTEON: Fix compile errors in pcie-octeon.c
9dc8932 MIPS/EDAC: Set error reporting state to polling
a9f275f MIPS/EDAC: Poll for LMC_INT_REG[nxm_wr_err]
16e25b9 MIPS/EDAC: Poll for all error bis in L2C_INT CSR.
aff0b6d MIPS: KDUMP: skip walking indirection page for crashkernels
f0e544f MIPS: KEXEC: Fixes Random crashes while loading crashkernel
2dae8fc MIPS:KDUMP: Fix build issues with previous commit.
00e1d1e MIPS: OCTEON: Use static resource allocation for CIU3 interrupt controller.
b6c9d50 MIPS: OCTEON: Get rid of some unlikely() in octeon-irq.c.
6cb0457 MIPS: Octeon: Fix HOTPLUG_CPU data structures for LITTLE_ENDIAN
af2be40 We are already in IRQ context, so we can call generic_handle_irq directly instead of re-entering IRQ context via do_IRQ.
1921683 MIPS: OCTEON: Add appropriate header file
4f95dee MIPS: OCTEON: Cleanup PCIe setup code
2b843fc MIPS: Octeon: Add HOTPLUG_CPU support in LITTLE_ENDIAN mode

fe793f9 MIPS: OCTEON: Sync up SE files.
	#SE

c77cb5c MIPS: OCTEON: Don't try to initialize MSI on CN78XX
447f41f MIPS: OCTEON: Fix non-smp build issues
80e1683 MIPS: OCTEON: Disable IOB_INT[outb_mat,intb_mat] for OCTEON3.
5b7810d MIPS: OCTEON: Initialize 3 PCIe ports for OCTEON3.
c84ff92 MIPS: OCTEON: Add preliminary cib_sata interrupt controller support.

a4307c0 Merge branch 'OCTEON-SDK-3.Y' of ssh://cagit1.caveonetworks.com/repo/git/linux/linux-octeon-sdk into OCTEON-SDK-3.Y
	---
	#MERGE

0b2d2ff MIPS: OCTEON: Generalize cib_sata interrupt controller support for all cib.

e83f1cc Merge branch 'OCTEON-SDK-3.Y' of ssh://cagit1.caveonetworks.com/repo/git/linux/linux-octeon-sdk into OCTEON-SDK-3.Y
	---
	#MERGE


ba2386c MIPS:OCTEON: Sync up some SE files.
	#SE

d326dd8 MIPS: OCTEON: Sync up more SE files.
	#SE

37342df MIPS: OCTEON: Use correct CSR to soft reset
db14a40 MIPS: OCTEON: Add header file to fix compilation errors.
116de25 MIPS: OCTEON: Remove unused function cvmx_reset_octeon()

2325125 Merge branch 'OCTEON-SDK-3.Y' of ssh://cagit1.caveonetworks.com/repo/git/linux/linux-octeon-sdk into OCTEON-SDK-3.Y
	---
	#MERGE

daf6e02 MIPS: OCTEON: Add missing phys_to_virt to octeon-irq.c

9f64a37 Merge branch 'OCTEON-SDK-3.Y' of ssh://cagit1.caveonetworks.com/repo/git/linux/linux-octeon-sdk into OCTEON-SDK-3.Y
	---
	#MERGE

95a301c MIPS: OCTEON: Add compatibility for Octeon

0698a5b MIPS: OCTEON: Sync up SE files.
	#SE

98f217c MIPS: OCTEON: Rename AGL interface as agl port.
b54d87b MIPS: OCTEON: Enable Micrel 9031 PHY for OCTEON.
f71c55a MIPS: OCTEON: Add support for CIU SUM2 interrupt sources.
8efb001 MIPS: OCTEON: Fix typos in octeon-irq.c
7b127a2 MIPS: OCTEON: Fix spelling of cavium,max-bits in device tree.

7120207 Merge tag 'v3.10.14' into OCTEON-SDK-3.Y
	---
	#MERGE

e82340a MIPS: OCTEON: Sync-up SE files.
	---
	#REVERTED 4f52d3e
	(#SE)

26b3c8e MIPS: OCTEON: Include new SE files.
	---
	#REVERTED 9c871d7
	(#SE)

9c871d7 Revert "MIPS: OCTEON: Include new SE files."
	---
	#REVERTS 26b3c8e
	(#SE)

4f52d3e Revert "MIPS: OCTEON: Sync-up SE files."
	---
	#REVERTS e82340a
	(#SE)

ca439d6 netdev: octeon-ethernet: Use correct CSR for processing receive errors
ecb0420 MIPS: OCTEON: Add register definitions for OCTEON III USB.

4b8dd9a usb: Hack up xhci, so that it works with the OCTEON III xHCI controller.
	???
	see also d59d94498bedabdf0dfc5581953150a354f6b0b2

28c1f9b MIPS: OCTEON: Sync up SE files.
	#SE

2db8850 Merge branch 'OCTEON-SDK-3.Y' of ssh://cagit1.caveonetworks.com/repo/git/linux/linux-octeon-sdk into OCTEON-SDK-3.Y
	---
	#MERGE

dd04d00 MIPS: OCTEON: Sync up more SE files.
	#SE

48562d3 netdev: octeon-ethernet: Allocate queues for QSGMII interface.
a89887d MIPS: OCTEON: Handle "level" triggering of CIB interrupts.

fe15c39 Fix macro name clash when KVM enabled
	>>>

5a2877b MIPS: Octeon: Hotplug_cpu: Fix available coremask printout Bug# 8263 Signed-off-by: Leonid Rosenboim <lrosenboim@caviumnetworks.com>

b90fdf2 MIPS: OCTEON: Fix FP context save.
	+++ (octeon_switch.01)

3793d03 MIPS: OCTEON: Allow CONFIG_CAVIUM_CN63XXP1 to be disabled.
c99652b MIPS: OCTEON: Export octeon_bootbus_sem.
fd3c36d Fix little-endian macro name clash when KVM enabled
c0bed96 octeon-pow-ethernet: bi-endian cluster support
e54c99a MIPS: OCTEON: Enable tlb parity error for O3
15d1fa0 MIPS: OCTEON: Keep reset value for COP0_ERRCTL

67ccfc0 MIPS: OCTEON: Sync up SE files
	#SE

8ac7d83 MIPS: paravirt: Handle SMP_ICACHE_FLUSH IPI message
7a9b08e MIPS: paravirt: Implement _machine_halt
d9e1c49 MIPS: Update mips_paravirt_defconfig
68ca379 MIPS:USB:OCTEON: Configure SHIM according to endianness

2c20421 MIPS: OCTEON: Sync up SE files
	#SE

0b2f4bf MIPS: OCTEON: Synchronize CP0.Count across CPUs.
7b659aa MIPS: Add definition of CP0_GUESTCTL2
9822eb5 MIPS: KVM-VZ updates.

9784a8b kvm tool: Add it to the tree.
	---
	#REVERTED e2e9a0f3fc6fe6fb4e76acd586c7993fe3600b8d

44ebde8 MIPS: Add user stack and registers to perf
e547682 perf tools: Add support for MIPS unwind & userspace DWARF callchains.
72c68f9 MIPS: Fix get_new_asid().
566293b MIPS: Define read_gc0_epc() and read_gc0_errorepc()
8cf07b1 MIPS kvm: Fix errors in kvm_mipsvz.
4825667 MIPS: Handle CPU_CAVIUM_OCTEON3 like CPU_CAVIUM_OCTEON2 in clear_page.
b1b97b4 MIPS: OCTEON: Fix plat_swiotlb_setup() for OCTEON3
330d18b MIPS: KDUMP: Fix to access non-sectioned memory
b41816f ftrace MIPS/recordmcount: Don't ignore the first function in a file

4242acd MIPS: OCTEON: Save and restore CP2 SHA3 state
	+++ (octeon_switch.01)

09a3f5d ed usb clock init for octeon to be called from dwc3 driver. Signed-off-by: Vinita Gupta <vgupta@caviumnetworks.com>
4540334 edac/octeon_edac-lmc: Fix kernel panic when 1 DDR present

6f4571c MIPS: OCTEON: Sync up SE files.
	#SE

184afca MIPS: OCTEON: Update performance counter events for OCTEONIII.

9d4191f Merge branch 'OCTEON-SDK-3.Y' of ssh://cagit1.caveonetworks.com/repo/git/linux/linux-octeon-sdk into OCTEON-SDK-3.Y
	---
	#MERGE

f96d80f MIPS: Octeon: RapidIO: Do not create the same sysfs file twice.
d81103b mmc: octeon_mmc: Handler multiple slots, and fix bugs.
d118a2c MIPS: Octeon: RapidIO: Initialize the spin lock.
6f367e5 EDAC: octeon_edac-lmc: Fixed crash for DIMM1-only case

ae75eac MIPS: OCTEON: hw_status tree, remove sleep-holding-rwlock issues
	---
	#REVERTED 458bea52f824dad7d9ae5174139253e09041b957

7cd3753 MIPS: Octeon: RapidIO: Set the ipd port, pko port, and pko queue base correctly.
6865dba mmc: octeon_mmc: Add driver parameters to limit multi-block transfers.

ce191e8 MIPS: OCTEON: Sync-up SE files.
	#SE

dc4a658 MIPS: OCTEON: Fix typo in 'fpmov' performance counter event.
9b0f8c9 mmc: octeon_mmc: Fix error recovery.
b28893d MIPS: octeon-hw-status: fix refcounting
299ab77 MIPS:OCTEON:SATA:hecked ata platform code to modify octeon SHIM according to endianess Signed-off-by: Vinita Gupta
73c2bf0 MIPS: Octeon: RapidIO: Set the MTU correctly and pad small packets to 64 bytes.
b36a314 MIPS:USB:OCTEON:warning and other clean up
07f6edf MIPS:SATA:OCTEON: compiler warning clean up
fadc36e MIPS:OCTEON:USB: fixed bug to make lodable dwc3 module working
6a1b6c0 MIPS: octeon3 power throttle support
a7cb16e MIPS: simplify octeon power throttle support
1a76eed MIPS: OCTEON: Reduce the amount of console output probing CIB interrupt blocks.
dff2868 net: Export skb_release_head_state.
622d3b9 netdev: octeon-ethernet: Enable SKB recycling of transmitted packets.
7f3e712 MIPS:OCTEON:SATA: fixed code to make sata loadable module working

e187678 Merge branch 'OCTEON-SDK-3.Y' of ssh://cagit1.caveonetworks.com/repo/git/linux/linux-octeon-sdk into OCTEON-SDK-3.Y
	---
	#MERGE

94297db netdev: octeon_ethernet: Rename octeon_recycle_tx parameter to recycle_tx
9e43b57 MIPS perf: Add notifiers on pmu_enable/pmu_enable
8a778e2 MIPS perf: OCTEON: Handle PMU pmu_enable/pmu_diable notifications.
4412829 MIPS: Octeon: KDUMP: Fixed handling IPI in secondary cores, during crash
20435f8 MIPS: OCTEON: Backport SGMII mode support for Cortina PHY
ea711be MIPS: OCTEON: Add new file for Cortina PHY support
bb9f502 MIPS perf: Update handling of OCTEON raw perf events.
e39ed68 MIPS perf: Rework the mipspmu notifiers.
f1b87aa MIPS: OCTEON:  Set the extended bits of DIDTTO too.
cd975a4 MIPS: cavium-octeon: fix early boot hang on EBH5600 board
5bd9c53 MIPS: OCTEON: Fix compilation warnings in Cortina PHY code.
2557b05 From 0ae2a41e63160475d37bb058ffc106731d8c800e Mon Sep 17 00:00:00 2001 From: Prem Mallappa <pmallappa@caviumnetworks.com> Date: Fri, 8 Nov 2013 13:05:36 +0530 Subject: [PATCH] MIPS: Octeon:smp.c: Fix compilation, removed duplicate  declaration
e0ce0b5 ata sata_octeon: Set proper DMA masks.
636368f MIPS: Octeon: RapidIO: Add little endian support.

020b5b1 MIPS: OCTEON: Sync up SE files.
	#SE

95430a7 MIPS: OCTEON: Sync up SE files.
	#SE

458bea5 Revert "MIPS: OCTEON: hw_status tree, remove sleep-holding-rwlock issues"
	---
	#REVERTS ae75eac54673f5a15460e411a72dfd7b50cc3c7e,

35e58db MIPS: octeon hw_status debugfs interface
61944fe MIPS: octeon-hw-status tree-walker should visit irq objects
631ebe8 MIPS: octeon-hw-status rework
c55e1c6 MIPS: octeon-hw-status merge typos
5c6c73c mmc octeon_mmc: Clean up device tree accesses.
6cd5ce58 MIPS: octeon-hw-status: cleanup no-irq logic
9381636 MIPS: octeon-power-throttle: allow booting in low-power mode
7de4094 MIPS: octeon-hw-status only free IRQs we own!
4fcf177 mmc octeon_mmc: Add configurable clock skew settings.
236bc26 mmc octeon_mmc: Set MIO_BOOT_CTL correctly on cn70XX
41272ed netdev: octeon-ethernet:  Get rid of bogus locking.

2a11301 MIPS: OCTEON: Sync up SE files.
	#SE

08161a9 Merge branch 'OCTEON-SDK-3.Y' of ssh://cagit1.caveonetworks.com/repo/git/linux/linux-octeon-sdk into OCTEON-SDK-3.Y
	---
	#MERGE

2c94cea netdev: octeon-ethernet: Added .shutdown method
15aa0c7 netdev: octeon-ethernet: Fix compile errors.

26a0434 kvm tool: Add compiler.h to fix compilation errors.
	---
	#REVERTED 625647a488025302259aeb6a3d57f5252fbb00a3

19905f3 MIPS: msi-octeon: Rename mis_ena_reg to msi_ena_reg
8606f7a MIPS: octeon-power-throttle: new attributes, fix scaling
6fdf501 usb: octeon2-common.c: Improve clock initialization sequence.
12b3724 usb: octeon2-commom.c: Added host controller reset for kexec/kdump to work
3890dc8 usb: octeon2-common.c: Added new header file
8a97c77 usb: octeon2-common.c: Improve clock initialization sequence (Again).
aee8bd0 MIPS: OCTEON: Fix device tree usbn compatible property.

90a3e21 MIPS: OCTEON: Sync-up SE files.
	#SE

1e89891 usb: octeon2-common: Only reset EHCI/OHCI on OCTEON2 devices.
5c41dc8 ata: sata_octeon: Adjust DMA parameters.
6f020de MIPS: octeon-power-throttle: max/minthr attrs for cn7xxx debug
995e0a0 MIPS: octeon-power-throttle: keep maxthr at 0xff
2808f39 MIPS: oct_ilm: Fix debugfs file permissions.
1373cf7 netdev: octeon-ethernet: Reenable lockless PKO access.
bdfd9a7 netdev: octeon-ethernet: Add some likely()/unlikely() to speed up NAPI rx.
73f27f1 usb: octeon2-common: Update clock initialization.
d7644cb MIPS: octeon-hw-status use-count fix
24007511 MIPS: flush octeon-cib IRQs at boot

9326919 MIPS: OCTEON: Sync up SE files (cvmx-l2c only)
	#SE

aae260b perf: u64 printf formats & other gcc fluff
769e36a spi: spi-octeon.c: Allow faster speeds on octeonIII boards.
f2b40aa spi: spi-octeon.c: Use device tree values to set the controller's maximum frequency.
5fb9a92 MIPS: Octeon: RapidIO: Check skb headroom before pushing data.
390cd9f usb: xhci-octeon: Update power control.

cf7e849 Merge branch 'OCTEON-SDK-3.Y' of git://cagit1.caveonetworks.com/linux/linux-octeon-sdk into OCTEON-SDK-3.Y
	---
	#MERGE

f35b363 MIPS: OCTEON: Sync up SE files.
	#SE

22993e5 MIPS: OCTEON: NAND: Updated to support bch ecc correction.
9280658 # HG changeset patch # User Ronny Meeus <ronny.meeus@alcatel-lucent.com> # Date 1386156030 -3600 #      Wed Dec 04 12:20:30 2013 +0100 # Node ID 2ba522e9bb1949c61327c3cca0afedb7c09a3702 # Parent  b1603c6392f81b0537b97ded34f5c6c685886260 alu change: NAND driver: disable subpage reads
085af60     # HG changeset patch     # User Ronny Meeus <ronny.meeus@alcatel-lucent.com>     alu change: MIPS: OCTEON: Improve PHY mode setting
cb5662c usb: xhci-octeon: replaced cvmx_wait with udelay/ndelay
097645e netdev: octeon-ethernet: Initialize gmx_base for SPI interface.
91a46c5 # User Ronny Meeus <ronny.meeus@alcatel-lucent.com> # Date 1386156065 -3600 #      Wed Dec 04 12:21:05 2013 +0100 # Node ID a0615a4c69c8749f43f285c4fdb756dbf572a38c # Parent  2ba522e9bb1949c61327c3cca0afedb7c09a3702 alu change: enable unicast filter for all relevant network interfaces
c2bf961 MIPS: msi-octeon: Add msi-x support.
da5d8f0 of/gpio: Define OF_GPIO_OPEN_DRAIN flag for Open Drain outputs.
e86aecf netdev/phy: Clean up structure names in vsc848x.c
08de367 netdev/phy: Add driver for TI tlk10232 dual-10G PHY.
9f1ddc0 MIPS OCTEON: Fix OOPs in pci console.
a5c6866 netdev/phy: tlk10232: Fix phy register write.
4c031b3 MIPS/OCTEON: Use non-threaded irqs for CIB chaining.
287d490 MIPS/OCTEON: Allow each interrupt major block to use its own domain.
3f2ec04 MIPS/OCTEON: Point fix for PKO initialization defect.
cd02103 MIPS: allow modular octeon usb
6939c9c MIPS: panic_on_oops: remove ssleep()
636f3fd MIPS: octeon-hw-status refcount rework
c62fc8f MIPS: OCTEON: Per process XKPHYS support
2d4a01d MIPS: OCTEON: Per-process XKPHYS access.
b0895e2 MIPS: Allow __cpu_number_map to be larger than NR_CPUS
9fc2719 MIPS/OCTEON: Fix bugs in multi-node CIU3 support.
77d9d3c MIPS/OCTEON: Use wide coremasks in smp.c to allow for more than 32 CPUs.

4554bc8 Merge branch 'OCTEON-SDK-3.Y' of ssh://cagit1.caveonetworks.com/repo/git/linux/linux-octeon-sdk into OCTEON-SDK-3.Y
	---
	#MERGE

5d45271 MIPS/OCTEON: Fix bad coremask passed by some bootloaders.
0da29216 MIPS/OCTEON: Disable cvmx_app_hotplug_global things as they are broken.
5fcdc1b MIPS: octeon-ether teardown cleanup
fc48187 MIPS: perf: octeon uncore events
6622eb8 perf: context-sensitive keywords: for uncore_foo/miss/
d4d4cbb MIPS: perf: octeon uncore_xxx/store/ renames

33fbc77 MIPS/OCTEON: Update S.E. to r94829
	#SE

d59d944 usb/xhci: Revert CONFIG_PCI change to allow driver to work on x86
	???
	this reverts a chunk of 4b8dd9ac169aa3c25dd9dc52ec6526f7d88aa314


6ee8820 MIPS/OCTEON: Add msi/msi-x support for ciu3.
1fff293 MIPS/OCTEON: Handle cvmx_octeon_num_cores() for cn78xx
8d718c1 MIPS/OCTEON: Quit doing non-cn78XX operations on cn78XX
89b7b0a watchdog: Octeon: Add 78xx support.
b1cc38b MIPS/OCTEON: Allow virtual irqs greater than 256.
744de1b gpio: gpio-octeon: Add preliminary cn78XX support.

58d1aab Merge branch 'OCTEON-SDK-3.Y' of ssh://cagit1.caveonetworks.com/repo/git/linux/linux-octeon-sdk into OCTEON-SDK-3.Y
	---
	#MERGE

fbb99c8 MIPS/OCTEON: Update S.E files and kernel code to match.
	#SE

8d659cd MIPS/OCTEON: Fix FPA breakage in BCH code.
616d461 MIPS/OCTEON: CIU/CIU2 use random msi irqs.

ffee00b MIPS: OCTEON: Use correct instruction to read 64-bit COP0 register
	+++ (octeon_switch.01)

7e1617a MIPS:OCTEON: Enable access to CVMSEG for user space
4b8468f MIPS: OCTEON: Fix compilation issues for debugging kernel

ed57d99 MIPS: OCTEON: Update S.E. files to r96774.
	#SE

f26e15c netdev: Preliminary Ethernet driver for Cavium cn78XX.
59cb0dc netdev: octeon3-ethernet: Fixes to build as module.

440662e MIPS: OCTEON: Update S.E to r96842.
	#SE

1463ec5 netdev: octeon3-ethernet: Replentish RX buffer pool.

55d342a MIPS: OCTEON: Update S.E. Files.
	#SE

fb46975 netdev: octeon3-ethernet: Initial support for hardware checksumming.
cb0b3ef netdev: octeon3-ethernet: Clarify the Kconfig text.
3bdc689 netdev: octeon3-ethernet: Move some init code to .ndo_init()
b86fd45 OCTEON: OCLA driver to support blocking IO.
ed7d399 OCTEON: Fix merge conflict.
fff94439 OCTEON: Fix section mismatch.
35275f7 MIPS: OCTEON: Nand: Fix setting the ecc_strength.
7ed8e0c MIPS:OCTEON:PHY: Added Atheros 8033.
41589fc netdev: octeon3-ethernet: Add Preliminary device statistics.
4145e5d MIPS: octeon CONFIG_TRACE_IRQFLAGS balancing

9ce68b3 MIPS: drop octeon flash-setup if unused
	---
	#REVERTED 4b33103

bd677d7 mmc: core: Only execute tuning for SDR50 and SDR104
201a8c3 mmc: block: fix a bug of error handling in MMC driver
a03b507 mmc: core: Set data timeout for mmc bus test commands (CMD14 and CMD19).
d1a8ae9 mmc: core: mmc DDR mode should not depend on UHS_DDR50
c64eb0b mmc: fix host release issue after discard operation
865eca0 mmc: core: Use generic CMD6 time while switching to eMMC HS200 mode
9d2facd MMC: rmmod octeon_mmc should quiesce device
e192fda MMC: octeon_mmc multi-block dma

4b33103 Revert "MIPS: drop octeon flash-setup if unused"
	---
	#REVERTS 9ce68b31b62bb53aa94c63e7827357cf4d631abb

93c8806 MIPS: OCTEON: Default to 48 cores
	---
	#REVERTED 852355d

f2231b8 mmc octeon_mmc: Do request_irq later to avoid OOPS.
e51cd25 MIPS: OCTEON: Whole tree make device tree compatible strings consistent for cn7890.

852355d Revert "MIPS: OCTEON: Default to 48 cores"
	---
	#REVERTS 93c88068e63972548b412a9e88cbfeb06becee01.

4d11f03 watchdog: octeon-wdt: Fix count rate for cn78XX SoC.
f37c0fb mmc octeon_mmc: Add back the mmc_serializer semaphore for cn78XX

af7c520 MIPS: OCTEON: Update S.E. files.
	#SE

789e833 netdev: octeon3-ethernet: Add initial PHY support.
8a42fd8 netdev: octeon3-ethernet: missing bgx exports
7fc2fae netdev: octeon3-ethernet: Try to set BGX mode correctly.
8838492 MIPS: OCTEON: Add initial error bit detection for cn78XX.
3a9cbf0 netdev: octeon3-ethernet: Undo setting of mac_phy_mode.

662c9fe MIPS: OCTEON: Update S.E files.
	#SE

1a27305 netdev: octeon3-ethernet: Allocate PKI qpg per port.
5c0c5c5 MIPS:Cavium: Fix uninitialized warnings when ftrace of ifs are turned on.
21c6f52 netdev: octeon3-ethernet: Changed to make it work on hardware.

5de0b18 MIPS: OCTEON: Update cvmx-pow.h from S.E.
	#SE

23323af netdev: octeon3-ethernet:  Enable HW checksums.
e7f42eb netdev: octeon3-ethernet: Enable MAC address filtering.
cb3d922 mmc: octeon_mmc: Prevent concurrent entry to irq handler.
4c17faf netdev: octeon3-ethernet: Disable hardware checksums.
d415eae netdev: octeon3-ethernet: Enable HW checksums.
04a6cd7 MIPS: OCTEON: Fix typos in CIU3 interrupt handler code.

07613b9 MIPS: OCTEON: Sync up S.E. files.
	#SE

7e63c5c Fixed Linux octeon-NAND device driver and cvmx-BCH-support.
c63f49f MIPS:OCTEON: NAND: Minor cleanup.
85bd44c MIPS:OCTEON:MSI: Fix intsn for MSI interrupts
d3bd51e MIPS: OCTEON: Fix enabling of MSI-X interrupts for cn78XX.
8e80302 MIPS: OCTEON: Reorganize PCIe controller data structures.
46b74c1 MIPS: OCTEON: Cleanup MSI handling code.
1c14448 MIPS: OCTEON: Implement PCI INTA interrupts for cn78XX
ca65c65 MIPS: Don't used EHB in TLB handlers when not needed.
ff01302 MIPS: OCTEON: Add preliminary GPIO interrupt support for cn78XX.
cd23717 MIPS: OCTEON: Fix io_resource end value
701923d mmc: octeon_mmc: Implment host bus lock-up workaround.
d3ced3d netdev: octeon3_ethernet: Get rid of TX complete WQEs.

44e867f MIPS: OCTEON: Update S.E. files to r98762
	#SE

d6da61b netdev: octeon3-ethernet: Fix multi RX buffer packets for large MTU.
6587193 MIPS: OCTEON: Disable cn78xx PA_ERR_INT[2].
6cbf06c MIPS: OCTEON: Disable cn78XX PKI_GEN_INT[DRP_NOAVAIL]
00ea681 netdev: octeon3-ethernet: Implement .ndo_stop function.

7f5831a MIPS: OCTEON: Update S.E. files to r99037.
	#SE

3b25a02 updated only the part compiled for Linux
e658b4d OCTEON: Ocla: add overflow to ddr support.

80cb386 MIPS: OCTEON: Update S.E. to r99053.
	#SE

8c3d917 netdev: octeon3-ethernet: Move FCS and padding to BGX.
894b0ac netdev: octeon3-ethernet: Use proper minimum packet size padding for 10G ports.

749b093 MIPS: OCTEON: Update S.E. to r99080.
	#SE

a46cf56 MIPS: OCTEON: Update S.E. to r99089.
	#SE

24e3fb3 MIPS: OCTEON: Fix routing of cn78XX PCIe intA interrupts.
53d6d08 mmc: octeon_mmc DDR support
d1bf344 mmc: octeon_mmc DDR clocks at half SDR by default
9a3f2a7 mmc: octeon_mmc: correct memcpy of short transfer
e5073e3 mmc: octeon_mmc: avoid deadlocks on add/remove host

5f48f71 mmc: octeon_mmc: add card-detect polling
	---
	#REVERTED 212938d

014f6b0 mmc: octeon_mmc: recover from DMA errors
bf9d71c netdev: octeon3-ethernet: Disable SCTP checksum for CN78XX_PASS1.
f81537f netdev: octeon3-ethernet: Set affinity_hints for irqs.

d47750b MIPS: OCTEON: Update S.E. to r99468.
	#SE

462a1db netdev: octeon3-ethernet:  Remove some cvmx probing calls.
ae0c5cd MIPS: OCTEON: Disable error interrupts for Erratum PKI-20858
5f88d64 netdev: octeon3-ethernet:  Fix little endian RX.
e2c61df netdev: octeon3-ethernet: Implement PKI-20775
074504e netdev: octeon3-ethernet: Use separate PKO pools for SSO and PKO.
7756177 mmc: octeon_mmc: Disable debug printing.
d91c00e netdev: octeon3-ethernet: Autoconf the ports if no PHY present.

8859a91 MIPS:OCTEON: Sync up SE files
	#SE

212938d Revert "mmc: octeon_mmc: add card-detect polling"
	---
	#REVERTS 5f48f714267929b1457e3c233fb8724302efcdde.

6ccdf73 Fixed Linux NAND driver and friends
	---
	#REVERTED a3d8e46

a3d8e46 Revert "Fixed Linux NAND driver and friends"
	---
	#REVERTS 6ccdf73

ceeaa4c cleanup scripts/checkpatch.pl error/warning messages

625647a Revert "kvm tool: Add compiler.h to fix compilation errors."
	---
	#REVERTS 26a04345d096796e76a110385d171ec682455c0f

7100192 KVM: MIPS-VZ: Handle KVM_EXIT_MMIO
1ef5539 MIPS: Adapt hypercall numbers in kvm_mipsvz

e2e9a0f Revert "kvm tool: Add it to the tree."
	---
	#REVERTS 9784a8bda30a5035ba5e932cc884725d9cf6fb32

6708247 tools: Add Native Linux KVM Tool (lkvm) as of v3.13-rc1-1449-gf023d13 to the tree.
f6e5743 kvm tools: Adapt signature of kvm_cpu__emulate_io
10afcfc kvm tools, mips: Fix linkage of guest_init.o with octeon3 toolchain
4698e15 MIPS: inst.h: Rename BITFIELD_FIELD to __BITFIELD_FIELD.
b5ade09 MIPS: Move definition of __BITFIELD_FIELD to sharable header.
8335bdb MIPS: paravirt: Misc adaptions to sync /w mainline Linux
0c0f54d MIPS: paravirt: Sync code for pci-virtio-guest.c /w mainline
4bd5eb6 MIPS: paravirt: Use common bitfield macro in pci-virtio-guest.c
7820ade MIPS: paravirt: Sync hypercalls with mainline Linux
7e4d8b2 MIPS: paravirt: Enable more virtio drivers in mips_paravirt_defconfig
7f46013 netdev: ethernet.c: Use at least 8 pko queues per port.

7b8cd3e MIPS: OCTEON: Update S.E. to r100235
	#SE

3e24ef6 netdev: octeon3-ethernet: Use seperate threads for memory allocation.
9dbdcd1 MIPS: Mask/unmask some PKI_GEN_INT bits.
58625ab mips: n32: use compat getsockopt syscall
b1c71e7 mmc: octeon_mmc: Try to avoid OOPs
252b318 Merge MIPS/KVM updates into OCTEON-SDK-3.Y
94f7cc0 kvm tools, mips: Rewrite mips-fix-e_flags.sh so it doesn't use xxd.
6a0b67b MIPS/OCTEON: Add multiple msi support.
a1ee584 netdev: octeon3-ethernet: Pass the correct device ID to free_irq().
6915ed5 MIPS: Load invalid TLB entries on VM size overflow.
caee250 MIPS: Revert most of the KVM hooks in exception handling code.
a020f91 MIPS/KVM: Rewrite exception handling code.

c742987 MIPS: OCTEON: Update NAND driver bug fix from S.E. sources
	#SE

43cb3e1 MIPS: paravirt: Fix off-by-one error that prevented boot w/ numcpus==NR_CPUS

0ad1697 MIPS: OCTEON: Update S.E Files.
	#SE

85f1f4c MIPS/KVM: Remove KVM hooks from thread_struct.
65a454c kvm tools, mips: Fix offset for ELF class 32 in mips-fix-e_flags.sh
168b715 MIPS/KVM: Remove KVM changes to struct pt_regs.
1bd93a2 MIPS: OCTEON: NAND with HW BCH: fix to use private buffer for BCH The caller's buffer can be vmalloced(), which can not be translated into phys addresses for BCH hardware to access, therefore, the priv->data page buffer already used throughout the driver is now also used for source and destination of BCH HW operations.
170fef1 MIPS: OCTEON: Fix missing line in previous commit, typo
5cf92cf virtio_ring/kvm tools: Add barriers before accessing avail->idx, used->idx
3056d92 kvm tools: Introduce common struct for pthread handling for virtio-net
72f07e4 netdev: octeon3-ethernet: Add workaround for 78xx pass 1.x bug PKO-20096.
fd13253 MIPS/KVM: cond_resched() upon reentry to VM.
27cc59f MIPS/KVM: Remove leftover srcu_read_{unlock,lock} from mipsvz_vcpu_run
9718519 MIPS/KVM: Fix emulation of CP0_ErrCtl.
8ddf9f5 MIPS/KVM: Support KVM_CAP_MAX_VCPUS with CONFIG_KVM_MIPS_VZ
d269abd MIPS: Fix demand activation of OCTEON CVMSEG region.
1c40c91 kvm tools: Set names for virtio-net-ctrl and term-poll threads
e8f40d4 MIPS: Octeon: confine hotplug named block to KSEG0 to support N32 apps
e08e0d2 MIPS: Octeon: Get first 256MB from 32-bit addresable memory This amount should satisfy the needs of SWIOTLB and drivers that require 32-bit DMA buffers. The need to explicitly specify the address range becomes obvious when the cvmx_bootmem allocation policy is changed to "last fit", preferring high memory to conserve low memory for clients that really need it, and specify their address range explicitly.
920658c MIPS: OCTEON: Automatically provision CVMSEG space.
a2c20be MIPS: Octeon: Resurrect HOTPLUG_CPU Update the method for locating boot vector with latest bootloader methods, namely named block AND moveable region last 2 words; Fix boot-time SMP coremask handling for >32 cores;

3afa11e MIPS: Octeon: Sync SE files, bootmem "last-fit" policy implemented The "Last fit" policy will allocate memory from the highest physical address that fits the range spec, so that low memory is only used when necesary, or when it is the only remaining free memory. The memory population in setup.c has been already changed to guarantee a fixed amount of 32-bit memory for the kernel in a previous commit.
	#SE

57007b0 netdev: octeon3-ethernet: Add ethtool support.

8048e16 mips: octeon: add mii details for EAP7000/ROUTER7000
	---
	#REVERTED 34fe143

0b5a6ab net: octeon-ethernet: ethtool reset hook for qca833x/at803x support
1c6119c net: phy: add qca833x phy-headed-switch

34fe143 Revert "mips: octeon: add mii details for EAP7000/ROUTER7000"
	---
	#REVERTS 8048e167a69843cc47805c66b87855cabbb210e9.

ca040b2 net: phy: qca833x does not need MDIO_BUS_MUX
757854c MIPS: Octeon: Revise memory allocation from bootloader The heneric MIPS memory initialization does not allow free memory preceding the kernel image itself, make sure all memory that is allocated from firmware follows the kernel image. Cleanup the firmware memory allocation code for clarity.
c054ebe MIPS: OCTEON: Add/Build new cvmx-boot-vector code.
5c02795 watchdog: octeon-wdt: Remove bootloader dependencies.
770fd1b MIPS: OCTEON: Remove oct-app-ctl hooks from SMP handlers.
eb3de99 MIPS: OCTEON: Remove unused include from setup.c
fa3e541 MIPS: OCTEON:  Add sysfs hooks to add and remove CPUs.
21319e7fd MIPS: OCTEON: Update cvmx-boot-vector.c
72240023 Use the compiler-gcc4.h header for all GCC >=4. The versioning scheme for GCC has changed such that the next release is 5.1.0 and then the next year will be 6.1.0.
bb3df74 MIPS: OCTEON: Update cvmx-boot-vector code.
08e4b9f mips: octeon-ethernet: simplify ethtool.reset()
312274e net: phy: qca833x: split _init & unhang-time _re_init
e158c90 mips: octeon-ethernet: extend ethtool PCS-reset to 30mS
dd91308 net: phy: qca833x cleanup, save/restore settings on reset
e4673db mips:octeon-ethernet: drop dead variable
62b9c13 MIPS: OCTEON: Do mb() for octeon_flush_data_cache_page()
e808a73 MIPS: Remove race window in page fault handling
999e97c doc: Add device-tree binding documentation for Cavium CIB.

d970c6e MIPS:OCTEON: Call is_vmalloc_addr() directly
	---
	#REVERTED 61f8ffab5393b1532c2e7817a1e3b22c84515c14

16bafc8 MIPS: OCTEON: Define cvmx_dprintf as pr_debug.
185eec8 netdev: octeon3-ethernet: Poll the state of interfaces without a phy and re-initialize them if needed.

2f9501b MIPS: OCTEON: Sync up OSM and LAP SE files
	#SE

59d2770 MIPS:OCTEON: Fix IO resources start address
7d2839f MIPS: OCTEON: Update some cvmx files.
6c8151b MIPS: OCTEON: Cleanup cvmx.h

cc5d7f2 MIPS: OCTEON: Update cvmx-debug.c from S.E.
	#SE

4dcf8fa MIPS: Remove accidentally committed file kvm_mipsvz_emul.c
7187c53 MIPS: Change type of asid_cache to unsigned long
f697cc6 netdev: octeon3-ethernet: Move netdev_info message to where it prints without errors.
32eaa35 MIPS: OCTEON: cpu_state not just for _HOTPLUG

50c550b MIPS: Octeon: Sync SE files, update ethernet driver to match
	#SE

8806baa MIPS: Octeon: sync SE files to r103928
	#SE

61f8ffa Revert "MIPS:OCTEON: Call is_vmalloc_addr() directly"
	---
	#REVERTS d970c6e5859a96e9619105d07c3533e769e08cab.

3c80579 MM: Export "is_vmalloc_or_module_addr()" pointer validation in modules
0aec724 MIPS:OCTEON: Sync-up cvmx-fpa-resource.c file.
35b1b11 netdev: octeon-bgx-nexus: Only init port config data if probed.
e0b278c MIPS: OCTEON: Trivial, fix a few code formatting issues in setup.c.

e083736 MIPS: OCTEON: Sync-up SE files.
	#SE

bdd7040 netdev: octeon3-ethernet: Fix XLAUI/XFI & RXAUI interfacees.

e0b2881 MIPS: OCTEON: Update S.E. to r104679
	#SE

09b2f64 MIPS: usb: octeon: allow modular usb
8817dda usb: dwc3: simplify OCTEON ifdefs

46f1adc MIPS: usb: octeon cn78xx multinode
	---
	#REVERTED 6d429af

1a842ae MIPS: octeon-ethernet: remove hard-coded pool count
d51787c MIPS: octeon-ethernet: no need for sentinel pool
d4ad773 MIPS: Make XPHYSADDR() work for all addresses.

cc7b99d MIPS: Increase sparsemem MAX_PHYSMEM_BITS to 48.
	---
	#REVERTED 9477842

9477842 Revert "MIPS: Increase sparsemem MAX_PHYSMEM_BITS to 48."
	--- 
	#REVERTS cc7b99d834dd8eb5d905fdbbdd1caeff916abd8b.

0ecffe9 MIPS: Make setting of MAX_PHYSMEM_BITS settable per sub-architecture.
	???
	see also cc7b99d, 9477842

1c93521 MIPS: KVM/MIPSVZ: Implement workaround for GC0_EPC corruption
8dda451 MIPS: paravirt: Fix build error
5940f4b netdev: octeon3-ethernet: Replace wait_event by wait_event_interruptible
83a786b netdev: octeon3-ethernet: Change GFP flags for allocation when holding RCU lock
f27cf02 MIPS:OCTEON: Call appropriate error interrupts based on model.
aa5523d MIPS: Add the concept of BOOT_MEM_KERNEL to boot_mem_map.
fd363e7 MIPS: Allow sub-architecture 'machines' to override bootmem initialization.
dec7e48 MIPS: OCTEON: Add NUMA support for cn78XX

6d429af Revert "MIPS: usb: octeon cn78xx multinode"
	---
	#REVERTS 46f1adcc141366645d18baf356ad50462a9fd6e4.


e610471 netdev:mips: separated interface enabled from port enable

36ddde9 MIPS:OCTEON: Sync up SE files
	#SE

453dce5 Merge branch 'OCTEON-SDK-3.Y' of ssh://cagit1.caveonetworks.com/repo/git/linux/linux-octeon-sdk into OCTEON-SDK-3.Y
	---
	#MERGE

a85578b MIPS: OCTEON:  Try to allocate at least 64MB of DMA32 memory.
df155e5 MIPS: OCTEON: Fix typo in octeon_up_prepare().
f20155b PCI:OCTEON: Fix the array size of pcie devices.

242d261 MIPS: OCTEON: Fix Automatic provisioning CVMSEG space.
	!!! leave it for now

e3388bd MIPS: KVM/MIPSVZ: Fix misc memory leaks
108968f MIPS: KVM/MIPSVZ: Call put_page for mapped user pages
ddbbf49 MIPS: OCTEON:  Try to allocate at least 256MB of DMA32 memory.

531e32d Merge branch 'OCTEON-SDK-3.Y' of ssh://cagit1.caveonetworks.com/repo/git/linux/linux-octeon-sdk into OCTEON-SDK-3.Y
	---
	#MERGE

09ad2f1 MIPS: OCTEON: Don't crash if no memory available on node.
7431da5 MIPS: OCTEON: Cleanup memory initialization and allow for more than 32GB.

68e2229 Merge branch 'OCTEON-SDK-3.Y' of ssh://cagit1.caveonetworks.com/repo/git/linux/linux-octeon-sdk into OCTEON-SDK-3.Y
	---
	#MERGE

0951e27 MIPS: OCTEON: Don't add kernel image when adding memory from named blocks.
5602d30 MIPS: OCTEON: Export __node_data for use in modules.
3db628e MIPS: OCTEON: Use IRQF_NO_THREAD when chaining MSIs

8eae476 Merge branch 'OCTEON-SDK-3.Y' of ssh://cagit1.caveonetworks.com/repo/git/linux/linux-octeon-sdk into OCTEON-SDK-3.Y
	---
	#MERGE

8418f3a6 netdev: octeon3-ethernet:  Add comments about buffer layout.
db8dca7 netdev: octeon3-ethernet:  Fix comment.
c35a500 MIPS: OCTEON: Fix saving of CVMSEG per-task state.
24217a9 PCI:OCTEON: Fix the array size of pcie devices.
901c1a9 netdev: Add MODULE_LICENSE to phy/qca833x.c

7c57f9d Merge branch 'OCTEON-SDK-3.Y' of ssh://cagit1.caveonetworks.com/repo/git/linux/linux-octeon-sdk into OCTEON-SDK-3.Y
	---
	#MERGE

2a6d7f3 netdev: octeon3-ethernet: Performance improvements.

c25a875 Merge branch 'OCTEON-SDK-3.Y' of ssh://cagit1.caveonetworks.com/repo/git/linux/linux-octeon-sdk into OCTEON-SDK-3.Y
	---
	#MERGE

29a81fb MIPS: KVM/MIPSVZ: Fix ASID handling

737ba6d MIPS: OCTEON: Update S.E. files to r105733
	#SE

36ec55e Merge branch 'OCTEON-SDK-3.Y' of ssh://cagit1.caveonetworks.com/repo/git/linux/linux-octeon-sdk into OCTEON-SDK-3.Y
	---
	#MERGE

021a2b6 netdev: octeon-ethernet:  Disable preemption in critical sections of xmit.
d08ed04 MIPS: OCTEON: Remove some unused functions and declarations.
fa4c7fd MIPS: OCTEON: Print warning message if OCTEON II kernel run on earlier chips.

ad9f716 Merge branch 'OCTEON-SDK-3.Y' of ssh://cagit1.caveonetworks.com/repo/git/linux/linux-octeon-sdk into OCTEON-SDK-3.Y
	---
	#MERGE

c048d77 netdev: octeon3-ethernet: get work asynchronously.
21bebab netdev: octeon-pow-ethernet: Add support for CN78XX devices.
ef1076c netdev: octeon3-ethernet: Added app_config export support.
1041df6 MIPS: Sort and merge /proc/iomem RAM regions.

e1276e0 Merge branch 'OCTEON-SDK-3.Y' of ssh://cagit1.caveonetworks.com/repo/git/linux/linux-octeon-sdk into OCTEON-SDK-3.Y
	---
	#MERGE


2c6cfd0 MIPS: OCTEON: Update S.E. to r106025
	#SE

a7d2321 Merge branch 'OCTEON-SDK-3.Y' of ssh://cagit1.caveonetworks.com/repo/git/linux/linux-octeon-sdk into OCTEON-SDK-3.Y
	---
	#MERGE

c0c0a53 Bug #12592 netdev: octeon3-ethernet: Apply SSO-22704 workaround.
f2c5a01 i2c: i2c-octeon: Add support for cn78XX chips.

c042083 Merge branch 'OCTEON-SDK-3.Y' of ssh://cagit1.caveonetworks.com/repo/git/linux/linux-octeon-sdk into OCTEON-SDK-3.Y
	---
	#MERGE

af42d99 Bug #12593 netdev: octeon3-ethernet: Calculate the right L4 checksum for IP fragments.

451731d Merge branch 'OCTEON-SDK-3.Y' of ssh://cagit1.caveonetworks.com/repo/git/linux/linux-octeon-sdk into OCTEON-SDK-3.Y
	---
	#MERGE

c65cb35 MIPS:OCTEON: Reduce the size of IO resources
ead8763 netdev: octeon3-ethernet: Use the number of fragments when recycling skbs.
53e5597 netdev: octeon-bgx-nexus: Request octeon3-ethernet driver...
3e506f4 MIPS: OCTEON: Define cpu_has_local_ebase to 0
6889e59 MIPS: tlbex/kvm: Allow create KVM specific TLB Refill handler.
cff4f4d MIPS: Make KVM_MIPS_VZ *not* depend on !FAST_ACCESS_TO_THREAD_POINTER
9ef92a9 netdev: octeon3-ethernet: Temporary fix for apparent memory corruption.
c69d694 netdev: octeon3-ethernet: Don't set PKO_SEND_HDR_S[N2] to 1 in Pass-1 chips
684b82f MIPS: OCTEON: Implement of_node_to_nid()
cb6959f netdev: Octeon3-ethernet: Don't swap packet linked pointers in LE mode. Signed-off-by: Vinita Gupta <vgupta@caviumnetworks.com>
6083226 MIPS: OCTEON: Handle NULL of_node in of_node_to_nid().
7f54579 raid6/test: fix makerule syntax
02dc733 MIPS: octeon-i2c: export twsix symbols for usb modules
879dcd0 gpio: gpio-octeon: Add support for multiple GPIO controllers.
f1a8fb8 MIPS: OCTEON: Define NR_IRQS_LEGACY.
5c540d9 MIPS: OCTEON: Panic if non-NUMA kernel is executed on multi-node system.
0c08e6f MIPS: OCTEON: Fix interrupt controller code for multi-node/NUMA
8de7f5d watchdog: octeon-wdt: Correct spelling and make do_countdown boolean.
303503c watchdog: octeon-wdt: Disable building as a module.
d238d14 watchdog: octeon-wdt: Fix to work on multi-node systems.
a734e33 MIPS: OCTEON: Rename csrc-octeon clocksource variables for clarity.
8719780 MIPS: OCTEON: Add csrc-fpa-clk.
305193b Fix compile error in case CONFIG_FAST_ACCESS_THREAD_REGISTER=n
f7d7106 genirq: Add irq_domain-aware core IRQ handler
ce66a58 MIPS: OCTEON: Use handle_domain_irq to fix suspicious RCU usage
e25f108 MIPS: Call trace_hardirqs_on before irqs are re-enabled in syscall_exit_work
c1d994c MIPS: OCTEON: #define a bunch of topology.h symbols.
2e01593 MIPS: OCTEON: Fix octeon_ciu3_errbits_enable_intsn() for multi-node.
c65e803 MIPS: OCTEON: Fix octeon-error-tree.c for multi-node cn78XX.
8bd00e8 MIPS: OCTEON: Define cvmx_get_local_core_num()

9902ad8 MIPS: OCTEON: Update S.E. to r107316
	#SE

9f21d12 netdev: octeon3-ethernet: Fix for NUMA operation.
2434510 MIPS: KVM/MIPSVZ: Add hypercall to pass host time to guest
acefbcb MIPS: paravirt: Add new clocksource based on host time (in ns)


645bf34 netdev: octeon3-ethernet: Don't try to calculate IPv6 checksums.
	---
	#REVERTED ae0b78b

ae0b78b Revert "netdev: octeon3-ethernet: Don't try to calculate IPv6 checksums."
	---
	#REVERTS 645bf34f7066c96965e614dc7b124421a0a242ad.

09d0598 netdev: octeon3-ethernet: Fix IPv6 TCP and UDP checksum generation.

4d880ee MIPS: Linux: Update S.E. to r107520 and adjust callers.
	#SE

c6907be MIPS: Supply OCTEON-II specific read/write lock implementation.

3d04319 MIPS: OCTEON: Update S.E. to r107786
	#SE

13d5d9c usb: xhci-octeon: Fix for multi-node systems.
24e7b51 MIPS: Select USB_ARCH_HAS_XHCI for CAVIUM_OCTEON_SOC
