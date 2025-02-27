# codealpha_tasks
The user’s input is used to compute the CGPA, which includes information like the number of courses taken and the grades earned in each one. The program also shows each student’s overall course grade. CGPA Calculator calculates a student’s Cumulative Grade Point Average (CGPA) from the given exam results. 

#include <iostream>
#include <vector>
using namespace std;

class Course {
public:
    string name;
    int credits;
    float grade;

    Course(string n, int c, float g) : name(n), credits(c), grade(g) {}
};

class Student {
private:
    vector<Course> courses;

public:
    void addCourse(string name, int credits, float grade) {
        courses.push_back(Course(name, credits, grade));
    }

    void displayCourses() {
        cout << "Course Details:" << endl;
        for (auto &course : courses) {
            cout << "Name: " << course.name << ", Credits: " << course.credits << ", Grade: " << course.grade << endl;
        }
    }

    float calculateCGPA() {
        float totalGradePoints = 0;
        int totalCredits = 0;
        for (auto &course : courses) {
            totalGradePoints += course.grade * course.credits;
            totalCredits += course.credits;
        }
        return totalGradePoints / totalCredits;
    }
};

int main() {
    Student student;
    int numberOfCourses;

    cout << "Enter number of courses: ";
    cin >> numberOfCourses;

    for (int i = 0; i < numberOfCourses; ++i) {
        string courseName;
        int credits;
        float grade;

        cout << "Enter details for course " << i + 1 << ":" << endl;
        cout << "Course Name: ";
        cin >> courseName;
        cout << "Credits: ";
        cin >> credits;
        cout << "Grade: ";
        cin >> grade;

        student.addCourse(courseName, credits, grade);
    }

    student.displayCourses();
    cout << "CGPA: " << student.calculateCGPA() << endl;

    return 0;
}
