
```python
import sys

def binary_to_text(binary):
    binary = binary.split(" ")
    converted_string = ""
    for b in binary:
        converted_string += chr(int(b, 2))
    return converted_string

def octal_to_text(octal):
    octal = octal.split(" ")
    converted_string = ""
    for b in octal:
        converted_string += chr(int(b, 8))
    return converted_string

def hex_to_text(hex):
    return bytes.fromhex(hex).decode('utf-8')

def text_to_binary(text):
    return ' '.join(format(ord(x), 'b') for x in text)

def text_to_octal(text):
    return ' '.join(format(ord(x), 'o') for x in text)

def text_to_hex(text):
    return ''.join(format(ord(x), 'x') for x in text)

def main():
    if len(sys.argv) != 3:
        print(f"Usage: python {sys.argv[0]} [binary|octal|hex|text] [value]")
        sys.exit(1)
    if sys.argv[1] == "binary":
        print(binary_to_text(sys.argv[2]))
    elif sys.argv[1] == "octal":
        print(octal_to_text(sys.argv[2]))
    elif sys.argv[1] == "hex":
        print(hex_to_text(sys.argv[2]))
    elif sys.argv[1] == "text":
        print("Binary: " + text_to_binary(sys.argv[2]))
        print("Octal: " + text_to_octal(sys.argv[2]))
        print("Hex: " + text_to_hex(sys.argv[2]))
    else:
        print(f"Usage: python {sys.argv[0]} [binary|octal|hex|text] [value]")
        sys.exit(1)

if __name__ == "__main__":
    main()
```
