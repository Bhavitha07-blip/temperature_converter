# temperature_converter
import tkinter as tk
from tkinter import ttk

def convert_temperature():
    try:
        temp = float(entry_temp.get())
        unit = combo_units.get()

        if unit == "Celsius":
            f = (temp * 9/5) + 32
            k = temp + 273.15
            result.set(f"Fahrenheit: {f:.2f} °F\nKelvin: {k:.2f} K")

        elif unit == "Fahrenheit":
            c = (temp - 32) * 5/9
            k = c + 273.15
            result.set(f"Celsius: {c:.2f} °C\nKelvin: {k:.2f} K")

        elif unit == "Kelvin":
            c = temp - 273.15
            f = (c * 9/5) + 32
            result.set(f"Celsius: {c:.2f} °C\nFahrenheit: {f:.2f} °F")

    except ValueError:
        result.set("❌ Please enter a valid number!")


# Main window
root = tk.Tk()
root.title("Temperature Converter")
root.geometry("330x250")
root.config(bg="#f0f0f0")

# Label
tk.Label(root, text="Enter Temperature:", font=("Arial", 12), bg="#f0f0f0").pack(pady=5)

# Input field
entry_temp = tk.Entry(root, font=("Arial", 12))
entry_temp.pack()

# Dropdown
tk.Label(root, text="Select Input Unit:", font=("Arial", 12), bg="#f0f0f0").pack(pady=5)

combo_units = ttk.Combobox(root, values=["Celsius", "Fahrenheit", "Kelvin"], font=("Arial", 12))
combo_units.current(0)
combo_units.pack()

# Convert button
btn = tk.Button(root, text="Convert", font=("Arial", 12), bg="#4CAF50", fg="white", command=convert_temperature)
btn.pack(pady=10)

# Result label
result = tk.StringVar()
tk.Label(root, textvariable=result, font=("Arial", 12), bg="#f0f0f0").pack(pady=10)

# Run
root.mainloop()
