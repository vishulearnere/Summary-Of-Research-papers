# ## Paper-4: A Multimodal Framework for the Detection of Hateful Memes :Phillip Lippe∗, Nithin Holla∗, Shantanu Chandra
### Problem statement
Proposing  a multimodal hateful memes detection framework
### Methodology / Solution / Architecture
##### Image feature extraction and base model selection
- UNITER outperforms LXMERT and Oscar by a large margin for both their base and large versions
##### Confounder upsampling and loss re-weighting
- upsample the confounders in the batches during the supervised fine-tuning step of UNITER
-  a loss re-weighting strategy during training and weigh the loss of the hateful class higher, subsequently affecting the update##### s of the model parameters
##### Cross-validation ensemble
##### Training with margin ranking loss
##### Fine-grained YOLO9000 object tags
### Metrics
- AUROC (Area Under the Receiver Operating Characteristics )
### Experiment
- LXMERT, UNITER, Oscar, BERT, R-CNN
### Code repository / supplemental material
- https://arxiv.org/abs/2012.12871
- https://github.com/Nithin-Holla/meme_challenge
### Result
| Model                               | AUROC    | AUROC |AUROC |
|-------------------------------------|:--------:|-------|--------|
|                                     | Development| Phase 1 |Phase 2|
|ViLBERT CC | 70.07 |70.03|  –
|VisualBERT COCO |73.97 |71.41| –
|UNITER |78.04 |74.73| –|
|LXMERT |72.33| – |–|
|Oscar |72.00 |– |–|
|UNITERCV10 |79.81| – |–|
|UNITERCV10 + CFU |79.64| –| –|
|UNITERCV10 + CFU + HW| 80.01 |78.60| –|
|UNITERCV15 + CFU + HW | 80.65 | 79.06 | –|
|UNITERCV30 + CFU + HW |81.36 |78.98 |–|
|UNITERCV15 + CFU + HW + MRL |80.44 |78.14| –|
|UNITERCV15 + CFU + HW + YOLO |80.67 |78.21| –|
|UNITERENSEMBLE 1 |81.71 |79.13 |80.33|
|UNITERENSEMBLE 2 |81.76 |79.10 |80.40|
|UNITERFINAL |77.39 |79.07 |80.53|

AUROC scores of our models on the development set (dev-seen) as well as the Phase 1 and 2 test sets of the challenge.

### Conclusion 
- Proposed a multimodal hateful memes detection framework that ranked 4th in Phase 2 of the 2020 Hateful Memes Challenge launched by Facebook
- Proposed solution and other state-of-the-art architectures such as Oscar there is a lot of room for improvement in terms of their ability to perform “true” multimodal reasoning.
### Future work
- the observations while building this model can further inform future research in the field
- Recent developments in the field, such as ERNIE-ViL, a multimodal model that incorporates structured knowledge from scene graphs in its pretraining tasks, is another interesting avenue for future work.



## Paper-5 :Classification of Multimodal Hate Speech -- The Winning Solution of Hateful Memes Challenge: Xiayu Zhong
### Problem statement
To create an algorithm that identifies multimodal hate speech in internet meme
### Methodology / Solution / Architecture
- Proposed a classification algorithm that combined the multimodal with rules.
#####  1. Exploration and Rules Extraction
#####  2. Pretrained Model Selection
#####  3. Model Enhancement
#####  4. Semi-supervised Learning
#####  5. Adjustment Based on Rule 2
#####  6. Exploration and Rules Extraction
####   7. Models Stacking
Extracted classification rules from training set, and these rules could be used to generate pseudo-label or adjust classification
probability. Using rules above, part of samples in test set can almost be determined, expending these samples to training
set can greatly improve the metrics of model. adjusted the predictions of each model with rules, then stack models to generate final prediction
### Metrics
Accuracy and AUROC
### Experiment
VisualBERT,  VisualBERT COCO, ViLBERT, ViLBERT CC, MMBT-Region, UNITER and  Masked Region Modeling(MRM)
### Code repository / supplemental material
- https://arxiv.org/abs/2012.01002
- 
### Result
| Pretrained model              | AUROC    |
|-------------------------------|:-------|
|visual_bert.pretrained.cc.full| 0.7260|
|visual_bert.pretrained.cc.small_fifty_pc| 0.7396|
|visual_bert.pretrained.coco.full| 0.7355|

      Scores of top 3 pretrained model

| Pretrained model              | AUROC    |
|-------------------------------|:-------|
|visual_bert.pretrained.cc.full+MRM |0.7400|
|visual_bert.pretrained.coco.full+MRM |0.7376|
|visual_bert.finetuned.hateful_memes.direct+MRM |0.7386|

       Scores of top 3 models with MRM

The combination of rules extracted from data set with multimodal framework, which improved both the accuracy and the AUROC more than 13% which leades to accuracy and AUROC of 86.8% and 0.923 respectively.

### Conclusion
- Implemented MRM to VisualBert to enhance its effectiveness in Hateful Memes, and applied several common technologies such as K-fold, model stacking, semi-supervised learning, significantly improved the AUROC and accuracy of classification
- The features of the dataset are too conspicuous, this makes it possible for me to extract rules from data, but these rules may not be so practical in real world scenarios
### Future work
- To focus on improving  the multimodal framework
