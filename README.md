# Linux-Monitoring-Script

 Part A is focused on process monitoring and tracking the resource utilisation of every user. Part B is focused on file monitoring and tracking the permissions and number of files opened by each user. Each part addresses a critical part of system security and the two work together to give a holistic solution. Together these scripts offer a framework for improving security by giving admins extra visibility into their linux systems, aiding them in preventing potential threats.


Part A: Process monitoring:
This script was developed to provide a detailed report of resource utilisation sorted per user. It aggregates data across processes belonging to the user, and outputs an overview of cpu utilisation, memory consumption and the number of open files. This allows for admins to see resource intensive users. To achieve this the script uses linux commands like ps to loop through all the users currently with a process active on the linux system. Awk is used to get the cpu time rather than percentage and to convert the memory used by each user from KB to MB. Grep is used to find the number of files opened by each user along with wc -l to actually count each file as one per line.

Part B File monitoring:


This script was developed to monitor the issue of file permissions for individual users. It works by identifying files with specific permissions that may pose a risk. By numbering the amount of Setuid/Setgid permissions and world writable files per user, the script allows admins to have a comprehensive view of potential security flaws. The users are looped through and the find command is used along with the -perm option to find setgid and setuid files. Permission 4000 returns all setuid files while permission 2000 returns all setgid files, in order to not overwhelm the admin all error codes are sent to /dev/null and are not printed in the terminal.
