# 🎓 Student GradeBook System

A simple JavaScript project that manages student records including their grades, averages, and top performers. Built using object methods .



------------------------------------------

##  Features

- Add new students with their grades
- Remove existing students
- Update student grades
- Calculate average grade for a student
- Find the top-performing student
- Display all student records

------------------------------------------

##  Built With


- JavaScript (Object Methods, Array Methods)

---------------------------------------------



const gradeBook = {
  students: [],

  addStudent(name, grades) {
    this.students.push({ name, grades });
  },

  removeStudent(name) {
    this.students = this.students.filter(student => student.name !== name);
  },

  updateGrades(name, newGrades) {
    for (let i = 0; i < this.students.length; i++) {
      if (this.students[i].name === name) {
        this.students[i].grades = newGrades;
        return;
      }
    }
    console.log("Student not found");
  },

 
  averageGrade(name) {
    for (let i = 0; i < this.students.length; i++) {
      if (this.students[i].name === name) {
        const grades = this.students[i].grades;
        const total = grades.reduce((sum, g) => sum + g, 0);
        return (total / grades.length).toFixed(2);
      }
    }
    return null;
  },


  topStudent() {
    let top = null;
    let highest = 0;

    this.students.forEach(student => {
      const avg = this.averageGrade(student.name);
      if (avg > highest) {
        highest = avg;
        top = student;
      }
    });

    return top;
  }
};

gradeBook.addStudent("Ali", [85, 90, 78]);
gradeBook.addStudent("Muhammad", [92, 88, 95]);
gradeBook.addStudent("Ayesha", [75, 80, 79]);
gradeBook.addStudent("Bilal", [90, 93, 89]);
gradeBook.addStudent("Sara", [88, 84, 91]);
gradeBook.addStudent("Hassan", [70, 76, 68]);



console.log("All Students:", gradeBook.students);
console.log("Sara's Average:", gradeBook.averageGrade("Sara"));
console.log("Ali's Average:", gradeBook.averageGrade("Ali"));
console.log("Ayesha's Average:", gradeBook.averageGrade("Ayesha"));
console.log("Hassan's Average:", gradeBook.averageGrade("Hassan"));
console.log("Bilal's Average:", gradeBook.averageGrade("Bilal"));
console.log("Muhammad's Average:", gradeBook.averageGrade("Muhammad"));

console.log("Top Student:", gradeBook.topStudent());
