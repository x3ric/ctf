
```python
def bin_operations(a, b, operations):
  if operations == '+':
    result = bin(a + b)
  elif operations == '-':
    result = bin(a - b)
  elif operations == '*':
    result = bin(a * b)
  elif operations == '>>':
    num = input("Choose number a or b: ")
    if num == 'a':
      result = bin(a >> 1)
    elif num == 'b':
      result = bin(b >> 1)
    else:
      print("Invalid number to choose")
  elif operations == '<<':
    num = input("Choose number a or b: ")
    if num == 'a':
      result = bin(a << 1)
    elif num == 'b':
      result = bin(b << 1)
    else:
      print("Invalid number to choose")
  elif operations == '&':
    result = bin(a & b)
  elif operations == '|':
    result = bin(a | b)
  else:
    print("Invalid operations")
  
  return(result)

if __name__ == "__main__":
  a = input("Input number a: ")
  b = input("Input number b: ")
  a = int(a, 2)
  b = int(b, 2)
  for i in range(6):
    operations = input("Choose the binary operations: ")
    result = bin_operations(a, b, operations)
    print("Binary result: ", result)
    if i == 5:
        print(f"Hexadecimal result: {hex(int(result, 2))}")
```

```bash
nc titan.picoctf.net 51363
```

```bash
Welcome to the Binary Challenge!"
Your task is to perform the unique operations in the given order and find the final result in hexadecimal that yields the flag.

Binary Number 1: 11010100
Binary Number 2: 11000100


Question 1/6:
Operation 1: '|'
Perform the operation on Binary Number 1&2.
Enter the binary result: 0b11010100
Correct!

Question 2/6:
Operation 2: '+'
Perform the operation on Binary Number 1&2.
Enter the binary result: 0b110011000
Correct!

Question 3/6:
Operation 3: '<<'
Perform a left shift of Binary Number 1 by 1 bits.
Enter the binary result: 0b110101000
Correct!

Question 4/6:
Operation 4: '>>'
Perform a right shift of Binary Number 2 by 1 bits .
Enter the binary result: 0b1100010
Correct!

Question 5/6:
Operation 5: '&'
Perform the operation on Binary Number 1&2.
Enter the binary result: 0b11000100
Correct!

Question 6/6:
Operation 6: '*'
Perform the operation on Binary Number 1&2.
Enter the binary result: 0b1010001001010000
Correct!

Enter the results of the last operation in hexadecimal: 0xa250
```
