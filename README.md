*Dump out the complete contents of a file with cat like this: cat /var/log/apache2/access.log
*Use less to open the same file, like this: less /var/log/apache2/access.log - and move up and down through the file with your arrow keys, then use “q” to quit.
*Again using less, look at a file, but practice confidently moving around using gg, GG and /, n and N (to go to the top of the file, bottom of the file, to search for something and to hop to the next "hit" or back to the previous one)
*View recent logins and sudo usage by viewing /var/log/auth.log with less
*Look at just the tail end of the file with tail /var/log/apache2/access.log (yes, there's also a head command!)
*Follow a log in real-time with: tail -f /var/log/apache2/access.log (while accessing your server’s web page in a browser)
*You can take the output of one command and "pipe" it in as the input to another by using the | (pipe) symbol
*So, dump out a file with cat, but pipe that output to grep with a search term - like this: cat /var/log/auth.log | grep "authenticating"
*Simplify this to: grep "authenticating" /var/log/auth.log
*Piping allows you to narrow your search, e.g. grep "authenticating" /var/log/auth.log | grep "root"
*Use the cut command to select out most interesting portions of each line by specifying "-d" (delimiter) and "-f" (field) - like: grep "authenticating" /var/log/auth.log| grep "root"| cut -f 10- -d" " (field 10 onwards, where the delimiter between field is the " " character). This approach can be very useful in extracting useful information from log data.
*Use the -v option to invert the selection and find attempts to login with other users: grep "authenticating" /var/log/auth.log| grep -v "root"| cut -f 10- -d" "
