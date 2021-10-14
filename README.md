# FaceQgen
FaceQgen: Quality Assessment for Face Recognition Based on GANs

This repository is based on the paper:  <a href="https://arxiv.org/abs/1904.01740" rel="nofollow">"Quality Assessment for Face Recognition Based on GANs: FaceQgen"</a>.


FaceQgen is a a face quality assessment method based on GANs capable of inferring quality directly from face images. 
It avoids using any type of numerical labelling of the training images thanks to following a semi-supervised learning approach without the need of a specific measurement of quality for its groundtruth apart from selecting a single high quality image per subject.

FaceQgen performs face image restoration, returning a high quality image (frontal pose, homogeneous background, etc.) when receiving a face image of unknown quality. We use three different similarity measures between the original and the restored images as quality measures: SSIM,MSE, and the output of the Discriminator of
FaceQgen. Faces of high quality will experience less transformations during restoration, so the similarity values obtained in those cases will be higher than the ones obtained from low quality images.

The training of FaceQgen was done using the SCFace database.

-- Configuring environment in Windows:

1) Installing Conda: https://conda.io/projects/conda/en/latest/user-guide/install/windows.html

  Update Conda in the default environment:

    conda update conda
    conda upgrade --all

  Create a new environment:

    conda create -n [env-name]

  Activate the environment:

    conda activate [env-name]

2) Installing dependencies in your environment:

  Install Tensorflow and all its dependencies: 
    
    pip install tensorflow
    
  Install Keras:
  
    pip install keras
    
  Install OpenCV:

    conda install -c conda-forge opencv
  
 3) If you want to use a CUDA compatible GPU for faster predictions:
  
   You will need CUDA and the Nvidia drivers installed in your computer: https://docs.nvidia.com/deeplearning/sdk/cudnn-install/
  
   Then, install the GPU version of Tensorflow:
    
    pip install tensorflow-gpu
  
-- Using FaceQgen for predicting scores:

  1) Download or clone the repository. 
  2) Due to the size of the video example, please download one of the the FaceQgen pretrained model and place the downloaded .h5 file it in the /src folder:  
  
  - <a href="https://github.com/uam-biometrics/FaceQnet/releases/download/v0/FaceQnet.h5" rel="nofollow">FaceQgen pretrained model</a> 
  
  3) Edit and run the FaceQgen_obtainscores_Keras.py script.
     - You will need to change the folder from which the script will try to charge the face images. It is src/Samples_cropped by default. 
     - The best results will be obtained when the input images have been cropped just to the zone of the detected face. In our experiments we have used the MTCNN face detector from <a href="https://kpzhang93.github.io/MTCNN_face_detection_alignment/index.html" rel="nofollow">here</a>, but other detector can be used.
     - FaceQgen will ouput a quality score for each input image. All the scores will are saved in a .txt file into the src folder. This file contain each filename with its associated quality metric.





