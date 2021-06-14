# Airline Reservation System

This is my project done for **Delhi Technological University (formerly, Delhi College of Engineering), Faculty of Information Technology** for a beginner course in **Programming Fundamentals in C (Course Code - CO101)**.

A basic implementation of Airline Reservation System in ```C``` language using the concept of **structures** and **data file handling**.

---

# Documentation

**Definition** - An airline reservation system contains details about flight schedules and its flight tariffs, passenger reservations and ticket records.

**Problem Statement** - The task is to create an airline reservation system which can perform the following operations:
1. Add new records.
2. List records.
3. Modify records.
4. Change flight rates.
5. Delete records.

**Approach** - The idea is to write individual block of code for every operation. All the blocks of code are unified together to form the main program.

Following caveats would help to understand the program easily:
* **Add new records** - Addition of records must always take place at the end of the existing records in the file, much in the same way you would add new records in a register manually.
* **List records** - Listing records means displaying the existing records on the screen. Naturally, records should be listed from first record to last record.
* **Modify records** - While modifying records, first we must ask the user which record he intends to modify. Instead of asking the record number to be modified, it would be more meaningful to ask for the name of the person whose record is to be modified. On modifying the record, the existing record gets overwritten by the new record.
* **Change flight rates** - To do this, first we must ask the user to enter the code for the flight whose flight rates are to be changed. After that, we ask the user to enter new flight rates for that flight.
* **Delete records** - In deleting records, except for the record to be deleted, rest of the records must first be written to a temporary file, then the original file must be deleted, and the temporary file must be renamed back to original.
* Observe carefully the way the file has been opened, first for reading & writing, and if this fails (the first time you run this program it would certainly fail, because that time the file is not existing), for writing and reading. It is imperative that the file should be opened in binary mode.
* Note that the file is being opened only once and closed only once, which is quite logical. 
