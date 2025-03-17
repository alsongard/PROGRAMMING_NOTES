# tar 
``tar`` meaning :Tape ARchive
the tar command is used for archiving files  and folders.

**Syntax**
``tar [operations and options] [archive_name] [file names]``

**OPERATION**
--create  (-c) : used in creating a file archive.
--extract (-x) : used for extracting files from an archive.
--list (-t) : displays a list of files in an archive.

**OPTIONS**
--file=archive=name (-f archivefilename)  - specifies the archive filename
--verbose (-v) : show files while being process both for extracting and archiving.



**/dev/null**
the /dev/null is a special file in linux that discards anything written to it. 
Linux has 3 standard input/output streams:

| value | meaning                 |
| ----- | ----------------------- |
| 0     | standard input          |
| 1     | standard output(normal) |
| 2     | for error messages      |
when your execute the command ``find / -iname "err*.txt" 2>/dev/null`` any error messages will be sent to the /dev/null file. And as informed above it discards any data written to it.
