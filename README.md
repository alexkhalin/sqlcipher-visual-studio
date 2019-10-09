SQLCipher for Visual Studio 2019, building platforms x32 and x64
===========================

[sqlcipher-visual-studio](https://github.com/torsch/sqlcipher-visual-studio) is a simple port of the open-source [SQLCipher](http://sqlcipher.net/) library [[src](https://github.com/sqlcipher/sqlcipher)] for Visual Studio 2015. Everything should work out of the box to compile x32 and x64 versions of SQLCipher.
Actually this is just an updated fork from [T0SCH/sqlcipher-visual-studio](https://github.com/T0SCH/sqlcipher-visual-studio) which is a fork from [karlosp/sqlcipher-visual-studio](http://github.com/karlosp/sqlcipher-visual-studio) where you can get an older version for Visual Studio 2013.

Versions
--------

`sqlcipher-visual-studio` is a combination of
* [SQLite 3.11.0](http://www.sqlite.org/src/zip/SQLite-3d862f20.zip?uuid=3d862f207e3adc00)
* [SQLCipher 3.4.0](https://github.com/sqlcipher/sqlcipher/releases/tag/v3.4.0)

and has been successfully built with the following versions of OpenSSL:
  * [Win32 OpenSSL v1.0.2h](https://www.conan.io/source/OpenSSL/1.0.2h/lasote/stable) 
  * [Win64 OpenSSL v1.0.2h](https://www.conan.io/source/OpenSSL/1.0.2h/lasote/stable)

The easiest way to manually update with new version of SQLite or SQLCipher
--------
On linux or Cygwin run the following commands:
* git clone https://github.com/sqlcipher/sqlcipher.git
* cd sqlcipher
* ./configure --enable-tempstore=yes CFLAGS="-DSQLITE_HAS_CODEC" 
* make

If everything went OK, you should be able to run sqlcipher with following command: ./sqlcipher and you should get an output like:
```
SQLCipher version 3.11.0 2016-02-15 17:29:24
Enter ".help" for instructions
Enter SQL statements terminated with a ";"
Connected to a transient in-memory database.
Use ".open FILENAME" to reopen on a persistent database.
sqlite>
```

Final step: copy following source files from the current directory (linux / Cygwin) to the sqlcipher-visual-studio directory:
* `shell.c   --> Shell/src`
* `sqlite3.h --> StaticLib/inc`
* `sqlite3.c --> StaticLib/src`

Now you can build the solution in Visual Studio.

Why are included OpenSSL headers and libraries?
--------
Because I just want to work EVERYTHING out of the box ;)
