OLED Display Script for Raspberry Pi

A Python script to display multi-line text on an I2C OLED screen using the Luma.OLED library. Supports text positioning, custom display time, and an indefinite run mode.

Features

✅ Multi-line text support (via \n or -M "Line 1\nLine 2")
✅ Adjustable text position (-P x,y argument)
✅ Custom display duration (-T seconds argument)
✅ Indefinite run mode (-I runs until Ctrl + C is pressed)
✅ Handles Ctrl + C cleanly

🚀 Installation

1️⃣ Install Dependencies

Ensure you have the required libraries installed:

pip install luma.oled Pillow

2️⃣ Connect OLED to Raspberry Pi

Wire your SSD1306 OLED display to the Raspberry Pi via I2C:

OLED Pin

Raspberry Pi Pin

VCC

3.3V (Pin 1)

GND

GND (Pin 6)

SDA

SDA (Pin 3)

SCL

SCL (Pin 5)

Enable I2C on your Pi using:

sudo raspi-config

Navigate to Interfacing Options → I2C → Enable.

📌 Usage

Basic Command

python3 script.py -M "Hello, World!"

Multi-Line Text

python3 script.py -M "Line 1\nLine 2\nLine 3"

Custom Positioning

python3 script.py -M "Top Left" -P "10,10"

Set Display Time (Seconds)

python3 script.py -M "Displayed for 10 sec" -T 10

Run Indefinitely (Until Ctrl + C)

python3 script.py -M "Persistent Display" -I

🛠 Arguments

Argument

Description

-M "text"

Sets the message to display (supports \n for multi-line)

-P x,y

Sets the (x, y) position of the text on the screen

-T seconds

Sets the display duration (default: 15s)

-I

Runs indefinitely until Ctrl + C is pressed

📷 Example Output

Hello
World

⚡ Troubleshooting

Check I2C Address

Run the following to detect your OLED display:

sudo i2cdetect -y 1

Expected output (common addresses: 0x3C or 0x3D):

     0  1  2  3  4  5  6  7  8  9  A  B  C  D  E  F
00:                         -- -- -- -- -- -- -- --
10: -- -- -- -- -- -- -- -- -- -- -- -- -- -- -- --
20: -- -- -- -- -- -- -- -- -- -- -- -- -- -- -- --
30: -- -- -- -- -- -- -- -- -- -- -- -- 3C -- -- --

No Display Output?

1️⃣ Ensure I2C is enabled (sudo raspi-config → Interfacing Options → I2C).2️⃣ Double-check wiring.3️⃣ Run as sudo if permission issues occur.4️⃣ Try changing the I2C address in i2c(port=1, address=0x3C).

🎯 To-Do

🔹 Add word-wrapping for long text.🔹 Support custom fonts via TTF files.🔹 Implement a scrolling text mode.

📜 License

This project is licensed under the MIT License.

🙌 Credits

Developed by [Your Name]. Contributions & suggestions welcome!

