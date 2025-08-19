![image alt](https://github.com/mdsaquibzaidi/Tkinter-Calculator/blob/f09ed7fd52eac2e0a18bae85439718634828513a/Screenshot%202025-08-19%20204822.png)
from tkinter import *

def click(event):
    text = event.widget.cget("text")
    if text == "=":
        try:
            value = eval(screen_var.get())
            screen_var.set(value)
        except Exception:
            screen_var.set("Error")
    elif text == "C":
        screen_var.set("")
    else:
        screen_var.set(screen_var.get() + text)

# Main window
root = Tk()
root.geometry("400x600")
root.title("Calculator by Zaidi")

# Entry widget
screen_var = StringVar()
screen_var.set("")
screen = Entry(root, textvar=screen_var, font="lucida 30 bold", bd=8, relief=SUNKEN, justify=RIGHT)
screen.pack(fill=X, ipadx=8, pady=10, padx=10)

# Button layout
buttons = [
    ["C", "%", "/", "*"],
    ["7", "8", "9", "-"],
    ["4", "5", "6", "+"],
    ["1", "2", "3", "="],
    ["00", "0", ".", ""]
]

for row in buttons:
    f = Frame(root, bg="black")
    for text in row:
        if text != "":
            button = Button(f, text=text, padx=20, pady=20, font="lucida 20 bold")
            button.bind("<Button-1>", click)
            button.pack(side=LEFT, padx=8, pady=8)
    f.pack()

root.mainloop()
