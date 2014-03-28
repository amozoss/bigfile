bigfile
=======

A way to verify iappend works
#### Navigate to xv6 directory (~/classes/xs5460/xv6) 
    cd ~/classes/xs5460/xv6
    
#### Get md5 files
    wget --no-check-certificate https://raw.githubusercontent.com/amozoss/bigfile/master/md5.c
    wget --no-check-certificate https://raw.githubusercontent.com/amozoss/bigfile/master/md5.h

#### Update UPROGS in makefile
       UPROGS=\
      _cat\
        .
       .
        .
       _md5\
        100mb\


#### Generate a large file named "100mb" with random numbers (takes a while)
     dd if=/dev/urandom of=100mb bs=1M count=100
      
100+0 records in

100+0 records out

104857600 bytes (105 MB) copied, 11.6309 s, 9.0 MB/s


#### Generate hash value from large file in unix shell
    md5sum 100mb
    
 25b5036ade0d5cba78d4fb473fb8b0a9  100mb 
      
#### Start qemu
    make qemu-nox

(init: starting sh, starting text)
#### Run md5 in xv6 (also takes awhile, note 100mb is the name of the file generated in unix with dd)
    md5 100mb
        
 opening file
 
 start md5
 
 finish md5
 
 print md5
 
 25B536ADED5CBA78D4FB473FB8B0A9 is the md5sum

#### Check the hash value from the unix shell matches the one generated in xv6
If they are equal there iappend works properly 
("25b5036ade0d5cba78d4fb473fb8b0a9".upcase == "25B536ADED5CBA78D4FB473FB8B0A9")
