************************************************
Polypixel
************************************************

Polyp:
======
The code in xxx is used to cross-validate the performance of the different models on the provided development set, containing 1000 polyp images and masks. The results from our experiments are available in `Neptune.ai <https://app.neptune.ai/o/SSCP/org/HyperKvasir/experiments?split=tbl&dash=charts&viewId=462168ad-5b4d-45d8-b5db-014a90a675e4>`_

In code yyy we train the final model based on the best model from cross-validation on the development set (ranked based on Dice score). The final model is then applied on the test set and the masks are saved in the same resolution as the original image.

Instrument:
===========
The code in xxx is used to cross-validate the performance of the different models on the provided development set, containing 590 endoscopic tool images and masks. The results from our experiments are available in `Neptune.ai <https://app.neptune.ai/o/SSCP/org/HyperKvasir/experiments?split=tbl&dash=charts&viewId=462168ad-5b4d-45d8-b5db-014a90a675e4>`_

In code yyy we train the final model based on the best model from cross-validation on the development set (ranked based on Dice score). The final model is then applied on the test set and the masks are saved in the same resolution as the original image.

Counting polyps in masks:
^^^^^^^^^^^^^^^^^^^^^^^^^
In addition to the segmentation model we have also developed an algorithm which detects the borders and counts the segmented polyps or instruments in the dataset. We belive this feature has clinical relevance, because the clinician now may only use time on interpreting the images with detected polyps and not the images without polyps. On the other hand this should be used with caution because undetected polyps will not be counted and thus not be reviewed by the clinician. Figure 1 show an 

.. image:: https://github.com/ylefen/medai2021-polypixel/blob/main/img/polyp_count.png
**Figure 1:** Counting number of polyps in the segmented image

