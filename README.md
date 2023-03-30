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

### Source
```javascript
defmodule ElixirFizz do
 
  def build(file_name) do 
    file_name 
    |> File.read() |> handle_file()
  end

  defp handle_file({:ok, result}) do
    result 
    |> String.split(",") |> Enum.map(&convert_and_verify/1)
  end
     
      defp handle_file({:error, reason}), do: "file reading error, type: #{reason}"

  defp convert_and_verify(body) do 
    body
    |> String.to_integer() |> verify_numbers()
  end

  defp verify_numbers(number) when rem(number, 3) == 0 and rem(number, 5) == 0, do: :fizzbuzz
  defp verify_numbers(number) when rem(number, 3) == 0, do: :fizz
  defp verify_numbers(number) when rem(number, 5) == 0, do: :buzz
  defp verify_numbers(number), do: number
end
```
