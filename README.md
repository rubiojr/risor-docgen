# Risor API Documentation Generator

A command-line tool for automatically generating API documentation in Markdown format from Risor source files. This tool extracts documentation comments, method signatures, and other metadata to create comprehensive API documentation.

## Features

- Extracts documentation from Risor source code
- Supports both class methods and global functions
- Parses description, parameter, and return value documentation
- Generates formatted Markdown output
- Automatic example code generation

## Installation

1. Ensure you have Risor installed on your system
2. Clone this repository
3. Build the binary with RSX
   ```
   rsx build
   ```

## Usage

```
./risor-docgen -i <input_file> -o <output_file>
```

### Arguments

- `-i, --input` - Input Risor file (default: "tlz.risor")
- `-o, --output` - Output Markdown file (default: "api.md")

## Documentation Format

The generator looks for specific comment patterns in your Risor code:

### Function/Method Documentation

```go
// Description of the function
// This can span multiple lines
//
// Parameters:
// - param1: Description of first parameter
// - param2: Description of second parameter
//
// Returns: Description of what is returned
```

### Class or Function Annotations

The tool looks for special annotation comments:

- `@object.class` - Marks a class declaration
- `@object.method` - Marks a class method
- `@global.function` - Marks a global function

## Example

Input Risor file:

```go
// @object.class
Calculator := {
  // Adds two numbers
  //
  // Parameters:
  // - a: First number
  // - b: Second number
  //
  // Returns: Sum of a and b
  // @object.method
  add = func(a, b) {
    return a + b
  }
}
```

Output Markdown:

````markdown
# Calculator class

## add

Adds two numbers

### Parameters

- a: First number
- b: Second number

### Returns

Sum of a and b

### Example

```go
// Example usage of add
Calculator.add(a, b)
```
````

## License

This project is licensed under the MIT License - see the LICENSE file for details.

## Contributing

Contributions are welcome! Please feel free to submit a Pull Request.
