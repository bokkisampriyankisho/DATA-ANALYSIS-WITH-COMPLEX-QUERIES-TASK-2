# DATA-ANALYSIS-WITH-COMPLEX-QUERIES-TASK-2

QUERIE FOR CREATING EMPLOYEES TABLE:

CREATE TABLE Employees (
    emp_id INT PRIMARY KEY,
    emp_name VARCHAR(50),
    department VARCHAR(50),
    salary DECIMAL(10,2),
    hire_date DATE
);
QUERIE FOR CREATING PROJECTS TABLE
CREATE TABLE Projects (
    project_id INT PRIMARY KEY,
    project_name VARCHAR(100),
    emp_id INT,
    hours_worked INT,
    FOREIGN KEY (emp_id) REFERENCES Employees(emp_id)
);


