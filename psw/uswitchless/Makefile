#
# Copyright (C) 2011-2019 Intel Corporation. All rights reserved.
#
# Redistribution and use in source and binary forms, with or without
# modification, are permitted provided that the following conditions
# are met:
#
#   * Redistributions of source code must retain the above copyright
#     notice, this list of conditions and the following disclaimer.
#   * Redistributions in binary form must reproduce the above copyright
#     notice, this list of conditions and the following disclaimer in
#     the documentation and/or other materials provided with the
#     distribution.
#   * Neither the name of Intel Corporation nor the names of its
#     contributors may be used to endorse or promote products derived
#     from this software without specific prior written permission.
#
# THIS SOFTWARE IS PROVIDED BY THE COPYRIGHT HOLDERS AND CONTRIBUTORS
# "AS IS" AND ANY EXPRESS OR IMPLIED WARRANTIES, INCLUDING, BUT NOT
# LIMITED TO, THE IMPLIED WARRANTIES OF MERCHANTABILITY AND FITNESS FOR
# A PARTICULAR PURPOSE ARE DISCLAIMED. IN NO EVENT SHALL THE COPYRIGHT
# OWNER OR CONTRIBUTORS BE LIABLE FOR ANY DIRECT, INDIRECT, INCIDENTAL,
# SPECIAL, EXEMPLARY, OR CONSEQUENTIAL DAMAGES (INCLUDING, BUT NOT
# LIMITED TO, PROCUREMENT OF SUBSTITUTE GOODS OR SERVICES; LOSS OF USE,
# DATA, OR PROFITS; OR BUSINESS INTERRUPTION) HOWEVER CAUSED AND ON ANY
# THEORY OF LIABILITY, WHETHER IN CONTRACT, STRICT LIABILITY, OR TORT
# (INCLUDING NEGLIGENCE OR OTHERWISE) ARISING IN ANY WAY OUT OF THE USE
# OF THIS SOFTWARE, EVEN IF ADVISED OF THE POSSIBILITY OF SUCH DAMAGE.
#
#

include ../../buildenv.mk

# CXXFLAGS += -fPIC -Werror -g
CFLAGS += -Werror -D_GNU_SOURCE -fPIC -g
CFLAGS += $(ADDED_INC)

CFLAGS += -I$(SGX_HEADER_DIR)          \
          -I$(COMMON_DIR)/inc          \
          -I$(COMMON_DIR)/inc/internal

OBJS := sl_fcall_mngr_untrusted.o \
		sl_siglines_untrusted.o \
		sl_workers_untrusted.o \
		sgx_ecall_switchless_untrusted.o \
		sl_uswitchless_untrusted.o \
		sl_fcall_mngr_common.o \
		sl_once_common.o \
		sl_memlog_common.o \
		sl_siglines_common.o

vpath %.c $(COMMON_DIR)/src

LIBUSWITCHLESS := libuswitchless.a

.PHONY: clean all
all: $(LIBUSWITCHLESS)

$(LIBUSWITCHLESS): $(OBJS)
	$(AR) rcs $@ $^

$(OBJS): %.o: %.c
	$(CC) -c $(CFLAGS) $< -o $@

.PHONY: clean
clean:
	@$(RM) $(LIBUSWITCHLESS) $(OBJS)
