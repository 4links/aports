all:	uboot_tool boot.scr
uboot_tool: uboot.c
	$(CC) -Wall -static -static-libgcc $< -o $@
boot.scr: boot.cmd
	mkimage -A arm64 -T script -C none -n "Boot script" -d $< $@
clean:
	rm -r uboot_tool
	rm -r boot.scr
install: uboot_tool boot.scr
	install -D -m 755 uboot_tool $(DESTDIR)/usr/sbin/uboot_tool
	install -D -m 755 boot.scr $(DESTDIR)/uboot/boot.scr
