sweet16_vic20
=============

A port of Apple's Sweet 16 pseudo machine interpreter, written by Steve Wozniak, over to the Commodore VIC-20.  This code creates a 16-bit virtual machine in around 300 bytes.  The port is written for the [XA](https://www.floodgap.com/retrotech/xa/) assembler.


The original Sweet 16 source code has been published a number of times including in [Byte Magazine Volume 02 Number 11 - November 1977](https://archive.org/details/byte-magazine-1977-11-rescan/page/n151/mode/2up).  In this article Steve Wozniak encourages users to modify Sweet 16 and even to port it to other processors, so hopefully he won't mind its being ported to the Vic.  However, despite this and the fact that the code is widely available, it is still probably under copyright and therefore the port relies on patching the original source code rather than supplying a complete version.

## Patching Sweet 16 Source Code for the VIC-20

The source used for patching is from the article: [Porting Sweet 16](http://www.6502.org/source/interpreters/sweet16.htm).  Save the Sweet 16 source code from this article, with no blank lines at the top or bottom, in a file called _sweet16-original.asm_.  Then patch it using the following:

    patch -o sweet16.a65 -l sweet16-original.a65 sweet16_vic20.patch

You will now have a file called _sweet16.a65_.

If you are using a different version of the original source code then you will have to manually inspect the patch file to see the changes.

## Assembling Test

The test code uses `#include` to include the ported Sweet 16 code and runs a test of memory copying using the Sweet 16 VM.  To assemble the test:

    $ xa -o test-sweet16.prg test-sweet16.a65

Now on a VIC-20 load the program:

    LOAD "*",8,1
    SYS 4744


The screen should show:

    TESTING
    MEMCPY...PASS
    MUL......PASS
    NEGATE...PASS


# Licence

## Original Sweet 16 Source Code
The original Sweet 16 source code retains its original copyright and I make no claim on that, nor do I make any claim on the copyright of the parts changed.

## Test Source Code

The test source code is released into the public Domain.

<p xmlns:dct="http://purl.org/dc/terms/">
  <a rel="license"
     href="http://creativecommons.org/publicdomain/zero/1.0/">
    <img src="https://licensebuttons.net/p/zero/1.0/88x31.png" style="border-style: none;" alt="CC0" />
  </a>
  <br />
  To the extent possible under law,
  <a rel="dct:publisher"
     href="https://lawrencewoodman.github.io">
    <span property="dct:title">Lawrence Woodman</span></a>
  has waived all copyright and related or neighboring rights to
  this work.
</p>
