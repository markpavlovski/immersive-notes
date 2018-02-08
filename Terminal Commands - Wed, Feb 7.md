# Tools

## Homebrew

- Specific to Mac
- brew --version
- brew update
- brew install

## Node

- node -v

## Git

- git --version

## Killing apps:

- Ctrl - C: throws error
- Ctrl - D: goes to end document

## Enviromnmental Variable

- printenv
- env

- which env - shows you wwhere a certain command lives

- setting an environmental var: export VARIABLE=123

  - This will set it up for the current session
  - to set it up for every time, we can put it in bash_profile

## $PATH

- usr/local/bin - user installed (maybe brew?)
- usr/bin - system

## resources

- <https://github.com/agarrharr/awesome-cli-apps>

  - A lot of good

## terminal commands

- using | will take output from the first command and stick it into second.
- printenv > envs.txt will write the output into a text file
- echo "END OF FILE" >> classmates.txt appends text to bottom of the file

- rm -rf folder/ removes the folder

## GREP Lecture

- 'Roger'.replace('R','r')
- regexone.com:
- . - dash is the escape character, which will read dot as a dot, not for its meaning of a wildcard
- [abc] - a or b or c
- [^b].. - will ignore any three letter word that starts with b using carrot

## From Regexone.com:

```
abc…    Letters
123…    Digits
\d    Any Digit
\D    Any Non-digit character
.    Any Character
\.    Period
[abc]    Only a, b, or c
[^abc]    Not a, b, nor c
[a-z]    Characters a to z
[0-9]    Numbers 0 to 9
\w    Any Alphanumeric character
\W    Any Non-alphanumeric character
{m}    m Repetitions
{m,n}    m to n Repetitions
*    Zero or more repetitions
+    One or more repetitions
?    Optional character
\s    Any Whitespace
\S    Any Non-whitespace character
^…$    Starts and ends
(…)    Capture Group
(a(bc))    Capture Sub-group
(.*)    Capture all
(abc|def)    Matches abc or def



\s will search for space (␣), the tab (\t), the new line (\n) and the carriage return (\r) (useful in Windows environments),
```

## using grep

1. grep "by Dan Brown" books.txt
2. sort books.txt >> sorted_books.txt
3. sort books.txt | grep "by George Orwell" >> books_by_george_orwell.txt

4. Bonus:

We need to take a list of books, get the list of authors, and write unique sorted list to a file.

```

grep -o 'by .*' books.txt |  grep -o '[A-Z].*' | sort -u > authors.txt
```

Define pattern one letter at a time, the * sign is used to repeat the previous pattern.

--------------------------------------------------------------------------------

## Solutions to Command Line Mystery:

1. Find all people who have all 4 memberships:

  ```
  grep -f AAA Museum_of_Bash_History | grep -f Delta_SkyMiles | grep -f Terminal_City_Library > ../my_solution/SUSPECTS
  ```

2. Find All male suspects:

  ```
  grep -f my_solution/SUSPECTS people | grep "M\t" | grep -o "[A-Z].*[a-z].[A-Z].*[a-z]\t" > my_solution/MALE-SUSPECTS
  ```

3. Find all Annabels

  ```
  grep "Annabel" ../people > ANNABEL
  ```

4. Find interviews that mentioned cars

  ```
  grep " car " interview/*
  ```

5. Identify drivers of the car that matches the descriptions given by Annabel.

  ```
  grep -A 5 "L337.*9.*" vehicles |
  grep -B 2 -A 3 "Color: Blue" |
  grep -B 4 -A 1 "Height: 6.*" |
  grep "Make: Honda" -B 1 -A 4 |
  grep -o "wner:.*" | grep -o "[A-Z].*" |
  grep -f my_solution/SUSPECTS >
  my_solution/FINAL-SUSPECTS
  ```

6. And finally we get the likely offender, Jeremy Bowers:

```
grep -f my_solution/FINAL-SUSPECTS my_solution/MALE-SUSPECTS
```

### And finally we get the likely offender, **Jeremy Bowers**!

<!-- if __name__ == '__main__': rpn = RON() rpn.run also try: except: loop -->
