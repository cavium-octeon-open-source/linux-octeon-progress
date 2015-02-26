ethernet.c

in de87944^
11f4318 MIPS: OCTEON: netdev/ethernet Fix build error
fd9bc4f netdev: octeon-ethernet: Add support for Little Endian kernels.
721cbcb netdev/staging: octeon-ethernet: Only initialize PHYs when a netdevice is open
83b3ab9 netdev/staging: octeon-ethernet: Clean up PHY handling.

in HEAD
dab363f Merge tag 'staging-3.19-rc1' of git://git.kernel.org/pub/scm/linux/kernel/git/gregkh/staging
030739f staging: octeon-ethernet: drop multiple NAPI instances
a4652e8 staging: octeon: drop owner assignment from platform_drivers
6c71ea5 staging: octeon: Fix warning of prefer ether_addr_copy.
99f8dbc staging: octeon: Fix line 80 characters in ethernet.c
0a5fcc6 staging: octeon: Fix quoted string split warning.
39bc751 staging: octeon: Fix missing blank line warning.
ec3a220 staging: octeon-ethernet: Move PHY activation to .ndo_open().
7ad24ea net: get rid of SET_ETHTOOL_OPS
9041961 staging: octeon-ethernet: make num_packet_buffers static
5ff8bebb staging: octeon-ethernet: drop CONFIG_CAVIUM_OCTEON_NUM_PACKET_BUFFERS
885a947 staging: delete non-required instances of include <linux/init.h>
4d97845 staging: octeon: drop redundant mac address check
851ec8c staging: octeon: Removed space at start of line
b186410 staging: octeon: Fixed line over 80 chars warning

ethernet-mdio.c

in de87944^
721cbcb netdev/staging: octeon-ethernet: Only initialize PHYs when a netdevice is open
83b3ab9 netdev/staging: octeon-ethernet: Clean up PHY handling.

in HEAD
ec3a220 staging: octeon-ethernet: Move PHY activation to .ndo_open().
de82a6d staging: octeon: ethernet-mdio.c Fix line over 80 characters.
0da50c6 staging:octeon: remove space after opening parentheses

ethernet-mem.c

in de87944^

in HEAD
883d29e Staging: octeon: minor style cleanups
8a125b0 staging:octeon: Replace pr_warning by preferred pr_warn
5c2f26d staging: octeon-ethernet: add missing include
a5de43c staging: octeon-ethernet: remove skb alloc failure warnings

ethernet-rgmii.c

in de87944^
721cbcb netdev/staging: octeon-ethernet: Only initialize PHYs when a netdevice is open
83b3ab9 netdev/staging: octeon-ethernet: Clean up PHY handling.

in HEAD
42e0e19 staging: octeon: Combined seperate strings.
5a2da4a staging: octeon: Fix missing blank line warning.
ec3a220 staging: octeon-ethernet: Move PHY activation to .ndo_open().
f09d144 staging/octeon:ethernet-rgmii.c: Fix line over 80 characters.
4504b1b Staging: octeon: Fix coding style
54bf917 staging: octeon-ethernet: make global_register_lock static
7cc4fa1 staging: octeon-ethernet: rgmii: enable interrupts that we can handle

ethernet-rx.c

in de87944^

in HEAD
f884625 staging: octeon: Fix checkpatch 80 character limit warnings
030739f staging: octeon-ethernet: drop multiple NAPI instances
a6a39a7 staging: octeon-ethernet: disable load balance for receiving packet when CONFIG_RPS is enabled.
61e15f0 staging: octeon: Combined seperate strings.
885a947 staging: delete non-required instances of include <linux/init.h>
d2ca24c staging: octeon-ethernet: allow to use only 1 CPU for packet processing
cd39f73 staging: octeon-ethernet: allow to set IRQ smp_affinity freely
811a751 staging: octeon: Fix typo in staging/octeon
a5de43c staging: octeon-ethernet: remove skb alloc failure warnings
da029d0 staging: octeon-ethernet: make dropped packets to consume NAPI budget

ethernet-sgmii.c

in de87944^
721cbcb netdev/staging: octeon-ethernet: Only initialize PHYs when a netdevice is open
83b3ab9 netdev/staging: octeon-ethernet: Clean up PHY handling.

in HEAD
c2e9154 Staging: octeon: Missing a blank line after declarations
ec3a220 staging: octeon-ethernet: Move PHY activation to .ndo_open().

ethernet-spi.c

in de87944^
721cbcb netdev/staging: octeon-ethernet: Only initialize PHYs when a netdevice is open

in HEAD
d7c9fde Staging: octeon: quoted string split across lines in ethernet-spi.c

ethernet-tx.c

in de87944^
fd9bc4f netdev: octeon-ethernet: Add support for Little Endian kernels.

in HEAD
b9fc9cf Staging: octeon: ethernet-tx: fixed coding style warnings, missing blank lines
cd6362b Merge git://git.kernel.org/pub/scm/linux/kernel/git/davem/net-next
8b6da5f staging/octeon-ethernet: Call dev_kfree/consume_skb_any instead of dev_kfree_skb.
54396b6 staging: octeon-ethernet: make cvm_oct_free_tx_skbs static
885a947 staging: delete non-required instances of include <linux/init.h>
a012649 Staging: octeon: fix line over 80 characters in ethernet-tx.c
6b478c2 Staging: octeon: fix quoted string split across lines in ethernet-tx.c
811a751 staging: octeon: Fix typo in staging/octeon

ethernet-xaui.c

in de87944^
721cbcb netdev/staging: octeon-ethernet: Only initialize PHYs when a netdevice is open
83b3ab9 netdev/staging: octeon-ethernet: Clean up PHY handling.

in HEAD
e2ce061 Staging: octeon: Fix missing blank line warning.
38064eb staging: octeon: fix coding style
ec3a220 staging: octeon-ethernet: Move PHY activation to .ndo_open().

ethernet-defines.h

in de87944^

in HEAD
5ff8bebb staging: octeon-ethernet: drop CONFIG_CAVIUM_OCTEON_NUM_PACKET_BUFFERS

ethernet-mdio.h

in de87944^
721cbcb netdev/staging: octeon-ethernet: Only initialize PHYs when a netdevice is open

in HEAD
885a947 staging: delete non-required instances of include <linux/init.h>

ethernet-util.h

in de87944^

in HEAD
aa66d88 staging: octeon: Removed unnecessary else expression.

octeon-ethernet.h

in de87944^

721cbcb netdev/staging: octeon-ethernet: Only initialize PHYs when a netdevice is open
83b3ab9 netdev/staging: octeon-ethernet: Clean up PHY handling.

in HEAD
030739f staging: octeon-ethernet: drop multiple NAPI instances 
ec3a220 staging: octeon-ethernet: Move PHY activation to .ndo_open().
3661cdf staging: octeon: octeon-ethernet.h Fix Unnecessary space after function pointer name

