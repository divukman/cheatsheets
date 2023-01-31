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
## Systemd

* List all loaded systemd units
  ```
  systemctl
  ```

* List all loaded services
  ```
  systemctl --type=service
  ```

* List all loaded active services
  ```
  systemctl list-units --type=service --state=active
  ```

* List all loaded running services
  ```
  systemctl --type=service --state=running
  ```



# Ranger: 
- [Arch Linux wiki] (https://wiki.archlinux.org/title/ranger#Hidden_files)

* Copy config files
    ```
	ranger --copy-config=all 
    ```

* Drop to command line (opens shell on the current directory) 
    ```
	Shift + S
    ```

* Return to Ranger: 
    ```
	Ctrl + D
    ```

* Show hidden files:

    ```
	rc.conf
	---
	set show_hidden true
    ```

    ```
	:set show_hidden!
	:set show_hidden true
    ```
    
#VIM
- View available color schemes, start VIM and type:
    ```
	:colorscheme + space + tab
    ```
To make permanent change, update .vimrc (~/.vimrc, /etc/vim/vimrc), add line colorscheme <theme>:
    ```
	colorscheme morning
    ```


# Links

## VIM Plugins

 | PLUGIN      | URL                                          |
 | --------    | -----------------------------------------    |
 | NERDTree    | https://github.com/preservim/nerdtree        |
 | CtrlP.vim   | https://github.com/ctrlpvim/ctrlp.vim        |
 | Tabular"    | https://github.com/godlygeek/tabular         |
 | Easy-motion | https://github.com/easymotion/vim-easymotion |
 | Fugitive    | https://github.com/tpope/vim-fugitive        |
 | indentLine  | https://github.com/Yggdroot/indentLine       |
 | ale	       | https://github.com/dense-analysis/ale	      |
