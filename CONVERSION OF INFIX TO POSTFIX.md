# Exp.No:32  
## CONVERSION OF INFIX TO POSTFIX

---

### AIM  
To write a Python program to convert given Infix expression to Postfix expression by following the precedence and associative rule.  The input expression contains only  Modulo, Multiplication and Bitwise OR . Use dictionary to set the priority for operators. Use set to hold the operators used in the given expression.

---

### ALGORITHM

1. **Start the program.**
2. **Initialize an empty stack** and an empty output string.
3. **Iterate through each character** in the infix expression:
   - If the character is **not an operator**, append it directly to the output string.
   - If the character is an **open parenthesis '('**, push it onto the stack.
   - If the character is a **close parenthesis ')'**, pop from the stack and append to the output until encountering a left parenthesis '('.
   - If the character is an **operator**, handle it based on precedence:
     - While there’s an operator at the top of the stack with higher or equal precedence, pop the stack and append those operators to the output.
     - Push the current operator onto the stack.
4. **Use a priority dictionary** to define operator precedence, ensuring higher precedence operators are placed before lower precedence ones.
5. Once the expression is fully processed, continue popping any remaining operators from the stack and append them to the output.
6. **Return the final postfix expression.**
7. **Print the result.**
8. **End the program.**

---

### PROGRAM

```
Operators = set(['%','*','|','(',')'])  
Priority = {'*':2,'%':2,'|':1}
def infixToPostfix(expression):
    stack = [] 
    output = '' 
    for character in expression:
        if character not in Operators:
            output += character
        elif character == '(':
            stack.extend('(')
        elif character == ')':
            while stack and stack[-1] != '(':
                output += stack.pop()
            stack.pop()
        else:
            while stack and stack[-1] !='(' and Priority[character] <= Priority[stack[-1]]:
                output += stack.pop()
            stack.append(character)
            
    while stack:
        output += stack.pop()
    return output
expression = input()
print("infix notation: ",expression)
print("postfix notation: ",infixToPostfix(expression))

```

### OUTPUT

![image](https://github.com/user-attachments/assets/4aa61e6b-b40b-49f4-902a-be3e2752d4ac)

### RESULT
Thus the Python program to convert given Infix expression to Postfix expression by following the precedence and associative rule was implemented and executed successfully.
