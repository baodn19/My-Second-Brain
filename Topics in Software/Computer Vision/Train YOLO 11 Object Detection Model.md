# Source: [How to Train YOLO 11 Object Detection Models Locally with NVIDIA - EJ Technology Consultants](https://www.ejtech.io/learn/train-yolo-models)

# Important Parameters of Model
- *mAP:* relative accuracy of model
- *params & FLOPs:* size of model; the bigger -> more compute resources; large: slow, accurate
- *Resolution:* default - 640x640
	- Modify w/ `-imgsz`
	- Low resolution = fast, inaccurate
- *# epochs:* a pass through full **training** dataset
	- data < 200 images: 60 epochs
	- data > 200 images: 40 epochs

# YOLO
- `yolo detect train data=data.yaml model=yolo11s.pt epochs=60 imgsz=640`:
	- *Function:* run training
	- *data:* path to training config file
	- *model:* e.g. “yolo11s.pt, “yolo11l.pt"
	