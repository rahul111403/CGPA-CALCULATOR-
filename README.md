#include <iostream>
#include <vector>
#include <iomanip>
using namespace std;

struct Course {
    string name;
    double grade;
    double creditHours;
};

int main() {
    int numCourses;
    cout << "Enter the number of courses: ";
    cin >> numCourses;

    vector<Course> courses(numCourses);
    double totalCredits = 0.0;
    double totalGradePoints = 0.0;

    for (int i = 0; i < numCourses; ++i) {
        cout << "\nEnter details for Course " << i + 1 << ":\n";
        cout << "Course name: ";
        cin.ignore();  // to handle leftover newline
        getline(cin, courses[i].name);
        cout << "Grade (e.g., 4.0 for A, 3.0 for B, etc.): ";
        cin >> courses[i].grade;
        cout << "Credit hours: ";
        cin >> courses[i].creditHours;

        totalGradePoints += courses[i].grade * courses[i].creditHours;
        totalCredits += courses[i].creditHours;
    }

    if (totalCredits == 0) {
        cout << "No valid credits entered. Cannot compute CGPA.\n";
        return 0;
    }

    double cgpa = totalGradePoints / totalCredits;

    cout << "\n--- Course Grades ---\n";
    for (int i = 0; i < numCourses; ++i) {
        cout << fixed << setprecision(2);
        cout << courses[i].name << " | Grade: " << courses[i].grade
             << " | Credit Hours: " << courses[i].creditHours
             << " | Grade Points: " << courses[i].grade * courses[i].creditHours << "\n";
    }

    cout << "\nFinal CGPA: " << fixed << setprecision(2) << cgpa << "\n";

    return 0;
}
