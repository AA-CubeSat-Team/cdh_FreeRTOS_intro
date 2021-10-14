# FreeRTOS tutorial for new CDH members
We developed this project as a way to get people up-to-speed with using the
FreeRTOS middleware.

FreeRTOS is an real-time operating system for microcontrollers designed to
schedule tasks and introduce multitasking.

If you encounter any difficulties, please contact Junqi on AACT Slack channel
or via email jy98@uw.edu

## Getting started
Things you need
- [Visual Studio 2019](https://visualstudio.microsoft.com/) or newer (community version should be free)
- a Window system

## Step  0
- the directory we will be using is `FreeRTOSv10.0.1\FreeRTOS\Demo\WIN32-MSVC`. We will be modifying the `main.c` file.
- use this [FreeRTOS documentation](https://www.freertos.org/a00106.html) for more information on the specific API.
- The most common API are:

| Task Creation| TaskControl|
|--------|-------|
| xTaskCreate() |  vTaskDelay()|
|xTaskDelete()| vTaskDelayUntil()|
||vTaskSuspend()|
||vTaskResume()|

## Step 1
- Navigate to the directory `FreeRTOSv10.0.1\FreeRTOS\Demo\WIN32-MSVC`. Inside,
you will find `WIN32.vcxproj` file. If you have Visual Studio installed, double
clicking the file will open the project in Visual Studio.
- Open `main.c` and navigate to **line 173**
- On line 173, you will find three `xTashHandle`, this is used to reference FreeRTOS tasks we will create later. Right now, they will be set to `NULL`


## Step 2
- Head to **line 158**, This is where we will create our tasks. Follow the [documentation](https://www.freertos.org/a00125.html) 
and example codes to implement the API call.
- Create the tasks with the following parameters

| Task |pritority | stack depth |
|-----|-----|-----|
|**Task1**|3|100|
|**Task2**|4|100|
|**Task3**|5|100|

- *Note: task with higher, i.e. larger number, pritority will take precedence when scheduled at the same time. You will see this later in the result.

## Step 3
- Head to **line 170**, this is where we will define the tasks itself.
- The internal structure of a task is similar to our main funtion, where the the setup code is place in front of a infinity loop (`while (1)` or `for(;;)`).
- The schedular tracks the infinity loop and will handle the tasks switching; the program does not get trap in one loop forever.
- Use `vTaskDelay()` to set the delay interval.
- Use `printf()` and `xTaskGetTickCount()` to display both task number and the current time ticks.

## Step 4
- `vTaskStartScheduler()` on **line 166** is used to initlize and start the schedular. Nothing needs to be done here.


## Step 5 
- On the top of the VS IDE, choose build the project and run the windows debug.
- A window should pop up and once the program is running. Read through the log and indentify that the period matches the delay.
- *Note from earlier: when tasks are running at the same time, tasks with higher priority get to operate first, this is why we see tasks3 finished before tasks2 during the same time tick.

</br>

## If you have trouble with the program, Or is finished the all steps
Head to the solution branch and take a look at the code I wrote. 

</br>

## Final thoughts
FreeRTOS helps us achieve multitasking ability by abstracting many internal mechanisms. We will mainly be developing our flight software within the tasks definition. I hope you learned the basic structure of FreeRTOS and feel less intimitated by it. Let me or Jay know if you have any other questions!
