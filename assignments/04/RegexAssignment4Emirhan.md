# Regular Expressions

In the following, you will parse information from text-based files with the command line and Unix tools and Python in the next step. Please note that even though the files are provided as structured csv files you are not supposed to simply read out the columns, but you should use regular expressions instead.

## Parsing contact information from the command line

In this directory, you will find a txt-file called `csv/contacts.csv`. Use regular expressions to extract the following information from it.

Remember that you can use different tools like `grep`, `awk`, or `sed` to use regular expressions from the command line. Pipes might also be helpful. 

You can add your command line in- and outputs directly to this README file. Alternatively, you can write a bash script with all commands and commit it to this directory.

1. Extract all email addresses from the text.
``` 
echo "Email addresses:"
grep -oE "[a-zA-Z0-9._%+-]+@[a-zA-Z0-9.-]+\.[a-zA-Z]{2,}" "$FILE"
``` 
2. Extract all phone numbers from the text.
``` 
grep -oE "\(555\) [0-9]{3}-[0-9]{4}" "$FILE"
``` 
3. Extract all names that start with the letter ‘J’.
``` 
awk '$1 ~ /^J/' "$FILE" | awk '{print $1, $2}'
``` 
4. Extract all street names that contain the word 'St'.
``` 
grep -oE "[0-9]+ [A-Za-z ]*St" "$FILE"
``` 
5. Extract all addresses in ‘USA’.
``` 
grep "USA" "$FILE"
``` 
6. Extract the last names of all people.
``` 
awk '{print $2}' "$FILE"
``` 
7. Extract all email domains (part after the @ sign).
``` 
awk -F'@' '{print $2}' "$FILE" | sort | uniq
``` 
8.	Extract all instances of the first name ‘David’ along with their full address (street and city).
``` 
grep "^David" "$FILE"
``` 
9.	Find all entries where the phone number ends with ‘7’.
``` 
grep -oE "\(555\) [0-9]{3}-[0-9]{3}7" "$FILE"
``` 
10.	Extract all instances of first names that end with the letter 'e'.
``` 
awk '$1 ~ /e$/' "$FILE" | awk '{print $1}'
``` 
