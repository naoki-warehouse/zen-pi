kernel.img: boot.zen
	zen build-exe boot.zen -target armv6-freestanding-eabihf --linker-script rpi.ld
	arm-none-eabi-objcopy -O binary boot kernel.img


run: kernel.img
	@qemu-system-arm \
	-kernel $< \
	-append "qemu" \
	-cpu arm1176 \
	-M versatilepb \
	-m 256 \
	-no-reboot \
	-nographic \
	-monitor null \
	-serial stdio

debug: kernel.img
	@qemu-system-arm \
	-kernel $< \
	-append "qemu" \
	-cpu arm1176 \
	-M versatilepb \
	-m 256 \
	-no-reboot \
	-nographic \
	-monitor null \
	-serial stdio \
	-gdb tcp::4321 -S

clean:
	rm kernel.img boot boot.o
