# tkinter Tutorial

#### Hello World

We always need to follow two steps no matter how big the application is, there is always two steps. initialize the widget and shove it on the screen that it.

```python
from tkinter import Tk,\
    Label
#initializing tkinter application
root = Tk()
# Creating label widget
myLabel = Label(root, text="Hello World!")
# Shoving it into the screen
myLabel.pack()
#start the application loop
root.mainloop()
```

Output:

![](https://imgur.com/caPeURX.png)



## Grid System

**row**: tells in which row to show

**column**: tells in which column to show

```python
from tkinter import Tk,\
    Label

root = Tk()
# Creating label widget
myLabel1 = Label(root, text="Hello World!")
myLabel2 = Label(root, text="My name is Prince Billy Graham")
# Shoving it into the screen
myLabel1.grid(row=0, column=0) #grid
myLabel2.grid(row=0, column=1) #grid

root.mainloop()
```

**Output:**

![](https://imgur.com/8IBBKV0.png)

## Button

Here "fg" and "bg" supports only hex and  text value. it does not support rgb values.

```python
from tkinter import Tk, \
    Button,\
    Label

root = Tk()
def myClick():
    """Action for clicked button"""
    myLabel = Label(root, text="Look! I clicked a Button!!")
    myLabel.pack()
myButton = Button(root,
                  text="Click me",
                  # state="disabled", #disables button
                  padx=50,  #padding horizontal
                  pady = 20 #padding vertical
                  command=myClick, #onclick event 
                  fg="#fff",  #foreground color 
                  bg="#000"	  #background color
                  )
                  
myButton.pack()
root.mainloop()
```

![](https://i.ibb.co/kGsf13w/click.gif)

 

## Input fields

```python
from tkinter import Tk, \
    Button, \
    Label, \
    Entry

root = Tk()

e = Entry( #input called as entry
    root,
    width=50,
    bg="blue",
    fg="white"
)
e.pack()
e.insert(0, "Enter your name") # placeholder


def my_click():
    """Action for clicked button"""
    my_label = Label(root, text="Hello, " + e.get()) #get the value in entry
    my_label.pack()


my_button = Button(root,
                   text="Click me",
                   # state="disabled",
                   padx=50,
                   command=my_click,
                   fg="#fff",
                   bg="#000"
                   )

my_button.pack()
root.mainloop()

```

**Output:**

![](https://i.ibb.co/pw3gmmR/entry.gif)



## A simple calculator app

```python
from tkinter import Tk, \
    Button, \
    Entry

#global variables
first_number = 0
is_stack_empty = True
math = 'addition'

root = Tk()
root.title("Simple Calculator")  # set title of core window


e = Entry(
    root,
    borderwidth=5
)

e.grid(
    row=0,
    column=0,
    columnspan=3,
    padx=10,
    pady=10
)

e.insert(0, "0") # set 0 as placeholder from 0 postion of entry


def button_click(n):
    global is_stack_empty
    current = ''
    if is_stack_empty:
        is_stack_empty = False
    else:
        current = e.get()

    e.delete(0, "end")
    print(current)
    e.insert(0, current + str(n))


def clear_screen():
    """clear the screen"""
    e.delete(0, "end") # deletes entry value from 0 to end


def add():
    """saves first number to global variable"""
    global first_number
    global math
    math = "addition"
    first_number = int(e.get()) #gets entry value
    e.delete(0, "end")  # deletes entry value from 0 to end


def divide():
    """saves first number to global variable"""
    global first_number
    global math
    math = "division"
    first_number = int(e.get()) #gets the value of entry
    e.delete(0, "end") # deletes entry value from 0 to end


def multiply():
    """saves first number to global variable"""
    global first_number
    global math
    math = "multiplication"
    first_number = int(e.get())
    e.delete(0, "end") # deletes entry value from 0 to end


def subtract():
    """saves first number to global variable"""
    global first_number
    global math
    math = "subtraction"
    first_number = int(e.get())
    e.delete(0, "end") # deletes entry value from 0 to end


def evaluate():
    """shows the result of calculation"""
    global is_stack_empty
    second_number = int(e.get())
    e.delete(0, "end") # deletes entry value from 0 to end

    if math == "addition":
        result = first_number + second_number
    if math == "subtraction":
        result = first_number - second_number
    if math == "multiplication":
        result = first_number * second_number
    if math == "division":
        result = first_number / second_number

    e.insert(0, str(result))
    is_stack_empty = True


button_1 = Button(root, text='1', padx=40, pady=20, command=lambda: button_click(1))
button_2 = Button(root, text='2', padx=40, pady=20, command=lambda: button_click(2))
button_3 = Button(root, text='3', padx=40, pady=20, command=lambda: button_click(3))
button_4 = Button(root, text='4', padx=40, pady=20, command=lambda: button_click(4))
button_5 = Button(root, text='5', padx=40, pady=20, command=lambda: button_click(5))
button_6 = Button(root, text='6', padx=40, pady=20, command=lambda: button_click(6))
button_7 = Button(root, text='7', padx=40, pady=20, command=lambda: button_click(7))
button_8 = Button(root, text='8', padx=40, pady=20, command=lambda: button_click(8))
button_9 = Button(root, text='9', padx=40, pady=20, command=lambda: button_click(9))
button_0 = Button(root, text='0', padx=40, pady=20, command=lambda: button_click(0))

button_add = Button(root, text='+', padx=39, pady=20,
                    command=add)
button_equal = Button(root, text='=', padx=91, pady=20,
                      command=evaluate)
button_clear = Button(root, text='Clear', padx=79, pady=20,
                      command=clear_screen)

button_minus = Button(root, text='-', padx=42, pady=20,
                      command=subtract)
button_mult = Button(root, text='x', padx=42, pady=20,
                     command=multiply)
button_divide = Button(root, text='/', padx=45, pady=20,
                       command=divide)

button_1.grid(row=3, column=0)
button_2.grid(row=3, column=1)
button_3.grid(row=3, column=2)

button_4.grid(row=2, column=0)
button_5.grid(row=2, column=1)
button_6.grid(row=2, column=2)

button_7.grid(row=1, column=0)
button_8.grid(row=1, column=1)
button_9.grid(row=1, column=2)

button_0.grid(row=4, column=0)
button_clear.grid(row=4, column=1, columnspan=2)

button_add.grid(row=5, column=0)
button_equal.grid(row=5, column=1, columnspan=2)

button_minus.grid(row=6, column=0)
button_mult.grid(row=6, column=1)
button_divide.grid(row=6, column=2)

root.mainloop()

```

output:

![](https://i.ibb.co/Qp5CCRT/calc.gif)



## Show images in tkinter

```shell
pip install Pillow
```

```python
from tkinter import Tk, Label, Button, DISABLED, SUNKEN, E, W

from PIL import ImageTk, Image

root = Tk()
root.title("Simple Image Viewer by princebillygk")

images = [
    ImageTk.PhotoImage(Image.open('assets/img/pic_1.webp')),
    ImageTk.PhotoImage(Image.open('assets/img/pic_2.webp')),
    ImageTk.PhotoImage(Image.open('assets/img/pic_3.webp')),
    ImageTk.PhotoImage(Image.open('assets/img/pic_4.webp'))
]


class ImageViewer:
    """Image gallery widget"""

    def __init__(self, rootWidget):
        # init
        self.root = rootWidget
        self.my_label = Label(image=images[0])
        self.button_back = Button(rootWidget, text="<<", state=DISABLED)
        self.button_exit = Button(rootWidget, text="Exit Program", command=root.quit)
        self.button_forward = Button(rootWidget, text=">>", command=lambda: self.forward(1))
        self.status_bar = Label(rootWidget, text="1 of %d" % len(images), bd=1, relief=SUNKEN, anc=E)
        # render
        self.my_label.grid(row=0, column=0, columnspan=3)
        self.button_back.grid(row=1, column=0)
        self.button_exit.grid(row=1, column=1, pady=10)
        self.button_forward.grid(row=1, column=2)
        self.status_bar.grid(row=2, column=0, columnspan=3, sticky=W + E)

    def forward(self, index):
        """Go to next img"""
        # update
        self.my_label = Label(self.root, image=images[index])
        self.button_back = Button(self.root, text="<<", command=lambda: self.back(index - 1))
        if index >= 3:
            self.button_forward = Button(self.root, text=">>", state=DISABLED)
        else:
            self.button_forward = Button(self.root, text=">>", command=lambda: self.forward(index + 1))
        self.status_bar = Label(self.root, text="%d of %d" % (index + 1, len(images)), bd=1, relief=SUNKEN, anc=E)

        # re-render
        self.my_label.grid(row=0, column=0, columnspan=3)
        self.button_back.grid(row=1, column=0)
        self.button_forward.grid(row=1, column=2)
        self.status_bar.grid(row=2, column=0, columnspan=3, sticky=W + E)

    def back(self, index):
        """Go to previous img"""
        # update
        self.my_label = Label(self.root, image=images[index])
        if index <= 0:
            self.button_back = Button(self.root, text="<<", state="disabled")
        else:
            self.button_back = Button(self.root, text="<<", command=lambda: self.back(index - 1))
        self.button_forward = Button(self.root, text=">>", command=lambda: self.forward(index + 1))
        self.status_bar = Label(self.root, text="%d of %d" % (index + 1, len(images)), bd=1, relief=SUNKEN, anc=E)

        # re-render
        self.my_label.grid(row=0, column=0, columnspan=3)
        self.button_back.grid(row=1, column=0)
        self.button_forward.grid(row=1, column=2)
        self.status_bar.grid(row=2, column=0, columnspan=3, sticky=W + E)


imageViewer = ImageViewer(root)
root.mainloop()

```

![](https://i.ibb.co/pL6XS2D/img.gif)

Loads image

```python
ImageTk.PhotoImage(Image.open('assets/img/pic_1.webp')
```



Loading Status bar

```python
 self.status_bar = Label(self.root, text="%d of %d" % (index + 1, len(images)), bd=1, relief=SUNKEN, anc=E)
 # bd for border
 # relief = SUNKEN sunk the item into the screen
 # anc = E  Algn East
self.status_bar.grid(row=2, column=0, columnspan=3, sticky=W + E) 
 #stick=W + E streach width from West to East
```

## Frame

Frames works as div (html)

we can either pack or grid in frame no matter what organization we have used in the parent widget of frame

```python
from tkinter import Tk,Button, Frame

root = Tk()
root.title("Frame")

frame = Frame(root)
frame.pack(padx=10, pady=10)

button = Button(frame, text="Don't click here")
button.grid(row=0, column=0)
button1 = Button(frame, text="Click here")
button1.grid(row =0, column=1)
button2 = Button(root, text="Outside of frame")
button2.pack()

root.mainloop()
```

![](https://i.ibb.co/Bc8Yk6W/image.png)

#### Using LabelFrame instead of Frame in the above example

```diff
- frame = Frame(root)
+ frame = LabelFrame(root, padx=5, pady=5)
```

![](https://imgur.com/UgeW0px.png)

##### Text above label frame

```diff
- frame = LabelFrame(root, padx=5, pady=5)
+ frame = LabelFrame(root, text="My Text" padx=5, pady=5)
```

![](https://imgur.com/zzfMJGG.png)