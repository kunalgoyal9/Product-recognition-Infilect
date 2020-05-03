# Grocery Product Detection

I Fine tuned MobileNet SSD architecture for `21k` steps for a batch size of `32` images with anchor boxes of two aspect ratio viz `0.33` and `0.5` (these two gave good mAp).

## File description

1) ```Making deliverables.ipynb```

Visualize model trained in `trained-inference-graphs-21482-steps` directory and generates `metrics.json` and `image2products.json`

2) `scripts/generate_tfrecord.py`

This is preprocessing file for reading annotation txt to generate `test_labels.csv` and `train_labels.csv` 

3. `eval_detection/image_000*`

Some sample images to visualize images

## Hyperparameters:

#### lr:

```
    initial_learning_rate: 0.0040000002
    decay_steps: 800720
    decay_factor: 0.94999999
```

#### anchors:

I used two anchor boxes having aspect ratio of ```0.5``` and ```0.33299```

## Results:
 
```
{

"mAP@0.5IOU": 0.946939,
"average_precision": 0.946939, 
"classification_loss": 1.317305, 
"localization_loss": 0.25065

}
```

## Q&A

#### 1. What is the purpose of using multiple anchors per feature map cell?

Anchor boxes are used to predefine the location of different objects of different sizes in the image. 

For any output cell, we define the part of image to be taken using these anchor boxes. SSD uses 6 anchor boxes of aspect ration 1/2, 1, 1/3, 2, 3 and last one is interpolated.



#### 2. Does this problem require multiple anchors? Please justify your answer.

This problem requires only one anchor box as the ratio of width to the height. As most of the boxes on the shelf are of same ratio. For my training, I took boxes of two aspect ratio 0.5 and 0.33 as in some examples they varied.

 
