# DATA-ANALYSIS-WITH-COMPLEX-QUERIES-TASK-2

1️⃣TABLE-1 : EMPLOYEES TABLE

QUERIE FOR CREATING AND INSERTING VALUES EMPLOYEES TABLE 1:

CREATE TABLE Employees (
    Emp id INT PRIMARY KEY,
    Emp name VARCHAR(50),
    Dept VARCHAR(50),
    Salary DECIMAL(10,2),
    Hire date DATE
);

INSERT INTO Employees (Emp id, Emp name, Dept, Salary, Hire date) VALUES
(1, 'Janu', 'IT', 70000, '2023-01-15'),
(2, 'Hema', 'HR', 50000, '2022-03-20'),
(3, 'Harshini', 'IT', 60000, '2024-07-10'),
(4, 'Charmi', 'Finance', 80000, '2021-11-01'),
(5, 'Siri', 'IT', 75000, '2019-05-22'),
(6, 'Trisha', 'HR', 55000, '2023-09-05'),
(7, 'Pallavi', 'Finance', 90000, '2018-04-17'),
(8, 'Sindhu', 'IT', 65000, '2020-06-12');


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


2️⃣TABLE-2 : PROJECTS TABLE

QUERIE FOR CREATING AND INSERTING VALUES PROJECTS TABLE 2:

CREATE TABLE Projects (
    Project id INT PRIMARY KEY,
    Project name VARCHAR(100),
    Emp id INT,
    Hours worked INT,
    FOREIGN KEY (Emp id) REFERENCES Employees(Emp id)
);

INSERT INTO Projects (Project id, Project name, Emp id, Hours worked) VALUES
(101, 'Website Dev', 1, 120),
(102, 'Recruitment', 2, 80),
(103, 'Cloud Setup', 3, 150),
(104, 'Budgeting', 4, 100),
(105, 'AI Research', 5, 200),
(106, 'Training', 6, 90),
(107, 'Audit', 7, 160),
(108, 'Cyber Sec', 8, 130);

|Project id | Project name  | Emp id  | Hours worked|
|-----------|---------------|---------|-------------|
| 101       | Website Dev   | 1       | 120         |
| 102       | Recruitment   | 2       | 80          |
| 103       | Cloud Setup   | 3       | 150         |
| 104       | Budgeting     | 4       | 100         |
| 105       | AI Research   | 5       | 200         |
| 106       | Training      | 6       | 90          |
| 107       | Audit         | 7       | 160         |
| 108       | Cyber Sec     | 8       | 130         |

COMPLEX QUERIES & OUTPUTS :

🟧1.WINDOW FUNCTION-SALARY RANK WITHIN DEPARTMENT:

QUERY :

SELECT 
    Emp_name,
    Dept,
    Salary,
    RANK() OVER (PARTITION BY Dept ORDER BY Salary DESC) AS Dept_rank
FROM Employees;  

🟢OUTPUT:

|Emp name   | Dept   | Salary  | Dept_rank |
|-----------|--------|---------|-----------|
| Siri      | IT     | 75000   | 1         |
| Janu      | IT     | 70000   | 2         |
| Sindhu    | IT     | 65000   | 3         |
| Harshini  | IT     | 60000   | 4         |
| Trisha    | HR     | 55000   | 1         |
| Hema      | HR     | 50000   | 2         |
| Pallavi   | Finance| 90000   | 1         |
| Charmi    | Finance| 80000   | 2         |

🟦2.CTE(COMMON TABLE EXPRESSIONS)-AVERAGE SALARY PER DEPARTMENT

QUERY :

WITH DeptAvg AS (
    SELECT Dept, AVG(Salary) AS Avg salary
    FROM Employees
    GROUP BY Dept
)
SELECT e.Emp_name, e.Dept, e.Salary, d.Avg salary
FROM Employees e
JOIN DeptAvg d ON e.Dept = d.Dept
WHERE e.Salary > d.Avg salary;

🟢OUTPUT :

|Emp name  |Dept    |Salary   |Avg salary |
|----------|--------|---------|-----------|
| Siri     | IT     | 75000   | 67500     |
| Trisha   | HR     | 55000   | 52500     |
| Pallavi  | Finance| 90000   | 85000     |

🟪3.SUBQUERY-EMPLOYEE WHO WORKED MORE THAN AVG HOURS

QUERY :

SELECT Emp name, Hours worked
FROM Projects p
JOIN Employees e ON p.Emp id = e.Emp id
WHERE Hours worked > (
    SELECT AVG(hours worked) FROM Projects
);

🟢OUTPUT :

|Emp name  | Hours worked |
|----------|--------------|
| Harshini | 150          |
| Siri     | 200          | 
| Pallavi  | 160          |
| Sindhu   | 130          |















