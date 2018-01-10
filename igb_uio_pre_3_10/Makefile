KERNEL_PATH := /lib/modules/$(shell uname -r)/build
PWD := $(shell pwd)

EXTRA_CFLAGS = -Winline -Wall -Werror -I$(src)
obj-m := igb_uio.o

all:
	make -C $(KERNEL_PATH) M=$(PWD) modules

clean:
	make -C $(KERNEL_PATH) M=$(PWD) clean
