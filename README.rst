************************************************
Polypixel
************************************************



Polyp:
======

|PWC_2|

.. |PWC_2| image:: https://img.shields.io/endpoint.svg?url=https://paperswithcode.com/badge/transfer-learning-in-polyp-and-endoscopic/medical-image-segmentation-on-hyper-kvasir
    :target: https://paperswithcode.com/sota/medical-image-segmentation-on-hyper-kvasir?p=transfer-learning-in-polyp-and-endoscopic

The code in `hyperkvasir-polyp-cv.ipynb <https://github.com/ylefen/medai2021-polypixel/blob/main/Polyp%20Segmentation%20Task/hyperkvasir-polyp-cv.ipynb>`_  is used to cross-validate the performance of the different models on the provided development set, containing 1000 polyp images and masks. The results from our experiments are available in `Neptune.ai <https://app.neptune.ai/o/SSCP/org/HyperKvasir/experiments?split=tbl&dash=charts&viewId=462168ad-5b4d-45d8-b5db-014a90a675e4>`_

In the code; `hyperkvasir-polyp-testset-prediction.ipynb <https://github.com/ylefen/medai2021-polypixel/blob/main/Polyp%20Segmentation%20Task/hyperkvasir-polyp-testset-prediction.ipynb>`_ , we train the final model based on the best model from cross-validation on the development set (ranked based on Dice score). The final model is then applied on the test set and the masks are saved in the same resolution as the original image.

Results:
--------
Our model achieves the following performance on :
`Hyper-kvasir <https://datasets.simula.no/hyper-kvasir/>`_
 
 .. table:: Results polyp segmentation
   :widths: auto

   ======  ================================  ========
   Metric  Training set (Cross-validation)   Test set
   ======  ================================  ========
   Dice    :math:`0.874 $\pm$ 0.011`           0.857
   IoU     :math:`0.804 $\pm$ 0.013`           0.800
   ======  ================================  ========


Instrument:
===========

|PWC|

.. |PWC| image:: https://img.shields.io/endpoint.svg?url=https://paperswithcode.com/badge/transfer-learning-in-polyp-and-endoscopic/medical-image-segmentation-on-kvasir
    :target: https://paperswithcode.com/sota/medical-image-segmentation-on-kvasir?p=transfer-learning-in-polyp-and-endoscopic/medical-image-segmentation-on-kvasir


The code in `kvasir-instrument-cv.ipynb <https://github.com/ylefen/medai2021-polypixel/blob/main/Instrument%20Segmentation%20Task/kvasir-instrument-cv.ipynb>`_  is used to cross-validate the performance of the different models on the provided development set, containing 590 endoscopic tool images and masks. The results from our experiments are available in `Neptune.ai <https://app.neptune.ai/o/SSCP/org/HyperKvasir/experiments?split=tbl&dash=charts&viewId=462168ad-5b4d-45d8-b5db-014a90a675e4>`_

In code `kvasir-instrument-testset-prediction.ipynb <https://github.com/ylefen/medai2021-polypixel/blob/main/Instrument%20Segmentation%20Task/kvasir-instrument-testset-prediction.ipynb>`_ we train the final model based on the best model from cross-validation on the development set (ranked based on Dice score). The final model is then applied on the test set and the masks are saved in the same resolution as the original image.

Results:
--------
Our model achieves the following performance on :
`Hyper-kvasir <https://datasets.simula.no/kvasir-instrument/>`_
 
 .. table:: Results instrument segmentation
   :widths: auto

   ======  ================================  ========
   Metric  Training set (Cross-validation)   Test set
   ======  ================================  ========
   Dice    :math:`0.937 \pm 0.015`           0.948
   IoU     :math:`0.893 \pm 0.020`           0.911
   ======  ================================  ========

Pretrained models:
==================
The pretrained segmentation models were downloaded from this scource: `segmentation_models <https://github.com/qubvel/segmentation_models>`_


Counting polyps in masks:
=========================
In addition to the segmentation model we have also developed an algorithm which detects the borders and counts the segmented polyps in the dataset ( `polyp-counter.ipynb <https://github.com/ylefen/medai2021-polypixel/blob/main/Polyp%20Counter/polyp-counter.ipynb>`_ ). We belive this feature has clinical relevance, because the clinician now may only use time on interpreting the images with detected polyps and not the images without polyps. On the other hand this should be used with caution because undetected polyps will not be counted and thus not be reviewed by the clinician. Figure 1 show an example of the counting algorithm where the model has successfully counted 1 and 2 segmented polyps.

.. image:: https://github.com/ylefen/medai2021-polypixel/blob/main/img/1%20and%202%20polyps.png
**Figure 1:** Counting number of polyps in the segmented image

In some cases the predicted masks are fragmented and the counter algorithm may interpret one polyps as two or more like in figure 2.

.. image:: https://github.com/ylefen/medai2021-polypixel/blob/main/img/1%20polyp%20-%20segmented%20as%202.png
**Figure 2:** One polyp, segmented with a small outlier, interpreted as two polyps by the counter algorithm

Kaggle - interactive jupyter notebooks with GPU:
===============================================
The same jupyter notebooks that is avilable here are also available in Kaggle which gives you free GPU wich is necessary to train the models and reproduce the results:

- The `hyperkvasir-polyp-cv.ipynb <https://github.com/ylefen/medai2021-polypixel/blob/main/Polyp%20Segmentation%20Task/hyperkvasir-polyp-cv.ipynb>`_ is available as a Kaggle notebook  `here <https://www.kaggle.com/bjoernjostein/hyperkvasir-starter-code>`_

- The `kvasir-instrument-cv.ipynb <https://github.com/ylefen/medai2021-polypixel/blob/main/Instrument%20Segmentation%20Task/kvasir-instrument-cv.ipynb>`_ is available as a Kaggle notebook `here <https://www.kaggle.com/bjoernjostein/kvasir-instrument-starter-code>`_

- The final training and prediction on the the test set `hyperkvasir-polyp-testset-prediction.ipynb <https://github.com/ylefen/medai2021-polypixel/blob/main/Polyp%20Segmentation%20Task/hyperkvasir-polyp-testset-prediction.ipynb>`_ is available as a Kaggle notebook `here <https://www.kaggle.com/bjoernjostein/hyperkvasir-polyp-testset>`_

- The final training and prediction on the the test set `kvasir-instrument-testset-prediction.ipynb <https://github.com/ylefen/medai2021-polypixel/blob/main/Instrument%20Segmentation%20Task/kvasir-instrument-cv.ipynb>`_ is available as a Kaggle notebook `here <https://www.kaggle.com/bjoernjostein/kvasir-instrument-testset-prediction>`_
