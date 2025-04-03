# **Conditionals**

## **7.1. Intro: What We Can Do with Turtles and Conditionals**

### **7.1.1. Learning Goals**

- Understand how conditionals work in programming.
- Explore the use of turtles in Python to illustrate conditional logic.
- Learn to write conditional statements for decision-making in programs.

### **7.1.2. Objectives**

- Implement conditional execution using `if`, `if-else`, and `elif`.
- Utilize Boolean expressions and logical operators.
- Understand the precedence of operators.
- Apply conditionals in problem-solving and simulations.

## **7.2. Boolean Values and Boolean Expressions**

- Boolean values: `True` and `False`.
- Boolean expressions evaluate to `True` or `False`.
- Examples:
  ```python
  x = 10
  print(x > 5)  # True
  print(x == 5)  # False
  ```

## **7.3. Logical Operators**

- `and`, `or`, `not`
- Examples:
  ```python
  x = 5
  print(x > 2 and x < 10)  # True
  print(x > 10 or x == 5)  # True
  print(not(x == 5))  # False
  ```

### **7.3.1. Smart Evaluation**

- Also known as short-circuit evaluation.
- In `and`, if the first condition is `False`, the second condition is not evaluated.
- In `or`, if the first condition is `True`, the second condition is not evaluated.
- Example:

  ```python
  def check():
      print("Function executed")
      return True

  print(False and check())  # Function is not executed
  print(True or check())  # Function is not executed
  ```

## **7.4. The `in` and `not in` Operators**

- Used to check membership in lists, tuples, and strings.
- Example:
  ```python
  fruits = ["apple", "banana", "cherry"]
  print("apple" in fruits)  # True
  print("grape" not in fruits)  # True
  ```

## **7.5. Precedence of Operators**

- `not` > `and` > `or`
- Example:
  ```python
  print(True or False and False)  # True
  print((True or False) and False)  # False
  ```

## **7.6. Conditional Execution: Binary Selection**

- The `if-else` structure allows decision-making.
- Example:
  ```python
  age = 18
  if age >= 18:
      print("You can vote.")
  else:
      print("You cannot vote.")
  ```

## **7.7. Omitting the Else Clause: Unary Selection**

- `if` without `else` executes only when the condition is `True`.
- Example:
  ```python
  x = 10
  if x > 5:
      print("X is greater than 5")
  ```

## **7.8. Nested Conditionals**

- `if` inside another `if`.
- Example:
  ```python
  num = 10
  if num > 0:
      if num % 2 == 0:
          print("Positive even number")
  ```

## **7.9. Chained Conditionals**

- Using `elif` for multiple conditions.
- Example:
  ```python
  score = 85
  if score >= 90:
      print("A grade")
  elif score >= 80:
      print("B grade")
  else:
      print("C grade")
  ```

## **7.10. The Accumulator Pattern with Conditionals**

- Used to accumulate values conditionally.
- Example:
  ```python
  numbers = [1, 5, 3, 8, 2]
  total = 0
  for num in numbers:
      if num % 2 == 0:
          total += num
  print(total)  # 10
  ```

### **7.10.1. Accumulating the Max Value**

- Example:
  ```python
  numbers = [3, 7, 2, 9, 5]
  max_value = numbers[0]
  for num in numbers:
      if num > max_value:
          max_value = num
  print(max_value)  # 9
  ```

## **7.11. 👩💻 Setting Up Conditionals**

### **7.11.1. Choosing Your Type of Conditional**

- Use `if` for a single condition.
- Use `if-else` for two possible outcomes.
- Use `if-elif-else` for multiple conditions.
- Example:
  ```python
  temperature = 30
  if temperature > 35:
      print("It's too hot!")
  elif temperature < 15:
      print("It's too cold!")
  else:
      print("The weather is pleasant.")
  ```

---

## **7.12. Exception Handling with Conditionals**

- Using `try-except` blocks to handle conditional errors.
- Example:
  ```python
  try:
      num = int(input("Enter a number: "))
      if num < 0:
          raise ValueError("Negative numbers not allowed!")
  except ValueError as e:
      print("Error:", e)
  ```

---

### **Problem 6: Bank Loan Eligibility System**

- Create a program to check if a user is eligible for a bank loan based on salary, age, and credit score using nested conditionals.
```python
def check_loan_eligibility(age, salary, credit_score):
    if age >= 21:
        if salary >= 25000:
            if credit_score >= 650:
                return "Congratulations! You are eligible for a loan."
            else:
                return "Sorry, your credit score is too low for loan eligibility."
        else:
            return "Sorry, your salary does not meet the minimum requirement for a loan."
    else:
        return "Sorry, you must be at least 21 years old to apply for a loan."

age = int(input("Enter your age: "))
salary = float(input("Enter your monthly salary: "))
credit_score = int(input("Enter your credit score: "))

result = check_loan_eligibility(age, salary, credit_score)
print(result)
```

### **Problem 7: AI Chatbot with Conditional Responses**

- Design a simple chatbot that responds differently based on user input (e.g., greetings, questions, or farewell messages).
```python
def chatbot_response(user_input):
    user_input = user_input.lower()
    
    if any(word in user_input for word in ["hi", "hello", "hey"]):
        return "Hello! How can I assist you today?"
    elif "how are you" in user_input:
        return "I'm just a bot, but I'm functioning perfectly! How about you?"
    elif any(word in user_input for word in ["bye", "goodbye"]):
        return "Goodbye! Have a great day!"
    elif "your name" in user_input:
        return "I'm a simple chatbot created to assist you!"
    elif "help" in user_input:
        return "Sure! Let me know how I can help you."
    else:
        return "I'm not sure I understand. Could you rephrase that?"

while True:
    user_input = input("You: ")
    if user_input.lower() in ["bye", "goodbye"]:
        print("Chatbot: " + chatbot_response(user_input))
        break
    print("Chatbot: " + chatbot_response(user_input))
```
### **Problem 8: Traffic Light Simulation**

