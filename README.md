# Student Expense Tracker

## Problem Statement
We aim to address the issue of reckless spending among students. Many students spend their allowances impulsively on non-essential items (such as Labubus) without careful financial planning or budgeting.

## Project Objectives
* **Objective 1:** Analyze and summarize financial data from a chosen JSON dataset.
* **Objective 2:** Help users gain meaningful insights into their spending habits (e.g., averages, trends, and patterns).
* **Objective 3:** Practice JSON data handling and core Python programming concepts.

## Features
* **Feature 1:** Calculate the recommended daily expense limit for the week.
* **Feature 2:** Provide a daily expense recommendation adjusted for a specific savings goal.
* **Feature 3:** Welcoming a returnee user.
* **Feature 4:** Logging a new expense and categorizing it
* **Feature 5:** Summary/Save Calculator

## Planned Inputs and Outputs

### Inputs
* User's name
* Total available cash/allowance
* Current expenses and target savings amount

### Outputs
* Recommended daily spending limit for the week
* Adjusted daily spending limit while saving for a specific item or goal

## Logic Plan


## Pseudocode


```text
Load JSON data (initialize empty structure if file does not exist)

input name
normalized_name = lowercase(name)

if normalized_name exists in JSON data:
  load user profile and past expenses
  print "Welcome back, " + name
else:
  create new profile for name
  print "Welcome, " + name

loop:
  Display Choices
    [1] Calculations for average expense for the whole week
    [2] Calculations for daily recommended expense for saving
    [3] Log a new expense
    [4] View spending summary
    [5] Save and Exit

  input choice

  if choice == 1:
    input cash
    input day
    if day > 0:
      a_e = cash / day
      print a_e
    else:
      print "Days must be greater than 0."

  elif choice == 2:
    input cash
    input day
    if day > 0:
      input save
      if save > cash:
        print "Savings goal cannot be greater than available cash."
      else:
        savecash = (cash - save) / day
        print savecash
    else:
      print "Days must be greater than 0."

  elif choice == 3:
    input amount
    input category
    if amount > 0:
      append (amount, category) to user's past expenses
      print "Expense logged."
    else:
      print "Amount must be greater than 0."

  elif choice == 4:
    if user's past expenses is empty:
      print "No expenses logged yet."
    else:
      total_spent = sum of amount in user's past expenses
      print "Total spent: " + total_spent
      for each expense in user's past expenses:
        print expense.category + ": " + expense.amount

  elif choice == 5:
    save JSON data to file
    print "Goodbye!"
    break

  else:
    print "Invalid choice."
```

## Flowchart (HEADS-UP THIS WILL NOT WORK ON FLOWGORITHIM AS THIS IS MERELY A MEANS TO SHOW THE LOGIC)
flowchart TD

```mermaid
flowchart TD
    Start([Start]) --> LoadJSON[Load JSON data in Python]
    LoadJSON --> InputName[Input name]
    InputName --> CheckReturnee{IsReturnee = true?}
    CheckReturnee -->|Yes| WelcomeBack[Output Welcome Back name]
    CheckReturnee -->|No| WelcomeNew[Output Welcome name]
    WelcomeBack --> LoopCond{condition = T?}
    WelcomeNew --> LoopCond

    LoopCond -->|No| End([End])
    LoopCond -->|Yes| Menu[Display Choices 1 to 5]
    Menu --> InputChoice[Input choice]

    InputChoice --> C1{choice = 1?}
    C1 -->|Yes| In1Cash[Input cash]
    In1Cash --> In1Day[Input day]
    In1Day --> D1{day > 0?}
    D1 -->|Yes| CalcAE[ae = cash / day]
    CalcAE --> OutAE[Output ae]
    OutAE --> LoopCond
    D1 -->|No| ErrD1[Output Days must be greater than 0]
    ErrD1 --> LoopCond

    C1 -->|No| C2{choice = 2?}
    C2 -->|Yes| In2Cash[Input cash]
    In2Cash --> In2Day[Input day]
    In2Day --> D2{day > 0?}
    D2 -->|Yes| In2Save[Input save]
    In2Save --> S2{save > cash?}
    S2 -->|Yes| ErrS2[Output Savings goal exceeds cash]
    ErrS2 --> LoopCond
    S2 -->|No| CalcSave[savecash = cash - save / day]
    CalcSave --> OutSave[Output savecash]
    OutSave --> LoopCond
    D2 -->|No| ErrD2[Output Days must be greater than 0]
    ErrD2 --> LoopCond

    C2 -->|No| C3{choice = 3?}
    C3 -->|Yes| In3Amt[Input amount]
    In3Amt --> In3Cat[Input category]
    In3Cat --> A3{amount > 0?}
    A3 -->|Yes| AppendExp[Append amount and category to history]
    AppendExp --> OutLogged[Output Expense Logged]
    OutLogged --> LoopCond
    A3 -->|No| ErrA3[Output Amount must be greater than 0]
    ErrA3 --> LoopCond

    C3 -->|No| C4{choice = 4?}
    C4 -->|Yes| EmptyCheck{No past expenses?}
    EmptyCheck -->|Yes| OutEmpty[Output No expenses logged yet]
    OutEmpty --> LoopCond
    EmptyCheck -->|No| CalcTotal[totalspent = sum of expenses]
    CalcTotal --> OutTotal[Output totalspent]
    OutTotal --> LoopExp[Output each expense category and amount]
    LoopExp --> LoopCond

    C4 -->|No| C5{choice = 5?}
    C5 -->|Yes| SaveJSON[Save data to JSON file]
    SaveJSON --> OutBye[Output goodbye]
    OutBye --> SetExit[condition = Z]
    SetExit --> LoopCond
    C5 -->|No| OutInv[Output Invalid Choice]
    OutInv --> LoopCond
```
   
## GitHub Repository Link
[Project Repository](https://github.com/ktdiamante2031-tech/Project_Template_ComputerScience2)

