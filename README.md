<img width="1280" height="829" alt="lab exp 1" src="https://github.com/user-attachments/assets/f9e31ef4-8724-46d6-944b-ed7ab1409e61" />

<img width="1280" height="829" alt="lab exp 1" src="https://github.com/user-attachments/assets/d99cc32a-8dfb-49bf-a14d-d7d0f94d0d64" />
<img width="1280" height="829" alt="lab exp 1" src="https://github.com/user-attachments/assets/b26d0cef-c382-4af9-bedf-248a67d16abd" />

# Caesar Cipher
def caesar_encrypt(text, shift):
    result = ""

    for char in text:
        if char.isalpha():
            start = ord('A') if char.isupper() else ord('a')
            result += chr((ord(char) - start + shift) % 26 + start)
        else:
            result += char

    return result


def caesar_decrypt(text, shift):
    return caesar_encrypt(text, -shift)


# Vigenere Cipher
def vigenere_encrypt(text, key):
    result = ""
    key = key.upper()
    key_index = 0

    for char in text:
        if char.isalpha():
            shift = ord(key[key_index % len(key)]) - ord('A')
            start = ord('A') if char.isupper() else ord('a')

            result += chr((ord(char) - start + shift) % 26 + start)
            key_index += 1
        else:
            result += char

    return result


def vigenere_decrypt(text, key):
    result = ""
    key = key.upper()
    key_index = 0

    for char in text:
        if char.isalpha():
            shift = ord(key[key_index % len(key)]) - ord('A')
            start = ord('A') if char.isupper() else ord('a')

            result += chr((ord(char) - start - shift) % 26 + start)
            key_index += 1
        else:
            result += char

    return result


# Main program

print("CLASSICAL SYMMETRIC CIPHERS")
print("----------------------------")

# Caesar Cipher
text = "HELLO WORLD"
shift = 3

encrypted = caesar_encrypt(text, shift)
decrypted = caesar_decrypt(encrypted, shift)

print("\nCaesar Cipher")
print("Plaintext :", text)
print("Shift     :", shift)
print("Encrypted :", encrypted)
print("Decrypted :", decrypted)


# Vigenere Cipher
text = "ATTACKATDAWN"
key = "LEMON"

encrypted = vigenere_encrypt(text, key)
decrypted = vigenere_decrypt(encrypted, key)

print("\nVigenere Cipher")
print("Plaintext :", text)
print("Key       :", key)
print("Encrypted :", encrypted)
print("Decrypted :", decrypted)
