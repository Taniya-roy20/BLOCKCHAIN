# **Practical 2 : Student records** 
# **Write a contract that manages a list of student records (name, roll number). Allow adding and retrieving student data.**
**code: StudentRecords.sol**


    // SPDX-License-Identifier: MIT
      pragma solidity ^0.8.0;

     contract StudentRecords {
    
    // Define a structure to hold student details
    struct Student {
        string name;
        uint rollNumber;
    }

    // Dynamic array to store student records
    Student[] private students;

    // Function to add a new student
    function addStudent(string memory _name, uint _rollNumber) public {
        students.push(Student(_name, _rollNumber));
    }

    // Function to get student details by index
    function getStudent(uint index) public view returns (string memory, uint) {
        require(index < students.length, "Student index out of bounds");
        Student memory s = students[index];
        return (s.name, s.rollNumber);
    }

    // Optional: Get total number of students
    function getStudentCount() public view returns (uint) {
        return students.length;
     }
   }


 ![image](https://github.com/user-attachments/assets/e2ab6e37-8072-43be-a3a7-5c42d09b2d0e)
 ![image](https://github.com/user-attachments/assets/c1f73643-07ac-477f-8636-8d48937cb9e7)

# STEPS

**How to Test in Remix**

Paste the code in a new file: StudentRecords.sol.

Compile with Solidity ^0.8.0.

Deploy the contract.

Use addStudent("Alice", 101) and addStudent("Bob", 102).

Call getStudent(0) and getStudent(1) to retrieve data.

Use getStudentCount() to check the total number of students added.


![image](https://github.com/user-attachments/assets/78150f68-e6a5-4c0c-ae6a-e193f7fe12f4)

![image](https://github.com/user-attachments/assets/236b05a5-8b8f-4590-8009-948ff88cb0c7)


# Output


![image](https://github.com/user-attachments/assets/4002552e-b50d-441f-8da4-f979b3b3968f)

![image](https://github.com/user-attachments/assets/a9a7d91f-850e-44cc-a8a9-df283b96f333)

![image](https://github.com/user-attachments/assets/baf80fd0-0c86-416b-8e40-5fd8ab4bfcc7)

![image](https://github.com/user-attachments/assets/7e62ec07-6ca4-4bda-b0f1-665bbaa080fa)

![image](https://github.com/user-attachments/assets/ea794423-b477-4b86-b1ce-31758a34653b)

![image](https://github.com/user-attachments/assets/95f8b2c7-7f83-401a-a2d1-928517cb1715)
