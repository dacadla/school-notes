1. **Function Definition:**
   - Begin with the keyword `func` followed by the function name.
   - Inside parentheses, list the arguments with their names followed by a colon and their types.
   - Define the function body within curly braces `{}`.

2. **Function Call:**
   - Call functions by their name followed by parentheses.
   - Inside the parentheses, specify argument names followed by a colon and the values. Arguments can be provided in any order due to the named argument feature.

3. **Prototype Definition:**
   - Use the keyword `prototype` followed by the prototype name to define a new prototype.
   - Inside curly braces `{}`, define properties with the `var` keyword, and methods with the `func` keyword.
   - Method definition within prototypes follows the same pattern as standalone function definition.

4. **Prototype Inheritance:**
   - Use the keyword `extends` followed by the name of the existing prototype to create a new prototype that inherits properties and methods of the existing one.

5. **Method Call:**
   - Methods are called on objects using the dot (`.`) operator, followed by the method name and arguments within parentheses.
   - Like function calls, method arguments are specified with their names followed by a colon and the values.

6. **Default Argument Values:**
   - While defining functions or methods, default values for arguments can be specified by using the equals sign (`=`) followed by the default value after the type.

7. **String Interpolation:**
   - Strings prefixed with a dollar sign (`$`) followed by double quotes (`""`) allow for interpolation.
   - Variables and expressions to be interpolated are enclosed in curly braces (`{}`) within the string.

8. **Object Creation and Property Access:**
   - Create new objects using the `new` keyword followed by the prototype name.
   - Set and access properties using the dot (`.`) operator.

# Parallelism
1. **Keyword for Fiber Definition:**
   - Introduce a keyword `fiber` to denote a coroutine. The `fiber` keyword precedes the function name and follows the same syntax as function definition but is used to declare a coroutine instead.

2. **Fiber Body:**
   - The body of the fiber is enclosed within curly braces `{}`. Inside the body, define the operations the coroutine should perform.

3. **Await Keyword:**
   - Introduce an `await` keyword within the fiber body to indicate points where the coroutine can be paused, waiting for some asynchronous operation to complete. When an `await` expression is encountered, the fiber is paused until the awaited operation is finished, at which point the fiber is resumed.

4. **Creating a Fiber Instance:**
   - Create instances of a fiber by calling the fiber function, similar to how you'd call a regular function. This returns a fiber object.

5. **Resuming a Fiber:**
   - Define a method `resume()` on the fiber object which, when called, resumes the execution of the fiber from the point where it was last paused.

6. **Example Code:**

```
// Define a fiber using the 'fiber' keyword
fiber fetchData(url: String) {
    // Simulate a non-blocking I/O operation
    var data = await io.get(url);  // Assume 'await' pauses the fiber and resumes when data is available
    process(data);  // Process the data
}

// Create a new fiber instance
var dataFiber = fetchData("https://example.com/data");

// Resume the fiber to start its execution
dataFiber.resume();

// Later in the code...
// Resume the fiber again, if needed (e.g., after an await)
dataFiber.resume();
```

In this example:

- A fiber named `fetchData` is defined with the `fiber` keyword.
- The `fetchData` fiber is designed to perform a simulated non-blocking I/O operation using an `await` keyword.
- A new fiber instance `dataFiber` is created by calling `fetchData`.
- The `resume()` method is used to start or continue the execution of the `dataFiber` instance.

# Importing and exporting
### Importing:

1. **Importing Entire Modules:**
   Users can import an entire module, bringing all of its exported items into scope.

```pl
import Math;  // Import everything from the Math module
```

2. **Importing Specific Items:**
   Users can import specific items from a module, which can help to reduce name conflicts and improve clarity.

```pl
import { sqrt, pow } from Math;  // Import specific items from the Math module
```

3. **Aliasing:**
   Users can give imported items an alias to avoid name conflicts or for convenience.

```pl
import { sqrt as squareRoot } from Math;  // Import sqrt as squareRoot
```

### Exporting:

1. **Explicit Exports:**
   Items (functions, prototypes, variables, etc.) are exported explicitly with an `export` keyword, making it clear what is part of the module's public interface.

```pl
export func square(x: Int): Int {
    return x * x;
}
```

2. **Default Exports:**
   Each module can have one default export, which is the primary exported value for the module. This is useful for modules that export a single item.

```pl
export default func square(x: Int): Int {
    return x * x;
}
```

3. **Export Lists:**
   Alternatively, at the end of the module, an export list can specify all the items to be exported.

```pl
func square(x: Int): Int {
    return x * x;
}

func cube(x: Int): Int {
    return x * x * x;
}

export { square, cube };  // Export list
```

### Module Resolution:

1. **File-based Modules:**
   Modules could correspond to files in the filesystem, with the module name matching the file name.

2. **Folder-based Modules:**
   If a folder is specified instead of a file, the system could look for an `index` file in that folder as the module.

3. **Path Resolution:**
   A system of path resolution for finding modules, possibly with configurable paths and support for relative and absolute paths.

4. **Package Management:**
   A package management system could be developed to download and manage third-party modules, similar to npm or pip.

5. **Cyclic Dependencies:**
   The system should handle cyclic dependencies gracefully, possibly with an error or warning.

