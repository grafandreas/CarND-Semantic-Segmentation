# Semantic Segmentation
## Introduction
In this project, you'll label the pixels of a road in images using a Fully Convolutional Network (FCN).

## Configuration
The code for this project was run with TF 1.8. It was run in two variants

- Retraining VGG: The first try was on a local GPU, w/o freezing any layers. That failed, because of memory issues with the GPU. Since I was experienceing problems with AWS, I decided to run it on CPU, having it run for about 13 hrs.
- Then I froze the layers, according to https://medium.com/@subodh.malgonde/transfer-learning-using-tensorflow-52a4f6bcde3e, like this:

```python
    vgg_layer7_out = tf.stop_gradient(vgg_layer7_out)
    vgg_layer4_out = tf.stop_gradient(vgg_layer4_out)
    vgg_layer3_out = tf.stop_gradient(vgg_layer3_out)
```

and introducing more code to deal correctly with the variables.

## Loss
Both runs have significantly improvement on loss during the epochs, however, obviously, the full retraining achieves even better values.

These are results from the run:
| | Variant A | Variant B |
|---|---|---|
|frozen|no|yes|
|epochs|50|50|
|batch size|1|3|
|[uu_000099.png|![][cpu-png/uu_000099.png]|![][gpu-png/uu_000099.png]|

