### Ex. No: 1  
**Date:**  
### **AIM**  
To develop a lexical analyzer to recognize specific patterns in C, such as **Identifiers, Constants, Comments, Operators, etc.,** and to implement a symbol table.  

---

### **ALGORITHM**  

1. **Start the program.**  
2. **Read the input string.**  
3. **Analyze the string** based on specific rules:  
   - Check if it is an **identifier, operator, symbol, or keyword** using `lex` rules.  
4. **Classification logic:**  
   - If the string starts with a letter followed by any number of letters or digits, classify it as an **identifier**.  
   - If the string matches an operator pattern, classify it as an **operator**.  
   - If the string is numeric, classify it as a **number**.  
   - If the string is a keyword (like `int`, `float`), classify it as a **keyword**.  
   - Handle other cases like punctuation, special characters, etc.  
5. **Display the classification result.**  
6. **Stop the program.**  

---

### **PROGRAM**

```c
%{
#include <stdio.h>
%}

%%

bool|int|float|char      { printf("Keyword\n"); }
[-+]+                    { printf("Operators\n"); }
[0-9]+                   { printf("Numbers\n"); }
[,.'"]+                  { printf("Punctuation Chars\n"); }
[&%*$@!]+                { printf("Special Characters\n"); }
[a-zA-Z_][a-zA-Z0-9_]*   { printf("Identifiers\n"); }

%%

int main() {
    yylex();
    return 0;
}

int yywrap() {
    return 1;
}
```

---

### **OUTPUT**  
**Input Examples:**  
1. **Input:** `int`  
   **Output:** Keyword  

2. **Input:** `+`  
   **Output:** Operator  

3. **Input:** `123`  
   **Output:** Number  

4. **Input:** `variable`  
   **Output:** Identifier  

---

### **CONCLUSION**  
Thus, a lexical analyzer to recognize various patterns in C, such as **Identifiers, Constants, Comments, Operators, etc.,** was successfully implemented.
