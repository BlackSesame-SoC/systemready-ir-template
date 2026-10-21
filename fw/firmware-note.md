# Firmware Configuration

1. `u-boot-adas.bin` is a U-Boot image that supports EFI boot. Flash it using the official BST flashing tool.
2. Use `dd` to write an open-source Linux ISO with kernel version v7.2 or later to a USB drive.
3. After running `dd`, copy the DTB from the `fw` directory to `efi/boot/` on the USB drive.
4. Configure `bootcmd` as follows:

   ```console
   usb start;load usb 0:2 0x8d9000000 efi/boot/bootaa64.efi;load usb 0:2 0x8d0000000 efi/boot/bstc1200-uefi.dtb;bootefi 0x8d9000000 0x8d0000000
   ```

5. Run `bootcmd`.
