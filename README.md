# Windows-basic-commands-batchscript
Ex08-Windows-basic-commands-batchscript

# AIM:
To execute Windows basic commands and batch scripting

# DESIGN STEPS:

### Step 1:

Navigate to any Windows environment installed on the system or installed inside a virtual environment like virtual box/vmware 

### Step 2:

Write the Windows commands / batch file . Save each script in a file with a .bat extension. Ensure you have the necessary permissions to perform the operations. Adapt paths as needed based on your system configuration.
### Step 3:

Execute the necessary commands/batch file for the desired output. 




# WINDOWS COMMANDS:
## Exercise 1: Basic Directory and File Operations
Create a directory named "my-folder"

## COMMAND AND OUTPUT
![445628639-95be5947-af99-4821-a2b0-40df82c5b331](https://github.com/user-attachments/assets/6286f3ec-68c9-483a-a7c8-bd736be55ad1)


Remove the directory "my-folder"

## COMMAND AND OUTPUT
![445651439-8c7d24cf-4a76-4577-aadb-39ad07f1119e](https://github.com/user-attachments/assets/3f280ec9-0b72-4d82-81ff-cd75e1b227a3)


Create the file Rose.txt

## COMMAND AND OUTPUT
![445651857-e0a014e9-31be-4abd-bf79-a4c2a4481450](https://github.com/user-attachments/assets/9462134b-dea3-4a62-9a96-c4437b1ccd7d)


Create the file hello.txt using echo and redirection

## COMMAND AND OUTPUT
![445652236-1064fa0e-ba45-447b-abcc-1396d7b49efe](https://github.com/user-attachments/assets/e5a515c3-0485-4097-96f9-35ae0a59f24c)

Copy the file hello.txt into the file hello1.txt

## COMMAND AND OUTPUT
![445652889-0094a22d-96c6-48d6-97a6-d874651e0d90](https://github.com/user-attachments/assets/e9874443-a1b7-4db8-9cff-d49bd0804e9d)

Remove the file hello1.txt

## COMMAND AND OUTPUT
![445653971-a3ba46ca-8b7b-44e6-9221-6847a0c40684](https://github.com/user-attachments/assets/654e599b-eb0d-4160-a6c9-2bbc3571f841)

List out the file hello1.txt in the current directory

## COMMAND AND OUTPUT
![445654398-b738bf88-30b2-4fdf-896e-db3562cbf48f](https://github.com/user-attachments/assets/5333cb19-d83c-43c8-99be-b5df4e88ed45)

List out all the associated file extensions 

## COMMAND AND OUTPUT
![445653971-a3ba46ca-8b7b-44e6-9221-6847a0c40684](https://github.com/user-attachments/assets/678e71b1-4b39-4e25-bd46-43f3d0c3215e)


Compare the file hello.txt and rose.txt

## COMMAND AND OUTPUT
![445654398-b738bf88-30b2-4fdf-896e-db3562cbf48f](https://github.com/user-attachments/assets/b9ea4536-c0d0-4dde-a995-e22589ef899b)

## Exercise 2: Advanced Batch Scripting
Create a batch file named on the desktop. The batch file need to have a variable assigned with a desired name for ex. name="John" and display as "Hello, John".





## OUTPUT
@echo off
set name=John
echo Hello, %name%
pause
![445647413-6c011d00-6959-4f4d-8b11-43c45bcaa4dd](https://github.com/user-attachments/assets/1922ca43-b06a-4116-a18d-4d52f1c3f415)

![445647908-7f453def-106e-4ff0-b718-94627b5bf4a1](https://github.com/user-attachments/assets/63aa9e5b-ca49-4c11-bf72-91599f5de8c6)


Create a batch file  on the desktop that checks whether a user-input number is odd or not. The script should:
Prompt the user to enter a number.
Calculate the remainder when the number is divided by 2.
Display whether the number is odd or not.
Ask the user if they want to check another number.
Repeat the process if the user enters Y, and exit with a thank-you message if the user enters N.
Handle invalid inputs for the continuation prompt (Y/N) gracefully.



## OUTPUT
@echo off
:loop
set /p num=Enter a number: 
set /a rem=%num% %% 2

if %rem%==0 (
    echo %num% is Even
) else (
    echo %num% is Odd
)

:ask
set /p ans=Do you want to check another number? (Y/N): 
if /I "%ans%"=="Y" goto loop
if /I "%ans%"=="N" goto end
echo Invalid input. Please enter Y or N.
goto ask

:end
echo Thank you!
pause

![445648490-743fb946-f2fe-4177-aaa8-42fd945d345a](https://github.com/user-attachments/assets/b862aa66-924f-4d18-8adc-f455ab9341c3)



Write a batch file that uses a FOR loop to iterate over a sequence of numbers (1 to 5) and displays each number with the label Number:. The output should pause at the end.




## OUTPUT
@echo off
for /L %%i in (1,1,5) do (
    echo Number: %%i
)
pause

![445649075-2362bb0c-d8be-4e7e-8f2b-bd0e5a4a8bea](https://github.com/user-attachments/assets/67089cc3-2372-487d-b9be-23ee9e954f60)


Write a batch script to check whether a file named sample.txt exists in the current directory. If the file exists, display the message sample.txt exists. Otherwise, display sample.txt does not exist. Pause the script at the end to view the result.

Instructions:
Use the IF EXIST conditional statement.
Make sure the script works for files located in the same directory as the batch file.
Use pause to keep the command window open after displaying the message.
Expected Output (if the file exists):

## OUTPUT

@echo off
if exist sample.txt (
    echo sample.txt exists.
) else (
    echo sample.txt does not exist.
)
pause
![445649709-81b5a9a9-4af3-44ca-84ba-96dd515f496e](https://github.com/user-attachments/assets/b0423006-de23-402b-aa9a-c22475d6e55f)


Write a batch script that displays a simple menu with three options:
Say Hello – Displays the message Hello, World!
Create a File – Creates a file named newfile.txt with the content This is a new file
Exit – Exits the script with a goodbye message
The script should repeatedly display the menu until the user chooses to exit. Use goto statements to handle menu navigation.


## OUTPUT

@echo off
:menu
cls
echo 1. Say Hello
echo 2. Create a File
echo 3. Exit
set /p choice=Choose an option (1-3): 

if "%choice%"=="1" goto hello
if "%choice%"=="2" goto create
if "%choice%"=="3" goto exit
echo Invalid choice.
pause
goto menu

:hello
echo Hello, World!
pause
goto menu

:create
echo This is a new file > newfile.txt
echo File newfile.txt created.
pause
goto menu

:exit
echo Goodbye!
pause
exit
![445650251-d73a392d-d05f-4908-ad20-01686519af38](https://github.com/user-attachments/assets/55bba47b-fee6-4872-851f-4e19ddd77df0)




# RESULT:
The commands/batch files are executed successfully.

