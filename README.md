# Wav2Lip Documentation

## **Overview**
The Wav2Lip project synchronizes lip movements in videos with audio using a pre-trained deep learning model. This guide provides an in-depth explanation of the project setup, functionality, and deployment workflows, including converting the model for iOS applications.

The app uses components to process video and audio inputs and integrates them into a CoreML model for real-time lip synchronization. This README references the actual implementation from the [Wav2Lip-App repository](https://github.com/Ialzouby/Wav2Lip-App).

---

## **Model Conversion for iOS Deployment**

### **Purpose:**
The pre-trained PyTorch model from Wav2Lip needs to be converted to CoreML format for use in iOS applications. This involves exporting the model for ONNX compatibility and then converting ONNX to CoreML.

### **Steps Overview:**
1. **Export to ONNX:**
   - Analyze the PyTorch model's input requirements.
   - Export the model using dummy inputs to create an ONNX file.
2. **Convert ONNX to CoreML:**
   - Use CoreMLTools to convert the ONNX model.
   - Validate the CoreML model to ensure compatibility with iOS.

**Read `modelconversion.txt` for more details.**

---

## **Project Setup**

### **Initial Steps**
1. Install required tools:
   - **Homebrew** for macOS package management.
   - **Pyenv** for managing Python versions.
2. Create a virtual environment to ensure isolated dependency management.
3. Clone the [Wav2Lip repository](https://github.com/Rudrabha/Wav2Lip) and install dependencies.

**Read `projectsetup.txt` for more details.**

---

## **Best Practices**

### **Data Requirements:**
- Use MP4 videos for better compatibility and processing speed.
- Ensure audio is in WAV format with appropriate sampling rates.

### **Performance Optimization:**
- Compress video resolution for faster processing (e.g., 1080p or 720p).
- Keep video length and audio duration aligned to avoid truncation or mismatch.

### **Testing:**
- Test the CoreML model with various inputs to ensure robustness.
- Validate each iOS component independently to identify potential issues.

**Read `bestpractices.txt` for more details.**

---

## **Project Components**

### **1. ContentView.swift**
#### **Purpose:**
`ContentView.swift` serves as the main interface for the app, allowing users to interact with core features like selecting videos, processing audio and video, and preparing data for the CoreML model.

#### **Key Features:**
- **Video Selection:** Users select two videos—one for the audio and another for the content.
- **Status Display:** Displays information about the selected files and their processing status.
- **Processing Workflow:** Triggers methods to preprocess and extract audio and prepare video frames for the CoreML model.
- **Integration Hub:** Coordinates the workflow by connecting `VideoPicker`, `AudioExtractor`, and `VideoPreprocessor` components.

**Read `contentview.txt` for more details.**

---

### **2. VideoPicker.swift**
#### **Purpose:**
This component enables users to choose videos from their iOS device library. It bridges SwiftUI and UIKit using a controller to provide a seamless file selection experience.

#### **Key Features:**
- **File Selection:** Focused on video files, ensuring compatibility with the app's requirements.
- **Data Handling:** Captures and stores the selected video's URL for further processing.
- **Integration:** Smoothly integrates into the app’s SwiftUI views, making it accessible and easy to use.

**Read `videopicker.txt` for more details.**

---

### **3. AudioExtractor.swift**
#### **Purpose:**
Extracts audio from a video file, converting it into a WAV format for model compatibility.

#### **Key Features:**
- **Audio Track Extraction:** Identifies and extracts the audio track from the selected video.
- **Conversion:** Converts the audio into the Linear PCM WAV format, which is required for CoreML input.
- **Asynchronous Operation:** Ensures the UI remains responsive by processing audio extraction in the background.

#### **Workflow:**
1. Loads the audio track from the video.
2. Processes and saves it in the specified format.
3. Passes the extracted audio for synchronization with video.

**Read `audioextractor.txt` for more details.**

---

### **4. VideoPreprocessor.swift**
#### **Purpose:**
Prepares the video content by resizing and converting frames to match the input requirements of the CoreML model. It also handles format conversions, such as from MOV to MP4.

#### **Key Features:**
- **Format Conversion:** Converts video files to MP4 to ensure compatibility with the processing pipeline.
- **Frame Preprocessing:** Resizes frames and adjusts their format for the CoreML model.
- **Optimization:** Uses efficient image and video processing techniques to improve performance.

**Read `videopreprocessor.txt` for more details.**

---

## **Additional Resources**
- **Wav2Lip Pretrained Model:** [GitHub Repository](https://github.com/Rudrabha/Wav2Lip)
- **iOS Implementation:** [Wav2Lip-App Repository](https://github.com/Ialzouby/Wav2Lip-App)

---

## **Contact**
For questions or feedback, contact [ialzouby@gmail.com](mailto:ialzouby@gmail.com).

---

This README provides a high-level overview to get started with the Wav2Lip project while detailing the workflow and components. **Refer to the individual `.txt` files for more implementation details.**
