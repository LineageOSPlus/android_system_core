ANDROID_TOP_DIR=$(shell realpath ../../..)

SOURCES = \
    config_utils.c \
    fs_config.c \
    canned_fs_config.c \
    hashmap.c \
    iosched_policy.c \
    load_file.c \
    native_handle.c \
    open_memstream.c \
    process_name.c \
    record_stream.c \
    sched_policy.c \
    strdup16to8.c \
    strdup8to16.c \
    strlcpy.c \
    threads.c \
    fs.c \
    multiuser.c \
    socket_inaddr_any_server_unix.c \
    socket_local_client_unix.c \
    socket_local_server_unix.c \
    socket_loopback_client_unix.c \
    socket_loopback_server_unix.c \
    socket_network_client_unix.c \
    str_parms.c

CFLAGS+= \
    -fPIC \
    -DBUILD_WITH_LINARO \
    -I$(ANDROID_TOP_DIR)/system/core/include
LDFLAGS+= -shared

OBJECTS=$(patsubst %.c,%.o,$(SOURCES))

TARGET=libcutils.so

all: $(TARGET)

$(TARGET): $(OBJECTS)
	$(CC) $(CFLAGS) $(OBJECTS) -o $@ $(LDFLAGS)

%.o: %.cpp
	$(CC) -c $(CFLAGS) -o $@ $<

clean:
	rm -rf $(OBJECTS) $(TARGET)

.PHONY: clean all
