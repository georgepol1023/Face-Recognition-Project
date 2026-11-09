# Face Recognition

Real-time face recognition from a webcam in about 50 lines of Python. Put photos of the
people you want to recognise in a folder, run the script, and it draws a box and a name
around every face it sees.

## How it works

1. **Learn the known faces.** Every `.jpg` or `.png` in `known_faces/` is turned into a
   128-number face encoding with the [`face_recognition`](https://github.com/ageitgey/face_recognition)
   library (built on dlib). The file name becomes the person's name, so `alice.jpg` is labelled "alice".
2. **Read the webcam.** Each frame is captured with OpenCV and converted to RGB.
3. **Find and encode faces.** Every face in the frame is located and encoded the same way.
4. **Match.** Each face is compared against the known encodings, and the closest one is used if it is
   within the library's default distance threshold (0.6). Otherwise it is labelled "Unknown".
5. **Draw.** A green box and the name are drawn on the frame. Press `q` to quit.

## Run it

```bash
git clone https://github.com/georgepol1023/Face-Recognition-Project.git
cd Face-Recognition-Project
pip install -r requirements.txt
python recognise.py
```

Add one clear, front-facing photo per person to `known_faces/`, named after them
(for example `known_faces/alice.jpg`). Two sample photos are included.

`face_recognition` needs dlib. On Windows, `pip install dlib-bin` is the easiest way to get a
prebuilt copy; on macOS and Linux, `pip install dlib` builds it (CMake required).

## Limitations

- One reference photo per person, so side angles, poor lighting and glasses can cause misses.
- Every frame is processed at full size, so it can be slow on a laptop CPU.
  Shrinking frames before detection would speed it up.
- It can be fooled by a photo held up to the camera (no liveness check).

## Built with

Python, OpenCV, NumPy and `face_recognition` (dlib).

Face data is personal data: only use photos of people who have agreed to it.
