# DualHG

This repository contains the code and datasets about the paper:

## Requirements

python==3.6
pytorch==1.4
transformers==3.0.2

## Training and Testing

First, we need to appoint a backbone model, e.g. UniLM or BERT. Then use the train_test_dual_auto.sh file which provides an end-to-end script to train and evaluate the models. In total we have six steps in a pipieline way, shown as the following figure.
![1](https://user-images.githubusercontent.com/9100500/154612549-f21e3014-5a82-4e76-a4a5-0670290d59a8.png)

Actually, the training of marginkey model (abbr. margin model for key information prediction) and marginsum model (abbr. margin model for summarization generation) can be paralleled to speed up, shown as the following figure.
![2](https://user-images.githubusercontent.com/9100500/154612551-a05f3bd5-7648-4630-b9eb-cdb338664fae.png)

In the step of training dual models (dualkey model and dualsum model), we need to also load the marginkey model and marginsum model to run-timely compute the two marginal losses and infer the marginal summarization for each training batch, which is memory- and time-consuming. To further speed up, we can pre-compute the infered summarization by marginsum model and marginal losses, and store them. Because the margianl models only paly the role of inference when training dual models and would not be updated. The process is like the following figure. Thus, we can save the memory cost from four models to two, as well as the time cost.
![3](https://user-images.githubusercontent.com/9100500/154612554-2c5e56e4-ae9e-4f0a-b9ed-b8f0a1f07a6b.png)


## Acknowledgments


## License


## Contact Information
