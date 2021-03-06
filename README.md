# Optic-Disk-Cup-Segmentation and Glaucoma Screening

## Introduction

This repository contains the implementation of convolutional neural network for optic disk and cup segmentation and glaucoma screening from given fundus images

<hr>

# Segmentation Network

## Preprocesing

Images were cropped to nearest square size and re-sized to a dimension of (512, 512). The different lighting conditions and intensity variations among images across various databases were circumvented by perform-ing normalization of the histogram using Contrast Limited Adaptive HistogramEqualization (CLAHE). 2 different images were generated by varying parameters such as clip value & window level while performing CLAHE. Along with CLAHE, spatial co-ordinates information were also provided to thenetwork. This additional information aided in learning relative features (i.e. disklocation with respect to fovea)

<hr>

## Network Architecture

57 layered deep network was used for segmentation of optic disk and cup. Network architecture is illustrated in figure below...
![pipeline](./images/segnet.png)

<hr>

## Results

### Model predictions

Mask generation used for reducing false positives predicted by network...
![postprocessing](./images/maskgen.png)


![prediction](./images/Selection_007.png)
Image on left shows raw data and image on left shows model predictions...

<hr>

# Classification Network

## Preprocessing

The pixel level segmentation of the optic disk and
optic cup was utilized to generate images of dimension (550, 550) centered around the optic disk. 6 different images were generated by varying parameters such as clip  value  &  window  level  while  performing  CLAHE. 

## Network Architecture

A  DenseNet201 &  ResNet18 pre-trained  on natural images forms the ensemble. The hindmost layer in the network i.e. the classification layer was modified to have 2 neurons. An additional convolutional layer was appended before both the pre-trained models  to  convert  out  21  channel  input  to  3  channels.  To  make  the  network images accept inputs of variable dimension, the global average pooling layer was substituted with an adaptive average pooling layer.

## Results

The proposed classification network achieved a sensitivity of 0.75 at a specificity of 0.85 and 0.856 area under the ROC curve.

## How to use?

~~~~

git clone https://github.com/koriavinash1/Optic-Disk-Cup-Segmentation.git
cd Optic-Disk-Cup-Segmentation
pip install -r requirements.txt

~~~~

<hr>

## Folder structure

> ./src consists all source codes

> > ./src/segmentation code for all segmentation work

> > ./src/classification code for glaucoma screening

> > Tune parameters and run Main.py for executing task

<hr>

## Publication
Our paper is available on arXiv(https://arxiv.org/pdf/1809.05216.pdf)

Please cite with the following Bibtex code:
~~~
@article{agrawal2018enhanced,
  title={Enhanced Optic Disk and Cup Segmentation with Glaucoma Screening from Fundus Images using Position encoded CNNs},
  author={Agrawal, Vismay and Kori, Avinash and Alex, Varghese and Krishnamurthi, Ganapathy},
  journal={arXiv preprint arXiv:1809.05216},
  year={2018}
}
~~~

If any comments or issues, pull requests/issues are Welcomed....

Thankyou


### Contact 

* Avinash Kori (avinashgkori@smail.iitm.ac.in)
* Vismay Agrawal (vismay.iitm@gmail.com)


