# Ivan's Ruby style guide

You may not like all rules presented here, but they work very well for me and have helped producing high quality code.  Everyone is free to code however they want, write and follow their own style guides, but when you contribute to my code, please follow these rules:

## Formatting
* Use UTF-8.
* Use soft-tabs, 2 space width.
* Strip whitespace from all empty lines.
* Use Unix-style line endings.
* Use spaces around operators, after commas, colons and semicolons, around { and before }.
* No spaces after (, [ and before ], ).
* Indent when as deep as case.
e.g.
		
		case something
		when 1
			# do something here
		when 2
			# do something here
		else
			# do something else here
		end

* Do not indent code after `private` or `protected` statements.
All `end`'s should be consistently outdented if you do this correctly.
* Use an empty line before the return value of a method (unless it
  only has one line), and an empty line between method definitions.
* Document your code consistently where needed using your preferred documentation format e.g Rdoc
* Always write a Readme in the root of the project, preferably in Markdown.
* Use empty lines to break up a long method into logical paragraphs, but try to keep methods short and logical.
* Keep lines fewer than ~80 characters.
* Place public API methods at the top of your classes.

## Syntax
* If your class or module exposes more than one class method, nest them inside `class << self` instead of prefixing multiple methods with `self.`
* Use `def` with parentheses when there are arguments.
* Never use `for`, unless you exactly know why.
* Never use `then`.
* Use when x; ... for one-line cases.
* Use `&&`/`||` for boolean expressions, `and`/`or` for control flow.(Rule of thumb: If you have to use outer parentheses, you are using the wrong operators.)
* Avoid multiline ?:, use if.
* Suppress superfluous parentheses when calling methods, but keep them when calling "functions", i.e. when you use the return value in the same line.

    x = Math.sin(y)
    array.delete e
* Prefer {...} over do...end.  Multiline {...} is fine: having different statement endings (} for blocks, end for if/while/...) makes it easier to see what ends where. But use do...end for "control flow" and "method definitions" (e.g. in Rakefiles and certain DSLs.) Avoid do...end when chaining.
* Avoid return where not required.
* Avoid line continuation `\` where not required.
* Using the return value of = is okay:

		if v = array.grep(/foo/) ...

* Use ||= freely.
* Expect the default value of arguments to be nil and assign default on first line:

		def run(options = nil)
		  options ||= {}
		  ...

* Use non-OO regexps (they won't make the code better).  Freely use
  =~, $0-9, $~, $` and $' when needed.

## Naming
* Use `snake_case` for methods.
* Use `CamelCase` for classes and modules. (Keep acronyms like HTTP, RFC, XML uppercase.)
* Use `SCREAMING_SNAKE_CASE` for other constants.
* The length of an identifier determines its scope. Use one-letter
  variables for short block/method parameters, according to this
  scheme:

		a,b,c: any object
		d: directory names
		e: elements of an Enumerable
		ex: rescued exceptions
		f: files and file names
		i,j: indexes
		k: the key part of a hash entry
		m: methods
		o: any object
		r: return values of short methods
		s: strings
		v: any value
		v: the value part of a hash entry
		x,y,z: numbers

And in general, the first letter of the class name if all objects are of that type.

* Use _ or names prefixed with _ for unused variables.
* When using inject with short blocks, name the arguments |a, e|
  (mnemonic: accumulator, element)
* Prefer `map` over `collect`, `find` over `detect`, `find_all` over `select`, `size` over `length`.

## Comments
* Comments longer than a word are capitalised and use punctuation.
* Avoid superfluous comments, your code should be self documenting.

## Testing
* Prefer RSpec over TestUnit.
* Use TDD and BDD as much as possible.
* Write the minimum amount of code to make your tests pass. If you feel the need to write more code – you're probably not testing it properly.
* Follow the Red, Green, Refactor pattern.
* Write unit tests which do not require huge amounts of fixtures in order to run, if they do then you're doing it wrong.
* Only test your public API methods, private methods should be tested as a result of testing public methods.

## Rails specific
## Views
* Use snake_case for IDs
* Use dashes for class names e.g main-content
