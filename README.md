# -Calculator
Build a Simple Calculator with Python &amp; Tkinter | Step-by-Step Tutorial
 Define button press function
def press(key):
    expression.set(expression.get() + str(key))

# Define clear function
def clear():
    expression.set("")

# Define calculate function
def calculate():
    try:
        result = str(eval(expression.get()))
        expression.set(result)
    except Exception:
        expression.set("Error")

# Create main window
root = Tk()
root.title("SYNTEMY CALCULATOR")  # Title of the calculator
root.geometry("300x400")

# Set pink background
root.configure(background="pink")

# Variable to store the input expression
expression = StringVar()

# Entry widget for displaying input and results
entry_box = Entry(root, textvariable=expression, font=("Arial", 20), bd=10, insertwidth=2, bg="white", fg="black", justify='right')
entry_box.grid(row=0, column=0, columnspan=4, ipadx=8, ipady=8, pady=10)

# Button labels and layout
buttons = [
    ('7', 1, 0), ('8', 1, 1), ('9', 1, 2), ('/', 1, 3),
    ('4', 2, 0), ('5', 2, 1), ('6', 2, 2), ('*', 2, 3),
    ('1', 3, 0), ('2', 3, 1), ('3', 3, 2), ('-', 3, 3),
    ('0', 4, 0), ('.', 4, 1), ('+', 4, 2), ('=', 4, 3),
]

# Create buttons
for (text, row, col) in buttons:
    if text == "=":
        Button(root, text=text, command=calculate, bg="pink", fg="black", font=("Arial", 14)).grid(row=row, column=col, sticky="nsew", padx=5, pady=5)
    else:
        Button(root, text=text, command=lambda t=text: press(t), bg="pink", fg="black", font=("Arial", 14)).grid(row=row, column=col, sticky="nsew", padx=5, pady=5)

# Clear button
Button(root, text="C", command=clear, bg="pink", fg="black", font=("Arial", 14)).grid(row=5, column=0, columnspan=4, sticky="nsew", padx=5, pady=5)

# Adjust row/column weights for responsiveness
for i in range(5):
    root.grid_rowconfigure(i, weight=1)
for i in range(4):
    root.grid_columnconfigure(i, weight=1)

# Run the application
root.mainloop()

