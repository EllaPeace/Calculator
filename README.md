# Calculator
A simple python code for a calculator
import tkinter as tk

def on_click(event):
    button_text = event.widget["text"]

    if button_text == "=":
        try:
            result = str(eval(entry.get()))
            entry.delete(0, tk.END)
            entry.insert(tk.END, result)
        except Exception:
            entry.delete(0, tk.END)
            entry.insert(tk.END, "Error")
    elif button_text == "C":
        entry.delete(0, tk.END)
    else:
        entry.insert(tk.END, button_text)

root = tk.Tk()
root.title("Calculator")
root.geometry("300x400")
root.resizable(False, False)

entry = tk.Entry(root, font=("Arial", 20), borderwidth=5, relief=tk.RIDGE, justify="right")
entry.pack(fill=tk.BOTH, ipadx=8, ipady=15, padx=10, pady=10)

button_texts = [
    ["7", "8", "9", "/"],
    ["4", "5", "6", "*"],
    ["1", "2", "3", "-"],
    ["0", ".", "C", "+"],
    ["="]
]

for row_values in button_texts:
    row = tk.Frame(root)
    row.pack(expand=True, fill="both")
    for text in row_values:
        btn = tk.Button(row, text=text, font=("Arial", 18), relief=tk.RAISED, border=1)
        btn.pack(side="left", expand=True, fill="both", padx=2, pady=2)
        btn.bind("<Button-1>", on_click)

root.mainloop()
