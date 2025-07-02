# to-do-list-
Implement a console-based to-do list application that supports adding, editing, and deleting tasks.
import java.util.ArrayList;
import java.util.Scanner;

public class ToDoListApp {

    private static final ArrayList<String> tasks = new ArrayList<>();
    private static final Scanner scanner = new Scanner(System.in);

    public static void main(String[] args) {
        int choice;
        do {
            displayMenu();
            System.out.print("Enter your choice (1-5): ");
            choice = scanner.nextInt();
            scanner.nextLine(); // consume newline

            switch (choice) {
                case 1 -> viewTasks();
                case 2 -> addTask();
                case 3 -> editTask();
                case 4 -> deleteTask();
                case 5 -> System.out.println("Exiting... Goodbye!");
                default -> System.out.println("Invalid choice. Please choose between 1-5.");
            }
        } while (choice != 5);
    }

    private static void displayMenu() {
        System.out.println("\n====== TO-DO LIST MENU ======");
        System.out.println("1. View Tasks");
        System.out.println("2. Add Task");
        System.out.println("3. Edit Task");
        System.out.println("4. Delete Task");
        System.out.println("5. Exit");
    }

    private static void viewTasks() {
        if (tasks.isEmpty()) {
            System.out.println("No tasks available.");
        } else {
            System.out.println("\nYour Tasks:");
            for (int i = 0; i < tasks.size(); i++) {
                System.out.println((i + 1) + ". " + tasks.get(i));
            }
        }
    }

    private static void addTask() {
        System.out.print("Enter a new task: ");
        String task = scanner.nextLine();
        tasks.add(task);
        System.out.println("Task added successfully.");
    }

    private static void editTask() {
        viewTasks();
        if (!tasks.isEmpty()) {
            System.out.print("Enter the task number to edit: ");
            int taskNumber = scanner.nextInt();
            scanner.nextLine(); // consume newline

            if (taskNumber >= 1 && taskNumber <= tasks.size()) {
                System.out.print("Enter the updated task: ");
                String updatedTask = scanner.nextLine();
                tasks.set(taskNumber - 1, updatedTask);
                System.out.println("Task updated successfully.");
            } else {
                System.out.println("Invalid task number.");
            }
        }
    }

    private static void deleteTask() {
        viewTasks();
        if (!tasks.isEmpty()) {
            System.out.print("Enter the task number to delete: ");
            int taskNumber = scanner.nextInt();
            scanner.nextLine(); // consume newline

            if (taskNumber >= 1 && taskNumber <= tasks.size()) {
                tasks.remove(taskNumber - 1);
                System.out.println("Task deleted successfully.");
            } else {
                System.out.println("Invalid task number.");
            }
        }
    }
}
