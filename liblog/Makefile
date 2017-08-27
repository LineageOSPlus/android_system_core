ANDROID_TOP_DIR=$(shell realpath ../../..)

CFLAGS+= \
    -fPIC \
    -DBUILD_WITH_LINARO \
    -DLIBLOG_LOG_TAG=1005 \
    -DSNET_EVENT_LOG_TAG=1397638484 \
    -I$(ANDROID_TOP_DIR)/frameworks/native/include \
    -I$(ANDROID_TOP_DIR)/system/core/include \
    -I$(ANDROID_TOP_DIR)/libnativehelper/include
LDFLAGS+= -shared

SOURCES = \
	log_event_list.c \
	log_event_write.c \
	logger_write.c \
	config_write.c \
	logger_name.c \
	logger_lock.c \
	event_tag_map.c \
	config_read.c \
	log_is_loggable.c \
	logprint.c \
	pmsg_reader.c \
	pmsg_writer.c \
	logd_reader.c \
	logd_writer.c \
	logger_read.c

OBJECTS=$(patsubst %.c,%.o,$(SOURCES))

TARGET=liblog.so

all: $(TARGET)

$(TARGET): $(OBJECTS)
	$(CC) $(CFLAGS) $(OBJECTS) -o $@ $(LDFLAGS)

%.o: %.cpp
	$(CC) -c $(CFLAGS) -o $@ $<

clean:
	rm -rf $(OBJECTS) $(TARGET)

install:
	install -m 0644 -D $(TARGET) $(DESTDIR)/usr/lib/$(TARGET)

.PHONY: clean install all
