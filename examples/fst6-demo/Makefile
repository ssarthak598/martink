build-fst6-demo: build
	$(CXX) $(CXXFLAGS) -fno-exceptions -fno-rtti -c examples/fst6-demo/main.cpp -o examples/fst6-demo/main.o
	$(LD) -L$(srctree) $(LDFLAGS) -o examples/fst6-demo/fst6-demo -Wl,--start-group \
		 examples/fst6-demo/main.o -lk-$(BUILD) -lc -lm -lgcc \
	-Wl,--end-group 
	
install-fst6-demo:
	arm-none-eabi-objcopy -j .text -j .data examples/fst6-demo/fst6-demo examples/fst6-demo/fst6-demo.bin -O binary
	make -C $(srctree)/scripts/stm32flash/
	arm-none-eabi-size examples/fst6-demo/fst6-demo
	sudo $(srctree)/scripts/stm32flash/stm32flash -w examples/fst6-demo/fst6-demo.bin -v -g 0x0 /dev/ttyUSB0
