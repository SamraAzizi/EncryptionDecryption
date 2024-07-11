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

## License

This project is licensed under the MIT License. See the LICENSE file for details.

## Acknowledgements

- Tkinter for the GUI
- Base64 for encoding and decoding
