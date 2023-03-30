# Elixir-FizzBuzz
FizzBuzz with Elixir :)
Using Pattern matching, Guards and Pipe Controller.

### Creation requirements

- [x] Multiples of 3 replaced by Fizz
- [x] Multiples of 5 replaced by Buzz
- [x] Multiples of 3 and 5 replaced by FizzBuzz

### Example
Input -
```batch
[1, 2, 3, 4, 5, 10, 15, 20] 
```
Output -
```batch
[1, 2, fizz, 4, buzz, buzz, fizzbuzz, buzz]
```
<hr>

### Source Explication

This is an Elixir module called "ElixirFizz" that defines a function called "build" and some private functions. Here's an explanation of what the code does line by line:

```javascript
defmodule ElixirFizz do
```
Declaration of a new module called "ElixirFizz".


```javascript
def build(file_name) do 
  file_name 
  |> File.read() |> handle_file()
end
```
Declaration of the "build" function that takes a parameter "file_name", which is the name of a file to be read. The function reads the contents of the file and passes the result to the private function "handle_file".


```javascript
defp handle_file({:ok, result}) do
  result 
  |> String.split(",") |> Enum.map(&convert_and_verify/1)
end
```
Declaration of a private function called "handle_file" that takes a tuple with the tag :ok and the result of the file read. The function splits the content of the file into a list of strings using "," as a separator, and then calls the private function "convert_and_verify" for each element in the list.

```javascript
defp handle_file({:error, reason}), do: "file reading error, type: #{reason}"
```

Declaration of another private function "handle_file" that takes a tuple with the tag :error and the reason for the file read error. This function returns a string with the error message.


```javascript
defp convert_and_verify(body) do 
  body
  |> String.to_integer() |> verify_numbers()
end
```
Declaration of a private function "convert_and_verify" that takes a string. The function converts the string to an integer using "String.to_integer" and then calls the private function "verify_numbers" to check if the number is divisible by 3, 5, or both.

```javascript
defp verify_numbers(number) when rem(number, 3) == 0 and rem(number, 5) == 0, do: :fizzbuzz
defp verify_numbers(number) when rem(number, 3) == 0, do: :fizz
defp verify_numbers(number) when rem(number, 5) == 0, do: :buzz
defp verify_numbers(number), do: number
```
Declaration of four private functions "verify_numbers" that take an integer number. These functions check if the number is divisible by 3, 5, or both. If the number is divisible by 3 and 5, the function returns :fizzbuzz, if it's only divisible by 3, the function returns :fizz, if it's only divisible by 5, the function returns :buzz, and otherwise, the function returns the number itself.

In summary, the "ElixirFizz" module contains a "build" function that reads the contents of a file, converts each number to an integer, and checks if the number is divisible by 3, 5, or both. The "build" function returns a list with the numbers or with :fizz, :buzz, or :fizzbuzz, depending on the divisibility of each number.

