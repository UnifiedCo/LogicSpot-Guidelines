# LogicSpot JavaScript standards

This is a set of coding conventions and rules for use in JavaScript programming.

These rules are based on [Code Conventions for the JavaScript Programming Language](#http://javascript.crockford.com/code.html) by Douglas Crockford

## Table of Contents
1. [JavaScript Files](#javascript-files)
1. [Whitespace](#whitespace)
1. [Comments](#comments)
1. [Variable Declarations](#variable-declarations)
1. [Function Declarations](#function-declarations)
1. [Names](#names)
1. [Statements](#statements)
	- [Simple Statements](#simple-statements)
    - [Compound Statements](#compound-statements)
    - [Labels](#labels)
    - [return Statement](#return-statement)
    - [if Statement](#if-statement)
    - [for Statement](#for-statement)
    - [while Statement](#while-statement)
    - [do Statement](#do-statement)
    - [switch Statement](#switch-statement)
    - [try Statement](#try-statement)
    - [continue Statement](#continue-statement)
    - [with Statement](#with-statement)
1. {} and []
	- , comma Operator
	- [Assignment Expressions](#assignment-expressions)
	- === and !== Operators.
	- [Confusing Pluses and Minuses](#confusing-pluses-and-minuses)
	- [eval is Evil](#eval-is-evil)

## JavaScript Files

JavaScript programs should be stored in and delivered as .js files.

JavaScript code should not be embedded in HTML files unless the code is specific to a single session. Code in HTML adds significantly to pageweight with no opportunity for mitigation by caching and compression.

## Whitespace

Blank spaces should always be used in the following circumstances:

- A keyword followed by `(` left parenthesis should be separated by a space. Spaces are used to make things that are not invocations look less like invocations, so for example, there should be space after `if` or `while`.
- A blank space should not be used between a function value and its invoking `(` left parenthesis. This helps to distinguish between keywords and function invocations.
- The word function is always followed with one space.
- No space should separate a unary operator and its operand except when the operator is a word such as typeof.
- All binary operators should be separated from their operands by a space on each side except `.` period and `(` left parenthesis and `[` left bracket.
- Every `,` comma should be followed by a space or a line break.
- Each `;` semicolon at the end of a statement should be followed with a line break.
- Each `;` semicolon in the control part of a for statement should be followed with a space.

Every statement should begin aligned with the current indentation. The outermost level is at the left margin. The indentation increases by 4 spaces when the last token on the previous line is { left brace, [ left bracket, ( left paren. The matching closing token will be the first token on a line, restoring the previous indentation.

The ternary operator can be visually confusing when nesting, so if you're nesting `?` question mark always begins a line and increase the indentation by 4 spaces, and : colon always begins a line, aligned with the ? question mark.

```javascript
var integer = function (
    value,
    default_value
) {
    value = resolve(value);
    return (typeof value === "number")
        ? Math.floor(value)
        : (typeof value === "string")
            ? value.charCodeAt(0)
            : default_value;
};
```

If `.` period is the first character on a line, the indentation is increased by 4 spaces.

Avoid excessively long lines. When a statement will not fit nicely on a single line, it may be necessary to break it. It is best to break after a `{` left brace, `[` left bracket, `(` left paren, `,` comma, or before a `.` period, `?` question mark, or `:` colon. If such a break is not feasible, then break after an operator and continue on the next line with 8 spaces added to the current indentation. Those 8 spaces do not change the current indentation.

Clauses (`case`, `catch`, `default`, `else`, `finally`) are not statements and so should not be indented like statements.

Tabs and spaces should not be mixed. We should pick just one in order to avoid the problems that come from having both. Personal preference is an extremely unreliable criteria. Neither the tab nor the space offers a powerful advantage over the other. Fifty years ago, tab had the advantage of consuming less memory, but Moore's Law has eliminated that advantage. Space has one clear advantage over tab: there is still no reliable standard for how many spaces a tab represents, but it is universally accepted that a space occupies a space. So always use spaces. You can edit with tabs if you must, but make sure it is spaces again before you commit. Maybe someday we will finally get a universal standard for tabs, but until that day comes, the better choice is spaces.

## Comments

Be generous with comments. It is useful to leave information that will be read at a later time by people (possibly your future self) who will need to understand what you have done and why. The comments should be well-written and clear, just like the code they are annotating. An occasional nugget of humor might be appreciated. Frustrations and resentments will not.

It is important that comments be kept up-to-date. Erroneous comments can make programs even harder to read and understand.

Make comments meaningful. Focus on what is not immediately visible. Don't waste the reader's time with stuff like

```javascript
i = 0; // Set i to zero.
```
Generally use line comments. Save block comments for formal documentation.

## Variable Declarations

All variables should be declared before used. JavaScript does not require this, but doing so makes the program easier to read and makes it easier to detect undeclared variables that may become implied. Implied global variables should never be used. Use of global variables should be minimized.

The var statement should be the first statement in the function body.

It is preferred that each variable declarative statement and comment. They should be listed in alphabetical order if possible.

```javascript
var currentEntry; // currently selected table entry
var level;        // indentation level
var size;         // size of table
```

A JavaScript var does not have block scope, so defining variables in blocks can confuse programmers who are experienced with other C family languages. Define all variables at the top of the function.

## Function Declarations

All functions should be declared before they are used. Inner functions should follow the var statement. This helps make it clear what variables are included in its scope.

There should be no space between the name of a function and the `(` left parenthesis of its parameter list. There should be one space between the `)` right parenthesis and the `{` left curly brace that begins the statement body. The body itself is indented four spaces. The `}` right curly brace is aligned with the line containing the beginning of the declaration of the function.

```javascript
function outer(c, d) {
    var e = c * d;

    function inner(a, b) {
        return (e * a) + b;
    }

    return inner(0, 1);
}
```

This convention works well with JavaScript because in JavaScript, functions and object literals can be placed anywhere that an expression is allowed. It provides the best readability with inline functions and complex structures.

```javascript
function getElementsByClassName(className) {
    var results = [];
    walkTheDOM(document.body, function (node) {
        var array;                // array of class names
        var ncn = node.className; // the node's classname

		// If the node has a class name, then split it into a list of simple names.
		// If any of them match the requested name, then append the node to the list of results.

        if (ncn && ncn.split(" ").indexOf(className) >= 0) {
            results.push(node);
        }
    });
    return results;
}
```

If a function literal is anonymous, there should be one space between the word function and the ( left parenthesis. If the space is omitted, then it can appear that the function's name is function, which is an incorrect reading.

```javascript
div.onclick = function (e) {
    return false;
};

that = {
    method: function () {
        return this.datum;
    },
    datum: 0
};
```

Use of global functions should be minimized.

When a function is to be invoked immediately, the entire invocation expression should be wrapped in parens so that it is clear that the value being produced is the result of the function and not the function itself.

```javascript
var collection = (function () {
    var keys = [];
    var values = [];

    return {
        get: function (key) {
            var at = keys.indexOf(key);
            if (at >= 0) {
                return values[at];
            }
        },
        set: function (key, value) {
            var at = keys.indexOf(key);
            if (at < 0) {
                at = keys.length;
            }
            keys[at] = key;
            values[at] = value;
        },
        remove: function (key) {
            var at = keys.indexOf(key);
            if (at >= 0) {
                keys.splice(at, 1);
                values.splice(at, 1);
            }
        }
    };
}());
```

## Names

Names should be formed from the 26 upper and lower case letters (A .. Z, a .. z), the 10 digits (0 .. 9), and _ underbar. Avoid use of international characters because they may not read well or be understood everywhere. Do not use `$` dollar sign or `\` backslash in names.

Do not use `_` underbar as the first or last character of a name. It is sometimes intended to indicate privacy, but it does not actually provide privacy. If privacy is important, use closure. Avoid conventions that demonstrate a lack of competence.

Most variables and functions should start with a lower case letter.

Constructor functions that must be used with the new prefix should start with a capital letter. JavaScript issues neither a compile-time warning nor a run-time warning if a required new is omitted. Bad things can happen if new is not used, so the capitalization convention is the only defense we have.

Global variables should be in all caps. (JavaScript does not have macros, so there isn't much point in using all caps to signify a feature that JavaScript doesn't have.)

## Statements

### Simple Statements

Each line should contain at most one statement. Put a `;` semicolon at the end of every simple statement. Note that an assignment statement that is assigning a function literal or object literal is still an assignment statement and must end with a semicolon.

JavaScript allows any expression to be used as a statement. This can mask some errors, particularly in the presence of semicolon insertion. The only expressions that should be used as statements are assignments and invocations.

### Compound Statements

Compound statements are statements that contain lists of statements enclosed in { } curly braces.

- The enclosed statements should be indented four more spaces.
- The `{` left curly brace should be at the end of the line that begins the compound statement.
- The `}` right curly brace should begin a line and be indented to align with the beginning of the line containing the matching `{` left curly brace.
- Braces should be used around all statements, even single statements, when they are part of a control structure, such as an if or for statement. This makes it easier to add statements without accidentally introducing bugs.

### Labels

Statement labels should be avoided. Only these statements should be labeled: `while`, `do`, `for`, `switch`.

### return Statement

The return value expression must start on the same line as the return keyword in order to avoid semicolon insertion.

### if Statement

The if class of statements should have the following form:

```javascript
if (condition) {
    statements
}

if (condition) {
    statements
} else {
    statements
}

if (condition) {
    statements
} else if (condition) {
    statements
} else {
    statements
}
```

### for Statement

A for class of statements should have the following form:

```javascript
for (initialization; condition; update) {
    statements
}
```

### while Statement

A while statement should have the following form:

```javascript
while (condition) {
    statements
}
```

### do Statement

A do statement should have the following form:

```javascript
do {
    statements
} while (condition);
```

Unlike the other compound statements, the do statement always ends with a ; semicolon.

### switch Statement

A switch statement should have the following form:

```javascript
switch (expression) {
case expression:
    statements
default:
    statements
}
```

Each case is aligned with the switch. This avoids over-indentation. A case label is not a statement, and should not be indented like one.

Each group of statements (except the default) should end with break, return, or throw. Do not fall through.

### try Statement

The try class of statements should have the following form:

```javascript
try {
    statements
} catch (variable) {
    statements
}

try {
    statements
} catch (variable) {
    statements
} finally {
    statements
}
```

### continue Statement

Avoid use of the continue statement. It tends to obscure the control flow of the function.

### with Statement

The with statement should not be used.

## {} and []

Use `{}` instead of new `Object()`. Use `[]` instead of `new Array()`.

Use arrays when the member names would be sequential integers. Use objects when the member names are arbitrary strings or names.

### , comma Operator

Avoid the use of the comma operator. (This does not apply to the comma separator, which is used in object literals, array literals, var statements, and parameter lists.)

### Assignment Expressions

Avoid doing assignments in the condition part of if and while statements.

Is

```javascript
if (a = b) {
```

a correct statement? Or was

```javascript
if (a == b) {
```

intended? Avoid constructs that cannot easily be determined to be correct.

### === and !== Operators.

Use the `===` and `!==` operators. The `==` and `!=` operators do type coercion and should not be used.

### Confusing Pluses and Minuses

Be careful to not follow a `+` with `+` or `++`. This pattern can be confusing. Insert parens between them to make your intention clear.

```javascript
total = subtotal + +myInput.value;
```

is better written as

```javascript
total = subtotal + (+myInput.value);
```

so that the `+` `+` is not misread as `++`. Avoid `++`.

### eval is Evil

The eval function is the most misused feature of JavaScript. Avoid it.

eval has aliases. Do not use the Function constructor. Do not pass strings to setTimeout or setInterval.
