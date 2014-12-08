Public
------

- octeon_patches.22.move_change_load_address

	move "MIPS: OCTEON: Change load address to waste less memory." to the end of the patchset at it depends on CONFIG_MAPPED_KERNEL that was introduced later in
	"MIPS: OCTEON: Add support for running kernel in mapped address space."

- octeon_serial.01 -- a patch from David that has been sent upstream

- octeon_patches_SE01.14 -- David has comments on this branch

- octeon_patches.17.SE01 -- frozen work, till the first set of patches are sent upstream

Local
-----

- octeon_patches.22.test

	same as octeon_patches.22.move_change_load_address, but only up to "MIPS: OCTEON: Implement DCache errata workaround for all CN6XXX" for building/testing

- octeon_patches.21.v3.18 --

	rebased to v3.18
	Octeon -> OCTEON in subject

- octeon_patches.20.rebase --

	"MIPS: OCTEON Handle bootloader structures in little-endian mode.": Let's defer this patch.  In our current SDK kernel, I think we have removed all code that uses these, so it is probably unneeded.

	"9734af5 MIPS: OCTEON: Make cvmx-bootmem and packet I/O functions work Little Endian.": Introduces too many coding style changes, Let's also defer this patch for a little while.  We need to be very careful with these and only include necessary changes, and no formatting changes that are unrelated to the code changes.  For these cvmx-* files, we want to see if there are changes that should be made to our local copies that will decrease the size of future patches.

- octeon_patches.19.compile_octeon_III --

	"MIPS: Octeon: Do not require octeon3 instruction set" This must be folded into the earlier commit ("MIPS: OCTEON: Save/Restore wider multiply registers in OCTEON III CPUs"), so buildability is never broken.

- octeon_patches.18.BITFIELD_FIELD --

	The second part of the change "MIPS: OCTEON: Add little-endian support to asm/octeon/octeon.h" (to union octeon_cvmemctl) must be rewritten to use the __BITFIELD_FIELD() macro as is done in arch/mips/include/uapi/asm/inst.h

Archive
-------



