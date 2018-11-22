# I/O Standard Library
The I/O standard library will be called `io`.

### io.open(name, mode)
Opens file with name `name`. `mode` defaults to `r`. Modes are:
- `'r'`: read mode;
- `'w'`: write mode (clobbers file);
- `'a'`: append mode (appends to end of file);
- `'r+'`: update mode, all previous data preserved;
- `'w+'`: update mode, all previous data erased;
- `'a+'`: append update mode (same as 

### io.flush(f)
Saves any data written to `f`.

### io.read(f)
Writes to `f`.

### io.read(f)
Reads from `f`.

### io.close(f)
Closes `f`.

### io.seek(f, whence, offset)
Sets the position in the file

