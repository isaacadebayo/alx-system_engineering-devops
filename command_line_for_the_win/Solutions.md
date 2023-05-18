Solutions to the CMD Challenge
1 -> hello_world
Your first challenge is to print "hello world" on the terminal in a single command.
echo 'hello world'
2 -> current_working_directory
Print the current working directory.
pwd
3 -> list_files
List names of all the files in the current directory, one file per line.
find -type f -regex ".*" -printf "%f\n"
4 -> foo
5 -> foo
6 -> foo
7 -> foo
8 -> foo
9 -> foo
10 -> foo
11 -> foo
12 -> foo
13 -> foo
14 -> search_for_files_containing_string
Print all files in the current directory, one per line (not the path, just the filename) that contain the string "500".
grep -sl 500 * .*
15 ->
Print the relative file paths, one path per line for all filenames that start with "access.log" in the current directory.
find -type f -regex '.*/access.log.*'
16 -> search_for_string_in_files_recursive
Print all matching lines (without the filename or the file path) in all files under the current directory that start with "access.log" that contain the string "500".
cat `find -type f -regex '.*/access.log.*' | tr \n ' '` | grep 500
17 -> extract_ip_addresses
Extract all IP addresses from files that start with "access.log" printing one IP address per line.
cat `find -type f -regex '.*/access.log.*' | tr '\n' ' '` | grep -oE '^[0-9]+\.[0-9]+\.[0-9]+\.[0-9]+'
18 -> count_files
Count the number of files in the current working directory. Print the number of files as a single integer.
find -type f -regex '.*' | wc -l
19 -> simple_sort
Print the contents of access.log sorted.
cat access.log | sort
20 -> count_string_in_line
Print the number of lines in access.log that contain the string "GET".
cat access.log | grep -o GET | wc -l
21 -> split_on_a_char
The file split-me.txt contains a list of numbers separated by a ; character.
Split the numbers on the ; character, one number per line.
cat split-me.txt | tr ';' "\n"
22 -> print_number_sequence
Print the numbers 1 to 100 separated by spaces.
echo {1..9} {1..9}{0..9} 100
23 -> replace_text_in_files
This challenge has text files (with a .txt extension) that contain the phrase "challenges are difficult". Delete this phrase from all text files recursively.
Note that some files are in subdirectories so you will need to search for them.
find -type f -regex '.*\.txt' -execdir bash -c 'cat "{}" | sed "s/challenges are difficult//g" > "{}"' \;
24 -> sum_all_numbers
The file sum-me.txt has a list of numbers, one per line. Print the sum of these numbers.
echo $((`cat sum-me.txt | tr '\n' '+' | rev | cut -c 2- | rev`))
25 -> just_the_files
Print all files in the current directory recursively without the leading directory path.
find -type f -regex '.*' -execdir bash -c 'echo {} | cut -c 3-' \;
26 -> remove_extensions_from_files
Rename all files removing the extension from them in the current directory recursively.
find -type f -regex '.*' -execdir bash -c 'mv {} `echo {} | sed -r "s/\.[^.\S]+$//g"`' \;
27 -> replace_spaces_in_filenames
The files in this challenge contain spaces. List all of the files (filenames only) in the current directory but replace all spaces with a '.' character.
find -type f -regex '.*' -execdir bash -c 'echo {} | sed -r "s/\s/./g" | cut -c 3-' \;
28 -> dirs_containing_files_with_extension
In this challenge there are some directories containing files with different extensions. Print all directories, one per line without duplicates that contain one or more files with a ".tf" extension.
find -type f -regex '.*\.tf$' -exec bash -c 'echo {} | grep -oE ".*/" | cut -c 3- | rev | cut -c 2- | rev' \; | sort | uniq
29 -> files_starting_with_a_number
There are a mix of files in this directory that start with letters and numbers. Print the filenames (just the filenames) of all files that start with a number recursively in the current directory.
find -type f -regex ".*" -printf "%f\n" | grep -E "^[0-9]"
30 -> print_nth_line
Print the 25th line of the file faces.txt
head -n 25 faces.txt | tail -n 1
31 -> reverse_readme
Print the lines of the file reverse-me.txt in this directory in reverse line order so that the last line is printed first and the first line is printed last.
cat reverse-me.txt
28 -> foo

