import datetime

class ToDoList:
    def __init__(self):
        self.tasks = {}
        self.completed_tasks = {}

    def add_task(self, description, due_date=None, priority=None):
        task_id = len(self.tasks) + 1
        task = {"description": description, "due_date": due_date, "priority": priority}
        self.tasks[task_id] = task
        print(f"Task {task_id} added.")

    def display_tasks(self):
        print("\nToDo List:")
        for task_id, task in self.tasks.items():
            print(f"{task_id}. {task['description']}")
            if task['due_date']:
                print(f"   Due Date: {task['due_date']}")
            if task['priority']:
                print(f"   Priority: {task['priority']}")
            print()

        print("\nCompleted Tasks:")
        for task_id, task in self.completed_tasks.items():
            print(f"{task_id}. {task['description']}")
            print()

    def complete_task(self, task_id):
        if task_id in self.tasks:
            task = self.tasks.pop(task_id)
            self.completed_tasks[task_id] = task
            print(f"Task {task_id} marked as completed.")
        else:
            print("Task not found.")

    def update_task(self, task_id, description=None, due_date=None, priority=None):
        if task_id in self.tasks:
            task = self.tasks[task_id]
            if description:
                task['description'] = description
            if due_date:
                task['due_date'] = due_date
            if priority:
                task['priority'] = priority
            print(f"Task {task_id} updated.")
        else:
            print("Task not found.")

    def remove_task(self, task_id):
        if task_id in self.tasks:
            del self.tasks[task_id]
            print(f"Task {task_id} removed.")
        else:
            print("Task not found.")


def main():
    todo_list = ToDoList()

    while True:
        print("\n1. Add Task")
        print("2. Display Tasks")
        print("3. Complete Task")
        print("4. Update Task")
        print("5. Remove Task")
        print("6. Exit")

        choice = input("Enter your choice (1-6): ")

        if choice == '1':
            description = input("Enter task description: ")
            due_date = input("Enter due date (optional): ")
            priority = input("Enter priority (optional): ")
            todo_list.add_task(description, due_date, priority)

        elif choice == '2':
            todo_list.display_tasks()

        elif choice == '3':
            task_id = int(input("Enter task ID to mark as completed: "))
            todo_list.complete_task(task_id)

        elif choice == '4':
            task_id = int(input("Enter task ID to update: "))
            description = input("Enter new task description (press enter to keep the same): ")
            due_date = input("Enter new due date (press enter to keep the same): ")
            priority = input("Enter new priority (press enter to keep the same): ")
            todo_list.update_task(task_id, description, due_date, priority)

        elif choice == '5':
            task_id = int(input("Enter task ID to remove: "))
            todo_list.remove_task(task_id)

        elif choice == '6':
            print("Exiting ToDo List Application. Goodbye!")
            break

        else:
            print("Invalid choice. Please enter a number between 1 and 6.")


if __name__ == "__main__":
    main()
# todo_app.py
