TARGET= ./leveldb
CFLAGS := -Wall -w  -g -ggdb -O0 -Wno-unused -Wno-sign-compare -Wno-deprecated-declarations -Wno-deprecated\
-Wl,--no-as-needed -std=c++17
ccfiles := $(shell ls *.cc)
cfiles := $(-shell ls *.c)
OBJS := $(patsubst %.cc,./%.o, $(ccfiles) $(cfiles))
COBJS=${patsubst %.c,./%.o,$(cfiles)}
CXXOBJS=${patsubst %.cc,./%.o,$(ccfiles)}

DEPS=$(patsubst %.o,%.d,$(OBJS))

LIB= 

SO_LIB= 


.PHONY: all clean

all: ${TARGET}

${TARGET}: ${OBJS} ${LIB} 
	g++ -o $@ $^ ${LDFLAGS}${LIB} ${LIB64}  -lpthread
${CXXOBJS}:./%.o:./%.cc
	g++ -MMD -c -o $@ $< ${CFLAGS} 

${COBJS}:./%.o:./%.c
	${CC} -MMD -c -o $@ $< ${CFLAGS} 

-include $(DEPS)

clean:
	rm -f *.rdb *.log *.temp ${OBJS} ${TARGET} ${DEPS}

show:
	@echo GPROF=$(GPROF)
	@echo CFLAGS=$(CFLAGS)
	@echo LDFLAGS=$(LDFLAGS)
	@echo objs=$(OBJS)
	@echo ccfiels=$(ccfiles)
	@echo cfiels=$(cfiles)
	@echo DEPS=$(DEPS)
	@echo CXXOBJS=$(CXXOBJS)
	@echo COBJS=$(COBJS)

