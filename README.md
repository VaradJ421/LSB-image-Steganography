# LSB-image-Steganography
Steganography is a method of concealing secret information inside another file so that the presence of the hidden data is not noticeable. In this project, I implemented LSB (Least Significant Bit) Image Steganography using the C programming language.
# 🖼️ LSB Image Steganography

A **C-based LSB (Least Significant Bit) Image Steganography project** that demonstrates how secret information can be concealed inside an image without making the hidden data visually noticeable.

Steganography is the technique of hiding secret information inside another file, such as an image, audio file, or video, so that the existence of the hidden information is not apparent.

In this project, I implemented **Image Steganography using the Least Significant Bit (LSB) technique in C**.

## 📌 Project Overview

The project hides a secret message or file inside an image by modifying the **least significant bits of the image's pixel data**.

The resulting image looks visually similar to the original image, while the hidden information can later be extracted using the decoding process.

The project consists of two primary operations:

* 🔐 **Encoding** – Hide secret data inside an image.
* 🔓 **Decoding** – Extract hidden data from the encoded image.

## ✨ Features

* 🔐 Hide secret information inside an image
* 🔓 Extract hidden information from an encoded image
* 🖼️ Uses image data for information hiding
* 💻 Implemented entirely in C
* 📦 Uses LSB-based data embedding
* ✅ Validates input files and required arguments
* 📂 Supports file handling for reading and writing data
* 🧩 Demonstrates low-level data manipulation

## 🧠 How LSB Steganography Works

LSB stands for **Least Significant Bit**.

Digital images contain pixel data represented using binary values. In LSB steganography, the least significant bits of the image data are modified to store secret information.

For example:

```text
Original pixel:
10110110

Secret bit:
       1

Modified pixel:
10110111
```

Only the least significant bit changes, resulting in a very small change to the pixel value.

By repeating this process across multiple bytes/pixels, a message or file can be embedded into the image.

## 🔄 Encoding Process

```text
             Secret Message
                    │
                    ▼
             Convert to Bits
                    │
                    ▼
          ┌──────────────────┐
          │   Input Image    │
          └────────┬─────────┘
                   │
                   ▼
           Modify LSB Bits
                   │
                   ▼
          ┌──────────────────┐
          │ Stego Image      │
          │ (Encoded Image)  │
          └──────────────────┘
```

### Encoding Steps

1. Open the source image.
2. Open the secret file/message.
3. Read the image header and required metadata.
4. Encode a predefined magic string/signature.
5. Encode the secret file extension/type information.
6. Encode the secret file size.
7. Encode the secret data into the image's LSBs.
8. Generate the final stego image.

## 🔓 Decoding Process

```text
          ┌──────────────────┐
          │   Stego Image    │
          └────────┬─────────┘
                   │
                   ▼
            Read LSB Bits
                   │
                   ▼
          Verify Magic String
                   │
                   ▼
           Extract File Info
                   │
                   ▼
          Extract Hidden Data
                   │
                   ▼
          ┌──────────────────┐
          │  Secret File     │
          └──────────────────┘
```

### Decoding Steps

1. Open the encoded/stego image.
2. Read the encoded image data.
3. Extract and verify the magic string.
4. Extract the secret file extension.
5. Extract the secret file size.
6. Extract the hidden data from the LSBs.
7. Reconstruct and save the secret file.

## 🛠️ Technologies & Concepts

| Category      | Details                                |
| ------------- | -------------------------------------- |
| Language      | C                                      |
| Technique     | LSB Steganography                      |
| Input         | Image + Secret File                    |
| Output        | Stego Image                            |
| File Handling | C File I/O                             |
| Concepts      | Bit Manipulation, Pointers, Structures |
| Platform      | Linux / GCC                            |

## 📁 Project Structure

```text
LSB-image-Steganography/
│
├── encode.c
├── decode.c
├── encode.h
├── decode.h
├── types.h
├── common.h
├── main.c
├── Makefile
└── README.md
```

> Update the file names above if your repository has a different structure.

## ⚙️ Installation & Setup

### Clone the Repository

```bash
git clone https://github.com/VaradJ421/LSB-image-Steganography.git
```

### Navigate to the Project

```bash
cd LSB-image-Steganography
```

### Compile

If the project contains a Makefile:

```bash
make
```

Or compile using GCC:

```bash
gcc *.c -o steganography
```

## ▶️ Usage

### Encoding

The general format is:

```bash
./steganography -e source_image.bmp secret_file output_image.bmp
```

Example:

```bash
./steganography -e beautiful.bmp secret.txt stego.bmp
```

This hides `secret.txt` inside `beautiful.bmp` and creates `stego.bmp`.

### Decoding

The general format is:

```bash
./steganography -d stego_image.bmp output_file
```

Example:

```bash
./steganography -d stego.bmp recovered.txt
```

This extracts the hidden data from `stego.bmp`.

> Modify the commands above according to the exact command-line arguments implemented in your project.

## 🧪 Example Workflow

```text
Original Image
     +
Secret File
     │
     ▼
┌─────────────────┐
│     ENCODING    │
└────────┬────────┘
         │
         ▼
   Stego Image
         │
         ▼
┌─────────────────┐
│     DECODING    │
└────────┬────────┘
         │
         ▼
   Recovered File
```

For example:

```text
Input Image  : input.bmp
Secret File  : secret.txt
                    │
                    ▼
             LSB Encoding
                    │
                    ▼
Output Image : stego.bmp
                    │
                    ▼
             LSB Decoding
                    │
                    ▼
Recovered File: secret.txt
```

## 🔍 Key Concepts Demonstrated

### Bit Manipulation

The project uses bit-level operations to modify and retrieve individual bits.

Common operations include:

```c
value & 1
```

to retrieve the LSB and operations such as:

```c
value = (value & ~1) | bit;
```

to replace the LSB with a desired bit.

### File Handling

The project demonstrates C file operations such as:

```c
fopen()
fread()
fwrite()
fseek()
fclose()
```

These functions are used to read image data and store/recover the hidden information.

### Pointers

Pointers are used extensively for manipulating image buffers and transferring data efficiently.

## ⚠️ Limitations

* Primarily intended for learning and demonstration.
* The amount of data that can be hidden depends on the image size.
* Modifying or compressing the stego image may destroy the hidden information.
* LSB steganography alone should not be considered strong encryption.
* The implementation depends on the supported image format and project design.

## 🎓 Learning Outcomes

Through this project, I gained practical experience in:

* C programming
* Bitwise operations
* File handling
* Pointers
* Binary data processing
* Image data manipulation
* Encoding and decoding techniques
* Command-line argument handling
* Debugging and modular programming

## 🚀 Future Enhancements

Possible improvements include:

* [ ] Support additional image formats
* [ ] Add password-based encryption
* [ ] Encrypt the secret data before embedding
* [ ] Add capacity calculation
* [ ] Improve error handling
* [ ] Add steganography detection resistance
* [ ] Add a graphical user interface
* [ ] Support larger payloads
* [ ] Add automated test cases

## 📚 References

* Least Significant Bit (LSB) Steganography
* Digital Image Processing
* C File Handling
* Bitwise Operations in C

## 👨‍💻 Author

**Varad Umesh Jinturkar**

Embedded Systems | C Programming | Data & AI Enthusiast

GitHub: **[@VaradJ421](https://github.com/VaradJ421)**

## ⭐ Support

If you find this project useful for learning **C programming, bit manipulation, file handling, or steganography**, consider giving the repository a ⭐.

