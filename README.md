# Everything you need to know about Windows Unicode Handling if you are a C or C++ developer

## Open files when the file name contains Unicode characters

All filesystems supported by Windows since Windows XP *do* save the name of the files and folders in Unicode format. Regardless of this, both `fopen` and `std::*fstream` are strictly unable to open files when given UTF-8 strings containing non-ASCII characters in all current Windows version. Trying to do so will fail.

Possible solutions:

* *Windows 10 version 1803 and up only*: Override the locale in the context of the application to set it to UTF-8 (see [Microsoft's documentation about setlocale()](https://learn.microsoft.com/en-us/cpp/c-runtime-library/reference/setlocale-wsetlocale?view=msvc-170))
* Use [Boost::nowide](https://www.boost.org/doc/libs/master/libs/nowide/doc/html/index.html).