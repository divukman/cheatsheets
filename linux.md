# Linux Cheat-sheet

* Find text including subdirectories
    ```
	grep -rl "string" /path
	-r (or --recursive)     
	-l (or --files-with-matches) 
    ```

    ```
	grep -Hrn 'search term' path/to/files
	-H causes the filename to be printed (implied when multiple files are searched)
	-r does a recursive search
	-n causes the line number to be printed
    ```

* Replace a string in multiple files in linux command line
    ```
	cd /path/to/your/folder
    sed -i 's/foo/bar/g' *
    - Occurrences of "foo" will be replaced with "bar"
    ```
    
    ```
    find . -type f -exec sed -i 's/from/to/' {} \;
    ```
