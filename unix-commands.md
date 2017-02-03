## Unix commands

### Basics

#### cat

Show contents of the file.

```
cat some-file.txt
```

#### pwd

Show the name of the current working directory.

```
pwd
```

#### cd

Change the current working folder.

```
cd some-folder

cd ..    // move one folder up
cd /     // move to home folder
cd ~     // move to root
```

#### cp

Copy the file `some-file-1.txt` to the file `some-file-2.txt` in the current working folder.

```
cp some-file-1.txt some-file-2.txt
```

#### mv

Move or rename files.

```
mv some-file-1.txt some-file-2.txt    // Changes the names from "some-file-1.txt" to "some-file-2.txt"
mv /some-folder/some-file .           // Move the file from "some-file" from the folder "/some-folder" 
                                         to the current working folder.
```

#### rm

Remove the folder. Flag means remove recursively (deleting everything in folder)

```
rm -r folder
```

#### locate

Locates file or folder.

```
locate partial-name
```

#### ll

List all files in the current working directory in long listing format showing permissions, ownership, size, and time and date stamp.

```
ll
```
