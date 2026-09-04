# Image-Watermarking-with-Python
A simple Python script for automatically adding a watermark to multiple images in a folder.  The script uses Pillow (PIL) to open images, resize the watermark, place it in the bottom-right corner, and save the processed images into a separate output folder
✨ Features
💧 Add a watermark to multiple images at once
📁 Process all .png and .jpg images in a folder
📐 Automatically resize the watermark
📍 Place the watermark in the bottom-right corner
📂 Automatically create an output folder
🖼️ Preserve the base image's color mode where supported
⚡ Process an entire folder with a single command
🛠️ Technologies Used
Python 3
Pillow
OS module
📦 Installation

Clone the repository:

git clone https://github.com/your-username/image-watermarking.git
cd image-watermarking

Install Pillow:

pip install Pillow
🚀 Usage

Run the Python script:

python "Image Watermarking(2).py"

The program will ask for two paths:

Enter Folder Path:
Enter Watermark Path:
Example
Enter Folder Path: C:\Users\User\Pictures
Enter Watermark Path: C:\Users\User\Pictures\watermark.png

The script then scans the selected folder and processes .png and .jpg files.

📁 Project Structure
image-watermarking/
│
├── Image Watermarking(2).py
├── README.md
│
└── images/
    ├── image1.jpg
    ├── image2.png
    ├── image3.jpg
    └── watermark.png

After running the script, an output directory is created:

images/
│
├── image1.jpg
├── image2.png
├── image3.jpg
├── watermark.png
│
└── output/
    ├── image1.jpg
    ├── image2.png
    └── image3.jpg

The script creates the output directory automatically if it doesn't exist.

💧 How the Watermark Works

The watermark is converted to RGBA so that transparency can be used when placing it over the original image.

The watermark is resized to approximately 8% of the base image width:

newsize = (
    int(position[0] * 8 / 100),
    int(position[0] * 8 / 100)
)

It is then positioned 20 pixels from the right and bottom edges:

new_position = (
    position[0] - newsize[0] - 20,
    position[1] - newsize[1] - 20
)

The watermark is composited onto a transparent image before being saved.

🔄 Processing Flow
Start
  │
  ▼
Enter Image Folder
  │
  ▼
Enter Watermark Path
  │
  ▼
Read Images from Folder
  │
  ▼
Filter .png / .jpg
  │
  ▼
Open Image
  │
  ▼
Resize Watermark
  │
  ▼
Place Watermark
  │
  ▼
Save to output/
  │
  ▼
Next Image
🖼️ Supported Images

Currently, the script processes files ending with:

.png
.jpg

The extension check is implemented directly in the script.

📤 Output

Processed images are saved using the original filename inside the output directory:

output/image1.jpg
output/image2.png

The image is saved with optimization enabled and JPEG quality set to 100.

⚠️ Notes
The watermark is resized to a square based on the base image's width.
The current script only checks .png and .jpg extensions.
The script expects the watermark file path to be valid.
Existing files in the output directory with the same names may be overwritten.
The script currently uses interactive input() prompts rather than command-line arguments.
