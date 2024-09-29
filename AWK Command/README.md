NR - No. of record/row
NF - No. of fields
$0 - Print everything
$1,$2 - Field no.

1. To print the 4th and 5th column in a given file
   awk '{print $4, $5}' employee.txt

2. Print the last column
   awk '{print $NF}' employee.txt

3. To print total content of the file.
   awk '{print $0}' employee.txt

4. To check a specific word in the file.
   awk '/Paul/{print $0}' employee.txt

5. To print line numbers for the given file.
   awk '{print NR, $0}' employee.txt

6. To print the line number where ever the paul matches
   awk '/Paul{print NR, $0}' employee.txt

7. To print only the line number 6[The NR which is present in the flower brackets is optional this to     print line number 6]
   awk 'NR==6 {print NR, $0}' employee.txt

<<<<<<< HEAD
8. To print the range of lines[e.g 3rd line to 6th line]
   awk 'NR==3, NR==6 {print NR,$0}' employee.txt

9. To print the empty lines.
   awk 'NF==0 {print NR}' employee.txt

10. To search multiple files.
    awk '/Raju|Shyam|Alex/ {print $0}' employee.txt

11. Ignore case search
    awk 'BEGIN{IGNORECASE=1} /alexandr/ {print $0}' employee.txt

12. To search a word in a column
    awk '$2 ~ /a/ {print $0}' employee.txt

13. To print a specific column data
    awk -F, '{print $2}' employee.csv
=======
8.  
>>>>>>> 6e0e6d3016930ad7bbf6e000f275b232a2a16737
