# DensePose-Paddle
A reproduction of DensePose by PaddlePaddle
## 1. 首先复现detectron2，并没有使用facebook的代码，而是https://github.com/MILVLG/bottom-up-attention.pytorch
## 2. 训练

首先准备数据集 [dataset](http://densepose.org/#dataset) 格式如下:
<pre>
datasets/coco/
  annotations/
    densepose_{train,minival,valminusminival}2014.json
    <a href="https://dl.fbaipublicfiles.com/detectron2/densepose/densepose_minival2014_100.json">densepose_minival2014_100.json </a>  (optional, for testing only)
  {train,val}2014/
    # image files that are mentioned in the corresponding json
</pre>

训练过程先略去

3. 测试图片（运行代码和facebook的detectron2_0.6版本有些不同）
（1） Show bounding box and segmentation:
```bash
python apply_net.py show configs/densepose_rcnn_R_50_FPN_s1x.yaml model_final_162be9.pkl 1.jpg dp_segm,bbox --output 1_segm.png
```
![1_segm 0001](https://user-images.githubusercontent.com/23380949/150077639-cbbcec87-589a-426a-bf7c-e09662ebe56d.png  )

2. Show bounding box and estimated U coordinates for body parts:
```bash
python apply_net.py show configs/densepose_rcnn_R_50_FPN_s1x.yaml model_final_162be9.pkl 1.jpg dp_u,bbox --output 1_u.png
```
![1_dpu 0001](https://user-images.githubusercontent.com/23380949/150081003-e1de74f9-8f0a-4ed2-86f3-c5aa29f84b96.png)

3. Show bounding box and estimated V coordinates for body parts:
```bash
python apply_net.py show configs/densepose_rcnn_R_50_FPN_s1x.yaml model_final_162be9.pkl 1.jpg dp_v,bbox --output 1_v.png
```
![1_dpv 0001](https://user-images.githubusercontent.com/23380949/150080977-aa5e7e16-30d3-46b9-b1db-bcfaf3b6b780.png)

4. Show bounding box and estimated U and V coordinates via contour plots:
```bash
python apply_net.py show configs/densepose_rcnn_R_50_FPN_s1x.yaml model_final_162be9.pkl 1.jpg dp_contour,bbox --output 1_contour.png
```
![1_contour 0001](https://user-images.githubusercontent.com/23380949/150074670-d2b9fd88-7318-4b83-85b6-2d90d42d83da.png)


