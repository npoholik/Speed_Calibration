# CSCI2100_DataStruct_SpeedCalibration

> CSCI 2100 Final Project to calibrate data given in the form of a text file

----------------------------------------------------------------------------------------------------

The overall goal of this project and the program is to allow the user to access all necessary information regarding the GPS and smart watch data and subsequent calculations from it. As such, the GPS and smart watch data will be stored in member arrays of their respective class objects. The calculated accurate speed will be stored in a vector in the main function, and any further calculations involving this vector will be performed in functions defined in the main file. 

----------------------------------------------------------------------------------------------------

## Helpful References:

[C++ Language](https://cplusplus.com/doc/tutorial/)

----------------------------------------------------------------------------------------------------

## Results
1. Initialization:

![Alt text](Results/Initialization.png?raw=true "Initialization")

2. Main Menu:

![Alt text](Results/Menu.png?raw=true "Menu")

3. Searching for Speed:

![Alt text](Results/SearchingForSpeed.png?raw=true "SearchingForSpeed")

----------------------------------------------------------------------------------------------------

## Design Details
> The following is a short write up written as part of the final project report for CSCI 2100

Both the smart watch and the GPS classes hold the same member functions and variables. They both have two arrays initialized with a size of 99, one to store the raw data from the text file, and the other to store the data with the noise and inaccurate elements removed. They also have a member variable to store the noise. The constructor for both of these functions will use ifstream to read in data from their corresponding text file and input it into both arrays. A call to findWrongData for the adjusted array will be made, which will print the inaccurate values to the user while also setting them equal to -1. A call to findNoise for the adjusted array will be made, which will find the noise value for the member variable. Finally, a call to removeNoise for the adjusted array will be made so that all data will be corrected for the approximate noise. The destructor for both the smart watch and GPS will print a message to the ussr informing them that the database has been deleted. The function findNoise will set noise equal to the first element in the array, as speed is supposed to be 0 m/s, thus any deviation will approximate the noise. The function findWrongData will iterate through the array passed, and compare the current index to the previous and look for a fluctuation of +5 or -5 in speed. It is assumed that speed cannot change that quickly in a one second span, thus if that occurs at a value it will be printed out to the user and the value will be set equal to -1 for further use. The function removeNoise iterates through the passed array and simply subtracts the noise value stored in the member variable from each element. The function printData will iterate through the raw data array and print out each element from it. The function getIndex will return the value stored at any index passed. The function printInformation will be utilized in main, and will print out the noise as well as iterate through the raw data once again to find the inaccurate values. Finally, findSpeed will once again be utilized in main, and will take a value from the user, cast it to an int, and iterate through the raw data using a pointer to find a speed near the passed value. 

In main, there are three functions defined for use with a vector. The first is calculateSpeed, which will take a reference of the GPS and smart watch objects as well as the vector. This function will then iterate for all the elements in the adjusted arrays of the GPS and smart watch except for index 0, which has the value 0 pushed to it, and calculate their average if they are both valid entries. If one or the other is not valid, then only the valid entry will be pushed to the vector. If both of the entries are invalid, -1 will be pushed to indicate this and a message will be printed. The second function printSpeed will simply iterate through the vector and print out the speed at each index. Finally, the third function calculateAcceleration will find the acceleration for a given time passed by the user. It will print out 0 m/s^2 at 1, out of bounds for any time outside of 1-99, and for any time in between it will calculate the acceleration by dividing the difference of the current speed and previous speed over the current time and previous time. 

The actual main function of the program simply initializes a GPS object and a smart watch object, performs the real speed calculation, prints the result, and then prompts the user for menu options where they can print any necessary information they need using the previously defined functions. 
