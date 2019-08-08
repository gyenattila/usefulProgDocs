# Content
1. [File Systme Management](#fileSystemManagement)
2. [Keyboard Control](#keyboardControl)
3. [Unix / Linux Tutorial](#unixLinuxTutorial)
	1. [What's Unix](#whatIsUnix)
	2. [Unix Files](#unixFiles)
	3. [Listing Directories, Files and Processes](#listingDirectoriesFilesAndProcesses)
		1. [Listing Directories and Files](#listingDirectoriesAndFiles) 
		2. [Prefix and Description](#prefixAndDescription)
		3. [More Listing Option](#moreListingOption)
		4. [Listing Processes](#listingProcesses)
	4. [Who Are You](#whoAreYou)
	5. [Who is Logged In](#whoIsLoggedIn)
	6. [Metacharacters - Shell Wildcards](#metacharactersShellWildcards)
	7. [Hidden Files](#hiddenFiles)
	8. [Creating Files](#creatingFiles)
	9. [Display Content of a File](#displayContentOfAFile)
		1. [Displaying Parts of Files](#displayingPartsOfFiles)
	10. [Searching Files](#searchingFiles)
	11. [Translating Characters](#translatingCharacters)
	12. [Sorting Files](#sortingFiles)
	13. [Comparing Files](#comparingFiles)
	14. [Cutting Fields](#cuttingFields)
	15. [Counting Words in a File](#countingWordsInAFile)
	16. [Pasting Files](#pastingFiles)
	17. [Duplicate Lines](#duplicateLines)
	18. [Non ASCII Files](#nonASCIIFiles)
	19. [Deleting Files](#deletingFiles)
	20. [Copying Files](#copyingFiles)
	21. [Moving / Deleting Files](#movingDeletingFiles)
	22. [Linking Files](#linkingFiles)
		1. [Hard Links](#hardLinks)
		2. [Symbolic Links](#symbolicLinks)
	23. [Standard Unix Streams](#standardUnixStreams)
	24. [Home Directory](#homeDirectory)
	25. [Absolute / Relative Pathnames](#AbsoluteAndRelativePathnames)
	26. [Listing Directories .(dot) and .. (dotdot)](#listingDirectoriesDotAndDotdot)
	27. [Listing Directories](#listingDirectories)
	28. [Creating Directories](#creatingDirectories)
	29. [Removing Directories](#removingDirectories)
	30. [Changing Directories](#changingDirectories)
	31. [Renaming Directories](#renamingDirectories)
	32. [Permission Bits](#permissionBits)
	33. [Sticky Bit](#stickyBit)
	34. [Setting Permissions](#settingPermissions)
		1. [Symbolic Notation](#symbolicNotation)
		2. [Numeric Notation](#numericNotation) 
	35. [Default Permissions](#defaultPermissions)
	36. [Command Pipelines](#commandPipelines)
	37. [Composing Commands](#composingCommands)
4. [Foreground and Background Jobs](#foregroundAndBackgorundJobs)
	1. [Job Numbers](#jobNumbers)

<div style="page-break-after: always;"></div>

<a name="fileSystemManagement"></a>
# File System Management

First of all some useful command (described later) -

1. ```mkdir``` - create a directory
2. ```rmdir``` - delete a directory
2. ```ls```    - list files/directories in current directory
3. ```cd```    - change directory
4. ```cp```    - copy a file
5. ```cat```   - examine the contents of the file
6. ```rm```    - delete a file

<a name="keyboardControl"></a>
# Keyboard Control

Essential control signals

```
^C - interrupt command
^Z - suspend command
^D - end of file
^H - (^?) [DELETE] - delete last character
^W - delete last word
^U - delete line 
^S - suspend output (rarely used)
^Q - continue output (rarely used)
```

<div style="page-break-after: always"></div>

<a name="unixLinuxTutorial"></a>
# Unix / Linux Tutorial


<a name="whatIsUnix"></a>
## What's Unix?


The Unix operating system is a set of programs that act as a link between the computer and the user.

The computer programs that allocate the system resources and coordinate all the details of the computer's internals is called __operating system__ or the __kernel__.

Users communicate with the kernel trough a program know as the __shell__. The shell is a command line interpreter; it translates commands entered by the user and converts them into a language that is understood by the kernel.


<a name="unixFiles"></a>
## Unix Files

Files are stored within the Unix file system and contain __streams of bytes__ without structure. Files may contain _data_, _text_ or _executable_. Most Unix systems allow up to _256_ characters to be used in a filename.


<a name="listingDirectoriesFilesAndProcesses"></a>
## Listing Directories, Files and Processes


All data in Unix is organized into files and all files are organized into directories. These directories are organized into a _tree-like structure_ called the _filesystem_. Starting from an initial top-level ( _root_ ) directory sub-directories successively organise information into categories, and then sub-categories.


Every Unix system are setup with an _on-line_ manual. To use it type in your terminal the following command -

```
$ man nameOfTheCommand
```

The ```man``` provides a means of determining how commands works (not very useful if the user is unsure of the command's name). You can achieve this using the ```-k``` option -

```
$ man -k nameOfTheCommand
```

<div style="page-break-after: always;"></div>

<a name="listingDirectoriesAndFiles"></a>
### Listing Directories and Files

To list the files and directories in the current directory, use the following command - 

```
$ ls
```

here is the sample output of the above command - 

```
$ ls
bin     hosts   lib       res.03
docs    hw3     res.02    work
```

The ```ls``` command supports the ```-l``` option which would help you to get more information about the listed files - 

```
$ ls -l
total 2
drwxrwxr-x 2 JackSparrow JackSparrow  4096 Dec 23 09:59 uml
```

__The information about the listed columns__
  
1. column - represents the __file type__ and the permission given on the file.
2. column - represents the __number of memory blocks__ taken by the file or directory.
3. column - represents the __owner of the file__. The Unix user who created the file.
4. column - represents the __group of the owner__. Every Unix user will have an associated group.
5. column - represents the __file size in bytes__.
6. column - represents the __date and the time when this file was created or modified__ for the last time.
7. column - represents the __file or the directory name__.


<a name="prefixAndDescription"></a>
### Prefix & Description

1. __-__ -> regular file, such an ASCII text
2. __b__ -> block special file. Block I/O device file such as a physical hard drive.
3. __c__ -> character special file. Raw I/O device file such as a physical hard drive.
4. __d__ -> directory file that contains a listing of other files and directories.
5. __p__ -> named pipe. A mechanism for interprocess communications.
6. __s__ -> socket used for interprocess communication.
7. __l__ -> symbolic link file. Links on any regular file.

<a name="moreListingOption"></a>
### More Listing Options

<table>
	<tr>
    <th>Option</th>
    <th>Description</th> 
  </tr>
  <tr>
    <td>ls -a</td>
    <td>list all files including hidden files starting with '.'</td> 
  </tr>
  <tr>
    <td>ls -A</td>
    <td>list almost all files including hidden files starting with '.', <b>except the single '.' and '..'</b></td> 
  </tr>
  <tr>
    <td>ls -d</td>
    <td>the directory file not its contents</td> 
  </tr>
  <tr>
    <td>ls -F</td>
    <td>show file type</td> 
  </tr>
  <tr>
    <td>ls -i</td>
    <td>list files i-node index number</td> 
  </tr>
  <tr>
    <td>ls -l</td>
    <td>list with long format - shows permissions</td> 
  </tr>
  <tr>
    <td>ls -la</td>
    <td>list long format including hidden files</td> 
  </tr>
  <tr>
    <td>ls -lh</td>
    <td>list long format with readable file size</td> 
  </tr>
  <tr>
    <td>ls -ls</td>
    <td>list with long format with file size</td> 
  </tr>
  <tr>
    <td>ls -r</td>
    <td>list in reverse order</td> 
  </tr>
  <tr>
    <td>ls -R</td>
    <td>list recursively directory tree</td> 
  </tr>
  <tr>
    <td>ls -s</td>
    <td>list file size</td> 
  </tr>
  <tr>
    <td>ls -S</td>
    <td>sort by file size in ascending order</td> 
  </tr>
  <tr>
    <td>ls -t</td>
    <td>sort by time & date</td> 
  </tr>
  <tr>
    <td>ls -X</td>
    <td>sort by extension name</td> 
  </tr>
    <tr>
    <td>ls -g</td>
    <td>used with -l for group ownership</td> 
  </tr>
</table>

<div style="page-break-after: always;"></div>

<a name="listingProcesses"></a>
### Listing Processes

To list out processes use ```ps``` command -

```
$ ps
```

To see more information about the processes use ```ps -f``` instead of simple ```ps``` command- 

```
$ ps -f
```

Using the ```-u uid``` (own user ID) option it displays all processes owned by the user. Using the ```ps -ef``` options displays all processes on the system. In order to see the size of all programs, use ```ps -ely``` (```ps -el``` on macOS).

```
$ ps -e
```

Running ```ps``` with the ```-e``` option will show you all of the active processes on the system, regardless of who their owner is. Since there are usually a large number of active system processes, it is wise to pipe the results of this command to the more command.

You can use the ```-f``` and ```-e``` options together.


<a name="whoAreYou"></a>
## Who Are You

While logged into the system, you might be willing to know __Who am I__? 

The easiest way to find out "_whou you are_" is to enter the ```whoami``` command - 

```
$ whoami
JackSparrow
```

Basically ```who``` is a function which takes 2 arguments. The ```am``` and the ```I```.


<a name="whoIsLoggedIn"></a>
## Who is Logged in?


There are three commands available to get you know who is loggen into the system, based on how much you wish to know about the other users:

1. ```users```
2. ```who```
3. ```w```

```
$ users
JackSparrow WillTurner LizSwann

$ who
JackSparrow ttyp0 Oct 8 14:10 (limbo)
WillTurner  ttyp0 oct 4 0:45  (calliope)
LizSwann    ttyp0 Oct 8 12:11 (dent)
```

<a name="metacharactersShellWildcards"></a>
## Metacharacters - Shell Wildcards


Use '__*__' to match 0 or more characters, a question mark ('__?__') matches with single character and the '__[ab]__' _a_ or _b_ or _specified range_.

For exmaple - 

```
$ ls ch*.doc
```

Displays all the files, the names of which start with '__ch__' and end with '__.doc__'.

<a name="hiddenFiles"></a>
## Hidden Files

An invisible file is one, which start with a single dot character ( '__.__' ).

To list the invisible files, use ```-a``` option to ```ls```

```
$ ls -a
.       .profile    docs    lib     test_results
..      .rhtosts    hosts   pub     users
.emacs  bin         hw1     res.01  work
```

__Single dot ( '.' )__ - represents the __current__ directory.

__Double dot ( '..' )__ - represents the __parent__ directory.


<a name="creatingFiles"></a>
## Creating Files

To create files in Unix system you can use the following commands:

1. ```$ vi fileName```
2. ```$ > fileName```
3. ```$ touch fileName```


<a name="displayContentOfAFile"></a>
## Display Content of a File

Use ```cat``` ( _concatenate_ ) command to see the content of a file.

```
$ cat myfile
Hello World
```
To display the row numbers use ```-b``` option along with the ```cat``` command.

```
$ cat -b myfile
1. Hello World
```

__Note__: ```-b``` will add numbers to only non-empty lines. If you want to add row number to all lines, including empty lines too, use ```-n``` option - 

```
$ cat -n fileName
```

You can list out the content of the files almost the same way with ```more``` and with ```less```.


<a name="displayingPartsOfFiles"></a>
### Displaying Parts of Files

```head``` displays the first line of a file, by default the first 10 lines. Argument allows different number to be shown.


```
$ head [-number] fileName
```

```tail``` displays the last lines of a file, by default the last 10.

```
$ tail +|- number [-f] [-files ...]
```

```tail``` is more poweful than head, because it is able to output the end of the file relative to the start or to the end. Using ```tail -n``` it operates relative to the end, using ```tail +n``` it operates relative to the start. Using ```tail -f``` it outputs the end of the file and then waits.


<div style="page-break-after: always;"></div>

<a name="searchingFiles"></a>
## Searching Files

```grep``` searches files for strings.

```
$ grep [-cilnvw] <RegEx> [files ...]
```

```grep``` options -

1. ```-c``` - display count of matching lines
2. ```-i``` - case insensitive
3. ```-l``` - list names of files containing matching lines
4. ```-n``` - precede each line by its line number
5. ```-v``` - only display lines that do __not__ match
6. ```-w``` - search for the expression as a word


Regular expressions which can be used in ```grep``` - 

1. ```.``` - match any character
2. ```*``` - match zero or more occurrences of previous character
3. ```^``` - match beginning of line
4. ```$``` - match end of line
5. ```[abc]``` - match any one of _a_, _b_, _c_
6. ```[a-z]``` - match any character in range


<a name="translatingCharacters"></a>
## Translating Characters

```tr``` translates characters from the standard input. Characters mentioned in _first_ argument translated to corresponding character in second argument.

```
$ tr ’[a-z]’ ’[A-Z]’
hello
HELLO
```

__Note:__ 

```
$ tr '[:lover:]' '[:upper:]'
```

will do the same.


* Delete characters from an input stream

```
$ tr -d '[aeiou]'
Hello World
Hll wrld
```

* Use complement of input character pattern

```
$ tr -cd '[aeiou]'
Hello Worlds
eoo
```

* use ```-s``` (squeeze) option to remove duplicate replaced characters. The ```tr``` command needs some input so you can simply redirect the ```ls``` command's output into the ```tr```. For example -

```
$ ls | tr -s " "
```

<div style="page-break-after: always;"></div>

<a name="sortingFiles"></a>
## Sorting Files

```sort``` organises files into alpha-numeric order, by default ordering is increasing alphabetic order, entire line used as a key.

Lines are divided into fields

* space / tab characters used as separator
* allow more specific definition of sort keys


Options for sorting files - 

* ```-n``` - sort on numeric value
* ```-r``` - reverse sort
* ```-ka,b``` - sort key starts at field __a__ ( _1-based_ )
 and ends at field __b__.
 
```
$ sort -nr -k4,5 fileName
```

<a name="comparingFiles"></a>
## Comparing Files 

```diff``` displays only the differences between two files. 

* Lines in the __first__ file which differ from the second are prefixed with '__<__'.
* Lines in the __second__ file which differ from the first are prefixed with '__>__'.

```
$ diff file1 file2
```

The ```-e``` option causes ```diff``` to generate output which describes exactly how __file1__ can be generated from __file2__.
 
<div style="page-break-after: always;"></div>


<a name="cuttingFields"></a>
## Cutting Fields

```cut``` removes selected fields from each line of the file

* uses tab as field separator character.
* can also use character offsets specify cut region.

```
$ cut -d" " -f1 fileName
```

In the above example, ```cut``` selects field one from _fileName_, where fields are delimited by a single space. By default the field delimiter is a (single) tab.

You can use characters range to select which column you want to cut.

```
$ cut -c17-22 myFile
```

<a name="countingWordsInAFile"></a>
## Counting Words in a File

Use ```wc``` ( _word counter_ ) command to get a count of the total number of lines, words, and characters contained in a file.

```
$ cat myfile
Hello World

$ wc myfile
1 2 12 myfile
```
1. column represents the total number of __lines__ in the file. 
2. column represents the total number of __words__ in the file. 
3. column represents the total number of __bytes__ in the file. This is the actual size of the file. 
4. column represents the name of the file.


Options for ```wc``` - 

* ```-l``` - just report lines
* ```-w``` - just report words
* ```-c``` - just report characters

<div style="page-break-after: always;"></div>


<a name="pastingFiles"></a>
## Pasting Files

```paste``` allows you to combine the contents of two or more files, concatenating lines from the files into single lines in the output. If we reach the end of one of the files, then empty string is inserted into the result.

```
$ paste file1 file2
```

We can also use the filename '__-__' to represent using standard input as one of the files to read from.

```
$ cat file1 | paste file2 -
```


<a name="duplicateLines"></a>
## Duplicate Lines

```uniq``` removes duplicate adjanced lines from files.

```
$ uniq fileName
```

Options for ```uniq``` - 

* ```-c``` - count number of duplicate lines
* ```-d``` - only print repeated lines
* ```-u``` - only print non-repeated lines


<a name="nonASCIIFiles"></a>
## Non ASCII Files

Octal dump ```od``` displays the contents of any file in _octal_, _decimal_, _hexadecimal_ or _ASCII_ format.

Options for ```od``` - 

* ```-x``` - display in hexadecimal
* ```-c``` - display printable characters where possible
* ```-d``` - display in decimal


```
$ od -c fileName
```


<a name="deletingFiles"></a>
## Deleting Files


To delete an existing file, use ```rm``` ( _remove mapping_ ) command.  

```
$ rm fileName
```

__Cauction__ - a file may contain useful information. It is always recomennded to be careful while using this ```rm``` command. It is better to use the ```-i``` option along with ```rm``` command. _Remember: in Unix once deleted file never can be retrieved_.


Remove multiple files at a time -

```
$ rm fileName1 fileName2 ... fileNameN
```

The ```rm``` command also has the ```-r``` option similar to chose of ```cp```. The ```-r``` option is necessary if directory structures must be deleted.

```
$ rm -r nameOfDir
```


<a name="copyingFiles"></a>
## Copying Files

```cp``` copies files and directories around the file system. Copy means duplicating the bytes on disk representing the contents of the files being copied. ```cp``` is used with two arguments when copying from one file to another and with many arguments when copying a collection of files into a directory. ```cp``` is also be used to copy the contents of one directory to an another. In this case ```-r``` ( _recursive_ ) option must be supplied. When copying directories, if the target __d2__ exist, then the source __d1__ is created within it. A file __f1__ within __d1__ may also be accessed as __d2/d1/f1__. If, however, the target does not exist, the file __f1__ within __d1__, may now also be accesseed as __d2/d1__.

By default, the ```cp``` command overwrites any files which already exist with the target name. The ```-i``` ( _interactive_ ) option may be used in order to get ```cp``` to promt prior to overwriting any existing files.

To preserve a file's modification time and permission bits, use ```-p``` option. 

```
$ cp [-ip] f1 f2
$ cp [-ip] f1 f2 ... fn d
$ cp -r [-ip] d1 d2
```

__Copying multipe files it is important that the last argument must be a directory__.


<a name="movingDeletingFiles"></a>
## Moving / Deleting Files

```mv``` is used to rename files and directories. It does not cause the contents of the file to be physically moved, only the file's name is changed in its directory.

The new name may be a path to another directory, so ```mv``` can in fact move a file or directory from one place to another.

There is no need to recursive option. The ```-i``` option may be used if there is a danger of overwriting existing files.

```
$ mv [-i] f1 f2
$ mv [-i] f1 f2 ... fn d
$ mv [-i] d1 d2
```


<a name="linkingFiles"></a>
## Linking Files

All directories have at least two names, their name in the parent directory and in themselves. With each sub-directory, a new name is created for the parent.


<a name="hardLinks"></a>
### Hard Links

Use the ```ln``` command to create links -

```
$ ln existingFile linkName
```

It will increase the reference number to the given file or directory for which the link was created for. Links are destroyed by using the ```rm``` command. When the number of links referring to a file is zero, the actual file contents are removed.


<a name="symbolicLinks"></a>
### Symbolic Links - Symlinks

Look like hard links but implemented by reference. Symbolic file contains pathname of file it refers to, each has a distinct i-node number. To create symbolic link use the following command -

```
$ ln -s existingFile linkName
```

To reach the file or the directory it is always faster via hardlink than symlink.


<a name="standardUnixStreams"></a>
## Standard Unix Streams

Under normal circumstances, every Unix program has three streams (files) opened for when it starts up -

1. __stdin__ - this is referred to as the __standard input__ and the associated file descriptor is __0__.
2. __stdout__ - this is referred to as the __standard output__ and the associated file descriptor is __1__.
3. __stderr__ - this is deferred to as the __standard error__ and the associated file descriptor is __2__.


<a name="homeDirectory"></a>
## Home Directory

The directory in which you find yourself when you first login is called your home directory.

You can go in your home directory anytime using the following command - 

```
$ cd ~
```

Here ```~``` indicates the home directory. If you want to go to another user's home directory use the following command - 

```
$ cd ~anotherUserName
```

Go back to your last directory use -

```
$ cd -
```

Go to the root directory -

```
$ /
```

Unix using a hierarchial structure for oraganzing files and directories. This structure is often referred to as a directory tree. The tree has a single root node, the slash character ( ' __/__ ' ).

Go back to a parent directory -

```
$ cd ..
```

__Cauction__ - in the root directory ( ' __/__ ' ) the '__.__' and the '__..__' are the same. No difference between

```
$ cd .
```

and

```
$ cd ..
```


<a name="AbsoluteAndRelativePathnames"></a>
## Absolute / Relative Pathnames

Directories are arranged in a hierarchy with root ( ' __/__ ' ) at the top. The position of any file within the hierarchy is described by its pathname.

Elements of a pathname are separated by a ' __/__ '. A pathname is __absolute, if it is described in relation to root__, thus __absolute pathnames always begin with a  ' / '__. Absolute pathnames are unique. See in below example -

```
/etc/passwd/
/dev/rdsk0s3/
```

A pathname can also be relative to your current working directory. __Relative pathnames never begin with  ' / '__. Relative to user amrood's home directory. Relative pathnames are not unique since they depend on the directory in which the path is specified. Some pathnames might look like this - 

```
chem/notes
personal/res
```

To determine where you are within the filesystem hierarchy at any time, enter the command ```pwd``` ( _print working directory_ ) to print the current working directory -

```
$ pwd
/usr/local/JackSparrow
```

<a name="listingDirectoriesDotAndDotdot"></a>
## Listing Directories .(dot) and .. (dot dot)

The __filename .__ (dot) represents the current working directory; and the __filename ..__ (dot dot) represents the directory one level above the current working directory (expect when you are in the root [see above example]) often referred to as the parent directory.

If we enter the command to show a listing of the current working diretories/files and use the ```-a``` option to list all the files and the ```-l``` option to provide the long listing, you will receive the following result -

```
$ ls -la
drwxrwxr-x 4 teacher class 2048 Jul 16 17.56 .
```			

<a name="listingDirectories"></a>
## Listing Directories

To list the files in a directory use the following syntax -

```
$ ls dirName
```

To list the current directory, simply use ```ls```.

```
$ ls
```

You can add subdirectories in a directory. See below example -

```
$ ls usr/local/home
```

<div style="page-break-after: always;"></div>


<a name="creatingDirectories"></a>
## Creating Directories

Directories are created by the following command -

```
$ mkdir dirName
```

Here, directory is the absolute or relative pathname of the directory you want to create. For exmaple -

```
$ mkdir myDir
```

Creates the directory _myDir_ in the current directory. Another example -

```
$ mkdir /tmp/test
```

This command creates the directory _test_ in the _/tmp_ directory.

Using ```-p``` option, ```mkdir``` is able to create missing parent directories as needed - 

```
$ mkdir -p first/seconds/third
```

will create the missing parent directories _first_ and _second_ if they do not already exist.

If you give more than one directory on the command line, ```mkdir``` creates each of the directories. For example - 

```
$ mkdir docs pub
```

Creates the directories __docs__ and __pub__ under the current direcotry.


<a name="removingDirectories"></a>
## Removing Directories

Directories can be deleted using the ```rmdir``` command as follows -

```
$ rmdir dirName
```

__Note__ - to remove a directory, make sure it is empty which means there should not be any file or sub-direcotry inside this directory.

If you want to remove the sub-directories use the ```-r``` with ```rmdir```.

```
$ rmdir -r dirName
```

It will remove all sub-directories recursively which are in _dirName_.

Remove multiple directories at a time as follows -

```
$ rmdir dirName1 dirName2 .. dirNamN
```

The above command removes the directories if they are empty. The ```rmdir``` command produces no output if it is succesfull.


<a name="changingDirectories"></a>
## Changing Directories

Use ```cd``` command to change to any directory by specifying a valid absolute or relative path.

```
$ cd dirName
```

_dirName_ is the name of the directory that you want to change to.

Use absolut pathname to change the directory -

```
$ cd /usr/local
```

<a name="renamingDirectories"></a>
## Renaming Directories

The ```mv``` ( _move_ ) can also be used to rename directory - 

```
$ mv oldDir newDir
```

<a name="permissionBits"></a>
# Permission Bits

Every file carries permissions for its owner ( _user_ ), group and others ( _everyone else_ )

Permissions for files

* __r__ _read_ - read contents 
* __w__ _write_ - alter contents
* __x__ _execute_ - attempt to run program
* __s__ _set ID_ - change the UID or GID of process


Permission for directories

* __r__ _list_ - list contents
* __w__ _write_ - create and delete _any_ files
* __x__ _search_ - access the directory (with a _path_, ```cd```)
* __t__ _sticky_ - finer control over write access to directories 


The permission bits are organized in three sets of three bits, following the file type field.

<table>
	<tr>
		<th>type</th>
		<th>user</th>
		<th>group</th>
		<th>others</th>
	</tr>
	<tr>
		<td>d</td>
		<td>r w x</td>
		<td>r w -</td>
		<td>r - -</td>
	</tr>
	<tr>
		<td></td>
		<td>4 2 1</td>
		<td>4 2 -</td>
		<td>4 - -</td>
	</tr>
</table>

__Note__: about types see more in chapter: _Listing Directories, Files and Processes &#62; Prefix & Description_.

<a name="stickyBit"></a>
## Sticky Bit

The _Sticky Bit_ allows a file to be deleted if

* the user has write permission on the directory, and
* the user owns the file, or ownd the directory, or is the superuser

To add a sticky bit to your file use the following command - 

```
$ chmod +t fileName
```

for remove

```
$ chmod -t fileName
```

<a name="settingPermissions"></a>
## Setting Permissions

```chmod``` is used to change permissions. Only the owner may change the permissions, or the superuser.

```
$ chmod [-R] <permission-mode> file [files ...]
```

The ```-R``` option is enables recursion through a directory hierarchy.

The permission-mode may by specified using

* a __symbolic__ notation.
* a __numeric__ notation.


<div style="page-break-after: always;"></div>


<a name="symbolicNotation"></a>
### Symbolic Notation

The symbolic notation allows file permissions to be changed relative to the current permission.

```
$ chmod u + r files...
        g - w
        o = x
        a   s
            t
```

The permission is applied to __u__ ( _user_ ), __g__ ( _group_ ), __o__ ( _others_ ), __a__ ( _all of them_ ) or any combination thereof. Permissions may be added, substracted or assigned

* __+__ - addd new permission to the existing bits
* __-__ - remove new permission from the existing bits
* __=__ - override existing permission with new permission

Example -

```
$ chmod ug+rx, o-w myFile
```

<a name="numericNotation"></a>
### Numeric notation

Treats the permission as a bit pattern.

```
$ chmod 777
```

(r = 4 ,w = 2 ,x = 1 -> 4 + 2 + 1 = 7)

An extra leading octal digit may be used in the numeric notation. This provides for set 

* __UID__ (4) [User ID] 
* __GID__ (2) and 
* __sticky__ (1). 

Setting a file's permissions to _7777_ would enable everything, _rwsrwsrwt_.

__Note__: a lowercase _s_ or _t_ implies that the _x_ permission is also enabled. If _x_ is absent, then the _S_ and _T_ appear as capital letter.


<div style="page-break-after: always;"></div>

<a name="defaultPermissions"></a>
## Default permissions

```umask``` defines the default permission bits. Default for files and directories created by process. Not applied when files or directories are copied.


<a name="commandPipelines"></a>
## Command pipelines

The output of one command is directed into the input of another to from a pipeline. Always executed from __left to rigth__.

```
$ ls | grep '^d' | sort
```

The ```tee``` command enables the stream to be diverted.

```
$ ls | tee myFile | sort
```

The ```tee``` commands reads from __STDIN__ ( _0_ ) and writes to __STDOUT__ ( _1_ ) and to any files which are names as arguments. In the example above ```tee``` reads the output from the ```ls``` and writes this to _myFIle_ and passes the data to ```sort```.


<a name="composingCommands"></a>
## Composing Commands

Sequential composion

```
$ cmd1; cmd2
```

Parallel composion

```
$ cmd1 & cmd2
```

Conjuctive composion - the condition is true if both of them is true

```
$ cmd1 && cmd2
```

Disjunctive composion - the condition is true if one of them is true

```
cmd1 || cmd2
```

<div style="page-break-after: always;"></div>

<a name="foregroundAndBackgorundJobs"></a>
# Foreground and Background Jobs

* __A foreground job has access to the terminal for its input and output__
  * shell waits for foreground job to finish before promting for the next command
* __A background job has no access to the terminal for input__
  * may have access for output
  * shell will __not__ wait for background job to complete before promting for the next command.

 
Foreground and background jobs can be:

* terminated
* suspended
* resumed 

To start a process in the background use the ampersand character ( '__&__' ) after the command. For example -

```
$ sleep 30 &
```

<div style="page-break-after: always;"></div>

<a name="jobNumbers"></a>
## Job Numbers

When a background processes are invoked the shell tags them with a _job number_.

```
$ sleep 30 &
[1] 10708
```

Job number is __not__ the same as process id. To kill a backgound process use the ```kill``` command and the process ID like below - 

```
$ kill 10708
```
   	
If you want to see how many process running in the backgorund use the ```jobs``` keyword to list them out - 

```
$ jobs
[1]+ Running 			sleep 30 &
```

the __[1]__ is the job number which is running at the moment. The '__+__' sign indicates that it is the most recent background job and at the end of the line there is a process name itself.

Keyboard combinations for jobs:

```
^Z		suspends the foreground job
^C		terminates the foregorund job
fg		resumes a suspended job in the foreground
bg		resumes a suspended job in the background
jobs	list currently active jobs
stop	suspends the specified background job (ksh)
kill	send signal to job (ksh and bash)
```











