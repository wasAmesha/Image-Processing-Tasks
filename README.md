# Image Processing Tasks - README

A comprehensive Python implementation for digital image processing tasks including intensity level reduction, spatial averaging, image rotation, and block averaging. This code is designed to work seamlessly in Jupyter Notebook environments.

## 📋 Table of Contents

- [Features](#features)
- [Requirements](#requirements)
- [Installation](#installation)
- [Quick Start](#quick-start)
- [Task Descriptions](#task-descriptions)
- [Usage Examples](#usage-examples)
- [File Structure](#file-structure)
- [Troubleshooting](#troubleshooting)
- [Configuration Options](#configuration-options)

## ✨ Features

- **Task 1**: Intensity Level Reduction (256 → 2, 4, 8, 16, 32, 64, 128 levels)
- **Task 2**: Spatial Averaging with different neighborhood sizes (3×3, 10×10, 20×20)
- **Task 3**: Image Rotation (45° and 90° rotations)
- **Task 4**: Block Averaging for spatial resolution reduction (3×3, 5×5, 7×7 blocks)
- Support for both color (RGB) and grayscale images
- Automatic result visualization with matplotlib
- Automatic saving of processed images
- Comprehensive error handling

## 🔧 Requirements

### Python Libraries

```python
import cv2          # OpenCV for image processing
import numpy as np  # Numerical operations
import matplotlib.pyplot as plt  # Visualization
import os          # File system operations
```

### Installation Commands

```bash
# Install required packages
pip install opencv-python numpy matplotlib

# Alternative using conda
conda install opencv numpy matplotlib
```

## 🚀 Quick Start

### 1. Prepare Your Image

Place your image file in the same directory as your notebook or specify the full path.

### 2. Update Image Path

Replace `"input.jpg"` with your actual image filename in the code:

```python
IMAGE_PATH = "your_image_name.jpg"  # Change this line
```

### 3. Run in Jupyter Notebook

#### Option A: Run All Tasks (Recommended)

```python
# For color image processing
processor = ImageProcessor("your_image.jpg", use_color=True)
processor.run_all_tasks()
```

#### Option B: Run Individual Tasks

```python
# Initialize processor
processor = ImageProcessor("your_image.jpg", use_color=True)

# Run specific tasks
processor.task1_intensity_reduction()
processor.task2_spatial_averaging()
processor.task3_image_rotation()
processor.task4_block_averaging()
```

#### Option C: Quick Functions

```python
# Color processing
process_color_image("your_image.jpg")

# Grayscale processing
process_grayscale_image("your_image.jpg")
```

## 📝 Task Descriptions

### Task 1: Intensity Level Reduction

Reduces the number of intensity levels in an image from 256 to various powers of 2.

**Output**: 7 processed images with 2, 4, 8, 16, 32, 64, and 128 intensity levels
**Purpose**: Demonstrates quantization effects and bit-depth reduction

### Task 2: Spatial Averaging

Applies averaging filters to smooth the image using different neighborhood sizes.

**Output**: 3 processed images with 3×3, 10×10, and 20×20 averaging kernels
**Purpose**: Shows noise reduction and blur effects

### Task 3: Image Rotation

Rotates the image by specified angles while preserving the entire image content.

**Output**: 2 processed images rotated by 45° and 90°
**Purpose**: Demonstrates geometric transformations

### Task 4: Block Averaging

Replaces non-overlapping blocks with their average value to reduce spatial resolution.

**Output**: 3 processed images with 3×3, 5×5, and 7×7 block sizes
**Purpose**: Shows pixelation and resolution reduction effects

## 💡 Usage Examples

### Example 1: Processing a Color Image

```python
# Create processor instance
processor = ImageProcessor("sample_image.jpg", use_color=True)

# Run all tasks
processor.run_all_tasks()

# Check results in 'results/' folder
```

### Example 2: Processing in Grayscale

```python
# Process the same image in grayscale
processor_gray = ImageProcessor("sample_image.jpg", use_color=False)
processor_gray.run_all_tasks()
```

### Example 3: Custom Processing

```python
# Initialize processor
processor = ImageProcessor("image.png", use_color=True)

# Run only specific tasks
processor.task1_intensity_reduction()
processor.task3_image_rotation()

# Access the original image
original = processor.original_image
print(f"Image dimensions: {original.shape}")
```

### Example 4: Batch Processing Multiple Images

```python
import glob

# Process all JPG files in directory
image_files = glob.glob("*.jpg")

for img_file in image_files:
    print(f"Processing {img_file}...")
    processor = ImageProcessor(img_file, use_color=True)
    processor.run_all_tasks()
```

## 📁 File Structure

After running the code, your directory will look like this:

```
your_project_folder/
├── your_notebook.ipynb
├── your_image.jpg
├── results/
│   ├── original_image.png
│   ├── task1_intensity_2_levels.png
│   ├── task1_intensity_4_levels.png
│   ├── task1_intensity_8_levels.png
│   ├── task1_intensity_16_levels.png
│   ├── task1_intensity_32_levels.png
│   ├── task1_intensity_64_levels.png
│   ├── task1_intensity_128_levels.png
│   ├── task2_spatial_avg_3x3.png
│   ├── task2_spatial_avg_10x10.png
│   ├── task2_spatial_avg_20x20.png
│   ├── task3_rotated_45_degrees.png
│   ├── task3_rotated_90_degrees.png
│   ├── task4_block_avg_3x3.png
│   ├── task4_block_avg_5x5.png
│   └── task4_block_avg_7x7.png
```

## 🔧 Configuration Options

### Color vs Grayscale Processing

```python
# Color processing (default)
processor = ImageProcessor("image.jpg", use_color=True)

# Grayscale processing
processor = ImageProcessor("image.jpg", use_color=False)
```

### Supported Image Formats

- JPEG (.jpg, .jpeg)
- PNG (.png)
- BMP (.bmp)
- TIFF (.tiff, .tif)
- And other formats supported by OpenCV

### Customizing Parameters

You can modify the processing parameters by editing the arrays in the code:

```python
# Task 1: Change intensity levels
levels_list = [2, 4, 8, 16, 32, 64, 128]  # Modify as needed

# Task 2: Change kernel sizes
kernel_sizes = [3, 10, 20]  # Modify as needed

# Task 3: Change rotation angles
angles = [45, 90]  # Modify as needed

# Task 4: Change block sizes
block_sizes = [3, 5, 7]  # Modify as needed
```

## 🛠️ Troubleshooting

### Common Issues and Solutions

#### Issue 1: "Could not load image" Error

```python
# Check if file exists
import os
if os.path.exists("your_image.jpg"):
    print("File exists")
else:
    print("File not found - check the path")
```

#### Issue 2: Module Not Found Errors

```bash
# Install missing packages
pip install opencv-python numpy matplotlib

# If using conda
conda install -c conda-forge opencv numpy matplotlib
```

#### Issue 3: Images Not Displaying in Jupyter

```python
# Add this magic command at the beginning of your notebook
%matplotlib inline

# Or use this for interactive plots
%matplotlib widget
```

#### Issue 4: Memory Issues with Large Images

```python
# Resize large images before processing
def resize_image(image, max_width=1000):
    if image.shape[1] > max_width:
        scale = max_width / image.shape[1]
        new_width = int(image.shape[1] * scale)
        new_height = int(image.shape[0] * scale)
        return cv2.resize(image, (new_width, new_height))
    return image
```

#### Issue 5: Permission Errors When Saving

```python
# Check write permissions or change output directory
import os
os.makedirs('results', exist_ok=True)
```

## 📊 Performance Tips

### For Large Images

- Consider resizing images if they're very large (>2000px width)
- Process in grayscale mode for faster execution
- Use smaller block sizes for Task 4 to reduce processing time

### For Jupyter Notebooks

- Use `%time` magic command to measure execution time
- Clear output regularly to prevent memory buildup
- Save intermediate results if processing takes long

### Example Performance Monitoring

```python
# Time individual tasks
%time processor.task1_intensity_reduction()
%time processor.task2_spatial_averaging()
%time processor.task3_image_rotation()
%time processor.task4_block_averaging()
```

## 🎯 Expected Outputs

### Visual Results

Each task will display:

- A subplot showing original and processed images side by side
- Clear titles indicating the processing parameters
- Automatic scaling for proper visualization

### Console Output

```
TASK 1: INTENSITY LEVEL REDUCTION
============================================================
✓ Reduced to 2 intensity levels
✓ Reduced to 4 intensity levels
✓ Reduced to 8 intensity levels
✓ Reduced to 16 intensity levels
✓ Reduced to 32 intensity levels
✓ Reduced to 64 intensity levels
✓ Reduced to 128 intensity levels
```

### File Outputs

All processed images are automatically saved in the `results/` directory with descriptive filenames.

## 📄 License

This code is provided for educational purposes. Feel free to modify and use it for your image processing projects.

## 🤝 Contributing

Feel free to enhance the code by:

- Adding new image processing tasks
- Improving error handling
- Adding more visualization options
- Optimizing performance for large images

---

**Happy Image Processing! 🖼️✨**
