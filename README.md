Nuttx STM32F4 Discovery Base Board
-------------

    cd nuttx-stm32f4disc-bb/nuttx
    cd tools  
    ./configure.sh stm32f4discovery/bb
    cd ..

Building
---------

    make CROSSDEV=arm-none-eabi-


Modify Config
--------------------

    vi configs/stm32f4discovery/bb/defconfig
    cd tools
    ./configure.sh stm32f4discovery/bb
    cd ..


Programming
------------

    openocd -f board/stm32f4discovery.cfg -c "init" -c "reset halt" -c "flash write_image erase nuttx.bin 0x08000000 bin" -c "reset run" -c "exit"


Debugging
-------

    openocd -f board/stm32f4discovery.cfg -c "init"
    arm-none-eabi-gdb -tui nuttx -ex 'target remote localhost:3333' -ex 'monitor reset halt' -ex 'load'  -ex 'continue'


