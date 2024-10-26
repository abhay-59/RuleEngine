
## Overview

This application is a rule engine that determines user eligibility based on attributes such as age, department, salary, and experience. It uses an Abstract Syntax Tree (AST) to represent and manage conditional rules, allowing for dynamic rule creation, combination, and evaluation.


## Features


- **Overview** Basic structure of the Rule Engine.

  <img width="900" alt="image" src="https://github.com/user-attachments/assets/5b8fb217-21b7-458a-abe1-ae845e63c512">

- **Create Rules:** Define rules using a string format that gets converted into an AST.
  
  <img width="500" alt="image" src="https://github.com/user-attachments/assets/f598686b-6682-45db-aa45-81959318ab80">

- **Evaluate Rules:** Check if the given data meets the criteria defined by the AST.
  
  <img width="500" alt="image" src="https://github.com/user-attachments/assets/6e61e318-c7a6-49ab-8971-38f6e88aeffc">

- **Combine Rules:** Combine multiple rules into a single AST for more complex evaluations.

  <img width="500" alt="image" src="https://github.com/user-attachments/assets/de815f70-ff32-4502-8bee-1b9db920e9c9">


- **Tree Visualization:** Define or Combine Rule would should show Tree Representation.

## Tech Stack

- **Backend:** Node.js, Express.js
- **Database:** MongoDB

## Getting Started

### Prerequisites

- Node.js and npm installed
- MongoDB installed and running

### Installation

1. **Clone the Repository**
   ```bash
   git clone "https://github.com/abhay-59/RuleEngine"
   cd RuleEngine
   ```

2. **Install Backend Dependencies**

   ```bash
   npm install
   ```
   
3. **Start the backend and frontend**

   Ensure that MongoDB is running on online platform:

   ```bash
   npm start
   ```

## API Endpoints

1. **Create a Rule**
   - **Endpoint:** `/api/create_rule`
   - **Method:** POST
   - **Body:**

     ```json
     {
       "ruleString": "((age > 30 AND department = 'Sales') OR (age < 25 AND department = 'Marketing')) AND (salary > 50000 OR experience > 5)",
       "ruleName": "Rule 1"
     }
     ```
use appropriate spaces in Rules for correct results.

Rule should be in follow format:
variable operator value 

   - **Response:**

     ```json
     {
       "_id": "605c72ef1f4e3a001f4d2e9a",
       "rule_name": "Rule1",
       "rule_ast": { ... }
     }
     ```

2. **Combine Rules**
   - **Endpoint:** `/api/rules/combine_rules`
   - **Method:** POST
   - **Body:**

     ```json
     {
       "ruleIds": ["605c72ef1f4e3a001f4d2e9a", "605c730f1f4e3a001f4d2e9b"]
       "operators: op
     }
     ```
   - **Response:**

     ```json
     {
       "type": "operator",
       "value": operator,
       "left": { ... },
       "right": { ... }
     }
     ```

3. **Evaluate a Rule**
   - **Endpoint:** `/api/rules/evaluate_rule`
   - **Method:** POST
   - **Body:**

     ```json
     {
       "rule": { ... },
       "data": {
         "age": 35,
         "department": "Sales",
         "salary": 60000,
         "experience": 3
       }
     }
     ```
   - **Response:**

     ```json
     {
       "result": true
     }
     ```

## Running Tests

You can add and run tests to ensure everything is working correctly. 
```