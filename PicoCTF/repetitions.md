
```python
import base64

def decode_until_flag(encoded_str):
    current = encoded_str
    iterations = 0
    while True:
        try:
            decoded = base64.b64decode(current)
            decoded_str = decoded.decode('utf-8')
            print(f"Iteration {iterations + 1}: {decoded_str[:50]}...")
            if 'picoCTF' in decoded_str:
                return decoded_str
            current = decoded_str
            iterations += 1
            if iterations > 20:
                return "Too many iterations, might not be correct encoding"  
        except Exception as e:
            return f"Decoding stopped at iteration {iterations}: {str(e)}"

encoded = """VmpGU1EyRXlUWGxTYmxKVVYwZFNWbGxyV21GV1JteDBUbFpPYWxKdFVsaFpWVlUxWVZaS1ZWWnVh
RmRXZWtab1dWWmtSMk5yTlZWWApiVVpUVm10d1VWZFdVa2RpYlZaWFZtNVdVZ3BpU0VKeldWUkNk
MlZXVlhoWGJYQk9VbFJXU0ZkcVRuTldaM0JZVWpGS2VWWkdaSGRXCk1sWnpWV3hhVm1KRk5XOVVW
VkpEVGxaYVdFMVhSbFZrTTBKeldWaHdRMDB4V2tWU2JFNVdDbUpXV2tkVU1WcFhWVzFHZEdWRlZs
aGkKYlRrelZERldUMkpzUWxWTlJYTkxDZz09Cg=="""
encoded = "".join(encoded.split())
print("Starting decoding process...")
result = decode_until_flag(encoded)
print("\nFinal result:", result)
```
