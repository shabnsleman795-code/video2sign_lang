# Video to Sign Language Converter

Convert spoken video content into sign language using a multi-step AI pipeline.

This project is a proof-of-concept that translates videos containing speech into sign language sequences. It does this by extracting audio, separating speech tracks, transcribing them into text, and finally matching the recognized words or phrases with corresponding sign language video clips from a dataset.

## ✨ How It Works (The Corrected Pipeline)

This project follows a specific multi-stage process:

1.  **Audio Extraction**: Demucs is used to extract and clean the audio track from the input video file.
2.  **Source Separation**: The isolated audio is then processed by SpeechBrain to separate different sound sources (e.g., speech from background music), enhancing speech clarity for transcription.
3.  **Speech Recognition**: The cleaned speech audio is transcribed into text using the powerful OpenAI Whisper model, specifically `whisper-large-v3`.
4.  **Sign Matching**: A custom script matches the transcribed words with a pre-existing dataset of sign language videos. Each video file's name corresponds to a specific sign or word (e.g., `hello.mp4`, `thank_you.mp4`).
5.  **Video Assembly**: The matched sign language video clips are sequentially stitched together to form a final video output.

## 🛠️ Technical Components

| Component | Role in This Project | Key Feature |
|           |                      |             |
| **Demucs** | Extracts the raw audio track from the input video file. | Effective at isolating audio from video containers. |
| **SpeechBrain** | Separates the extracted audio into distinct sources to isolate clean speech. | Improves speech clarity by removing non-vocal audio, leading to more accurate transcription. |
| **OpenAI Whisper** | Converts the cleaned speech audio into accurate text. The `large-v3` model is used for its robustness across languages and accents. | Trained on 680k hours of multilingual data, offering high accuracy even with background noise and various accents. |
| **Custom Python Script** | Maps the transcribed text to filenames in the sign language video dataset and assembles the final video. | Core logic that bridges AI output with the visual dataset. |

## 📁 Project Structure

```
video2sign_lang/
├── data/                           # Directory for sign language video clips
│   ├── hello.mp4
│   ├── thank_you.mp4
│   └── ...                         # More clips named after words/signs
├── Whisper_STT_Results/            # Text files from Whisper transcription
├── SpeechBrain_Separation_Results/ # Audio files after source separation
├── Results_Untitled Video_20250906_164056/
├── FinalVersion.ipynb              # Main Jupyter Notebook pipeline
├── merged_videos_*.mp4             # Example of a final assembled video
└── README.md                       # This file
```

## 🚀 Getting Started

### Prerequisites
*   Python 3.8 or higher.
*   `ffmpeg` installed on your system (required by Whisper).

### Installation

1.  Clone the repository:
    ```bash
    git clone https://github.com/shabnsleman795-code/video2sign_lang.git
    cd video2sign_lang
    ```

2.  Install Python dependencies. Since a `requirements.txt` is not yet provided, install the core packages:
    ```bash
    pip install openai-whisper demucs speechbrain torch torchaudio moviepy
    ```

### Usage

1.  Place your input video (e.g., `my_video.mp4`) in the project root.
2.  Ensure your sign language video dataset is in the `data/` folder, with filenames corresponding to words.
3.  Open and run the `FinalVersion.ipynb` Jupyter Notebook. It will guide you through the steps.
4.  The final output, a merged video of sign language clips, will be generated in the root directory.

## 📝 Notes & Potential Issues

*   **Transcription Accuracy**: For Arabic speech, short words or specific dialects might sometimes be transcribed incorrectly by Whisper. Using a clearer audio input from the SpeechBrain separation step can help mitigate this.
*   **Dataset Requirement**: The project's success depends entirely on the completeness of your `data/` folder. The custom matching script will only find signs for which a correspondingly named video file exists.
*   **Pipeline Customization**: The logic for text-to-sign matching (splitting sentences, handling synonyms, etc.) is in the custom script and can be refined for more fluent results.

## 👤 Author

**Sha3bon**
 GitHub: [@shabnsleman795-code](https://github.com/shabnsleman795-code)

---

## 📋 How to Add This to Your GitHub Repository

1.  **Copy the entire text above** (from `# Video to Sign Language Converter` to the end).
2.  Go to your GitHub repository: https://github.com/shabnsleman795-code/video2sign_lang
3.  Click the **"Add file"** button, then select **"Create new file"**.
4.  Name the file **`README.md`** (exactly like this).
5.  **Paste the copied text** into the large text area.
6.  Scroll down to the **"Commit new file"** section.
7.  You can leave the commit message as default or write a short message like `"Add project README"`.
8.  Click the green **"Commit new file"** button.

