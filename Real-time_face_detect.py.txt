import cv2
model=cv2.CascadeClassifier('haarcascade_frontalface_default.xml')   #download xml file beforehand
cam = cv2.VideoCapture(0) 				#if arg = 0, input takes from webcam, otherwise put video path
while True:
    successful_frame_read, frame = cam.read() 		#consider each frame as a single image
    g_img = cv2.cvtColor(frame, cv2.COLOR_BGR2GRAY)	#convert each frame to bnw
    face_co = model.detectMultiScale(g_img)		#it returns co-ordinates of face
    for(x,y,w,h)in face_co:
        cv2.rectangle(frame,(x,y),(x+w, y+h),(255,0,0),2)	#draws rectangle in each frame
    
    cv2.imshow('face detector',frame)				#shows rectangle marked frame
    key = cv2.waitKey(1)
    if key==81 or key==113:					#stops when q is pressed
        break
    
    
cam.release()  

