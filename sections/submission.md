Users can participate in one or both of the following tracks:

#### **Track-1 |** 

In this track, participants are expected to train OV-PARTS models on the train set of Pascal-Part-116 and test on the test set of Pascal-Part-116.

##### *Evaluation Protocal*
This track focuses on evaluating the model's overall performance across both seen and unseen classes. 
We use the harmonic mean IoU (hIoU) metric to account for significant discrepancies in accuracies between seen and unseen classes.

#### **Track-2 |** 

In this track, participants are expected to train OV-PARTS models on the train set of ADE20K-234 or any other kinds of data except Pascal-Part-116 and test on the test set of Pascal-Part-116. **If you opt to use existing foundation models capable of segmenting parts, please submit your results in this track**.

##### *Evaluation Protocal*
This track focuses on evaluating the model's performance across different levels of part granularity.
We use the mean class-wise Intersection over Union (mIoU) metric.

**Note:**
For both tracks, the evaluation is under the *Oracle-Obj Setting*: The ground-truth mask and class of objects are assumed to be known. 


#### **Official Baseline**
1. ZSseg<sup>[1]</sup>.
We train ZSseg with two improvements: (1) An Object Mask Prompt strategy which introduces the object-awareness to the first part proposal stage. (2) A Compositional Prompt Tuning strategy which not only enhances object awareness in the second stage but also shifts CLIP’s attention from objects to object parts.


2. CLIPSeg<sup>[2]</sup>.
We finetune specific modules of CLIPSeg which is pretrained on the PhraseCut dataset.

Participants can refer to our *[Github Repo](https://github.com/OpenRobotLab/OV_PARTS)* for the implementations of baselines. 

#### **Submission**

Results for all test samples are aggregated in a single array which is saved as a single JSON file `submission.json`.
The results should be organized in the following format:

```json
    [
        {  
            "file_name": "str",  
            "category_id": "int",
            "segmentation": "RLE"
        },
        ...
    ]
```

Please encode the segmentation result of each object-part category in an image with a **single binary mask**. 
Binary masks should be encoded via RLE. See `encode_json_sem_seg()` in *[sem_seg_evaluation.py](https://github.com/facebookresearch/detectron2/blob/b7c7f4ba82192ff06f2bbb162b9f67b00ea55867/detectron2/evaluation/sem_seg_evaluation.py#L232)*

Participants are expected to submit the results to the *[evaluation server](https://eval.ai/)* hosted by *[EvalAI](https://eval.ai/web/challenges/challenge-page/2283/overview)*. 

**If you have any questions, please contact kellymeng0427@gmail.com.**

#### References

> [1] Xu, Mengde, et al. "A simple baseline for open-vocabulary semantic segmentation with pre-trained vision-language model." European Conference on Computer Vision. Cham: Springer Nature Switzerland, 2022.

> [2] Lüddecke, Timo, and Alexander Ecker. "Image segmentation using text and image prompts." Proceedings of the IEEE/CVF Conference on Computer Vision and Pattern Recognition. 2022.
