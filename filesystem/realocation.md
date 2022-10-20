# Reallocation
-------------
Sometimes it may be necessary to do a filesystem data realocation from one
machine to another, in these cases one option to do that is to reinstall the
whole system, another one is to do a system realocation by using archives.

## Creating a Safe House
The first thing that should be done is creating a backup of the files that
should be realocated to the other machine. For that the best option for it is
using tar (tape archive):  
```
tar -cvf <location of backup>/"$(date + '%Y%m%d%H%M%S')"-<name_of_backup>.tar .
```

Three things should be noted on that operation, the first is that the current
timestamp is prepended to the backup file using the format
*YearMonthDayHourMinuteSecond*, to be able to better organize it on the
filesystem. On second place **no compression is used** during this proccess,
the reason for that is the computing overhead involved in doing this operation
for very large filesystems, and to be able to recover files in case the
operation fails. Lastly the directory in which the operation is made is on the
root of the filesystem to be able to uncompact it in easier way on another
moment.

In case there are non-desired directories on the root directory it is possible
to use *--exclude* or in case of virtual filesystems (e.g.: /proc, /dev, /sys),
remount the root on another directory and make the operation from there.

## Rebuilding the House 
To recreate the filesystem on another device (assuming it is already formatted
and partitioned), simply run the reverse operation of tar on the backup:
```
tar xvf <backup_file_name>.tar <root_of_the_device>
```
