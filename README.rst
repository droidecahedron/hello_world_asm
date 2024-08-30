.. _hello_world:

hello_world_asm
###########

Overview
********
!!! Requires cortex-m33 device, such as a nrf5340 !!!

This sample prints to the console and has inline assembly and c-callable assembly blocks to show ways you can accomplish it in Zephyr/nRF Connect SDK.
This was tested on an nRF5340DK.


Sample Output
=============

.. code-block:: console

    *** Booting nRF Connect SDK v2.7.0-5cb85570ca43 ***
    *** Using Zephyr OS v3.6.99-100befc70c74 ***
    Hello World from: nrf5340dk/nrf5340/cpuapp/ns running Zephyr
    This application will add numbers using inline assembly and an externally called assembly function

    inline assembly: clearing r0, adding 7 to r0 then storing to r0.
            added 7 to register 0, stored in register zero.
            result (r0 value): 7

    external assembly function called in C.
            5 + 7 = 12 via asm

Extra Notes
=============
`m33 Register Description <https://developer.arm.com/documentation/100230/0004/functional-description/programmers-model/processor-core-registers-summary?lang=en#:~:text=When%20the%20Armv8-M%20Security%20Extension%20is%20included%2C%20there,the%20Non-secure%20state.%20PSP_S%20for%20the%20Secure%20state.>`_

`m33 instruction set <https://developer.arm.com/documentation/100235/0004/the-cortex-m33-instruction-set/cortex-m33-instructions>`_

.. code-block:: c
    // extra comments for my own edification
    /* #define _addb_(src, dest)	__asm__("addb %1, %0" : "=r" (dest) : \
                        "ri" ((unsigned char)src), "0" (dest) : "cc")
    */
    // register int regzero asm ("r0");
    //	__asm__ ("mrs %0, msp" : "=r" (r0) );
    // extern "C" {int a_add(int a, int b);}
    //__asm__ ("mov %0, r0" : "=r" (r0) ); // move register 0 to.. register 0?
