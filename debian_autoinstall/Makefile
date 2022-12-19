.phony: help
help:
	@echo "qemu-inst: Install system from ISO"
	@echo "qemu-boot: Boot installed system"

HDD_IMG_SIZE ?= 10G
QEMU ?= qemu-system-x86_64
QEMU_OPTS = -machine q35 -cpu host -accel hvf -smp 2 -m 4G
ISO ?= ~/.local/debinst/preseed-debian-11.6.0-amd64-netinst.iso

root.img:
	@qemu-img create -f qcow2 root.img $(HDD_IMG_SIZE)

.phony: qemu-inst
qemu-inst: root.img
	$(QEMU) $(QEMU_OPTS) \
		-hda root.img \
		-cdrom $(ISO)

.phony: qemu-boot
qemu-boot: root.img
	$(QEMU) $(QEMU_OPTS) \
		-hda root.img

.phony: clean
clean:
	@rm -f root.img
