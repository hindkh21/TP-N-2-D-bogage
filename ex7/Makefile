# Compiler options
CC = gcc
CFLAGS = -Wall -Wextra -pthread

# Source files
SRC = lock.c
OBJ = lock.o
# Object files
OBJ = $(SRC:.c=.o)

# Executable name
EXEC = threads_example

# Rule to compile .c files into .o files
%.o: %.c
	$(CC) $(CFLAGS) -c $< -o $@

# Rule to build the executable
$(EXEC): $(OBJ)
	$(CC) $(CFLAGS) $(OBJ) -o $(EXEC)

# Clean rule
clean:
	rm -f $(OBJ) $(EXEC)

# Phony target to avoid conflicts with file names
.PHONY: clean

