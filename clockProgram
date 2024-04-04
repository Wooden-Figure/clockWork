/* This program clockProgram (main.cpp) takes the current time from the user and outputs the time as
 * 12-hour and 24-hour clock. There are four different selections on the menu: increase hour, minute, second
 * or quit. These change the user's time. This program uses strings, classes, integers, switch statements,
 * boolean phrases, break statements, and others. Use this program if you want two clocks that update as requested.
 *
 * Author: Robert Soto
 * Date Created: 3/21/2024
 * Revisions: NA
 */

#include <iostream>
#include <string>
using namespace std;

// makes sure that the numbers are in a certain format even when there is only 1 number
string twoDigitString(int num) {
    // If the # is smaller than 10, it adds a 0
    return (num < 10) ? "0" + to_string(num) : to_string(num);
}

// used a class related to all time functions
class Time {
private:
    // initial variables used throughout the program
    int hour; // Stores hours in 24-hour format
    int minute;
    int second;

public:
    // starts the time at 0 across the board for all variables
    Time() : hour(0), minute(0), second(0) {}

    // ran into an issue where these variables were being mistaken for the original
    void setUserTime(int newHour, int newMinute, int newSecond) {
        hour = newHour % 24;
        minute = newMinute % 60;
        second = newSecond % 60;
    }

    // outputs the time in a 12-hour format, additionally outputs the AM/ PM
    [[nodiscard]] string getTwelveHourTime() const {
        int hour12 = hour % 12;
        hour12 = (hour12 == 0) ? 12 : hour12; // Convert 0 to 12 for 12-hour format
        string period = (hour < 12) ? "AM" : "PM";
        return twoDigitString(hour12) + ":" + twoDigitString(minute) + ":" + twoDigitString(second) + " " + period;
    }

    // outputs the time in a 24-hour format
    [[nodiscard]] string getTwentyFourHourTime() const {
        return twoDigitString(hour) + ":" + twoDigitString(minute) + ":" + twoDigitString(second);
    }

    // adds an hour to the time
    void addOneHour() {
        hour = (hour + 1) % 24;
    }

    // adds a minute to the time, if the minute causes the hour to go over - it adjusts for that
    void addOneMinute() {
        minute = (minute + 1) % 60;
        if (minute == 0) hour = (hour + 1) % 24; // Increment hour if minutes wrap
    }

    // adds a second to the time, similarly to the minute this function allows the program to adjust if the minute/ hour
    // is pushed over
    void addOneSecond() {
        second = (second + 1) % 60;
        if (second == 0) { // Increment minute (and possibly hour) if seconds wrap
            minute = (minute + 1) % 60;
            if (minute == 0) {
                hour = (hour + 1) % 24;
            }
        }
    }
};


void PrintClocks(const Time& myTime) {
    string twelveHourTime = myTime.getTwelveHourTime();
    string twentyFourHourTime = myTime.getTwentyFourHourTime();

    // 12-Hour Clock
    cout << endl;
    cout << "**************************" << endl;
    cout << "*       12-Hour Clock    *" << endl;
    cout << "*        " << twelveHourTime << "     *" << endl;
    cout << "**************************" << endl;

    // space between clocks
    cout << endl;

    // 24-Hour Clock
    cout << "**************************" << endl;
    cout << "*       24-Hour Clock    *" << endl;
    cout << "*        " << twentyFourHourTime << "        *" << endl;
    cout << "**************************" << endl;
    cout << endl;
}

// prints the menu
void PrintMenu() {
    cout << "************************" << endl;
    cout << "* Menu:                *" << endl;
    cout << "* 1 - Add One Hour     *" << endl;
    cout << "* 2 - Add One Minute   *" << endl;
    cout << "* 3 - Add One Second   *" << endl;
    cout << "* 4 - Exit Program     *" << endl;
    cout << "************************" << endl << endl;
}

int main() {
    bool quit = false;
    // saves the user's input
    int userOption;
    Time myTime;

    // initial time setup
    int initialHour, initialMinute, initialSecond;
    cout << "Enter initial hour (24-hour format): ";
    cin >> initialHour;
    cout << "Enter initial minute: ";
    cin >> initialMinute;
    cout << "Enter initial second: ";
    cin >> initialSecond;

    // sets the time to the user input
    myTime.setUserTime(initialHour, initialMinute, initialSecond);

    // shows the time
    PrintClocks(myTime);

    // loop ends upon quit
    while (!quit) {
        PrintMenu();
        cout << "Enter option: ";
        cin >> userOption;

        switch (userOption) {
            case 1:
                myTime.addOneHour();
                break;
            case 2:
                myTime.addOneMinute();
                break;
            case 3:
                myTime.addOneSecond();
                break;
            case 4:
                cout << "Quitting program." << endl;
                quit = true; // exits the program
                continue; // skip the time print for exit
            default:
                cout << "That is not a correct input! Input a number between 1 - 4.\n" << endl;
                continue; // skip the time print for incorrect input
        }
        // display updated time
        PrintClocks(myTime);
    }
    return 0;
}
