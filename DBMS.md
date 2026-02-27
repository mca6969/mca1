# Student-Enrollment Database.
Consider the following relations:
Student(snum: integer, sname: string, major: string, level: string, age: integer)
Class(name: string, meets at: string, room: string, fid: integer)
Enrolled(snum: integer, cname: string)
Faculty(fid: integer, fname: string, deptid: integer)
Enrolled has one record per Student-class pair such that the student is enrolled in the
class. Develop an ER schema by reverse engineering from the above relational schema.
Write the following queries in SQL.
1. Create the above tables by properly specifying all the integrity constraints.
2. Insert at least five tuples into each table. 
