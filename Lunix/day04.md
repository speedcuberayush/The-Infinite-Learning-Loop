    5. env (Environment)
            = env → shows variables
            = export → creates variables
            echo $HOME
            echo $USER
            env

            export TEST=hello, echo $TEST

            nano ~/.bashrc
            export TEST=hello
            source ~/.bashrc

        env = displays all environment variables, Used to run programs with modified environment
        What are Environment Variables? Key-value pairs used by shell/programs -> KEY=value

        env              # all variables
        printenv         # similar
        echo $HOME       # specific variable

        1. Shell variable (local) : TEST=hello
        2. Environment variable (exported) : export TEST=hello
        Remove Variable : unset TEST

        Run Command with Temporary Variable
        TEST=hello env
        TEST=hello bash


    6. cut : slice text
        cut [option] file.txt
        
            cut -c 1-5 file.txt        # first 5 characters
            cut -f 2 data.txt          # second column (TAB)
            cut -f 1 -d "," data.csv   # first column (CSV)


            1. Character-Based Extraction (-c) : Extract specific character positions from each line.
                cut -c 1-5 file.txt      # First 5 characters
                cut -c 3 file.txt        # Only 3rd character
                cut -c 1,3,5 file.txt    # Characters 1, 3, and 5
                cut -c 2- file.txt       # From 2nd character to end

            2. Byte-Based Extraction (-b) : Works like -c but operates on bytes.
                cut -b 1-5 file.txt

            3. Field-Based Extraction (-f) : Used for extracting columns (fields).
                👉 Default delimiter = TAB
                cut -f 2 data.txt        # Second column (TAB-separated)


            4. Custom Delimiter (-d) : Specify a delimiter (useful for CSV files).
                cut -d "," -f 1 data.csv   # First column (CSV)
                cut -d "," -f 2,3 data.csv # Columns 2 and 3
                cut -d "," -f 2-4 data.csv # Columns 2 to 4

            5. Ignore Lines Without Delimiter (-s) : cut -d "," -f 2 -s file.txt
            👉 Skips lines that don’t contain the delimiter.

            6. Change Output Delimiter : cut -d "," -f 1,2 --output-delimiter=" | " data.csv

            7. Using with Pipes : cat data.csv | cut -d "," -f 2 👉 Better: cut -d "," -f 2 data.csv
            
            Real-World Examples
                Extract usernames: cut -d ":" -f 1 /etc/passwd
                Extract email domains: cut -d "@" -f 2 emails.txt
                Extract first column: cut -d "," -f 1 file.csv
            
            Works only with fixed delimiters, Not ideal for irregular spacing

            👉 Alternatives: awk, sed



    7. paste : The paste command in Linux is used to merge lines from files side by side (horizontally).
        -s = make single line
        -d = choose separator  

        paste [OPTION] [FILE...] , If no file is provided, it reads from standard input.


        Basic Usage : paste file1.txt file2.txt

        👉 Merges lines:
                file1:    A        B        C
                file2:    1        2        3

                Output:
                A    1
                B    2
                C    3

                (Default separator = TAB)

                🔹 1. Single Line Mode (-s) : Combine all lines into one line => paste -s file.txt , A    B    C
                🔹 2. Custom Delimiter (-d) : Choose your own separator instead of TAB. => paste -d "," file1.txt file2.txt
                                A,1
                                B,2
                                C,3

                🔹 Multiple Delimiters : paste -d ",:" file1.txt file2.txt 👉 Uses delimiters in sequence (, then : then repeat)

                🔹 Combine -s and -d : paste -s -d "," file.txt 👉 Converts lines into CSV format: A,B,C
                🔹 Real-Life Examples 
                        Merge two columns into one file: paste names.txt marks.txt
                        Convert rows to single comma-separated line: paste -s -d "," list.txt
                        Join multiple files: paste file1.txt file2.txt file3.txt

    8. head : Shows beginning of a file
            head file.txt            → first 10 lines
            head -n 15 file.txt      → Shows first 15 lines

    9. tail : Shows end of a file
            tail file.txt            → last 10 lines
            tail -n 20 file.txt      → Shows last 20 lines
            tail -f file.txt  ( -f = follow live )

    10. expand : Converts TAB → spaces
            expand file.txt
            expand file.txt > new.txt

        unexpand : Converts spaces → TAB
            unexpand file.txt
            unexpand -a file.txt

    11. join : Combines two files based on a common field (column)
            join file1.txt file2.txt
            join -1 2 -2 1 file1.txt file2.txt
                            -1 2 → use column 2 of file1
                            -2 1 → use column 1 of file2
        
        split : Breaks large file into smaller files
            split file.txt
            split -l 100 file.txt (Each file → 100 lines)
            split -b 1M file.txt (Each file → 1MB)

    12. sort : Sorts lines in a file
                - sort names.txt          # A-Z
                - sort -r names.txt       # Z-A
                - sort -n numbers.txt     # numeric sort

    13. tr (Translate) : Changes / deletes characters, Works with stdin (input stream)
                - echo "hello world" | tr a-z A-Z
                - echo "abc123" | tr -d '0-9'           : -d → delete chars
                - echo "Hello     World" | tr -s ' '    : -s → remove duplicates

    14. uniq (Unique) : Removes duplicate lines (works only if duplicates are together)
            - uniq file.txt
            - sort file.txt | uniq ( Now duplicates come together → removed )
            - uniq -c file.txt (count duplicates)
            - uniq -u file.txt (Shows lines that appear once)
            - uniq -d file.txt (Shows repeated lines only)

    15. wc : word count  - Counts lines, words, bytes
            - wc file.txt [lines  words  bytes  filename]
            Specific counts
                - wc -l file.txt   # lines
                - wc -w file.txt   # words
                - wc -c file.txt   # bytes


        nl : number lines - Adds line numbers to text
            - nl file.txt

    16. grep : Searches for text (pattern) in files -> filter lines containing something : grep = search + filter text
               grep [OPTION] PATTERN FILE
            - grep fox file.txt
            - Ignore case : grep -i fox file.txt > Matches FOX, Fox, fox
            - Count matches : grep -c fox file.txt > Number of matching lines
            - Show only match : grep -o fox file.txt > Prints only the word “fox”
            - Use pattern starting with '-' : grep -e "-v" file.txt 
            - Multiple patterns : grep -f patterns.txt file.txt   


                    <!-- grep error log.txt        # find errors -->
                    <!-- grep -i user file.txt     # ignore case -->
                    <!-- env | grep USER           # Search inside output of another command -->