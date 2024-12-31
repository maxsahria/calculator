import tkinter as tk

# Function to update the expression in the entry widget
def press(key):
    entry_text.set(entry_text.get() + str(key))

# Function to evaluate the expression
def evaluate():
    try:
        result = eval(entry_text.get())
        entry_text.set(result)
    except Exception as e:
        entry_text.set("Error")

# Function to clear the entry widget
def clear():
    entry_text.set("")

# Create the main window
root = tk.Tk()
root.title("Simple Calculator")

# Variable to store the expression entered by the user
entry_text = tk.StringVar()

# Create an entry widget where the expression is displayed
entry = tk.Entry(root, textvariable=entry_text, font=("Arial", 20), bd=10, relief="solid", justify="right")
entry.grid(row=0, column=0, columnspan=4)

# Create buttons for digits and operations
buttons = [
    ('7', 1, 0), ('8', 1, 1), ('9', 1, 2), ('/', 1, 3),
    ('4', 2, 0), ('5', 2, 1), ('6', 2, 2), ('*', 2, 3),
    ('1', 3, 0), ('2', 3, 1), ('3', 3, 2), ('-', 3, 3),
    ('0', 4, 0), ('C', 4, 1), ('=', 4, 2), ('+', 4, 3)
]

# Create and place the buttons on the window
for (text, row, col) in buttons:
    if text == "=":
        button = tk.Button(root, text=text, font=("Arial", 20), width=5, height=2, command=evaluate)
    elif text == "C":
        button = tk.Button(root, text=text, font=("Arial", 20), width=5, height=2, command=clear)
    else:
        button = tk.Button(root, text=text, font=("Arial", 20), width=5, height=2, command=lambda t=text: press(t))
    button.grid(row=row, column=col, padx=5, pady=5)

# Start the Tkinter event loop
root.mainloop()

