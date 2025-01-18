# General
EXE    = weiss
SRC    = main.c pyrrhic/tbprobe.c query/*.c noobprobe/*.c  # 必要最小限のファイル
CC     = gcc

# Defines
POPCNT = -msse3 -mpopcnt
PEXT   = $(POPCNT) -DUSE_PEXT -mbmi2

# Flags
STD    = -std=gnu11
LIBS   = -pthread -lm
WARN   = -Wall -Wextra -Wshadow
NDEBUG = -DNDEBUG

# Size optimization flags
FLAGS  = $(STD) $(WARN) -Os -ffunction-sections -fdata-sections -fvisibility=hidden
CFLAGS = $(FLAGS) -flto -march=native -s
LDFLAGS = -Wl,--gc-sections -Wl,--strip-all -Wl,--as-needed

# Compilations
BASIC   = $(CC) $(CFLAGS) $(NDEBUG) $(SRC) $(LIBS) $(LDFLAGS) -o $(EXE)

# Targets
all: clean basic

basic: clean
	$(BASIC)

clean:
	@rm -f $(EXE)
	@rm -rf pgo
