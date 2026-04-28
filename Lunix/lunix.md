-Getting Started
    ✅ 1. Linux History
            UNIX = original recipe 🍲
            macOS = premium restaurant version 🍽️
            Linux = open-source DIY version 🧑‍🍳
            Windows = completely different cuisine 🍔
            Linux = UNIX-like + open source + customizable

    ✅ 2. Choosing a Linux Distribution    
            A distro = Linux kernel + tools + UI
            - Beginner Friendly : Ubuntu, Linux Mint
            - Stable / Enterprise : Debian, Red Hat Enterprise Linux (RHEL)
            - Cutting Edge : Fedora, 
            - Advanced / DIY : Arch Linux, Gentoo
            - Security / Hacking : Kali Linux, Parrot OS
            - Balanced : openSUSE

-Command Line
    ✅  1. The Shell
            - Shell = messenger 📩
            - You → type command
            - Shell → tells OS
            - OS → does the work

            - $ → normal user
            - # → root (admin)
            
            - structure : command_name option argument
            
    ✅  2. pwd (Print Working Directory)
    ✅  3. cd (Change Directory) : (., .., ~, -)
    ✅  4. ls (List Directories) list files
            ✅ -a → hidden files
            ✅ -l → detailed view
            ✅ -h → human-readable sizes
            ✅ -r → reverse
            ✅ -t → sort by time
            ✅ -S → sort by size
            ✅ -R → recursive

    <!-- File Handling -->
    ✅  5. touch → create empty file / update timestamp [-a, -m, -t, -d]  [-c, -r]
            ✅-a access time
            ✅-m modify time

    ✅ 6. file → detect file type
    ✅ 7. cat → display file content , cat > file.txt → create & write, -n number lines [-n,-b]
    ✅ 8. less → view large files efficiently 👉 doesn’t load full file (better than cat)
    ✅ 9. history [-c clear,-w,-d delete entry] (!5 -> cmd no. 5)


    10. cp (Copy) : (cp [SOURCE] [DESTINATION]) [-r, -i, -f, -p(org time, owner), [* → all files, ? → single character, [] → specific characters]]
    11. mv (Move) : (mv source destination, -t(destination first), [-i → ask before overwrite, -b → create backup (file~), -v → show what’s happening])
    12. mkdir (Make Directory, mkdir fld1 , mkdir fld1 fld2 fld3 ... , mkdir fld1/fld2/fld3)
    13. rm (Remove) : (rm file.txt, [-f, -i, -r, -rf, rmdir folder/])
    14. find (find [path] [condition], [-name , type -d, type -f])
    15. help (help command(inbuilt), --help(executables))
    16. man (manual man command)
    17. whatis (short desc)
    18. alias 
        - temporary alias ll='ls -la',unalias ll 
        - permanent nano ~/.bashrc, alias ll='ls -la'
          alias update='sudo apt update && sudo apt upgrade'
          source ~/.bashrc

    19. exit (Ends the shell → returns to previous shell or closes terminal, logout → also exits (mainly for login shells))


-Text-Fu
    1. stdout (Standard Out) 
        - echo Hello World
        - echo Hello World > file.txt (overwrite)
        - echo Hello World >> file.txt (append)

    2. stdin (Standard In)
        - cat < file.txt ( read from file)
        - cat < f1.txt > f2.txt (read from f1 write f2)

    3. stderr (Standard Error)
        - ls /fake > out.txt
        - File Descriptors (important)
            0 → stdin, 1 → stdout, 2 → stderr
            ls /fake 2> err.txt
            ls /fake /etc/passwd > all.txt 2>&1 = ls /fake /etc/passwd &> all.txt
            ls /fake 2> /dev/null
        

    4. pipe (|) : Takes output of one command → sends as input to another  : output → pipe → next command
                - ls | less
                    ls → produces output
                    | → passes it
                    less → displays it nicely
                - ls | grep ".txt"

       tee :  Splits output into TWO places (screen, file) : show + save
                - ls | tee file.txt (shows output on screen, saves same output in file.txt)
                - ls | tee file.txt | grep ".txt" (ls → list files, tee → save + pass forward, grep → filter)
                  ls → | → tee → | → grep
                            ↓
                        file.txt
                        
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

    6. cut : slice text
        cut [option] file.txt
            cut -c 1-5 file.txt        # first 5 characters
            cut -f 2 data.txt          # second column (TAB)
            cut -f 1 -d "," data.csv   # first column (CSV)

    7. paste : Merges lines together 
        paste = join lines
        -s = make single line
        -d = choose separator  

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
            - grep fox file.txt
            - Ignore case : grep -i fox file.txt > Matches FOX, Fox, fox
            - Count matches : grep -c fox file.txt > Number of matching lines
            - Show only match : grep -o fox file.txt > Prints only the word “fox”
            - Use pattern starting with '-' : grep -e "-v" file.txt 
            - Multiple patterns : grep -f patterns.txt file.txt   


                    <!-- grep error log.txt        # find errors -->
                    <!-- grep -i user file.txt     # ignore case -->
                    <!-- env | grep USER           # Search inside output of another command -->

