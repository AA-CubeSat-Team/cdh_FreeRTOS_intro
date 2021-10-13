# FreeRTOS Tutorial for new CDH members
We developed this project as a way to get people up-to-speed with using the
FreeRTOS middleware.

FreeRTOS is an real-time operating system for microcontrollers designed to
schedule tasks and introduce multitasking.

If you encounter any difficulties, please contact Junqi on AACT Slack channel
or via email jy98@uw.edu

## Getting started
Things you need
- Visual Studio 2019 or newer
- a Window system

## Step  0
- the directory we will be using is `FreeRTOSv10.0.1\FreeRTOS\Demo\WIN32-MSVC`
and we will be modifying the `main.c` file.
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
clicking the file will open the project on Visual Studio.
- Open `main.c` and navigate to **line 173**
