# Valgrind Exercise

## Standard install via command-line
```bash
# Configure the project and generate a native build system:
  # Must re-run this command whenever any CMakeLists.txt file has been changed.
  cmake -S ./ -B build/
# To build with debugging information, do:
  cmake -S ./ -B build/ -D CMAKE_BUILD_TYPE=Debug
# Compile and build the project:
  # rebuild only files that are modified since the last build
  cmake --build build/
  # or rebuild everything from scracth
  cmake --build build/ --clean-first
  # to see verbose output, do:
  cmake --build build/ --verbose
# Run program:
  ./build/app/shell-app
# Clean
  cmake --build build/ --target clean
# Clean and start over:
  rm -rf build/
```
## Q/As:
**1. What happens when the executable is linked statically?  Does Valgrind still detect those same bugs?**  
**Ans:** When the executable is linked statically, valgrind can still detect the same bugs as earlier but it does not report any memory allocations or leaks which we know is incorrect. Additionally it throws numerous conditional jump errors in methods that are not part of our code. Hence valgrind behavious irratically on static linking.

**2. Why or why not?**  
**Ans:** The issue is that valgrind requires dynamic linking for its functionalities and is therefore not able to suppress a lot of the irrelevant errors in the static linking configuration.

**Note:** The valgrind output before and after the fixes is kept in the [results](results) folder.