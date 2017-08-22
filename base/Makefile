ANDROID_TOP_DIR=$(shell realpath ../../..)

CPPFLAGS+= \
    -fPIC \
    -DBUILD_WITH_LINARO \
    -I$(ANDROID_TOP_DIR)/frameworks/native/include \
    -I$(ANDROID_TOP_DIR)/system/core/include \
    -I$(ANDROID_TOP_DIR)/libnativehelper/include \
    -Iinclude/
LDFLAGS+= -shared

SOURCES = \
    file.cpp \
    logging.cpp \
    parsenetaddress.cpp \
    stringprintf.cpp \
    strings.cpp \
    test_utils.cpp \
    errors_unix.cpp \

OBJECTS=$(patsubst %.cpp,%.o,$(SOURCES))

TARGET=libbase.so

all: $(TARGET)

$(TARGET): $(OBJECTS)
	$(CXX) $(CPPFLAGS) $(OBJECTS) -o $@ $(LDFLAGS)

%.o: %.cpp
	$(CXX) -c $(CPPFLAGS) -o $@ $<

clean:
	rm -rf $(OBJECTS) $(TARGET)

.PHONY: clean all
