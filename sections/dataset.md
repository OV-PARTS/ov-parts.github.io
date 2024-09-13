#### Goal

Given a natural image and a set of candidate object parts described by text labels, the segmentation model must accurately assign a label to each pixel. During inference, the segmentation model should be capable of handling classes out of the training vocabulary at both object-level and part-level.

#### Datasets

##### Pascal-Part-116

Pascal-Part dataset is an extension of the PASCAL VOC 2010 dataset, further annotating objects’ part masks. Pascal-Part-116 is a more practical version of Pascal-Part where some over-segmentation parts are merged.
Pascal-Part-116 includes a total of 116 object part classes across 20 object classes.

The download link for Pascal-Part-116 is *[here](https://drive.google.com/file/d/1hsbwNdfPe4c6yVLZDjzjPTC7NL65I-rr/view)*.

##### Data Format

For Pascal-Part-116, each training sample consists of:

* the training image

* the object segmentation
pixel indices correspond to 20 object classes.

* the part segmentation
pixel indices correspond to 116 part classes.

For both object and part segmentation images, index 255 corresponds to background or unlabelled.


##### ADE20K-Part-234

ADE20K dataset provides open-ended annotations of 847 objects and 1000+ parts, following the WordNet hierarchy. ADE20K-Part-234 only keeps the objects which have more than one frequently annotated part (over 100 occurrences) and the parts which have more than 10 occurrences. To reduce noise 
in the annotations, duplicated parts have been manually merged. 

The download link for ADE20K-Part-234 is *[here](https://drive.google.com/file/d/1EBVPW_tqzBOQ_DC6yLcouyxR7WrctRKi/view)*.

##### Data Format

For ADE20K-Part-234, each training sample consists of:

* the training image

* the instance-level object annotation in the format of  

    ```json
    {  
        "file_name": "str",  
        "height": 0,  
        "width": 0,  
        "obj_sem_seg_file_name": "str",  
        "sem_seg_file_name": "str",  
        "obj_annotations": [
            {
                "iscrowd": 0,
                "bbox": [0, 0, 0, 0],
                "category_id": 0,
                "segmentation": "RLE"
            }
        ]
    }


* the part segmentation
pixel indices correspond to 234 part classes.

For both object and part segmentation masks, index 65535 corresponds to background or unlabelled.

<!-- #### Evaluation Metric

Given the **ground truth object segmentation mask**, calculate the **mean class-wise Intersection over Union (mIoU)** on both seen and unseen classes and then calculate the harmonic mean IoU (hIoU) as: 
**hIoU = (2 * mIoU_{seen} * mIoU_{unseen} / (mIoU_{seen} + mIoU_{unseen}))**


#### Tasks

##### Generalized Zero-Shot Part Segmentation. 

Humans can categorize a new object based on its part descriptions related to a known object. This analogical reasoning ability is important in open vocabulary part segmentation because the existing large Vision Language Models (VLMs) have limited abilities to recognize parts and the available labeled data for training part segmentation models is scarce. Hence, this benchmark task aims to assess the model’s capability to generalize part segmentation from seen objects to related unseen objects.

##### Cross-Dataset Part Segmentation.

While objects are typically well-defined entities with strict boundaries, the granularity of parts can be flexible, posing the extra open granularity challenge that rarely occurs in object-level open-vocabulary semantic segmentation.
Hence, except for the zero-shot generalization ability, this benchmark task further aims to assess the model’s capability to generalize part segmentation across different datasets with varying levels of part granularity.

Evaluation Metric: mean class-wise Intersection over Union (mIoU) between the predicted segmentation mask and the ground truth mask on both datasets.  -->

