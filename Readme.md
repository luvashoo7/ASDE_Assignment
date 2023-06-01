#Task 1

SELECT d.NAME AS DEPT_NAME, AVG(s.AMT) AS AVG_MONTHLY_SALARY_USD
FROM Salaries s
JOIN Employees e ON e.id = s.EMP_ID
JOIN Departments d ON d.ID = e.DEPT_ID
GROUP BY d.NAME -- Group the results by department name
ORDER BY AVG(s.AMT) DESC -- Sort the average salary in descending order
LIMIT 3; -- Limit the output to the top 3 departments with the highest average salary

-----------------------------------------------------------------------------------------------------------

#Task 2

import pandas as p
employee = p.read_csv("C:\Users\ashis\Downloads\ASDE_Assignment\ASDE Assignment - Employees.csv")
salary = p.read_csv("C:\Users\ashis\Downloads\ASDE_Assignment\ASDE Assignment - Salaries.csv")
department = p.read_csv("C:\Users\ashis\Downloads\ASDE_Assignment\ASDE Assignment - Departments.csv")
df = p.merge(department,employee, left_on='ID',right_on='DEPT_ID')
data = p.merge(df,salary,left_on="ID_y",right_on='EMP_ID')
output = data.groupby(['NAME_x'])['AMT'].mean()
output.sort_values(ascending=False).head(3)

-----------------------------------------------------------------------------------------------------------

#Task 3 

def compute(n):
    if n < 10:
        out = n ** 2
    elif n < 20:
        out = 1
        for i in range(1, n-9):
            out *= i
    else:
        lim = n - 19
        out = lim * lim
        out = out - lim
        out = out / 2
    print(out)
    
    n = int(input("Enter an integer: "))
compute(n)

