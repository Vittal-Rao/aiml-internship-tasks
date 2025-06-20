# aiml-internship-tasks

vittaltask1 and2.ipynb

TASK 1 :- PASSWORD GENERATOR



import random
import string

def generate_password(length, use_uppercase=True, use_digits=True, use_specials=True):
    if length <= 0:
        return " Password length must be greater than 0."

    characters = string.ascii_lowercase
    required_chars = [random.choice(string.ascii_lowercase)]

    if use_uppercase:
        characters += string.ascii_uppercase
        required_chars.append(random.choice(string.ascii_uppercase))
    if use_digits:
        characters += string.digits
        required_chars.append(random.choice(string.digits))
    if use_specials:
        characters += string.punctuation
        required_chars.append(random.choice(string.punctuation))

    if not characters:
        return " No character sets selected!"

    remaining_length = length - len(required_chars)
    if remaining_length < 0:
        return " Password length too short for selected options."

    password = required_chars + [random.choice(characters) for _ in range(remaining_length)]
    random.shuffle(password)
    return ''.join(password)

print(" Password Generator ")

while True:
    try:
        length = int(input("Enter password length (minimum 4 recommended): "))
        if length <= 0:
            print(" Please enter a positive integer.")
            continue
        break
    except ValueError:
        print(" Please enter a valid number.")

use_upper = input("Include uppercase letters? (y/n): ").strip().lower() == 'y'
use_digits = input("Include digits? (y/n): ").strip().lower() == 'y'
use_specials = input("Include special characters? (y/n): ").strip().lower() == 'y'

password = generate_password(length, use_upper, use_digits, use_specials)
print(f"\n Generated Password: {password}")
 Password Generator 
Enter password length (minimum 4 recommended): 0123
Include uppercase letters? (y/n): y
Include digits? (y/n): n
Include special characters? (y/n): y

 Generated Password: Lmom":Zn^rKvfWA]'QgU.&L&P};@LcZk.kh/UL&T:U/fsmhet__b'p**W>AK+>uGOVO%Cs;HQ|,]o^V[amjd|~p;bQA/^fARmcW_iO.)Q(tf?SiW[;jx;vEYo:u
TASK 2 :- To-Do List App


[ ]
todo_list = []

def show_menu():
    print("\nTo-Do List Menu:")
    print("1. Add task")
    print("2. View tasks")
    print("3. Mark task as completed")
    print("4. Delete task")
    print("5. Exit")

def view_tasks():
    if not todo_list:
        print("\nNo tasks in the list.")
    else:
        print("\nYour Tasks:")
        for i, task in enumerate(todo_list, start=1):
            status = "Completed" if task['completed'] else "Pending"
            print(f"{i}. {task['task']} [{status}]")

def add_task():
    task = input("Enter the task description: ").strip()
    if task:
        todo_list.append({'task': task, 'completed': False})
        print("Task added successfully!")
    else:
        print("Task description cannot be empty.")

def mark_task_completed():
    view_tasks()
    try:
        idx = int(input("Enter task number to mark as completed: ")) - 1
        if 0 <= idx < len(todo_list):
            todo_list[idx]['completed'] = True
            print("Task marked as completed!")
        else:
            print("Invalid task number.")
    except ValueError:
        print("Please enter a valid number.")

def delete_task():
    view_tasks()
    try:
        idx = int(input("Enter task number to delete: ")) - 1
        if 0 <= idx < len(todo_list):
            removed = todo_list.pop(idx)
            print(f"Task '{removed['task']}' deleted.")
        else:
            print("Invalid task number.")
    except ValueError:
        print("Please enter a valid number.")

while True:
    show_menu()
    choice = input("Choose an option (1-5): ").strip()

    if choice == '1':
        add_task()
    elif choice == '2':
        view_tasks()
    elif choice == '3':
        mark_task_completed()
    elif choice == '4':
        delete_task()
    elif choice == '5':
        print("Exiting To-Do List. Goodbye!")
        break
    else:
        print("Invalid choice. Please try again.")


To-Do List Menu:
1. Add task
2. View tasks
3. Mark task as completed
4. Delete task
5. Exit
Choose an option (1-5): 1
Enter the task description: MEETING AT 9.00AM
Task added successfully!

To-Do List Menu:
1. Add task
2. View tasks
3. Mark task as completed
4. Delete task
5. Exit
Choose an option (1-5): 2

Your Tasks:
1. MEETING AT 9.00AM [Pending]

To-Do List Menu:
1. Add task
2. View tasks
3. Mark task as completed
4. Delete task
5. Exit
Choose an option (1-5): 3

Your Tasks:
1. MEETING AT 9.00AM [Pending]
Enter task number to mark as completed: 4
Invalid task number.

To-Do List Menu:
1. Add task
2. View tasks
3. Mark task as completed
4. Delete task
5. Exit
Choose an option (1-5): 5
Exiting To-Do List. Goodbye!
Colab paid products - Cancel contracts here
