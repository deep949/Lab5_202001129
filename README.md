# Lab5_202001129
Static Analysis


Name: Deep Jaimesh Shah<br>
ID: 202001129

GitHub Repo : https://github.com/randaller/llama-chat<br>
Tool Used : pylint extension in VSCode

Python Files in repo :<br>
1. example-chat.py
2. example.py
3. merge-weights.py
4. setup.py
5. __init__.py
6. generation.py
7. model.py
8. tokenizer.py



**List of all errors in the project directory.**

![image](https://user-images.githubusercontent.com/77284852/225572984-232d8a65-97ef-4701-803b-4dd442fd350c.png)

**Explaining the errors**

1. Type: [import]

![image](https://user-images.githubusercontent.com/77284852/225571858-e50e6c89-565b-469e-8981-0fb11aa5bd2b.png)

There are libraries for torch, torch.nn.functional, torch.nn.utils, and tqdm that have not yet been installed, as can be seen in the code at lines 11, 13, 14, and 16.

2. Type: [unspecified-encoding]

![image](https://user-images.githubusercontent.com/77284852/225577834-de526963-23fb-4cfa-a925-8eedd200cdc6.png)

Using open without explicitly specifying an encoding in line 42.


3. Type: [return value]

![image](https://user-images.githubusercontent.com/77284852/225572460-9d9fdc51-84e5-4515-bbd8-2396b12c04e6.png)

The function definition for "generate" states in line 36 that it will return a list of string values. Line 57 also initialises the variable "decoded" as an empty list with the initial values "None" and the size of the variable bsz. I.e., the size of the prompts.

![image](https://user-images.githubusercontent.com/77284852/225573109-0f8d44b9-d6ae-4b3f-88bd-ad55fb8c6fb0.png)

But, as can be seen, the list decoded is returned later on in the function while returning the value, in lines 110 and 116, which may not be saving all string values at each place. We are therefore receiving a return-value error.


4. Type: [assignment]

![image](https://user-images.githubusercontent.com/77284852/225574127-d8df7ee9-2057-4fff-80a9-1bb4b8748102.png)

The function definition declares a variable of type list called file in line 50. However, a value of None is given to the file at line 76, which is incompatible.

5. Type: [call-overload]

![image](https://user-images.githubusercontent.com/77284852/225574533-7dc4d3b6-05be-4a71-8910-a1cf65901824.png)

If d is None when the value of decoded is set, an error occurs when the value of decoded is assigned.

6. Type: [f-string]

![image](https://user-images.githubusercontent.com/77284852/225575415-86be09a7-610f-4a14-a6e1-f2bcf5232366.png)

Using an f-string that does not have any interpolated variables. Used when we detect an f-string that does not use any interpolation variables, in which case it can be either a normal string or a bug in the code.

7. Type: [name-defined]

![image](https://user-images.githubusercontent.com/77284852/225574986-3ccb1506-e4d5-47c9-900e-1ad2c6680c21.png)

The variable prompt_tokens_len is never used again in the code and is redundant.

8. Type: [missing-function-docstring]

![image](https://user-images.githubusercontent.com/77284852/225579685-ff617c6b-6c54-4143-8cf9-588e375f925a.png)

Line number 34, 39 has missing function or method docstring used when a function or method has no docstring. Some special methods like __init__ , protected, private functions, setters and deleters do not require a docstring.
