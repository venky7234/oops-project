import java.util.ArrayList;
import java.util.List;

// Base class Person
class Person {
    private String id;
    private String name;

    public Person(String id, String name) {
        this.id = id;
        this.name = name;
    }

    // Getter and Setter methods
    public String getId() {
        return id;
    }

    public void setId(String id) {
        this.id = id;
    }

    public String getName() {
        return name;
    }

    public void setName(String name) {
        this.name = name;
    }
}

// Student class extending Person
class Student extends Person {
    private List<Course> courses;
    private List<String> grades;

    public Student(String id, String name) {
        super(id, name);
        this.courses = new ArrayList<>();
        this.grades = new ArrayList<>();
    }

    // Enroll in a course
    public void enrollCourse(Course course) {
        courses.add(course);
        course.enrollStudent(this);
    }

    // Add a grade
    public void addGrade(String grade) {
        grades.add(grade);
    }

    // Getter methods
    public List<Course> getCourses() {
        return courses;
    }

    public List<String> getGrades() {
        return grades;
    }
}

// Teacher class extending Person
class Teacher extends Person {
    private List<Course> courses;

    public Teacher(String id, String name) {
        super(id, name);
        this.courses = new ArrayList<>();
    }

    // Assign a course
    public void assignCourse(Course course) {
        courses.add(course);
        course.assignTeacher(this);
    }

    // Getter method
    public List<Course> getCourses() {
        return courses;
    }
}

// Course class
class Course {
    private String courseId;
    private String courseName;
    private Teacher teacher;
    private List<Student> students;

    public Course(String courseId, String courseName) {
        this.courseId = courseId;
        this.courseName = courseName;
        this.students = new ArrayList<>();
    }

    // Enroll a student
    public void enrollStudent(Student student) {
        students.add(student);
    }

    // Assign a teacher
    public void assignTeacher(Teacher teacher) {
        this.teacher = teacher;
    }

    // Getter methods
    public String getCourseId() {
        return courseId;
    }

    public String getCourseName() {
        return courseName;
    }

    public Teacher getTeacher() {
        return teacher;
    }

    public List<Student> getStudents() {
        return students;
    }
}

// Main class to demonstrate the project
class Main {
    public static void main(String[] args) {
        // Create students
        Student student1 = new Student("S1", "D.venkatesh");
        Student student2 = new Student("S2", "E.jalandhar");

        // Create teachers
        Teacher teacher1 = new Teacher("T1", "Dr.Tharun Reddy");
        Teacher teacher2 = new Teacher("T2", "Prof. s.Koti Reddy");

        // Create courses
        Course course1 = new Course("C1", "Mathematics");
        Course course2 = new Course("C2", "Physics");

        // Assign teachers to courses
        teacher1.assignCourse(course1);
        teacher2.assignCourse(course2);java

        // Enroll students in courses
        student1.enrollCourse(course1);
        student2.enrollCourse(course1);
        student2.enrollCourse(course2);

        // Add grades
        student1.addGrade("A");
        student2.addGrade("B");
        student2.addGrade("A");

        // Print out information
        System.out.println("Course: " + course1.getCourseName() + " taught by " + course1.getTeacher().getName());
        for (Student s : course1.getStudents()) {
            System.out.println("Student: " + s.getName() + " enrolled in " + course1.getCourseName());
        }

        System.out.println("Course: " + course2.getCourseName() + " taught by " + course2.getTeacher().getName());
        for (Student s : course2.getStudents()) {
            System.out.println("Student: " + s.getName() + " enrolled in " + course2.getCourseName());
}
}
}