-Advanced Text-Fu
    1. regex (Regular Expressions):
        ^ , start of line
        $ , end of line
            grep "^Error" file.txt   # starts with Error
            grep "done$" file.txt    # ends with done

        🔤 Basic Matching
            . , any one character
            * , 0 or more of previous
            + , 1 or more of previous
                grep "c.t" file.txt   # cat, cot
                grep "lo*" file.txt   # l, lo, loo...
                grep "lo+" file.txt   # lo, loo...

        🧱 Character Sets
            [abc]	a OR b OR c
            [a-z]	lowercase letters
            [0-9]	digits
                grep "[0-9]" file.txt   # lines with numbers
                grep "[a-z]" file.txt   # lowercase letters

        🚫 Negation
            [^abc]	NOT a, b, c
                grep "[^0-9]" file.txt   # lines with non-digits

        🔁 Common Combos
                grep "^a.*z$" file.txt # starts with a, ends with z
                grep "^[0-9]" file.txt # lines starting with number
                grep "\.txt$" file.txt # ends with .txt

    2. Text Editors : Vim , Emacs
    
    3. Vim (Vi Improved) : 
                - Terminal-based text editor
                - Works without mouse
                - Fast + available everywhere

                vim file.txt
                    📌 Forward search : /word
                    📌 Backward search : ?word
                    🔁 Move between results : n → next, N → previous
                    h -> left, l -> right, j -> down, k -> up
                    i -> insert before cursor, a ->	insert after cursor, I -> start of line, A -> end of line
                    o -> new line below, O -> new line above

                    x -> delete char, dw ->	delete word, dd -> delete line,3dd -> delete 3 lines
                    cw -> change word, cc -> change line

                    yy -> copy line, p -> paste after, P -> paste before
                    u -> undo, Ctrl + r -> redo, . -> repeat last action, J->join lines

                    Commands (press : first)
                    :w -> save, :q -> quit, :q! -> force quit, :wq -> save + quit
                    ZZ : save + quit
                    Esc → command mode, i → type, :wq → save & exit
                    Esc = go back to Normal mode (important)
                    Commands like :wq only work in Normal mode
                    Everything depends on mode switching

                👉 Vim has modes: Normal → commands, Insert → typing
    
    
    9. Emacs
    
    10. Emacs Manipulate Files
    
    11. Emac Buffer Navigation
    
    12. Emacs Editing
    
    13. Emacs Exiting and Help


-User Management
    1. Users and Groups
    2. root
    3. /etc/passwd
    4. /etc/shadow
    5. /etc/group
    6. User Management Tools

-Permissions
    1. File Permissions
    2. Modifying Permissions
    3. Ownership Permissions
    4. Umask
    5. Setuid
    6. Setgid
    7. Process Permissions
    8. The Sticky Bit

<!-- ---------------------------- -->

-Processes
    1. ps (Processes)
    2. Controlling Terminal
    3. Process Details
    4. Process Creation
    5. Process Termination
    6. Signals
    7. kill (Terminate)
    8. niceness
    9. Process States
    10. /proc filesystem
    11. Job Control

-Packages
    1. Software Distribution
    2. Package Repositories
    3. tar and gzip
    4. Package Dependencies
    5. rpm and dpkg
    6. yum and apt
    7. Compile Source Code


-Devices
    1. /dev directory
    2. device types
    3. Device Names
    4. sysfs
    5. udev
    6. lsusb, lspci, lsscsi
    7. dd

-The Filesystem
    1. Filesystem Hierarchy
    2. Filesystem Types
    3. Anatomy of a Disk
    4. Disk Partitioning
    5. Creating Filesystems
    6. mount and umount
    7. /etc/fstab
    8. swap
    9. Disk Usage
    10. Filesystem Repair
    11. Inodes
    12. symlinks

-Boot the System
    1. Boot Process Overview
    2. Boot Process: BIOS
    3. Boot Process: Bootloader
    4. Boot Process: Kernel
    5. Boot Process: Init

-Kernel
    1. Overview of the Kernel
    2. Privilege Levels
    3. System Calls
    4. Kernel Installation
    5. Kernel Location
    6. Kernel Modules

-Init
    1. System V Overview
    2. System V Service
    3. Upstart Overview
    4. Upstart Jobs
    5. Systemd Overview
    6. Systemd Goals
    7. Power States

-Process Utilization
    1. Tracking processes: top
    2. lsof and fuser
    3. Process Threads
    4. CPU Monitoring
    5. I/O Monitoring
    6. Memory Monitoring
    7. Continuous Monitoring
    8. Cron Jobs

-Logging
    1. System Logging
    2. syslog
    3. General Logging
    4. Kernel Logging
    5. Authentication Logging
    6. Managing Log Files

<!-- NETWORKING -->
-Network Sharing
    1. File Sharing Overview
    2. rsync
    3. Simple HTTP Server
    4. NFS
    5. Samba

-Network Basics
    1. Network Basics
    2. OSI Model
    3. TCP/IP Model
    4. Network Addressing
    5. Application Layer
    6. Transport Layer
    7. Network Layer
    8. Link Layer
    9. DHCP Overview

-Subnetting
    1. IPv4
    2. Subnets
    3. Subnet Math
    4. Subnetting Cheats
    5. CIDR
    6. NAT
    7. IPv6

-Routing
    1. What is a router?
    2. Routing Table
    3. Path of a Packet
    4. Routing Protocols
    5. Distance Vector Protocols
    6. Link State Protocols
    7. Border Gateway Protocol

-Network Config
    1. Network Interfaces
    2. route
    3. dhclient
    4. Network Manager
    5. arp

-Troubleshooting
    1. ICMP
    2. ping
    3. traceroute
    4. netstat
    5. Packet Analysis

-DNS
    1. What is DNS?
    2. DNS Components
    3. DNS Process
    4. /etc/hosts
    5. DNS Setup
    6. DNS Tools
