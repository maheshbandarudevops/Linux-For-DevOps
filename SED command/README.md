The sed (Stream Editor) command in Linux is used to perform basic text transformations on an input stream (a file or input from a pipeline). Here are some common examples:

1. Substitute a word or pattern in a file (basic replacement)
   sed 's/original/replacement/' filename.txt
   sed 's/old/new/' sample.txt

2. Replace all occurrences of a word in a file
   sed 's/original/replacement/g' filename.txt
   sed 's/old/new/g' sample.txt
   This replaces all occurrences of "old" with "new" on each line, thanks to the g (global) flag.

3. Replace a word only on a specific line
   sed '3s/original/replacement/' filename.txt
   sed '3s/old/new/' sample.txt
   This will only replace "old" with "new" on line 3 of sample.txt.

4. Write changes to a new file
   You can redirect the output to a new file:
   sed 's/original/replacement/g' filename.txt > newfile.txt
   sed 's/old/new/g' sample.txt > updated_sample.txt
   This will replace all occurrences of "old" with "new" and save the changes to updated_sample.txt.

5. Edit the file in place (make the changes permanent)
   To apply the changes directly to the file, use the -i flag:
   sed -i 's/original/replacement/g' filename.txt

6. Delete lines containing a specific pattern
   sed '/pattern/d' filename.txt

7. Delete a specific line by number
   sed '3d' filename.txt

8. Insert a line after a specific line number
   sed '3a\This is a new line' filename.txt

9. Insert a line before a specific line number
   sed '3i\This is a new line' filename.txt

10. Replace text only within a range of lines
    sed '2,4s/original/replacement/' filename.txt

11. Replace a word only if it is surrounded by word boundaries
    sed 's/\bold\b/new/' filename.txt

12. Print specific lines using sed
    sed -n '2,4p' filename.txt

13. Remove blank lines
    sed '/^$/d' filename.txt

14. Find and replace text using a case-insensitive search
    sed 's/old/new/I' filename.txt

15. Print lines that match a pattern
    sed -n '/pattern/p' filename.txt




