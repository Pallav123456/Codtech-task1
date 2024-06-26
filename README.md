# Codtech-task1
import tkinter as tk

def on_click(event):
    text = event.widget.cget("text")
    if text == "=":
        try:
            result = eval(entry.get())
            entry.delete(0, tk.END)
            entry.insert(tk.END, str(result))
        except Exception as e:
            entry.delete(0, tk.END)
            entry.insert(tk.END, "Error")
    elif text == "C":
        entry.delete(0, tk.END)
    else:
        entry.insert(tk.END, text)

root = tk.Tk()
root.title("Calculator")

entry = tk.Entry(root, width=40, borderwidth=5)
entry.grid(row=0, column=0, columnspan=4)

buttons = [
    '7', '8', '9', '/',
    '4', '5', '6', '*',
    '1', '2', '3', '-',
    '.', '0', '=', '+',
    'C'
]

row_num = 1
col_num = 0

for button in buttons:
    btn = tk.Button(root, text=button, padx=20, pady=10)
    btn.grid(row=row_num, column=col_num)
    
    btn.bind("<Button-1>", on_click)

    col_num += 1
    if col_num > 3:
        col_num = 0
        row_num += 1

root.mainloop()
