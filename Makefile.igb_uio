# SPDX-License-Identifier: GPL-2.0
#
# Makefile & Kbuild file for building installing the igb_uio.ko driver
# options make, make install, make clean ...

IGB_UIO_VERSION ?= weka1.0.3

#default is to compile against the running kernel (kernel-devel installed on the system)
# do 'make KERNEL_PATH=/home/user/my_kernel_path/ to compile against an alternative path
KERNEL_PATH ?= /lib/modules/$(shell uname -r)/build
PWD := $(shell pwd)

# ~~~ This Part is the Kbuild side
EXTRA_CFLAGS = -Wall -I$(PWD) -D "IGB_UIO_VERSION=$(IGB_UIO_VERSION)"

obj-m := igb_uio.o

# ~~~ This part is so we can use make inside the source dir to make below target options
#
# this is the STD way to compile an out of tree Kernel module
all: igb_uio.c igb_uio.h compat.h Makefile
	make -C $(KERNEL_PATH) M=$(PWD) modules

# Kernel's modules_install is suppose to also do depmod
install:
	make -C $(KERNEL_PATH) M=$(PWD) modules_install

clean:
	make -C $(KERNEL_PATH) M=$(PWD) clean
