CXX = gcc
BIN_DIR = bin
OBJ_DIR = obj
PRG_EXE = examples_exe
PRG_EXE_1 = examples_exe_1
INCLUDES = -I../library
LIBS_PATH = -L../library/bin
LIBS = -l:zlib.so
CFLAGS = -O3 $(INCLUDES)
LIBNAME = $(shell pwd)/../library/bin/zlib.so

all: create_dirs $(BIN_DIR)/$(PRG_EXE) $(BIN_DIR)/$(PRG_EXE_1)

create_dirs:
	mkdir -p $(BIN_DIR)
	mkdir -p $(OBJ_DIR)

$(OBJ_DIR)/minigzip.o: minigzip.c ../library/zlib.h
	$(CXX) $(CFLAGS) -c minigzip.c -o $(OBJ_DIR)/minigzip.o

$(OBJ_DIR)/example.o: example.c ../library/zlib.h
	$(CXX) $(CFLAGS) -c example.c -o $(OBJ_DIR)/example.o

$(BIN_DIR)/$(PRG_EXE): $(OBJ_DIR)/example.o
	$(CXX) -o $@ $^ $(LIBS_PATH) $(LIBNAME)

$(BIN_DIR)/$(PRG_EXE_1): $(OBJ_DIR)/minigzip.o
	$(CXX) -o $@ $^ $(LIBS_PATH) $(LIBNAME)
