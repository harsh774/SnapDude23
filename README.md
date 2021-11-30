# SnapDude23
SnapDude23 is an code written in purely Python Language, with this code you can put filter of a boy who has glasses and mustaches on his face, 
This is very interesting code which makes you available one of famous filter of Snapchat on your compiler, This code is built using Open-cv library.

#code starts from here..

from cv2 import cv2
import cvzone
cap = cv2.VideoCapture(0)
cascade = cv2.cascadeClassifier('haarcascade_frontalface_default.xml')
overlay = cv2.imread('pirate.png', cv2.IMREAD_UNCHANGED)
while True:

    try:
        ret, frame = cap.read()
        gray_scale = cv2.cvtColor(frame, cv2.COLOR_BGR2GRAY)
        faces = cascade.detectMultiScale(gray_scale)
        for (x,y,w,h) in faces:
            #cv2.rectangle(frame,(x,y), (x+w, y+h), (0, 255, 0), 2)
            overlay_resize = cv2.resize(overlay, (int(w*1.5), int(h*1.5)))
            frame = cvzone.overlayPNG(frame, overlay_resize, [x-45, y-75])
        cv2.imshow('Snappy Boy', frame)
        if cv2.waitKey(10) == ord('q'):
            break
    except Exception as e:
        print("Please put you face properly in camera's centre")


