# LAB_3-ASSIGNMENT
KISLAYA
E22CSEU0541
class Employee:
    def __init__(self, emp_id, name, age, salary):
        self.emp_id = emp_id
        self.name = name
        self.age = age
        self.salary = salary

class EmployeeDatabase:
    def __init__(self):
        self.employees = []

    def add_employee(self, employee):
        self.employees.append(employee)

    def search_by_age(self, age):
        result = []
        for employee in self.employees:
            if employee.age == age:
                result.append(employee)
        return result

    def search_by_name(self, name):
        result = []
        for employee in self.employees:
            if employee.name.lower() == name.lower():
                result.append(employee)
        return result

    def search_by_salary(self, condition, salary):
        result = []
        for employee in self.employees:
            if condition == '>' and employee.salary > salary:
                result.append(employee)
            elif condition == '<' and employee.salary < salary:
                result.append(employee)
            elif condition == '>=' and employee.salary >= salary:
                result.append(employee)
            elif condition == '<=' and employee.salary <= salary:
                result.append(employee)
        return result

def main():
    emp_db = EmployeeDatabase()

    emp_db.add_employee(Employee("161E90", "Raman", 41, 56000))
    emp_db.add_employee(Employee("161F91", "Himadri", 38, 67500))
    emp_db.add_employee(Employee("161F99", "Jaya", 51, 82100))
    emp_db.add_employee(Employee("171E20", "Tejas", 30, 55000))
    emp_db.add_employee(Employee("171G30", "Ajay", 45, 44000))

    print("Search Options:")
    print("1. Age\n2. Name\n3. Salary")
    choice = int(input("Enter your choice: "))

    if choice == 1:
        age = int(input("Enter age to search: "))
        result = emp_db.search_by_age(age)
    elif choice == 2:
        name = input("Enter name to search: ")
        result = emp_db.search_by_name(name)
    elif choice == 3:
        condition = input("Enter condition (<, >, <=, >=): ")
        salary = int(input("Enter salary to search: "))
        result = emp_db.search_by_salary(condition, salary)
    else:
        print("Invalid choice.")
        return

    if result:
        print("\nSearch Result:")
        for employee in result:
            print(f"Employee ID: {employee.emp_id}, Name: {employee.name}, Age: {employee.age}, Salary: {employee.salary}")
    else:
        print("No matching records found.")

if __name__ == "__main__":
    main()
