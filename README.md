# SenseStudy Block Creation

This documentation showcases the main steps of how to create blocks for the SenseStudy platform with Javascript.

## Step 1 - Writing Down the Source Code in Python

Write down the Python source code of the experiment. Then, test it out first on SenseStudy to make sure that there are no apparent errors made.

For example, for the "AI Smart Fan" experiment, the following source code has been written prior to the blocks being developed.

```python
frame = None
target_x = None
videostream = cv2.VideoCapture(0)
def read_frame():
    global frame
    global videostream
    while True:
        ret,frame = videostream.read()
        #show_image(frame)

def face_parameter():
    global frame
    location = detect_face(frame)
    if location is not None:
        print(location)
        left,top,right,bottom = location[0:4]
        target_x=(left+right)/2
        width = right - left
        return target_x,width
    else:
        return None,None
        
read_frame_thread = Thread(target=read_frame, args=(), daemon=True)
read_frame_thread.start()

target_x,width = face_parameter()
print("target_x and width is: ",target_x,width)

motor_c = Motor("C")
motor_c.run_time(-35,0.01)
```

## Step 2 - Download the Templates for Block Creation
After testing and making sure that the source code works, you can now get started on creating blocks! Download the "DynamicBlock" folder, and you will see that there are generally two ways to prepare the blocks: Automatically (via Markdown) and Manually. 

For the blocks that cannot be generated automatically, please refer to the block code template in “Blocks_need_manul.js” and “Blocks_need_manul.xml”.  


## Case 1: Renaming an existing block in the template
```Pull requests are welcome. For major changes, please open an issue first to discuss what you would like to change.

Please make sure to update tests as appropriate.

## License
[MIT](https://choosealicense.com/licenses/mit/)
