ANDROID_TOP_DIR=$(shell realpath ../../..)

CPPFLAGS+= \
    -fPIC \
    -DBUILD_WITH_LINARO \
    -I$(ANDROID_TOP_DIR)/system/core/include
LDFLAGS+= -shared

SOURCES = \
    FileMap.cpp \
    JenkinsHash.cpp \
    LinearTransform.cpp \
    Log.cpp \
    NativeHandle.cpp \
    Printer.cpp \
    PropertyMap.cpp \
    RefBase.cpp \
    SharedBuffer.cpp \
    Static.cpp \
    StopWatch.cpp \
    String8.cpp \
    String16.cpp \
    SystemClock.cpp \
    Threads.cpp \
    Timers.cpp \
    Tokenizer.cpp \
    Unicode.cpp \
    VectorImpl.cpp \
    misc.cpp

OBJECTS=$(patsubst %.cpp,%.o,$(SOURCES))

TARGET=libutils.so

all: $(TARGET)

$(TARGET): $(OBJECTS)
	$(CXX) $(CPPFLAGS) $(OBJECTS) -o $@ $(LDFLAGS)

%.o: %.cpp
	$(CXX) -c $(CPPFLAGS) -o $@ $<

clean:
	rm -rf $(OBJECTS) $(TARGET)

.PHONY: clean all
