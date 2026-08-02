# Ex.No: 02 LINEAR AND POLYNOMIAL TREND ESTIMATION
Date: 25-07-2026
Tool: Google Colab
Dataset: BMW
### AIM:
To Implement Linear and Polynomial Trend Estiamtion Using Python.

### ALGORITHM:
Import necessary libraries (NumPy, Matplotlib)

Load the dataset

Calculate the linear trend values using least square method

Calculate the polynomial trend values using least square method

End the program
### PROGRAM:
A - LINEAR TREND ESTIMATION
```
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt

# Load dataset
data = pd.read_csv("/content/BMW sales data (2010-2024).csv")

# Calculate average price for each year
trend = data.groupby("year")["price"].mean().reset_index()

# Independent and dependent variables
X = trend["year"]
Y = trend["price"]

# Linear regression (degree = 1)
coeff = np.polyfit(X, Y, 1)
linear = np.poly1d(coeff)

# Predicted values
trend["Linear Trend"] = linear(X)

# Equation
print("Linear Trend Equation:")
print(f"y = {coeff[0]:.2f}x + {coeff[1]:.2f}")

# Plot
plt.figure(figsize=(10,6))
plt.plot(X, Y, 'o-', label="Actual Average Price")
plt.plot(X, trend["Linear Trend"], 'r--', linewidth=2, label="Linear Trend")

plt.title("Linear Trend Estimation")
plt.xlabel("Year")
plt.ylabel("Average Price")
plt.legend()
plt.grid(True)

plt.show()
```

B- POLYNOMIAL TREND ESTIMATION
```
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt

# Load dataset
data = pd.read_csv("/content/BMW sales data (2010-2024).csv")

# Calculate average price for each year
trend = data.groupby("year")["price"].mean().reset_index()

# Independent and dependent variables
X = trend["year"]
Y = trend["price"]

# Polynomial regression (degree = 2)
coeff = np.polyfit(X, Y, 2)
poly = np.poly1d(coeff)

# Predicted values
trend["Polynomial Trend"] = poly(X)

# Equation
print("Polynomial Trend Equation:")
print(f"y = {coeff[0]:.6f}x² + {coeff[1]:.2f}x + {coeff[2]:.2f}")

# Plot
plt.figure(figsize=(10,6))
plt.plot(X, Y, 'o-', label="Actual Average Price")
plt.plot(X, trend["Polynomial Trend"], 'g-', linewidth=2,
         label="Polynomial Trend")

plt.title("Polynomial Trend Estimation")
plt.xlabel("Year")
plt.ylabel("Average Price")
plt.legend()
plt.grid(True)

plt.show()
```

### OUTPUT

<img width="1203" height="643" alt="image" src="https://github.com/user-attachments/assets/1c599dea-c486-453b-9f3c-d1dab01a2596" />

<img width="1187" height="600" alt="image" src="https://github.com/user-attachments/assets/d5ff1b1a-c64c-4136-8777-c8084b711fef" />



### RESULT:
Thus the python program for linear and Polynomial Trend Estimation has been executed successfully.
