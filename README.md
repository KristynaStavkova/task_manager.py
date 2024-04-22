# task_manager.py
import datetime
class Task:
    def __init__(self, description):
        self.description = description
        self.timestamp = datetime.datetime.now()
tasks = {}
def add_task(description):
    task_id = len(tasks) + 1
    tasks[task_id] = Task(description)
    print(f"Úkol '{description}' byl přidán s ID {task_id}.")

def remove_task(task_id):
    if task_id in tasks:
        del tasks[task_id]
        print(f"Úkol s ID {task_id} byl odstraněn.")
    else:
        print("Úkol s daným ID neexistuje.")

def show_tasks():
    if tasks:
        print("Seznam úkolů:")
        for task_id, task in tasks.items():
            print(f"ID: {task_id}, Popis: {task.description}, Čas přidání: {task.timestamp}")
    else:
        print("Nejsou žádné úkoly k zobrazení.")
def main():
    while True:
        command = input("Zadejte příkaz (add/remove/show/exit): ").strip().lower()

        if command == "add":
            description = input("Zadejte popis úkolu: ")
            add_task(description)
        elif command == "remove":
            task_id = int(input("Zadejte ID úkolu k odstranění: "))
            remove_task(task_id)
        elif command == "show":
            show_tasks()
        elif command == "exit":
            print("Program ukončen.")
            break
        else:
            print("Neplatný příkaz. Zadejte 'add', 'remove', 'show' nebo 'exit'.")

if __name__ == "__main__":
    main()

