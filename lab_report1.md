# **Lab Report #1**
***

## 'cd' - change directory
***

no arguments - Absolute path: (/Users/ericpalafox)
- While running 'cd' with no arguments, there is no output since we are trying to change directory but do not give an argument. This simply means that we will change directories into the current directory that we are in, hence nothing happens. 

directory - Absolute path: (/Users/ericpalafox/Downloads)
- While running 'cd Downloads' with a directory (Downloads) as the argument, this will result in an output of the previous working directory along with the /Downloads appended since we have moved into the Downloads directory with the cd command.

file - Absolute path: (/Users/ericpalafox/Downloads/test.txt)
- While running 'cd test.txt' we are trying to change directories into a file, however, this is not possible since we are changing the working directory and this cannot be a file. In this case we can see the output as "cd: not a directory: test.txt" since we can only use cd to change into different directories, not files.

![Image](cd.png)

## 'ls' - list
***

no arguments - Absolute path: (/Users/ericpalafox)
- While running 'ls' with no arguments, the output will list all of the contents in our current working folder, in this case the contents listed in /Users/ericpalafox. Some of the contents in this directory are Downloads, Movies, Music, etc., also note that no argument was inputted so bash will automatically assume you would like the listed conetents of the current directory.

directory - Absolute path: (/Users/ericpalafox/)
- While running 'ls PycharmProjects' we are listing all of the contents found in the /Users/ericpalafox/Downloads/PycharmProjects and we can say that there are 3 different programs. The output will list all of the contents of the given path, this case we say ClockProgram, HarvardCS50, and PythonFullCourse which are directories in the PycharmProjects directory.

file - Absolute path: (/Users/ericpalafox/Downloads/PycharmProjects/ClockProgram)
- While running 'ls ClockProgram.py' the output will be the same argument which is "ClockProgram.py" since this is a file and there is nothing to list but the name of the file itself. If there were more contents within this location, then we would be able to see the list but this is the only file in ClockProgram.py.

![Image](ls.png)

## 'cat' - concatenate
***

no arguments - Absolute path (/Users/ericpalafox)
- While running 'cat' the terminal will actually stop running as there is no way to concatenate something that is empty. We must be sure that we are giving at least 1 argument to ensure that 'cat' will run properly, hence there is no output and we must terminate.

directory - Absolute path (/Users/ericpalafox)
- While running 'cat Downloads' we receive an error message which indicates that we cannot concatenate a directory, we are only able to concatenate files with other files, but not directories. This would certainly be an issue if it were possible as we may accidentally concatenate the wrong contents which may lead to potential issues.

file - Absolute path (/Users/ericpalafox/Downloads)
- While running 'cat t1 t2' we get no output since both t1 and t2 are files which contain nothing inside. These are dummy files and have no contents, if there were contents then the output would be the t1 and t2 files printed out together, hence contents of t2 have been appended to the end of contents of t1.

![Image](cat1.png)

![Image](cat2.png)
