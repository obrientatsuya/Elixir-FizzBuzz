# Elixir-FizzBuzz
fizzbuzz with elixir :) 

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
