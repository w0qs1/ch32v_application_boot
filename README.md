CH32V003 Application for the designed bootloader.

This is a sample application (led blink) designed to be used with the bootloader (https://github.com/w0qs1/ch32v_bootloader).

Changes made in the linker script(Link.ld):
1. Start of the application section is from 0x00000C00 with length 13K - 64.
2. Added one more section for storing end of text, location of SystemInit and location of main (64B).
3. The added section has been defined.
4. End of text (_etext) has been shifted to the start of .fini section (for proper length with alignment to 2B instead of 4B).

Steps for creating an application:
1. Modify the linker script as mentioned or use the script given.
2. Write the application code as usual.
3. Interrupt table is mapped to the application section, so no need to worry about interrupt vectors jumping to bootloader section.
3. Keep note of the length of the application as the possible size has been reduced from 16K to 13K-64.