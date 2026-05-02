    ✅ 14. find (find [path] [condition], [-name , type -d, type -f])
            
            find [path/(s)] [options/conditions]
            <!-- 📁 Basic -->
            ✅ find .                      # search in current directory
            ✅ find /home                  # search in /home
            ✅ find d1 d2                  # search in multiple directories

            <!-- 🔍 Name & Pattern -->
            ✅ find . -name "*.txt"        # find files with .txt extension (case-sensitive)
            ✅ find . -iname "*.txt"       # case-insensitive search
            ✅ find . -name "file.txt"     # exact file name

            <!-- 📂 Type -->
            ✅ find . -type f              # only files
            ✅ find . -type d              # only directories
            ✅ find . -type l              # symbolic links

            <!-- 🔗 Combine Conditions -->
            ✅ find . -type f -name "*.txt"     # files AND .txt
            ✅ find . -name "*.txt" -o -name "*.md"   # OR condition
            ✅ find . \( -name "*.txt" -o -name "*.md" \)   # proper OR usage
            ✅ find . -not -name "*.txt"        # NOT condition

            <!-- 📏 Size -->
            ✅ find . -size +1M           # greater than 1 MB
            ✅ find . -size -100k         # less than 100 KB
            ✅ find . -size 50k           # exactly 50 KB

            <!-- ⏱️ Time -->
            ✅ find . -mtime -1           # modified in last 1 day
            ✅ find . -mtime +7           # modified more than 7 days ago
            ✅ find . -atime -2           # accessed in last 2 days
            ✅ find . -ctime -3           # changed in last 3 days

            <!-- 📋 Depth Control -->
            ✅ find . -maxdepth 1         # current directory only
            ✅ find . -mindepth 2         # skip top levels

            <!-- ⚡ Execute Commands -->
            ✅ find . -name "*.txt" -exec rm {} \;     # delete files
            ✅ find . -name "*.txt" -exec cat {} \;    # print content
            ✅ find . -name "*.txt" -exec rm {} +      # faster delete

            <!-- 🧪 Useful Conditions -->
            ✅ find . -empty              # empty files & directories
            ✅ find . -type f -empty      # empty files only
            ✅ find . -readable           # readable files
            ✅ find . -writable           # writable files
            ✅ find . -executable         # executable files

            <!-- 👤 User / Permission -->
            find . -user root          # files owned by user root
            find . -perm 777           # exact permission
            find . -perm -644          # at least these permissions

            <!-- 🔎 Search in Specific Directories -->
            ✅ find d[1-3] -name "*.txt"   # inside d1, d2, d3
            ✅ find /var/log -name "*.log" # logs

            <!-- 📌 Print / Output -->
            ✅ find . -print              # print results (default)
            ✅ find . -name "*.txt" -ls   # detailed listing


    ✅ 15. help (help command(inbuilt), --help(executables))
    ✅ 16. man (manual man command)
    ✅ 17. whatis (short desc)
    ✅ 18. alias 
        ✅ - temporary alias ll='ls -la',unalias ll 
        ✅ - permanent nano ~/.bashrc, alias ll='ls -la'
        ✅   alias update='sudo apt update && sudo apt upgrade'
             source ~/.bashrc

-Text-Fu
    ✅ 1. stdout (Standard Out) 
       ✅  - echo Hello World
       ✅  - echo Hello World > file.txt (overwrite)
       ✅  - echo Hello World >> file.txt (append)

    ✅ 2. stdin (Standard In)
        ✅ - cat < file.txt ( read from file)
        ✅ - cat < f1.txt > f2.txt (read from f1 write f2)

    3. stderr (Standard Error)
        - ls /fake > out.txt
        - File Descriptors (important)
            0 → stdin, 1 → stdout, 2 → stderr
            ls /fake 2> err.txt
            ls /fake /etc/passwd > all.txt 2>&1 = ls /fake /etc/passwd &> all.txt
            ls /fake 2> /dev/null

    ✅ 4. pipe (|) : Takes output of one command → sends as input to another  : output → pipe → next command
                - ls | less
                    ls → produces output
                    | → passes it
                    less → displays it nicely
                - ls | grep ".txt"

       ✅  tee :  Splits output into TWO places (screen, file) : show + save
                - ls | tee file.txt (shows output on screen, saves same output in file.txt)
                - ls | tee file.txt | grep ".txt" (ls → list files, tee → save + pass forward, grep → filter)
                  ls → | → tee → | → grep
                            ↓
                        file.txt
