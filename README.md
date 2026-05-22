# 🖊️ Handwritten Digit Recognition

A Python desktop application that uses a **Convolutional Neural Network (CNN)** trained on the MNIST dataset to recognize handwritten digits (0–9) in real time. Draw a digit on the canvas, click **Recognise**, and the model predicts what you drew — along with a confidence score.

---

## 📸 How It Works

1. A CNN model is trained on the MNIST dataset (60,000 training images, 10,000 test images).
2. The trained model is saved as `mnist.h5`.
3. A Tkinter GUI lets you draw a digit on a canvas with your mouse.
4. On clicking **Recognise**, the canvas is captured as an image, preprocessed, and fed into the model.
5. The predicted digit and confidence percentage are displayed instantly.

---

## 🏗️ Project Structure

```
HandwrittenDigitRecognition/
│
├── Digit_Recognition_Trainer.py   # CNN model definition, training & saving
├── Digit_Recognition_UI.py        # Tkinter GUI that loads the model and runs predictions
├── mnist.h5                       # Pre-trained model (ready to use — no training needed)
└── README.md
```

---

## 🧠 Model Architecture

The CNN is built with Keras and has the following layers:

| Layer              | Details                          |
|--------------------|----------------------------------|
| Conv2D             | 32 filters, 5×5 kernel, ReLU     |
| MaxPooling2D       | 2×2 pool size                    |
| Conv2D             | 64 filters, 3×3 kernel, ReLU     |
| MaxPooling2D       | 2×2 pool size                    |
| Flatten            | —                                |
| Dense              | 128 units, ReLU                  |
| Dropout            | 30%                              |
| Dense              | 64 units, ReLU                   |
| Dropout            | 50%                              |
| Dense (output)     | 10 units, Softmax                |

- **Optimizer:** Adadelta  
- **Loss:** Categorical Cross-Entropy  
- **Epochs:** 10 | **Batch Size:** 128  
- **Test Accuracy:** ~99% on MNIST test set

---

## ⚙️ Prerequisites

- **Python 3.7–3.9** (recommended; TensorFlow/Keras compatibility)
- **Windows OS** (the UI uses `win32gui` for canvas capture)

### Required Libraries

Install all dependencies with:

```bash
pip install tensorflow keras numpy pillow pywin32
```

| Package      | Purpose                                      |
|--------------|----------------------------------------------|
| `tensorflow` | Backend for Keras model execution            |
| `keras`      | CNN model building and loading               |
| `numpy`      | Image array manipulation                     |
| `pillow`     | Image capture and preprocessing (`PIL`)      |
| `pywin32`    | Windows API for grabbing canvas coordinates  |

---

## 🚀 How to Run

> **The pre-trained model (`mnist.h5`) is already included**, so you can skip training and jump straight to the GUI.

### Step 1 — Clone the repository

```bash
git clone https://github.com/sehgalbhavya/HandwrittenDigitRecognition.git
cd HandwrittenDigitRecognition
```

### Step 2 — Install dependencies

```bash
pip install tensorflow keras numpy pillow pywin32
```

### Step 3 — Launch the GUI

```bash
python Digit_Recognition_UI.py
```

A window will open with a **300×300 white drawing canvas**.

---

## 🎮 Using the App

1. **Draw** a digit (0–9) on the white canvas using your mouse (left-click and drag).
2. Click the **Recognise** button.
3. The predicted digit and confidence score (e.g., `7, 94%`) will appear on the right.
4. Click **Clear** to reset the canvas and draw again.

---

## 🏋️ Re-training the Model (Optional)

If you want to retrain the model from scratch (takes ~5–10 minutes depending on your hardware):

```bash
python Digit_Recognition_Trainer.py
```

This will:
- Download the MNIST dataset automatically via Keras.
- Train the CNN for 10 epochs.
- Overwrite `mnist.h5` with the newly trained model.
- Print the final test loss and accuracy.

---

## 🐛 Troubleshooting

| Issue | Fix |
|---|---|
| `ModuleNotFoundError: No module named 'win32gui'` | Run `pip install pywin32` |
| `ModuleNotFoundError: No module named 'PIL'` | Run `pip install pillow` |
| `Could not load model 'mnist.h5'` | Make sure `mnist.h5` is in the same directory as `Digit_Recognition_UI.py` |
| Low prediction accuracy | Draw large, centered digits. The model expects single digits that fill most of the canvas. |
| `DLL load failed` on TensorFlow import | Ensure you are using Python 3.7–3.9 and a compatible TensorFlow version (`pip install tensorflow==2.9`) |

---

## 🛠️ Tech Stack

- **Language:** Python
- **Deep Learning:** TensorFlow / Keras
- **GUI Framework:** Tkinter
- **Dataset:** [MNIST](http://yann.lecun.com/exdb/mnist/) (Modified National Institute of Standards and Technology)
- **IDE:** Visual Studio Code

---

## 📄 License

This project was developed as part of an In-House Practical Training exercise. Feel free to use it for learning and experimentation.
