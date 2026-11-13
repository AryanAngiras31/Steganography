LSB-Steganography
=================

Python program based on stegonographical methods to hide files in images using the Least Significant Bit technique.

I used the most basic method which is the least significant bit. A colour pixel is composed of red, green and blue, encoded on one byte. The idea is to store information in the first bit of every pixel's RGB component. In the worst case, the decimal value is different by one which is not visible to the human eye. In practice, if you don't have space to store all of your data in the first bit of every pixel you should start using the second bit, and so on. You have to keep in mind that the more your store data in an image, the more it can be detected.


Information
-----------

LSBSteg module is based on OpenCV to hide data in images. It uses the first bit of every pixel, and every colour
of an image. The code is quite simple to understand; If every first bit has been used, the module starts using the second bit, so the larger the data, the more the image is altered.
The program can hide all of the data if there is enough space in the image. The main functions are:

* encode_text: You provide a string and the program hides it
* encode_image: You provide an OpenCV image and the method iterates for every pixel in order to hide them. A good practice is to have a carrier 8 times bigger than the image to hide (so that each pixel will be put only in the first bit).
* encode_binary: You provide a binary file to hide; This method can obfuscate any kind of file.


Installation
------------

This tool requires Python 3 and the packages listed in `requirements.txt`
(OpenCV, NumPy, and docopt).

1. Clone the repository and enter the project directory:

```bash
git clone https://github.com/AryanAngiras31/Steganography.git
cd Steganography
```

2. Create and activate a virtual environment (recommended):

```bash
python3 -m venv .venv
source .venv/bin/activate
```

On Windows, use the activation command for your shell instead:

```powershell
# PowerShell
.venv\Scripts\Activate.ps1

# Command Prompt
.venv\Scripts\activate.bat
```

3. Upgrade pip and install the dependencies:

```bash
python -m pip install --upgrade pip
pip install -r requirements.txt
```

4. Verify the installation:

```bash
python -c "import cv2, numpy, docopt; print('OpenCV', cv2.__version__)"
```

When you are finished, you can leave the virtual environment with:

```bash
deactivate
```

Usage
-----

```bash
LSBSteg.py

Usage:
  LSBSteg.py encode -i <input> -o <output> -f <file>
  LSBSteg.py decode -i <input> -o <output>

Options:
  -h, --help                Show this help
  --version                 Show the version
  -f,--file=<file>          File to hide
  -i,--in=<input>           Input image (carrier)
  -o,--out=<output>         Output image (or extracted file)
```

#### Example
```bash
python LSBSteg.py encode -i carrier.png -o hidden.png -f secret.txt

python LSBSteg.py decode -i hidden.png -o secret_check.txt
```

License
-------

This software is MIT-Licensed.
