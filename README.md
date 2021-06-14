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

**Header Files Added**:
1. ```stdio.h``` - For standard Input/Output (I/O) operations.
2. ```conio.h``` - For ```clrscr()``` and ```getch()``` functions.
3. ```string.h``` - For string handling.

**Understanding of the program**:
To understand how this program works, we need to be familiar with concept of pointers. A pointer is initiated whenever we open a file. On opening a file, a pointer is set up which points to the first record in the file. To be precise this pointer is present in the structure to which the file pointer returned by ```fopen()``` points to. On using the functions ```fread()``` or ```fwrite()```, the pointer moves to the beginning of the next record. On closing a file the pointer is deactivated. Note that the pointer movement is of utmost importance since ```fread()``` always reads that record where the pointer is currently placed. Similarly, ```fwrite()``` always writes the record where the pointer is currently placed.

The ```rewind()``` function places the pointer to the beginning of the file, irrespective of where it is present right now.

The ```fseek()``` function lets us move the pointer from one record to another. In the program, to move the pointer to the previous record from its current position, I used this function.

```C
fseek(fp, -recsize, SEEK_CUR);
```

Here, **-recsize** moves the pointer back by **recsize** bytes from the current position. ```SEEK_CUR``` is a macro defined in ```stdio.h```.
Similarly, the following ```fseek()``` would place the pointer beyond the last record in the file.

```C
fseek(fp, 0, SEEK_END);
```

In fact, **-recsize** or **0** are just the offsets that tell the compiler by how many bytes should the pointer be moved from a particular position. The third argument could be ```SEEK_END```, ```SEEK_CUR``` or ```SEEK_SET```. All these act as a reference from which the pointer should be offset. ```SEEK_END``` means move the pointer from the end of the file. ```SEEK_CUR``` means move the pointer with reference to its current position and ```SEEK_SET``` means move the pointer with reference to the beginning of the file.

If we wish to know where the pointer is positioned right now, we can use he function ```ftell()```. It returns this position as a ```long int``` wich is an offset from the beginning of the file. The value returned by ```ftell()``` can be used in subsequent calls to ```fseek()```. A sample call to ftell() is shown below:

```C
position = ftell(fp);
```

where **position** is a ```long int```.
===
