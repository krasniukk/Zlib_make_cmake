CXX = gcc
CFLAGS = -fPIC -Wall -Wextra -O2 -g
LDFLAGS = -shared
BIN_DIR = bin
OBJ_DIR = obj
TARGET_STATIC = zlib.a
TARGET_SHARED = zlib.so
SOURCES = adler32.c compress.c crc32.c deflate.c gzclose.c gzlib.c gzread.c gzwrite.c infback.c inffast.c inflate.c inftrees.c trees.c uncompr.c zutil.c
OBJS = $(patsubst %.c,$(OBJ_DIR)/%.o,$(SOURCES))

all: create_dirs $(BIN_DIR)/$(TARGET_STATIC) $(BIN_DIR)/$(TARGET_SHARED) clean

create_dirs:
	mkdir -p $(BIN_DIR)
	mkdir -p $(OBJ_DIR)

-include $(OBJS:.o=.d)

$(BIN_DIR)/$(TARGET_STATIC): $(OBJS)
	ar rcs $@ $^

$(BIN_DIR)/$(TARGET_SHARED): $(OBJS)
	$(CXX) -shared -fPIC -o $@ $^

$(OBJ_DIR)/%.o: %.c
	$(CXX) -fPIC -c $(CFLAGS) $< -o $@
	$(CXX) -MM -MP -MT $@ -MF $(OBJ_DIR)/$*.d $(CFLAGS) $<



.PHONY : clean
clean:
	rm -rf $(OBJ_DIR)/*.d
