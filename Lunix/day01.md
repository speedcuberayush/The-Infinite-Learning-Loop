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


    ✅ 10. cp (Copy) : (cp [SOURCE] [DESTINATION]) [-r, -i, -f, -p(org time, owner), [* → all files, ? → single character, [] → specific characters]]
    ✅ 11. mv (Move) : (mv source destination, -t(destination first), [-i → ask before overwrite, -b → create backup (file~), -v → show what’s happening])
            ✅ mv file.txt dir/ 
            ✅ mv file1.txt file2.txt dir/ 
            ✅ mv old.txt new.txt 
            ✅ mv dir1 dir2 
            mv -i file.txt dir/ 
            mv -f file.txt dir/ 
            mv -v file.txt dir/ 
            mv -b file.txt dir/ 
            ✅ mv -t dir file1 file2 file3

        
    ✅ 12. mkdir (Make Directory, mkdir fld1 , mkdir fld1 fld2 fld3 ... , mkdir fld1/fld2/fld3)
    ✅ 13. rm (Remove) : (rm file.txt, [-f, -i, -r, -rf, rmdir folder/])
            ✅ rm [OPTIONS] FILE
            ✅ rm file.txt (Deletes the file permanently (no recycle bin))
            ✅ rm file1.txt file2.txt file3.txt (Remove multiple files)
            ✅ rm *.txt (Remove using wildcards) , ✅ rm file?.txt ()
            ✅ rm -r dir (Remove directories)
            ✅ rm -i file.txt (interactive)
            ✅ rm -f file.txt (force)
            ✅ rm -r dir (Delete directories + contents)
            ✅ rm -iv file.txt  (shows what is deleted, asks confirmation)
            ✅ rm -rf dir (deletes everything inside immediately)

    14. find (find [path] [condition], [-name , type -d, type -f])
    15. help (help command(inbuilt), --help(executables))
    16. man (manual man command)
    17. whatis (short desc)
    18. alias 
        - temporary alias ll='ls -la',unalias ll 
        - permanent nano ~/.bashrc, alias ll='ls -la'
          alias update='sudo apt update && sudo apt upgrade'
          source ~/.bashrc

    ✅ 19. exit (Ends the shell → returns to previous shell or closes terminal, logout → also exits (mainly for login shells))
