# Weiss is a UCI compliant chess engine.
# Copyright (C) 2023 Terje Kirstihagen

# This program is free software: you can redistribute it and/or modify
# it under the terms of the GNU General Public License as published by
# the Free Software Foundation, either version 3 of the License, or
# (at your option) any later version.

# This program is distributed in the hope that it will be useful,
# but WITHOUT ANY WARRANTY; without even the implied warranty of
# MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE. See the
# GNU General Public License for more details.

# You should have received a copy of the GNU General Public License
# along with this program. If not, see <https://www.gnu.org/licenses/>.

# General settings
EXE    = weiss
SRC    = uci.c bitboard.c board.c endgame.c evaluate.c makemove.c move.c movegen.c \
          movepicker.c psqt.c search.c threads.c time.c transposition.c \
          query/query.c noobprobe/noobprobe.c onlinesyzygy/onlinesyzygy.c \
          pyrrhic/tbprobe.c
CC     = gcc

# Compiler and linker flags
CFLAGS = -std=gnu11 -Wall -Wextra -Wshadow -Os -flto -s \
         -ffunction-sections -fdata-sections -fvisibility=hidden -march=native
LDFLAGS = -Wl,--gc-sections -Wl,--strip-all -Wl,--as-needed
LIBS   = -pthread -lm
NDEBUG = -DNDEBUG

# Build commands
basic: clean
	$(CC) $(CFLAGS) $(NDEBUG) $(SRC) $(LIBS) $(LDFLAGS) -o $(EXE)

dev: clean
	$(CC) $(CFLAGS) -DDEV $(SRC) $(LIBS) $(LDFLAGS) -o $(EXE)

tune: clean
	$(CC) $(CFLAGS) -DTUNE -fopenmp $(SRC) $(LIBS) $(LDFLAGS) -o $(EXE)

release: clean
	$(CC) $(CFLAGS) $(NDEBUG) $(SRC) $(LIBS) $(LDFLAGS) -o $(EXE)

clean:
	@rm -f $(EXE)
	@echo "Cleaned build artifacts."

.PHONY: basic dev tune release clean
