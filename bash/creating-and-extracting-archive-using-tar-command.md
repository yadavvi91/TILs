# Creating and Extracting archive files using tar command

Tarballs (`.tar`, `.tar.gz`, `.tar.bz2` etc. files) are used to compress and share number of files/directories together.

An archive file (i.e. a tarball) can be either compressed and non-compressed. 

A `.tar` file is just a file that has all the files combined together, whereas a `.tar.gz` file is a file that has all the files combined together and is also compressed.

The size of a `.tar.gz` file (of a set directories/files) is less than its corresponding `.tar` file.


## Creating an archive/tarball

To create an archive we can use the following command - 

```bash
tar -czvf name-of-archive.tar.gz /path/to/directory-or-file
```
The meaning of the arguments are -

* -c: Create an archive
* -z: This archive should be compressed with gzip
* -j: This archive should be compressed with bzip2
* -v: Verbose
* -f: The name that follows is the filename of the resulting archive

**NOTE:** We **cannot** use both `-z` and `-j` together.

#### Add more than one directories/files

We can add a more than one directories/files in the archive like so -
```bash
tar -czvf name-of-archive.tar.gz <directory1> <directory2> <file1> <file2> <and so on ...>
```

#### Exclude directories/files

We can even **exclude** certain files from the archive that is being created like so -
```bash
tar -czvf name-of-archive.tar.gz <path-to-directory-or-file> --exclude=.git --exclude=*.mp4
```

#### Compressed file using gzip compression

The argument `-z` creates a gzip archive
```bash
tar -czvf name-of-archive.tar.gz <path-to-directory-or-file>
```

#### Compressed file using bzip2 compression

To create a bzip archive we use `-j` argument
```bash
tar -cjvf name-of-archive.tar.bz2 <path-to-directory-or-file>
```

#### Create a tar file *without* any compression

To only create a `.tar` file instead of a compressed archive we can use - 
```bash
tar -cvf name-of-archive.tar <path-to-directory-or-file>
```

## Extract an archive/tarball

We can extract a tarball using the tar command with `-x` option.
```bash
tar -xvf name-of-archive.tar.gz
```

The meaning of the arguments are -

* -x: Extract this archive

All the other arguments are similar to the ones used to create an archive.

#### Extract an archive to a give directory

We can extract a given archive to a specific directory using `-C` (capital c) as an argument like so -
```bash
tar -xvf name-of-archive.tar.gz -C <path-to-directory>
```

**NOTE:** When extracting **any** archive we do not need either `-j` and `-z` options. The tar command is intelligent enough to guess the compression algorithm.

## List the contents of an archive/Verify the integrity of an archive

Sometimes we only want to see the contents of an archive file **without** extracting it, we can do this like so -
```bash
tar -tvf name-of-archive.tar.gz
```
To verify the integrity of an archive we can use the same command.

**NOTE:** When listing or verifying an archive we do not need any compression algorithm specification. Thus we can list both bzip2 and gzip archives **without** using the `-j` and `-z` options respectively.