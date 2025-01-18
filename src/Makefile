# General
EXE    = weiss
SRC    = uci.c bitboard.c board.c endgame.c evaluate.c makemove.c move.c movegen.c movepicker.c psqt.c search.c threads.c time.c transposition.c query/query.c noobprobe/noobprobe.c onlinesyzygy/onlinesyzygy.c pyrrhic/tbprobe.c
CC     = gcc

# Defines
POPCNT = -msse3 -mpopcnt
PEXT   = $(POPCNT) -DUSE_PEXT -mbmi2

# Flags
STD    = -std=gnu11
LIBS   = -pthread -lm
WARN   = -Wall -Wextra -Wshadow -Werror -Wmissing-declarations
NDEBUG = -DNDEBUG

FLAGS  = $(STD) $(WARN) -Os -flto -s -ffunction-sections -fdata-sections -fvisibility=hidden
CFLAGS = $(FLAGS) -march=native
RFLAGS = $(FLAGS) -static

# Targets
basic: clean
	$(CC) $(CFLAGS) $(NDEBUG) $(SRC) $(LIBS) -Wl,--gc-sections -Wl,--strip-all -Wl,--as-needed -o $(EXE)

clean:
	@rm -f $(EXE)
