<h1>
  <span class="headline">Python Error Handling and Debugging</span>
  <span class="subhead">Programmatic Error Handling</span>
</h1>

**Learning objective:** By the end of this lesson, students will be able to implement try and except blocks to handle errors gracefully in Python programs, anticipate potential error scenarios, and raise custom exceptions to manage unexpected user inputs and external data issues.

| Lesson                      | Duration |
| --------------------------- | -------- |
| Programmatic Error Handling | 20 min   |

## User Input: Causing Errors Since Forever

### Common Offenders:

- Applications that require user input will, inevitably, get input from the user that isn't valid or doesn't make sense for the program.
- Applications that make requests to external data sources can sometimes get bad results, or no results, in response to their requests.

We need a way of creating programs that can anticipate when a block of code might run into an error.

> 💡 Ideally, we can keep modifying our programs until they're free of errors. However, for some programs, errors are inevitable. Applications that require user input and those that make requests to external data sources are repeat offenders.

## Try and Except Your Code

Fortunately, errors don't have to be the end of the world! Once you start to anticipate what could go wrong, you can use `try` and `except` statements to plan ahead.

```python
try:
    starting_value = int(input("Give me a number one through ten"))
except ValueError:
    print("Your input was not a number. Try again.")
```

> It is important to note the indentation, which defines which code block might throw the error, and what code should execute in the case of the expected error.

Try-Except statements are one way we can catch errors in Python. Sometimes you may expect certain code to throw an error, and you may want to handle that situation with a smooth error message as opposed to having your whole program shut down.

## Try-Except Options

We can catch -

**One error**:

```python
except ValueError:
```

**Multiple errors**:

```python
except (ValueError, KeyError):
```

**Any/every error**:

```python
except err:
```

> Always try to specify the error, if possible! You can even string several except statements to handle different errors differently.

## Accessing an Error

You can use the `as` statement, or aliasing, to turn your exception into a specific, accessible object:

```python
try:
    risky_function()
except ValueError as value_err:
    print("Value error: ", value_err)
except Exception as err:
    print(err)
```

> In this example, we have a catch-all except at the end, just in case there's a totally unanticipated type of error.

## Creating Your Own Errors (On Purpose This Time)

Sometimes, you might want your program to raise an error deliberately. This can be useful when the user's input doesn't meet certain expectations.

```python
lucky_number = int(input("Type a number that's less than 100"))
if(lucky_number > 100):
    raise ValueError("The number needs to be less than 100!")
```

But why would you do this?

Raising your own error helps ensure that the program stops if something unexpected happens. This is similar to how built-in errors work. Unless you handle the error with a try-except block, it will shut down the program, alerting the user that something went wrong.

<br>

<div class="activity discussion">
  <h2 class="title">Error Handling Possibilities</h2>
  <span class="minutes"></span>
</div>

Proper error handling is all about thinking through every possibility. You should have a plan for every logical situation. What's the plan below? Add comments to the code block to explain what each line is doing.

```python
try:
    lucky_number = int(input("Type a number that's less than 100"))
    if(lucky_number > 100):
        raise ValueError("The number needs to be less than 100!")
    process_valid_number(lucky_number)
except ValueError as err:
    print("You need to provide a number")
```

> We want a number that's less than 100, so there's three possibilities: We're not given a number, we're given a number that's not less than 100, or we're given a number that's less than 100.
