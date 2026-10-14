# C++ Notes
Following along: [LearnCPP.com](https://www.learncpp.com)

## C++ Dev Setup
- IDE: VSCode is good
- Compiler: software that takes written code and turns it into machine code
    - On mac/linux the compiler creates a binary that can run on the hardware
    - gcc is a good compiler for mac/linux
- Extensions: Install the C/C++ extension on VSCode
- Configure compiler in VSCode:
```json
{
	"version": "2.0.0",
	"tasks": [
		{
			"type": "cppbuild",
			"label": "C/C++: g++ build active file",
			"command": "/usr/bin/g++",
			"args": [
				"-fdiagnostics-color=always",
				"-g",
				"-std=c++20",
				"${workspaceFolder}/*",
				"-o",
				"${fileDirname}/${fileBasenameNoExtension}"
			],
			"options": {
				"cwd": "${fileDirname}"
			},
			"problemMatcher": [
				"$gcc"
			],
			"group": "build",
			"detail": "compiler: /usr/bin/g++"
		}
	]
}
```

## First Program
- The main function: the main function is the entry point for the C++ program.  It's the very first thing that will be run.
```cpp
#include <iostream>

int main(){

}
```
- Comments
```cpp
#include <iostream>
// single line comment
/*
Multi
line
comment
*/
int main(){

}
```
- Errors and Warnings
    1. Compile-time errors -- compiler finds something like a syntax error that it freaks out about
    2. Runtime errors -- program compiles, but something goes wrong when running it
    3. Warnings -- program will technically compile, but the compiler might warn you it's not going to end well (e.g. dividing by 0)
- Statements and Functions
	- Statement: Basic unit of code in C++ program.  always terminated in a semi-colon
		- Statements run from top to bottom, until a statement terminates the program
	- Function: A unit of code consisting of statments.  Takes inputs, provides and output.
		```cpp
		int add_numbers(int first_number, int second_number){
			int sum = first_number + second_number;
			return sum;
		}
		```
- Input and Output
  - std::cout, std::cin, std::cerr, std::clog -- output, input, error, log
	```cpp
	int age {21};
	std::cout << "The age is: " << age << std::endl;

	int favorite_number;
	std::cout << "What is your favorite number?" << std::endl;
	std::cin >> favorite_number;
	```

- Program and Execution Model
	- After compiling a program, it is converted into a binary file (literally a file with binary code)
	- When you run the binary, it is loaded up into memory
- Core Language Feature vs. Standard Library vs. STL
	- Core Feature: Is the basic/vanilla syntax and building blocks of the language
	- Standard Library: Set of turnkey, but more purpose built components for various applications
	- STL: A collections of specialized types, algorithms, and other things.  Part of the Standard Library.