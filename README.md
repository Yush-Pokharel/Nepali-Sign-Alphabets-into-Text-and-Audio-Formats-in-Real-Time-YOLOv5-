# Nepali Sign Language Alphabet Recognition

This project converts Nepali Sign Language (NSL) alphabets into **real-time text and audio** using a **YOLOv5** model.  
The model was trained on an **augmented dataset** of self-created images, alongside some preexisting ones.


## Table of Contents
1. Project Overview
2. Features
3. Getting Started
4. Step 1: Image Acquisition
5. Step 2: Organizing Files
6. Step 3: Preprocessing
7. Step 4: YOLO Data Preparation
8. Step 5: Model Training
9. Step 6: UI Integration
10. Usage


## Project Overview
This project enables **real-time NSL alphabet recognition**:
- Converts hand signs into text and audio.
- Uses a **custom YOLOv5 model** trained on both self-captured and augmented images.
- Provides a user-friendly interface for testing and real-time usage.


## Features
- Real-time hand sign detection.
- Conversion to both text and audio.
- Supports all Nepali alphabets.
- Lightweight UI with PyTorch and YOLOv5 integration.


## Getting Started
### Requirements
- Python 3.9+
- PyTorch with CUDA support:
  pip3 install torch torchvision torchaudio --index-url https://download.pytorch.org/whl/cu124
- Other dependencies:
  pip install opencv-python numpy matplotlib pyyaml wandb


## Step 1: Image Acquisition
1. **Convert Videos to Images**
   - `video_to_image`: Converts all single-letter videos into folders of images.
2. **Capture Letters from Combo Videos**
   - `combo_video_to_image`: Extracts each letter from a video and stores it in respective directories based on user input.
3. **Manual Image Capture**
   - `capture_image`: Captures images manually and stores them in vowel-specific folders.



## Step 2: Organizing Files
- Run `move_files.py` to move images into the proper directories for preprocessing.



## Step 3: Preprocessing
1. **Data Augmentation**
   - Perform augmentations to increase dataset variability.
2. **Train/Test/Validation Split**
   - Split dataset into training, testing, and validation sets.
3. **Hand Annotation**
   - Use `annotate_hands_eff`.
   - Note: CPU and memory intensive; run in batches.



## Step 4: YOLO Data Preparation
1. **Move YOLO Files**
   - `move_yolo_files`: Moves images and annotations into `train`, `test`, and `val` folders.
2. **Folder Structure**
   - Create master folder with subfolders:
     train/
       images/
       labels/
     test/
       images/
       labels/
     val/
       images/
       labels/
3. **Create YAML**
   - Create `data.yaml` pointing to the directories and listing all classes.



## Step 5: Model Training
1. Add WandB API key to log training metrics.
2. Train YOLOv5 in Google Colab or local GPU.
3. Download trained weights from `runs/weights/best.pt`.
4. Clone YOLOv5 repository and place `.pt` file for inference or further training.



## Step 6: UI Integration
1. Install PyTorch (CUDA-enabled) as shown above.
2. Integrate trained model into UI for real-time detection.
3. Check the cache folder before running.
4. Refactor code as needed for performance improvements.


## Usage
1. Run the UI script:
   python app.py
2. Show NSL alphabet in front of your camera.
3. The system will display **text** and play **audio** in real-time.
