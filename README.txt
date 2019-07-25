
In this repository you can find an implementation of a Secret Image Sharing method described in this paper:

https://www.researchgate.net/publication/220716528_A_Reliable_k_n_Image_Secret_Sharing_Scheme

This project was done for the Information Security and Criptography course at ITBA.
            
### How to use

> ./ss [-d|-r] -s <image> -m <image> -k <number> -n <number> -l <directory>

## Descripcion
-d:
    Indicates that an image will be distributed in other images
     
-r:
    Indicates that a secret image will be recovered from other images

-s image:
    "image" corresponds to the filepath of a file with .bmp extension.
     In case that the option -d was selected, this file must exist since it is the image
     that will be hidden. If the option -r was selected, this file will be an output file,
     with the secret image revealed after finishin the execution of the program.
      
-m image:
    "image" corresponds to the filepath of a file with .bmp extension.
    In case that the option -d was selected, this file will act as a watermark to verify all the process.
    If the option -r was selected, this file will contain the transformation of the watermark image, needed
    to verify the integrity of the recovered image.
    
-k number:
    "number" corresponds to the minimum ammount of shadows neccessary to recover the secret wih a (k,n) scheme.

-n number:
    "number" correspond to the total ammount of shadows in which the secret will be distributed with a (k,n) scheme.

-l directory:
    In case the option -d was selected, this is the directory where the carrier images are located, this is, the images in which the encrypted secret will be hidden.
    If the option -r was selected, this is the directory where the images that contains the encrpyted secret are.

### Examples

* Distribute the image “Albert.bmp” with watermark “Paris.bmp” using a (4,8) scheme,
storing the shadows in images located at directory “color280x440”:

> ./ss –d –s /home/User/Desktop/Images/Albert.bmp –m home/User/Desktop/Images/Paris.bmp –k 4 – n 8 –l color280x440/


* Recover the image “secreto.bmp”, with watermark “RW.bmp” using a (4,8) scheme, searching images located at directory color280x440/

> ./ss –r –s /home/User/Desktop/Secrets/secreto.bmp –m /RW/RW.bmp –k 4 –n 8 –l color280x440/
