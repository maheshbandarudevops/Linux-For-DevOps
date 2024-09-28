The awk command in Linux is a powerful text processing tool used for pattern scanning, text manipulation, and reporting. It processes input line by line and applies actions based on defined patterns.

Here's an end-to-end guide on how to use awk with examples:

1. Basic Syntax of awk:
The basic syntax of the awk command is as follows:

bash
Copy code
awk 'pattern {action}' file
pattern: The condition that must be met for awk to take action.
action: What awk should do if the pattern is met.
file: The file(s) to process.
2. Basic Example: Printing Specific Columns
Let's say you have a file data.txt with the following contents:

Copy code
John Doe 30
Jane Doe 25
Mike Smith 40
Alice Jones 35
Command:
bash
Copy code
awk '{print $1, $3}' data.txt
Output:
Copy code
John 30
Jane 25
Mike 40
Alice 35
Breakdown:
$1: Refers to the first field (column) of each line.
$3: Refers to the third field (column) of each line.
print $1, $3: Prints the first and third columns.
3. Example: Filtering Rows Based on a Condition
To display only the people who are older than 30:

Command:
bash
Copy code
awk '$3 > 30 {print $1, $2}' data.txt
Output:
Copy code
Mike Smith
Alice Jones
Breakdown:
$3 > 30: The condition that checks if the third field (age) is greater than 30.
print $1, $2: Prints the first and second columns (name) of the rows where the condition is true.
4. Example: Calculating the Sum of a Column
To calculate the total age of all individuals:

Command:
bash
Copy code
awk '{sum += $3} END {print "Total Age:", sum}' data.txt
Output:
mathematica
Copy code
Total Age: 130
Breakdown:
sum += $3: Adds the value of the third field (age) to the sum variable for each row.
END {print "Total Age:", sum}: After all lines are processed, prints the total sum of ages.
5. Example: Counting the Number of Rows
To count how many lines (people) are in the file:

Command:
bash
Copy code
awk 'END {print NR}' data.txt
Output:
Copy code
4
Breakdown:
NR: A built-in awk variable that holds the line number (row count).
END {print NR}: Prints the total number of rows after processing the file.
6. Example: Printing Only Lines that Match a Pattern
To print only the lines containing "Doe":

Command:
bash
Copy code
awk '/Doe/' data.txt
Output:
Copy code
John Doe 30
Jane Doe 25
Breakdown:
/Doe/: Matches lines containing the string "Doe".
7. Example: Changing the Field Separator
If the file comma_data.txt contains comma-separated values:

Copy code
John,Doe,30
Jane,Doe,25
Mike,Smith,40
Alice,Jones,35
To process this file, you need to tell awk to treat commas as field separators using the -F option:

Command:
bash
Copy code
awk -F ',' '{print $1, $3}' comma_data.txt
Output:
Copy code
John 30
Jane 25
Mike 40
Alice 35
Breakdown:
-F ',': Sets the field separator to a comma.
print $1, $3: Prints the first and third columns (name and age).
8. Example: Using Multiple Conditions
To print the names of people whose age is greater than 30 and whose last name is "Doe":

Command:
bash
Copy code
awk '$3 > 30 && $2 == "Doe" {print $1, $2}' data.txt
Output:
Copy code
John Doe
Breakdown:
$3 > 30 && $2 == "Doe": The condition checks if the third field (age) is greater than 30 and the second field (last name) is "Doe".
print $1, $2: Prints the first and second columns (name).
9. Example: Modifying Text in a File
To replace all instances of "Doe" with "Smith" and print the result:

Command:
bash
Copy code
awk '{gsub("Doe", "Smith"); print}' data.txt
Output:
Copy code
John Smith 30
Jane Smith 25
Mike Smith 40
Alice Jones 35
Breakdown:
gsub("Doe", "Smith"): Replaces all occurrences of "Doe" with "Smith".
print: Prints the modified line.
10. Example: Using awk with System Commands
You can also use awk with system commands like ls, df, ps, etc.

Example: Summing File Sizes in a Directory
bash
Copy code
ls -l | awk '{sum += $5} END {print "Total Size:", sum}'
Breakdown:
$5: Refers to the file size field in the ls -l output.
sum += $5: Adds the file size to the sum variable for each line.
END {print "Total Size:", sum}: Prints the total size after all lines are processed.
11. Example: Extracting Specific Data from a ps Command
To extract the PID and command name of processes owned by a specific user:

Command:
bash
Copy code
ps -u username | awk '{print $1, $11}'
Breakdown:
ps -u username: Lists the processes for the specified user.
print $1, $11: Prints the first field (PID) and the eleventh field (command name).
12. Example: Formatting Output with awk
To format output as a table:

Command:
bash
Copy code
awk 'BEGIN {printf "%-10s %-10s\n", "Name", "Age"} {printf "%-10s %-10s\n", $1, $3}' data.txt
Output:
Copy code
Name       Age       
John       30        
Jane       25        
Mike       40        
Alice      35        
Breakdown:
BEGIN {printf "%-10s %-10s\n", "Name", "Age"}: Before processing the file, prints the headers "Name" and "Age" in a formatted manner.
printf "%-10s %-10s\n", $1, $3: Formats the first and third fields (name and age) into two columns of width 10 characters.
Summary:
Basic field manipulation: awk '{print $1, $3}' file.txt
Filtering based on conditions: awk '$3 > 30 {print $1}' file.txt
Summing values: awk '{sum += $3} END {print sum}' file.txt
Working with system commands: ps aux | awk '{print $1, $2}'
Formatting output: awk 'BEGIN {print "Header"} {print $1}' file.txt
These examples give you an idea of how to use awk in different scenarios for text processing and automation in Linux.
