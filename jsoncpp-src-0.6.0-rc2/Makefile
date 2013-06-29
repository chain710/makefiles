GXX = g++
GCC = gcc
AR = ar

INCLUDE = -I./include -I./src
LIBS =
C_ARGS = -g -Wall $(INCLUDE)
AR_ARGS = rcs

BINARY = libjsoncpp.a
libjsoncpp.a_dep = src/lib_json/json_reader.o src/lib_json/json_value.o src/lib_json/json_writer.o

ALL_OBJS = $(foreach d,$(BINARY),$($(d)_dep))

%.o : %.cpp
	$(GXX) $(C_ARGS) -c  $< -o $(patsubst %.cpp,%.o,$<)
%.o : %.cc
	$(GXX) $(C_ARGS) -c  $< -o $(patsubst %.cc,%.o,$<)
%.o : %.c
	$(GCC) $(C_ARGS) -c  $< -o $(patsubst %.c,%.o,$<)
	
all : $(BINARY)

$(BINARY) : $(ALL_OBJS)
	@echo "now building:" $@
	@echo "dependency:" $($@_dep)
	rm -f $@
	$(AR) $(AR_ARGS) $@ $($@_dep)

clean:
	rm -f $(ALL_OBJS) $(BINARY)

print:
	@echo "print all vars"
	@echo "all objs:" $(ALL_OBJS)
