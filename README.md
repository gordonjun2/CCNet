# Using CCNet (CornerNet and CenterNet) with Docker
Credits:

[**CornerNet: Detecting Objects as Paired Keypoints**](https://arxiv.org/abs/1808.01244)  
Hei Law, Jia Deng

Original Github Repository: https://github.com/princeton-vl/CornerNet

[**CenterNet: Keypoint Triplets for Object Detection**](https://arxiv.org/abs/1904.08189)

Original Github Repository: https://github.com/Duankaiwen/CenterNet

**This repository contains CornerNet and CenterNet models for Object Detection task. Video object detection is also added in this repository, on top of the original repositories. You can also create a docker container version here. For more information on both their approaches to object detection, please refer to the research papers or Github repositories above.**

## Preparation without using Docker

1. Git clone this repository to your local machine.

2. Follow the README.md in both CornerNet and CenterNet folders (CCNet/CornerNet and CCNet/CenterNet) for installation and usage instructions.

## Preparation with Docker

1. Git clone this repository to your local machine.

2. Navigate to the root directory (ccnet/) using terminal and build the docker image using:

    ```
    USER_ID=$UID docker-compose run ccnet
    ```

3. To exit the container, just use 'Ctrl + d".

4. If changes are made in the Dockerfile, build using:

    ```
    docker-compose build ccnet
    ```

5. To use the docker container without building, use:

    ```
    docker-compose run ccnet
    ```

6. If 'docker-compose.yml' is updated, use:

    ```
    docker-compose up ccnet
    docker-compose build ccnet
    ```

7. Done and enjoy ccnet!

## Notes

Please read docker-compose.yml (ccnet/) to know more about the configurations used. 

Also, [**cocodataset/cocoapi**](https://github.com/cocodataset/cocoapi) is already added in both the CornerNet and CenterNet folders (ccnet/CornerNet and ccnet/CenterNet). You do not have to git clone the repository again.

**Where to download MSCOCO datasets and their annotations? Also, where to place them?**

1. Go to MSCOCO official website (http://cocodataset.org/#download) and download the datasets.

2. Create a folder 'coco' in the same directory as the 'docker-compose.yml' (ccnet/). In the 'coco' folder, create an 'images' folder and an 'annotations' folder.

3. Place the datasets into the 'images' folder (eg. ccnet/coco/images/val2017/(images here)).

4. Place the respective annotations into the 'annotations' folder (eg. ccnet/coco/annotations/instances_val2017.json).

5. All set!

**Where to download pretrained models for both CornerNet and CenterNet? Also, where to place them?**

1. Go to the respective model's Github repository to download their pretrained models.

CornerNet: https://github.com/princeton-vl/CornerNet

CenterNet: https://github.com/Duankaiwen/CenterNet

Their pretrained models can be found in their README.md instruction.

2. Create a folder 'cache' in the same directory as the 'docker-compose.yml' (ccnet/). In the 'cache' folder, create a 'nnet' folder.

3. Place the model's pretrained model into the 'nnet' folder (eg. ccnet/cache/nnet/CenterNet-104/CenterNet-104_480000.pkl)

4. All set!

**Is GPU enabled in the docker container?**

1. Yes, you do not have to run any additional command. See 'docker-compose.yml' (ccnet/).

**I am unable to do video objection detection inference because of this error:**

No protocol specified
: cannot connect to X server :0

1.  Enable non-network local connections to access control list by running this command in your terminal (not in docker container):

    ```
    xhost +local:root
    ```

2. It should be working now. Try to start the video object detection again.

3. Once it is done, disable non-network local connections to access control list by running this command in your terminal (not in docker container):

    ```
    xhost -local:root
    ```

**Can I see my GPU processes while using the container?**

1. Yes, you do not have to run any additional command. To see GPU processes, type:

    ```
    nvidia-smi
    ```

See 'docker-compose.yml' (ccnet/).

**Why are the packages in CornerNet and CenterNet so outdated?**

1. I am not sure myself too. They were developed using those packages.