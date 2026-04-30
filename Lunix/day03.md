chmod = change file mode (permissions) , Controls who can read, write, execute a file/directory

Users: u → user (owner), g → group, o → others, a → all (u+g+o)
Permissions: r = read (4), w = write (2), x = execute (1)

Syntax: chmod [who][operator][permission] file (+ → add , - → remove, = → set exact)

Directory meaning: r → list , w → create/delete, x → enter

Check: ls -l

Recursive: chmod -R 755 dir

Special permissions:
SUID (4) → chmod 4755
SGID (2) → chmod 2755
Sticky (1) → chmod 1777

umask → default permissions
