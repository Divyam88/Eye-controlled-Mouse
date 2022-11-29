# Eye-controlled-Mouse
As the name suggests, this project builds a mouse that can be controlled by human eye. It uses libraries like OpenCV, mediapipe, and pyautogui which enables user to nagivate the cursor through eyeball movement of the right eye and click by blinking the left eye. 

# Algorithm Identification:

Step 1: Import all the necessary files.
Step 2: An object cam is initialized to c2.videocapture(0)
Step 3: A variable facemesh is created to estimate face landmarks and then initialise screen_x and screen_y to pyautogui.size().
Step 4: Within an infinite loop, read() reads the frame of the video. The frames are then flipped.
Step 5: cvtColor() is used to change the color of the frame from bgr to rgb and processed using process().
Step 6: landmarks_points is initialised to output.multi_face_landmarks.
Step 7: if landmarks_point is not zero, initialize landmark to landmark_points[0].landmark.
       Step 7.1: Within a for loop, x and y are initialised to int(landmark.x * frame_w) and  int(landmark.y * frame_h) and passed into a function                          cv2.circle(frame,(x,y), 3, (0, 255, 0)) which draw a circle on the image.
       Step 7.2: If the id ==1, initialize screen_x and screen_y to (screen_w / frame_w * x) and(screen_h / frame_h * y) respectively and pass them to                      pyautogui.moveto() which moves the cursor.
Step 8: A list initialised that contain landmarks[145] and landmarks[159] which are the coordinates of the left eye.
Step 9: Again a for loop is ran, x and y are intialized to int(landmark.x * frame_w) and  int(landmark.y * frame_h) and pass it as an argument in cv2.circle(frame,(x,y), 3, (0, 255, 255)).
Step 10: if (left[0].y - left[1].y < 0.004), pyautogui.click() and pyautogui.sleep(0) is called.
Step  11: cv2.imshow(‘Eye Controlled mouse’, frame) is called which display the image captured by the camera and cv2.waitKey(1)is also called to allow user to display a window for a given milliseconds.

