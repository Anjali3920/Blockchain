### Write a contract that manages a list of student records (name, roll number). Allow adding and retrieving student data.
```
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.0;

contract StudentRecords {
    struct Student {
        string name;
        uint rollNo;
    }

    Student[] public students;

    function addStudent(string memory _name, uint _rollNo) public {
        students.push(Student(_name, _rollNo));
    }

    function getStudent(uint index) public view returns (string memory, uint) {
        require(index < students.length, "Invalid index");
        Student memory s = students[index];
        return (s.name, s.rollNo);
    }
}

```
![image](https://github.com/user-attachments/assets/1f4aac12-5cef-4396-93ff-e02e127a0fc3)

![image](https://github.com/user-attachments/assets/8b2cf992-4354-4a1a-ae05-e4fdfa87d4b9)

![image](https://github.com/user-attachments/assets/a610e46b-f8e8-4f46-a883-feea57b54660)

