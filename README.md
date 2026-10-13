#include <iostream>
#include <string>

using namespace std;

const int MAX_STUDENTS = 50;

// Structure to hold individual student data
struct Student {
    int id;
    string name;
    float grade;
};

// Function to display all student records
void displayStudents(const Student students[], int count) {
    if (count == 0) {
        cout << "No student records available.";
        return;
    }
    
    cout << "\n--- Student Records ---\n";
    for (int i = 0; i < count; i++) {
        cout << "ID: " << students[i] .id 
             << " | Name: " << students[i] .name 
             << " | Grade: " << students[i] .grade << "\n";
    }
}

// Function to calculate and display the average grade
void calculateAverage(const Student students[], int count) {
    if (count == 0) {
        cout << "\nNo records to calculate average.\n";
        return;
    }
    
    float sum = 0;
    for (int i = 0; i < count; i++) {
        sum += students[i] .grade;
    }
    cout << "\nClass Average Grade: " << (sum / count) << "\n";
}

int main() {
    Student students[MAX_STUDENTS];
    int studentCount = 0;
    int choice;

    do {
        cout << "\n=== School Management System ===";
        cout << "\n1. Add Student";
        cout << "\n2. View All Students";
        cout << "\n3. Calculate Average Grade";
        cout << "\n4. Exit";
        cout << "\nEnter your choice: ";
        cin >> choice;

        switch (choice) {
            case 1:
                if (studentCount < MAX_STUDENTS) {
                    cout << "Enter Student ID: ";
                    cin >> students[studentCount] .id;
                    cout << "Enter Student Name: ";
                    cin >> ws; // Clear input buffer
                    getline(cin, students[studentCount] .name);
                    cout << "Enter Student Grade: ";
                    cin >> students[studentCount] .grade;
                    studentCount++;
                    cout << "Student added successfully!\n";
                } else {
                    cout << "Error: Maximum student capacity reached!\n";
                }
                break;
                
            case 2:
                displayStudents(students, studentCount);
                break;
                
            case 3:
                calculateAverage(students, studentCount);
                break;
                
            case 4:
                cout << "Exiting system. Goodbye!\n";
                break;
                
            default:
                cout << "Invalid choice. Please try again.\n";
        }
    } while (choice != 4);

    return 0;
}
