# OPTIMIZATION-MODEL-from pulp import LpMaximize, LpProblem, LpVariable, value

# Create the LP model
model = LpProblem(name="product-mix", sense=LpMaximize)

# Define decision variables
x = LpVariable(name="Product_A", lowBound=0)
y = LpVariable(name="Product_B", lowBound=0)

# Objective function: Maximize profit
model += 30 * x + 50 * y, "Total Profit"

# Constraints
model += 2 * x + 1 * y <= 100, "Machine_1_Time"
model += 1 * x + 2 * y <= 80, "Machine_2_Time"

# Solve the model
model.solve()

# Results
print(f"Optimal units of Product A: {x.value()}")
print(f"Optimal units of Product B: {y.value()}")
print(f"Maximum Profit: ₹{value(model.objective)}")
Optimal units of Product A: 20.0
Optimal units of Product B: 30.0
Maximum Profit: ₹2100.0
