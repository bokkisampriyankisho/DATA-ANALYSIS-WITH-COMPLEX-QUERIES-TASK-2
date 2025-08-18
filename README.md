# DATA-ANALYSIS-WITH-COMPLEX-QUERIES-TASK-2

TABLE-1 : EMPLOYEES TABLE

QUERIE FOR CREATING AND INSERTING VALUES EMPLOYEES TABLE 1:

CREATE TABLE Employees (
    emp_id INT PRIMARY KEY,
    emp_name VARCHAR(50),
    department VARCHAR(50),
    salary DECIMAL(10,2),
    hire_date DATE
);

INSERT INTO Employees (emp_id, emp_name, department, salary, hire_date) VALUES
(1, 'Janu', 'IT', 70000, '2020-01-15'),
(2, 'Hema', 'HR', 50000, '2019-03-20'),
(3, 'Harshini', 'IT', 60000, '2021-07-10'),
(4, 'Charmi', 'Finance', 80000, '2018-11-01'),
(5, 'Siri', 'IT', 75000, '2017-05-22'),
(6, 'Trisha', 'HR', 55000, '2020-09-05'),
(7, 'Pallavi', 'Finance', 90000, '2016-04-17'),
(8, 'Sindhu', 'IT', 65000, '2019-06-12');


|Emp id  | Emp name   | Dept    |  Salary   | Hire date   |
|--------|------------|---------|-----------|-------------|
| 1      | Janu       | IT      | 70000     | 2023-01-15  | 
| 2      | Hema       | HR      | 50000     | 2022-03-20  |
| 3      | Harshini   | IT      | 60000     | 2024-07-10  |
| 4      | Charmi     | Finance | 80000     | 2021-11-01  |
| 5      | Siri       | IT      | 75000     | 2019-05-22  |
| 6      | Trisha     | HR      | 55000     | 2023-09-05  |
| 7      | Pallavi    | Finance | 90000     | 2018-04-17  |     
| 8      | Sindhu     | IT      | 65000     | 2020-06-10  |


TABLE-2 : PROJECTS TABLE

QUERIE FOR CREATING AND INSERTING VALUES PROJECTS TABLE 2:

CREATE TABLE Projects (
    project_id INT PRIMARY KEY,
    project_name VARCHAR(100),
    emp_id INT,
    hours_worked INT,
    FOREIGN KEY (emp_id) REFERENCES Employees(emp_id)
);

INSERT INTO Projects (project_id, project_name, emp_id, hours_worked) VALUES
(101, 'Website Dev', 1, 120),
(102, 'Recruitment', 2, 80),
(103, 'Cloud Setup', 3, 150),
(104, 'Budgeting', 4, 100),
(105, 'AI Research', 5, 200),
(106, 'Training', 6, 90),
(107, 'Audit', 7, 160),
(108, 'Cyber Sec', 8, 130);

|Priject id | Project name  | Emp id  | Hours worked|
|-----------|---------------|---------|-------------|
| 101       | Website Dev   | 1       | 120         |
| 102       | Recruitment   | 2       | 80          |
| 103       | Cloud Setup   | 3       | 150         |
| 104       | Budgeting     | 4       | 100         |
| 105       | AI Research   | 5       | 200         |
| 106       | Training      | 6       | 90          |
| 107       | Audit         | 7       | 160         |
| 108       | Cyber Sec     | 8       | 130         |

