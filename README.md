## How to run this version of AnyLabelling

1. Open the Perception Docker container

```
export TAG_NAME="latest" && xhost +local:docker && docker compose -f docker_files/docker-compose.yml run --rm perception`
```

2. Clone AnyLabelling from our fork

This should be done inside VS Code, so that you automatically use your Git credentials:
```
cd ~/ws_lab0/src
git clone git@github.com:LAB0-Inc/anylabeling.git
```

3. set AnyLabeling up
```
cd anylabeling
python3 -m pip install --user --no-cache-dir --break-system-packages  -r requirements-gpu.txt
sudo apt-get update
sudo apt-get install pyqt5-dev-tools
pyrcc5 -o anylabeling/resources/resources.py anylabeling/resources/resources.qrc
```

4. Run AnyLabelling with:
```
	cd ~/ws_lab0/src/anylabeling && python3 -m anylabeling.app
```

## Changes w.r.t. the original code
* Contours of boxes are drawn with 5 random colors, rather than all the same.
* Segments are drawn in semi-transparent white.
* Added shortcuts for hiding [Z] and for visualizing [X] the annotations.
* The default zoom level was adjusted so that the images are fully visibile.
* The images are visualized as raw: without smoothing and without the JPEG artifacts that appear in the original version of the code.
* The cross line is not visualized by default.
* When creating a new annotation, the latest label is automatically applied to it.
* Epsilon (the distance at which the mouse pointer sticks to contours) was reduced to 5 pixels. This allows selecting one small segment (by clicking in the middle of it, away from the contour) without having to first zoom in on it.