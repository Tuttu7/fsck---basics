

#### The fsck (File System Consistency Check) Linux utility checks filesystems for errors or outstanding issues. The tool is used to fix potential errors and generate reports.

|Option| Details|
|------|----------|
|-a    | Automatically repair the file system without any questions |
|-v    | Verbose output|
|-y    | Yes to all questions||
|-n    | ust check the file system but not repair|

#### Make sure to unmount the partition before performing fsck 

```
umount  /dev/xvdb1
```

```
[root@ip-172-31-45-189 ~]# fsck  /dev/xvdb1
fsck from util-linux 2.30.2
e2fsck 1.42.9 (28-Dec-2013)
/dev/xvdb1: clean, 11/427392 files, 67116/1709056 blocks
```


#### To check forcefully
```
[root@ip-172-31-45-189 ~]# fsck -f /dev/xvdb1
fsck from util-linux 2.30.2
e2fsck 1.42.9 (28-Dec-2013)
Pass 1: Checking inodes, blocks, and sizes
Pass 2: Checking directory structure
Pass 3: Checking directory connectivity
Pass 4: Checking reference counts
Pass 5: Checking group summary information
/dev/xvdb1: 11/427392 files (0.0% non-contiguous), 67116/1709056 blocks
```

#### To Display verbose output 
```
[root@ip-172-31-45-189 ~]# fsck -vf /dev/xvdb1
fsck from util-linux 2.30.2
e2fsck 1.42.9 (28-Dec-2013)
Pass 1: Checking inodes, blocks, and sizes
Pass 2: Checking directory structure
Pass 3: Checking directory connectivity
Pass 4: Checking reference counts
Pass 5: Checking group summary information

          11 inodes used (0.00%, out of 427392)
           0 non-contiguous files (0.0%)
           0 non-contiguous directories (0.0%)
             # of inodes with ind/dind/tind blocks: 0/0/0
             Extent depth histogram: 3
       67116 blocks used (3.93%, out of 1709056)
           0 bad blocks
           1 large file

           0 regular files
           2 directories
           0 character device files
           0 block device files
           0 fifos
           0 links
           0 symbolic links (0 fast symbolic links)
           0 sockets
------------
           2 files
```
#### Check filesytems for errors & repair automatically
```
[root@ip-172-31-45-189 ~]# fsck -a  /dev/xvdb1
fsck from util-linux 2.30.2
/dev/xvdb1: clean, 11/427392 files, 67116/1709056 blocks


[root@ip-172-31-45-189 ~]# fsck -a -f -v /dev/xvdb1
fsck from util-linux 2.30.2

          11 inodes used (0.00%, out of 427392)
           0 non-contiguous files (0.0%)
           0 non-contiguous directories (0.0%)
             # of inodes with ind/dind/tind blocks: 0/0/0
             Extent depth histogram: 3
       67116 blocks used (3.93%, out of 1709056)
           0 bad blocks
           1 large file

           0 regular files
           2 directories
           0 character device files
           0 block device files
           0 fifos
           0 links
           0 symbolic links (0 fast symbolic links)
           0 sockets
------------
           2 files
 ```
 
 ##### If you don't want to repair, just check the file system
 
 ```
 [root@ip-172-31-45-189 ~]# fsck -n /dev/xvdb1
fsck from util-linux 2.30.2
e2fsck 1.42.9 (28-Dec-2013)
/dev/xvdb1: clean, 11/427392 files, 67116/1709056 blocks
```


