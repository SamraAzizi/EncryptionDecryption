# Encryption and Decryption Program

This is a simple Python program that uses the Tkinter library to create a graphical user interface (GUI) for encrypting and decrypting messages using a base64 encoding scheme.

## Features

- Encrypt messages
- Decrypt messages
- User-friendly GUI
- Simple password protection for encryption and decryption

## Prerequisites

- Python 3.x
- Tkinter (usually included with Python installations)

## Installation

1. Clone the repository or download the source code.
2. Ensure you have Python 3 installed on your system.
3. (Optional) Create and activate a virtual environment:
    ```sh
    python -m venv env
    source env/bin/activate  # On Windows use `env\Scripts\activate`
    ```
4. Install required packages (if any):
    ```sh
    pip install tkinter
    ```

## Usage

1. Save an image named `keys.png` in the same directory as your script to use as the application icon.
2. Run the script:
    ```sh
    python script_name.py
    ```
3. Enter the text you want to encrypt or decrypt in the text box.
4. Enter the password (`1234`) in the secret key field.
5. Click "ENCRYPT" to encrypt the message or "DECRYPT" to decrypt it.
6. Use the "RESET" button to clear the fields.

## Code Overview

The main components of the script are:

- **Encryption**: Converts a plain text message into a base64 encoded string.
- **Decryption**: Converts a base64 encoded string back into the original plain text message.
- **GUI**: Built using Tkinter, providing an interface for users to input text and view results.

### Functions

- `decrypt()`: Decrypts the encoded message if the correct password is entered.
- `encrypt()`: Encrypts the message if the correct password is entered.
- `main_screen()`: Sets up the main GUI screen with text input fields and buttons.

### Example

```python
from tkinter import *
from tkinter import messagebox
import base64

def decrypt():
    password = code.get()
    if password == "1234":
        screen2 = Toplevel(screen)
        screen2.title("Decryption")
        screen2.geometry("400x200")
        screen2.configure(bg="#00bd56")
        message = text1.get(1.0, END).strip()
        if message:
            decode_message = message.encode("ascii")
            base64_bytes = base64.b64decode(decode_message)
            decrypted_message = base64_bytes.decode("ascii")
            Label(screen2, text="DECRYPTED", font="Arial", fg="white", bg="#00bd56").place(x=10, y=0)
            text2 = Text(screen2, font="Roboto 10", bg="white", relief=GROOVE, wrap=WORD, bd=0)
            text2.place(x=10, y=40, width=380, height=150)
            text2.insert(END, decrypted_message)
        else:
            messagebox.showerror("Decryption", "No message to decrypt")
    elif password == "":
        messagebox.showerror("Decryption", "Input Password")
    else:
        messagebox.showerror("Decryption", "Invalid password!")

def encrypt():
    password = code.get()
    if password == "1234":
        screen1 = Toplevel(screen)
        screen1.title("Encryption")
        screen1.geometry("400x200")
        screen1.configure(bg="#ed3833")
        message = text1.get(1.0, END).strip()
        if message:
            encode_message = message.encode("ascii")
            base64_bytes = base64.b64encode(encode_message)
            encrypted_message = base64_bytes.decode("ascii")
            Label(screen1, text="ENCRYPTED", font="Arial", fg="white", bg="#ed3833").place(x=10, y=0)
            text2 = Text(screen1, font="Roboto 10", bg="white", relief=GROOVE, wrap=WORD, bd=0)
            text2.place(x=10, y=40, width=380, height=150)
            text2.insert(END, encrypted_message)
        else:
            messagebox.showerror("Encryption", "No message to encrypt")
    elif password == "":
        messagebox.showerror("Encryption", "Input Password")
    else:
        messagebox.showerror("Encryption", "Invalid password!")

def main_screen():
    global screen
    global code
    global text1
    screen = Tk()
    screen.geometry("375x390")
    image_icon = PhotoImage(file="keys.png")
    screen.iconphoto(False, image_icon)
    screen.title("Encrypt and Decrypt")

    def reset():
        code.set("")
        text1.delete(1.0, END)

    Label(text="Enter text for encryption and decryption", fg="black", font=("Calibri", 13)).place(x=10, y=10)
    text1 = Text(font="Roboto 20", bg="white", relief=GROOVE, wrap=WORD, bd=0)
    text1.place(x=10, y=50, width=355, height=100)
    Label(text="Enter secret key for encryption and decryption", fg="black", font=("Calibri", 13)).place(x=10, y=170)

    code = StringVar()
    Entry(textvariable=code, width=19, bd=0, font=("Arial", 25)).place(x=10, y=200)
    Button(text="ENCRYPT", height=2, width=23, bg="#ed3833", fg="white", bd=0, command=encrypt).place(x=10, y=250)
    Button(text="DECRYPT", height=2, width=23, bg="#00bd56", fg="white", bd=0, command=decrypt).place(x=200, y=250)
    Button(text="RESET", height=2, width=50, bg="#1089ff", fg="white", bd=0, command=reset).place(x=10, y=300)
    screen.mainloop()

main_screen()
