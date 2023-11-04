import tkinter as tk
root=tk.Tk()
def button_click():
    label.config(text="Button Clicked")

button=tk.Button(root, text="Click Me",command=button_click)
root.geometry("800x500")
label=tk.Label(root,text="")
button.pack()
label.pack()
root.mainloop()


    
