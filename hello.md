# Compiler Design

### **1. Install MSYS2**

- Download the installer from the [MSYS2 website](https://www.msys2.org/).
- Follow the installation instructions provided on the website.

---

### **2. Update MSYS2**

1. Launch **MSYS2 MSYS**.
2. Run the following commands to update the package database and core system packages:

```bash
pacman -Syu
```

1. Close the terminal and relaunch it.
2. Run the update command again to ensure all packages are updated:

```bash
pacman -Syu
```

### **3. Install Required Tools**

To run compiler design programs, install GCC, Flex, and Bison:

```bash
pacman -S mingw-w64-ucrt-x86_64-gcc flex bison make
```

If you're using the 32-bit or different architecture versions, replace `ucrt-x86_64` with the appropriate prefix, e.g., `mingw-w64-i686`.

### **4. Set Up Environment**

Switch to the **MSYS2 MinGW UCRT64** terminal for 64-bit development. Launch it from your Start menu or by typing:

```bash
msys2_shell -defterm -here -no-start -mingw64
```

### **5. Write Your Compiler Programs**

1. Create a new `.c`, `.l` (Lex file), or `.y` (Bison file) using a text editor.

### **6. Compile and Run**

1. **For Flex Files (`.l`):**
    
    ```bash
    flex example.l
    gcc lex.yy.c -o lexer
    ./lexer < input.txt
    ```
    
2. **For Bison Files (`.y`):**
    
    ```bash
    bison -d example.y
    gcc example.tab.c -o parser
    ./parser
    ```
    
3. **For Combined Flex and Bison:**
- If you combine `example.l` and `example.y`:
    
    ```bash
    flex example.l
    bison -d example.y
    gcc lex.yy.c example.tab.c -o compiler
    ./compiler < input.txt
    ```