- Simulate a traffic light system using conditionals and loops.
```python
import time

def traffic_light_simulation(cycles=3):
    lights = [("Red", 5), ("Green", 5), ("Yellow", 2)]  
    
    for _ in range(cycles):
        for light, duration in lights:
            print(f"{light} light ON")
            time.sleep(duration)
            print(f"{light} light OFF")
    
    print("Traffic light simulation complete.")

traffic_light_simulation()
```

### **Problem 9: Smart Home Automation**

- Implement a conditional-based smart home system where temperature, humidity, and motion sensors determine actions (e.g., turning lights and fans on/off).
```python
def smart_home_system(temperature, humidity, motion_detected):
    actions = []
    
    if temperature > 25:
        actions.append("Turning ON the fan.")
    else:
        actions.append("Turning OFF the fan.")
    
    if humidity > 70:
        actions.append("Turning ON the dehumidifier.")
    else:
        actions.append("Turning OFF the dehumidifier.")
    
    if motion_detected:
        actions.append("Turning ON the lights.")
    else:
        actions.append("Turning OFF the lights.")
    
    return actions

# Example usage
temp = float(input("Enter the current temperature (°C): "))
humidity = float(input("Enter the current humidity (%): "))
motion = input("Is motion detected? (yes/no): ").strip().lower() == "yes"

results = smart_home_system(temp, humidity, motion)
for action in results:
    print(action)
```

### **Problem 10: Stock Market Trend Analysis**

- Write a program to analyze stock prices and predict buy/sell signals based on historical trends using conditionals.
```python
def analyze_stock_prices(prices):
    signals = []
    
    for i in range(1, len(prices)):
        if prices[i] > prices[i-1]:
            signals.append((i, "BUY"))
        elif prices[i] < prices[i-1]:
            signals.append((i, "SELL"))
        else:
            signals.append((i, "HOLD"))
    
    return signals

stock_prices = [100, 102, 101, 105, 103, 107, 106]
signals = analyze_stock_prices(stock_prices)

for day, signal in signals:
    print(f"Day {day}: {signal}")
```
---

### **1. Employee Attendance Tracker**

- Implement a system that tracks employee attendance.
- Use loops to process multiple employees and conditionals to check attendance.
- Mark employees as "Needs Attention" if absent for more than 3 consecutive days.
```python
def track_attendance(employee_records):
    attendance_status = {}
    
    for employee, attendance in employee_records.items():
        consecutive_absences = 0
        needs_attention = False
        
        for day in attendance:
            if day == "Absent":
                consecutive_absences += 1
            else:
                consecutive_absences = 0
            
            if consecutive_absences > 3:
                needs_attention = True
                break
        
        attendance_status[employee] = "Needs Attention" if needs_attention else "Good Standing"
    
    return attendance_status

employees = {
    "Alice": ["Present", "Absent", "Absent", "Absent", "Absent", "Present"],
    "Bob": ["Present", "Present", "Absent", "Absent", "Present", "Present"],
    "Charlie": ["Absent", "Absent", "Absent", "Absent", "Absent", "Absent"]
}

results = track_attendance(employees)
for emp, status in results.items():
    print(f"{emp}: {status}")
```

### **3. Password Strength Checker**

- Classify passwords as "Weak", "Medium", or "Strong" based on length, numbers, uppercase/lowercase letters, and special characters.
- Loop until a "Strong" password is entered.
```python
import re

def classify_password(password):
    length = len(password) >= 8
    has_digit = bool(re.search(r"\d", password))
    has_upper = bool(re.search(r"[A-Z]", password))
    has_lower = bool(re.search(r"[a-z]", password))
    has_special = bool(re.search(r"[@$!%*?&]", password))
    
    strength = sum([length, has_digit, has_upper, has_lower, has_special])
    
    if strength == 5:
        return "Strong"
    elif strength >= 3:
        return "Medium"
    else:
        return "Weak"
while True:
    user_password = input("Enter a password: ")
    classification = classify_password(user_password)
    print(f"Password strength: {classification}")
    
    if classification == "Strong":
        break
```
### **5. Banking System with ATM Functionality**

- Simulate an ATM system for checking balance, withdrawal, and deposit.
- Use loops for multiple transactions and conditionals to prevent overdraft.
```python
def atm_simulation():
    balance = 1000  
    
    while True:
        print("\nATM Menu:")
        print("1. Check Balance")
        print("2. Deposit")
        print("3. Withdraw")
        print("4. Exit")
        
        choice = input("Choose an option (1-4): ")
        
        if choice == "1":
            print(f"Your current balance is: ${balance:.2f}")
        elif choice == "2":
            amount = float(input("Enter deposit amount: "))
            if amount > 0:
                balance += amount
                print(f"Deposited ${amount:.2f}. New balance: ${balance:.2f}")
            else:
                print("Invalid deposit amount.")
        elif choice == "3":
            amount = float(input("Enter withdrawal amount: "))
            if 0 < amount <= balance:
                balance -= amount
                print(f"Withdrawn ${amount:.2f}. New balance: ${balance:.2f}")
            else:
                print("Insufficient balance or invalid amount.")
        elif choice == "4":
            print("Thank you for using the ATM. Goodbye!")
            break
        else:
            print("Invalid option. Please choose again.")
atm_simulation()
```