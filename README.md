# VMG_FACENET
****BIOFACENET Model implementation in Pytorch****  
The source code of paper: Deep Biophysical Face Image Interpretation  
Paper Source: https://arxiv.org/pdf/1908.10578.pdf  
Code Source in MATLAB: https://github.com/ssma502/BioFaces


The model was trained using Nvidia GPU using the Jupyter notebook. Lower batch size if GPU memory is being limited. Typically, only parameters in cell 3 have to be modified
Libraries used are in cell 2, please download them. For Pytorch I have used this command
"conda install pytorch torchvision torchaudio cudatoolkit=10.2 -c pytorch"


A parent folder/directory to store the models that we train has to be created using the follow steps  
•	Create a directory of your choice - This is your parentpath  
•	Copy the parent directory path to parentpath variable in cell 3   
•	Copy the matFiles folder from the GitHub to inside the parent folder  
•	Copy the modelParameters folder from the GitHub to inside the parent folder   
•	To run prediction using trained model, download this file from google drive https://drive.google.com/drive/folders/1rPLU3Z_r6ZztwBH3eonlFEAV6qiQZd7h?usp=sharing. Place it inside    the modelParameters folder  
•	In cell 3 of the jupyter notebook, Set DatasetAvailable = 0 if you want to download the dataset else set DatasetAvailable = 1 if it has been downloaded to prevent repeated downloads every time the code is being run  

**Training the model**

If you wish to simply test the model , skip running the cell no 28 for training,set ModelAvailable = 0 to train the model from scratch, for every 5 epochs the model parameters will be saved to modelsavepath folder   

**Testing the model**  
Make sure the variable parameterpath has the model file inside modelsavepath folder for testing  
Set ModelAvailable = 1  
Steps:  
   * Run cells 1 to 27

  * 27th cell  
    “makefolder(DatasetAvailable,Modelavailable)
    DownloadData(DatasetAvailable)
    dataset = CelebA(filename)”

  * Skip the 28th  cell  
  * Run 29th cell  
    “trypredict(parameterpath,dataset.images[103:108],dataset.actualmasks[103:108])”  
    
  * To predict use the trypredict function in cell 29, specify the indices in the testing set images and testing masks. ( Input images and masks have 4 dimensions, so if you wish to     use a single image you will have to unsqueeze)
  * Run cells 30 and 31 for edited maps

**Editing the image**  
Setting fmel_change to a value will add to the melanin map   
Setting fblood_change to a value will add to the haemoglobin map  

