# Rust Kernel Virtual Machine

RKVM is a basic kernel with a complicated virtual machine setup.

## Current ideas

- Kernel with the ability to be live-replaced without restarting, virtual machine host.
- User-space is a virtual machine you can switch between.
- Depending on the current VM being used, all hardware is passed through to it, unless configured for limitations and/or virtual hardware.
- RAM can mostly be given to VM, except for the size of the kernel and (don't suspend to memory please) VM image(s). (likely >100M)
- Switching between VMs will likely be a [suspend-to-memory/disk->debind hardware->load new VM from memory/disk->rebind hardware->finish loading] operation.
- Hardware-to-VM-and-back interpretation for penultimate performance of hardware, without having to pass through and rebind? (Such as GPU acceleration)
- At least one keyboard must be connected to the host for keybind operations pertaining to VM management, a virtual keyboard will be used on guests instead.

		[Hardware]
		 [Kernel]
	[VM 1] [VM 2] [VM 3] [...]
