import cv2
import sys

def is_4k_video(video_path):
    cap = cv2.VideoCapture(video_path)
    
    if not cap.isOpened():
        print("Error: Could not open video file.")
        return False
    
    width = int(cap.get(cv2.CAP_PROP_FRAME_WIDTH))
    height = int(cap.get(cv2.CAP_PROP_FRAME_HEIGHT))
    cap.release()
    
    print(f"Video Resolution: {width}x{height}")
    return width >= 3840 and height >= 2160

if __name__ == "__main__":
    if len(sys.argv) != 2:
        print("Usage: python detect_4k.py <video_file>")
        sys.exit(1)
    
    video_file = sys.argv[1]
    if is_4k_video(video_file):
        print("The video is in 4K resolution.")
    else:
        print("The video is not in 4K resolution.")
