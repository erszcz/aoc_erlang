CC=gcc
CFLAGS=-g -O3 -Wall -Werror -fPIC -I/usr/local/opt/openssl@1.1/include
LDFLAGS=-L/usr/local/opt/openssl@1.1/lib -arch x86_64 -flat_namespace -undefined suppress

# Get includes right in TravisCI
ifneq ($(ERLANG_ROOT_DIR),)
ERL_INC=-I$(ERLANG_ROOT_DIR)/usr/include
endif

all: aoc_nifs.so

aoc_nifs.o: aoc_nifs.c
	$(CC) $(CFLAGS) $(ERL_INC) -c $< -o $@

aoc_nifs.so: aoc_nifs.o
	$(CC) -shared -fPIC $(LDFLAGS) $^ -o $@

clean:
	rm -f *.so *.o
