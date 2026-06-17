# 👤 Face Recognition Project

<!-- ADD DEMO GIF HERE -->

**Real-time face detection and recognition using deep learning. Identify people in video streams or images with high accuracy.**

## The Problem

Automatic face recognition is essential for security, user authentication, attendance systems, and photo organization. This project demonstrates practical face detection and identification using pre-trained neural networks.

## How It Works

1. **Load Known Faces**: Encode reference images of known people
2. **Capture Video/Image**: Process input from webcam or file
3. **Detect Faces**: Locate faces in frame using CNN or Haar cascades
4. **Extract Features**: Generate 128-dimensional face encodings
5. **Match & Identify**: Compare unknown faces against known encodings (euclidean distance)
6. **Display Results**: Annotate video with names and confidence scores

## Tech Stack

- **Python 3.7+**
- **dlib** – face detection & encoding
- **face_recognition** – high-level API
- **OpenCV** – video I/O and visualization
- **NumPy** – numerical operations
- **Pillow** – image processing

## Quick Start

```bash
git clone https://github.com/georgepol1023/Face-Recognition-Project.git
cd Face-Recognition-Project
pip install -r requirements.txt
python face_recognition.py
```

**Setup Known Faces:**
1. Create directory: `known_faces/`
2. Add subdirectories per person: `known_faces/john/`, `known_faces/jane/`
3. Add sample images (.jpg, .png)
4. Run script – it will encode and cache encodings

## Customization

```python
# In face_recognition.py:
KNOWN_FACES_DIR = 'known_faces'
UNKNOWN_FACES_DIR = 'unknown_faces'
TOLERANCE = 0.6  # Lower = stricter matching (0.0-1.0)
MODEL = 'hog'    # 'hog' (fast) or 'cnn' (accurate)
```

## Output

- **Live Video**: Detected faces with bounding boxes and names
- **Confidence Scores**: Distance score for each match
- **CSV Export**: Save recognized faces with timestamps
- **Annotated Images**: Save output frames with annotations

## Key Metrics

| Metric | Performance |
|--------|-------------|
| Detection Accuracy | ~99% on benchmark datasets |
| Recognition Accuracy | ~99% (varies with image quality) |
| Inference Speed (HOG) | ~50-100ms per frame |
| Inference Speed (CNN) | ~300-500ms per frame |

## Limitations

⚠️ **Image Quality**:
- Requires clear, frontal face views
- Low resolution images (<50×50px) reduce accuracy
- Extreme angles/occlusions cause misses
- Identical twins may be confused

⚠️ **Technical**:
- Slow on large reference datasets (100+ people)
- No real-time liveness detection (can be fooled by photos)
- Struggles with very young/old faces
- No age/emotion estimation (separate models needed)

## Future Enhancements

- [ ] Liveness detection (distinguish photos from live faces)
- [ ] Age/gender/emotion estimation
- [ ] Multi-face tracking across frames
- [ ] Mask-aware recognition (COVID era)
- [ ] GPU acceleration (CUDA)
- [ ] Web API for remote recognition

## Use Cases

✅ Security access control  
✅ Attendance tracking  
✅ Photo album auto-tagging  
✅ Missing person identification  
✅ Presentation audience analysis  

## Files

- `face_recognition.py` – Main recognition engine
- `requirements.txt` – Dependencies
- `known_faces/` – Reference images (create manually)
- `output/` – Annotated results

## Performance Tips

- Use HOG model for webcam (faster)
- Pre-encode known faces and cache
- Resize input images to 480p for speed
- Batch process images for efficiency

## Privacy & Ethics

⚠️ This tool processes face data. Please ensure compliance with:
- GDPR/CCPA regulations
- Local biometric privacy laws
- Informed consent from subjects
- Proper data storage & security

## Author

[George Politis](https://github.com/georgepol1023)

## Resources

- [dlib C++ Library](http://dlib.net/python/index.html)
- [face_recognition Library](https://github.com/ageitgey/face_recognition)
- [OpenCV Face Detection](https://docs.opencv.org/master/d7/d8b/tutorial_py_face_detection_in_an_image.html)
- [LFW Face Database](http://vis-www.cs.umass.edu/lfw/)
