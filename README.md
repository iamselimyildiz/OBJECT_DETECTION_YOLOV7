# OBJECT_DETECTION_YOLOV7
Guide to detect objects using google colab+yolov7 


1-Hello friend, firstly open a new google colab project.
![1](https://github.com/iamselimyildiz/OBJECT_DETECTION_YOLOV7/assets/94224409/ed336663-cd77-4904-b401-8fec2591aa40)


2-Connecting our pc to a virtual computer (tesla graphic card).Go to Runtime/Change Runtime Type. Set Hardware accelerator to GPU
![2](https://github.com/iamselimyildiz/OBJECT_DETECTION_YOLOV7/assets/94224409/43d193c1-4466-4a45-a966-3ea6ab9a7220)

3- mount colab to google drive. Type the code and hit ctrl+Enter.

"from google.colab import drive

drive.mount("/content/gdrive")"

![3](https://github.com/iamselimyildiz/OBJECT_DETECTION_YOLOV7/assets/94224409/d82e8864-a6ba-470d-b198-3382a6ba4b3d)

4-Secondly,we'll create directories and clone  yolov7 repository. To reach the repo Please go to 
https://github.com/WongKinYiu/yolov7

and copy the link as shown.(https://github.com/WongKinYiu/yolov7.git)


![4](https://github.com/iamselimyildiz/OBJECT_DETECTION_YOLOV7/assets/94224409/5902cc5c-15d7-43cb-ae94-e5a8ba27ac12)

5-Download the pre-trained model. 
Here, go to the original yolov7 repository and scroll down to copy the link of the desired Yolo version. In this case, I copied the YOLOv7's address link.

![6](https://github.com/iamselimyildiz/OBJECT_DETECTION_YOLOV7/assets/94224409/767c8778-fbaf-4730-b0c2-3857a89c7b2b)

6-Now, we'll make some modifications in the code. Go to google drive/MyDrive/Colab Notebooks\yolov7_uygulaması\yolov7\utils\datasets.py

find "print(f'video {self.count + 1}/{self.nf} ({self.frame}/{self.nframes}) {path}: ', end='')" and comment it out as shown.

![7](https://github.com/iamselimyildiz/OBJECT_DETECTION_YOLOV7/assets/94224409/9dc43e16-c076-44ed-b1c0-c4d14d12c255)

6.1- Then go to google drive/MyDrive/Colab Notebooks\yolov7_uygulaması\yolov7\detect.py

right above def detect method type "random.seed(1)". It stops generating random colours for each run.

![8](https://github.com/iamselimyildiz/OBJECT_DETECTION_YOLOV7/assets/94224409/f174847a-fae7-459f-94a5-edb286675c9a)

6.2- go to line 70 find "t0=time.time()" right below write "startTime=0"


![9](https://github.com/iamselimyildiz/OBJECT_DETECTION_YOLOV7/assets/94224409/600e9985-9f6f-4ff4-94d9-1d542296c866)

6.3- Then go to "#Stream results" in file detect.py Right at the beggining type:

      "if dataset.mode!='image':
              currentTime=time.time()
              
              fps=1/(currentTime-startTime)
              startTime=currentTime
              cv2.putText(im0,'FPS: '+str(int(fps)),(20,70),cv2.FONT_HERSHEY_PLAIN,2,(0,255,0),2)"

              
![10](https://github.com/iamselimyildiz/OBJECT_DETECTION_YOLOV7/assets/94224409/a4f3359c-9457-471b-a15d-a5c50b0ae853)

6.4- find in line 152 "print(f" The image with the result is saved in: {save_path}")" cut it and paste it to line 169 right below the if statement.As shown.

![11](https://github.com/iamselimyildiz/OBJECT_DETECTION_YOLOV7/assets/94224409/faa3cd3c-7329-48ad-be41-af1f1e4a5cca)

6.5- Lastly we'll change the line thickness to 2 .Go to line 131 find this line 

"plot_one_box(xyxy, im0, label=label, color=colors[int(cls)], line_thickness=2)"


![12](https://github.com/iamselimyildiz/OBJECT_DETECTION_YOLOV7/assets/94224409/8f3d92bf-80b0-4dc4-9271-bf7441d09b8a)

7- Well done.. Now please copy and paste the desired photo or video  in google drive/MyDrive/Colab Notebooks\yolov7_uygulaması\yolov7.
And to apply the algorithm type and run. Please notice "cat-dog.jpg" is an example. Go ahead and try your own pic or vid.

"!python detect.py --weights yolov7.pt --conf 0.5 --img-size 640 --source cat-dog.jpg"

![13](https://github.com/iamselimyildiz/OBJECT_DETECTION_YOLOV7/assets/94224409/6cefe305-fdc9-478b-b0ca-77c2d94c66f0)


8-also thanks to TheCodingBug for his contribution. Here you may also check out his Youtube channel.TheCodinBug
https://www.youtube.com/watch?v=_CkXDjmT8dc&t=385s












