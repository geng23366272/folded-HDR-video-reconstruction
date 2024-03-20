# SSViT: Modulo High Dynamic Range Video Reconstruction via Selective Spatiotemporal Vision Transformer

By Tianyu Geng, Feng Ji, [Wee Peng Tay](https://github.com/wptay)

![](https://github.com/geng23366272/folded-HDR-video-reconstruction/blob/main/Structure_v2.png)


## Requirements

* Linux Distributions (tested on Ubuntu 20.04).
* NVIDIA GPU and CUDA cuDNN
* Python >= 3.7
* Pytorch >= 1.1.0
* cv2
* numpy
* tqdm
* tensorboardX (for training visualization)

## Inference

* for `.npy` format in `(H, W, 3)` shape:
```
python execute/infer_LearnMaskNet.py -r checkpoint/checkpoint-mask.pth --data_dir <path_to_modulo_images> --result_dir <path_to_result> --resume_edge_module checkpoint/checkpoint-edge.pth default
```

* Use `TonemapReinhard_npy.py` to visualize the results. Note that the default tonemap method we use is `cv2.createTonemapReinhard(intensity=-1.0, light_adapt=0.8, color_adapt=0.0)`.


## Training 

1. Make dataset from original data (HDR data in `.npy` format):
    * make dataset:
    ```
    python scripts/make_dataset.py --data_dir <path_to_original_data> --train_dir <path_to_training_dataset> --test_dir <path_to_test_dataset> --training_sample <number_of_training_samples>
    ```

2. Run:
```
    python execute/train.py -c <path_to_config_file>
```

## More results
![](https://github.com/geng23366272/folded-HDR-video-reconstruction/blob/main/highlight_results/1.png)
see  https://drive.google.com/drive/folders/1Dn4G8Fqm6DMJEdju3p5F2J8XBhCP7d5w?usp=sharing

