## Code 2 ##

```arduino

/*
Cooper Dieterle
ECE 387
Final Project

Two number input corresponds to a preset selection.
The preset choices can be found commented in the code
*/

#include <Keypad.h>
#include <Servo.h>

Servo myservo_1;
Servo myservo_2;
Servo myservo_3;
Servo myservo_4;
Servo myservo_5;
Servo myservo_6;

int count = 0;

int var_1 = NO_KEY;
int var_2 = NO_KEY;

//Postion the servos are closed (Different for each servo)
int Close_servo_1 = 0;
int Close_servo_2 = 45;
int Close_servo_3 = 90;
int Close_servo_4 = 135;
int Close_servo_5 = 135;
int Close_servo_6 = 135;

//Postion the servos are open (Different for each servo)
int Open_servo_1 = 90;
int Open_servo_2 = 135;
int Open_servo_3 = 180;
int Open_servo_4 = 45;
int Open_servo_5 = 45;
int Open_servo_6 = 45;

//Time it takes for each amount of liquid (Depends on the size of the tubes)
int Prime_time = 500;
int One_shot = 2050;
int Two_shot = 3750;
int Three_shot = 5750;
int Fill_one = 11750;
int Fill_two = 9750;
int Fill_three = 7750;
int Fill_empty = 13750;

const byte ROWS = 4; //four rows
const byte COLS = 3; //three columns
char keys[ROWS][COLS] = {
{'1','2','3'},
{'4','5','6'},
{'7','8','9'},
{'*','0','#'}
};
byte rowPins[ROWS] = {5, 4, 3, 2}; //connect to the row pinouts of the keypad
byte colPins[COLS] = {8, 7, 6}; //connect to the column pinouts of the keypad

Keypad keypad = Keypad( makeKeymap(keys), rowPins, colPins, ROWS, COLS );

void setup(){
Serial.begin(9600);
myservo_1.attach(A5);
myservo_2.attach(9);
myservo_3.attach(10);
myservo_4.attach(11);
myservo_5.attach(12);
myservo_6.attach(13);

myservo_1.write(Close_servo_1);
myservo_2.write(Close_servo_2);
myservo_3.write(Close_servo_3);
myservo_4.write(Close_servo_4);
myservo_5.write(Close_servo_5);
myservo_6.write(Close_servo_6);
}

void loop(){
char key = keypad.getKey();

if (count == 0) {
if (key == '0'){
var_1 = 0;
count = count + 1;
}
if (key == '1') {
var_1 = 1;
count = count + 1;
}
if (key == '2') {
var_1 = 2;
count = count + 1;
}
if (key == '3') {
var_1 = 3;
count = count + 1;
}
if (key == '4'){
var_1 = 4;
count = count + 1;
}
if (key == '5') {
var_1 = 5;
count = count + 1;
}
if (key == '6') {
var_1 = 6;
count = count + 1;
}
if (key == '7') {
var_1 = 7;
count = count + 1;
}
if (key == '8') {
var_1 = 8;
count = count + 1;
}
if (key == '9') {
var_1 = 9;
count = count + 1;
}
if (key == '#') {
var_1 = NO_KEY;
var_2 = NO_KEY;
count = 0;
}
}

if (count == 1) {
key = NO_KEY;
count = count + 1;
}

if (count == 2) {
if (key == '0') {
var_2 = 0;
count = count + 1;
}
if (key == '1') {
var_2 = 1;
count = count + 1;
}
if (key == '2') {
var_2 = 2;
count = count + 1;
}
if (key == '3') {
var_2 = 3;
count = count + 1;
}
if (key == '4') {
var_2 = 4;
count = count + 1;
}
if (key == '5') {
var_2 = 5;
count = count + 1;
}
if (key == '6') {
var_2 = 6;
count = count + 1;
}
if (key == '7') {
var_2 = 7;
count = count + 1;
}
if (key == '8') {
var_2 = 8;
count = count + 1;
}
if (key == '9') {
var_2 = 9;
count = count + 1;
}
if (key == '#') {
var_1 = NO_KEY;
var_2 = NO_KEY;
count = 0;
}
}

if (count == 3) {
key = NO_KEY;
count = count + 1;
}

if (count == 4) {
if (key == '#') {
var_1 = NO_KEY;
var_2 = NO_KEY;
count = 0;
}
if (key == '*') {
if (var_1 == 0 && var_2 == 0) {
//Prime All
myservo_1.write(Open_servo_1);
myservo_2.write(Open_servo_2);
myservo_3.write(Open_servo_3);
myservo_4.write(Open_servo_4);
myservo_5.write(Open_servo_5);
myservo_6.write(Open_servo_6);
delay(Prime_time);
myservo_1.write(Close_servo_1);
myservo_2.write(Close_servo_2);
myservo_3.write(Close_servo_3);
myservo_4.write(Close_servo_4);
myservo_5.write(Close_servo_5);
myservo_6.write(Close_servo_6);
count = 0;
}
if (var_1 == 0 && var_2 == 1) {
//One Shot 1 Only
myservo_1.write(Open_servo_1);
delay(One_shot);
myservo_1.write(Close_servo_1);
count = 0;
}
if (var_1 == 0 && var_2 == 2) {
//Two Shot 1 Only
myservo_1.write(Open_servo_1);
delay(Two_shot);
myservo_1.write(Close_servo_1);
count = 0;
}
if (var_1 == 0 && var_2 == 3) {
//Three Shot 1 Only
myservo_1.write(Open_servo_1);
delay(Three_shot);
myservo_1.write(Close_servo_1);
count = 0;
}
if (var_1 == 0 && var_2 == 4) {
//One Shot 2 Only
myservo_2.write(Open_servo_2);
delay(One_shot);
myservo_2.write(Close_servo_2);
count = 0;
}
if (var_1 == 0 && var_2 == 5) {
//One Shot 2 Only
myservo_2.write(Open_servo_2);
delay(Two_shot);
myservo_2.write(Close_servo_2);
count = 0;
}
if (var_1 == 0 && var_2 == 6) {
//One Shot 2 Only
myservo_2.write(Open_servo_2);
delay(Three_shot);
myservo_2.write(Close_servo_2);
count = 0;
}
if (var_1 == 0 && var_2 == 7) {
//One Shot 3 Only
myservo_3.write(Open_servo_3);
delay(One_shot);
myservo_3.write(Close_servo_3);
count = 0;
}
if (var_1 == 0 && var_2 == 8) {
//Two Shot 3 Only
myservo_3.write(Open_servo_3);
delay(Two_shot);
myservo_3.write(Close_servo_3);
count = 0;
}
if (var_1 == 0 && var_2 == 9) {
//Three Shot 3 Only
myservo_3.write(Open_servo_3);
delay(Three_shot);
myservo_3.write(Close_servo_3);
count = 0;
}
if (var_1 == 1 && var_2 == 0) {
//One Shot 1, Rest 4
myservo_1.write(Open_servo_1);
delay(One_shot);
myservo_1.write(Close_servo_1);
myservo_4.write(Open_servo_4);
delay(Fill_one);
myservo_4.write(Close_servo_4);
count = 0;
}
if (var_1 == 1 && var_2 == 1) {
//One Shot 1, Rest 5
myservo_1.write(Open_servo_1);
delay(One_shot);
myservo_1.write(Close_servo_1);
myservo_5.write(Open_servo_5);
delay(Fill_one);
myservo_5.write(Close_servo_5);
count = 0;
}
if (var_1 == 1 && var_2 == 2) {
//One Shot 1, Rest 6
myservo_1.write(Open_servo_1);
delay(One_shot);
myservo_1.write(Close_servo_1);
myservo_6.write(Open_servo_6);
delay(Fill_one);
myservo_6.write(Close_servo_6);
count = 0;
}
if (var_1 == 1 && var_2 == 3) {
//Two Shot 1, Rest 4
myservo_1.write(Open_servo_1);
delay(Two_shot);
myservo_1.write(Close_servo_1);
myservo_4.write(Open_servo_4);
delay(Fill_two);
myservo_4.write(Close_servo_4);
count = 0;
}
if (var_1 == 1 && var_2 == 4) {
//Two Shot 1, Rest 5
myservo_1.write(Open_servo_1);
delay(Two_shot);
myservo_1.write(Close_servo_1);
myservo_5.write(Open_servo_5);
delay(Fill_two);
myservo_5.write(Close_servo_5);
count = 0;
}
if (var_1 == 1 && var_2 == 5) {
//Two Shot 1, Rest 6
myservo_1.write(Open_servo_1);
delay(Two_shot);
myservo_1.write(Close_servo_1);
myservo_6.write(Open_servo_6);
delay(Fill_two);
myservo_6.write(Close_servo_6);
count = 0;
}
if (var_1 == 1 && var_2 == 6) {
//Three Shot 1, Rest 4
myservo_1.write(Open_servo_1);
delay(Three_shot);
myservo_1.write(Close_servo_1);
myservo_4.write(Open_servo_4);
delay(Fill_three);
myservo_4.write(Close_servo_4);
count = 0;
}
if (var_1 == 1 && var_2 == 7) {
//Three Shot 1, Rest 5
myservo_1.write(Open_servo_1);
delay(Three_shot);
myservo_1.write(Close_servo_1);
myservo_5.write(Open_servo_5);
delay(Fill_three);
myservo_5.write(Close_servo_5);
count = 0;
}
if (var_1 == 1 && var_2 == 8) {
//Three Shot 1, Rest 6
myservo_1.write(Open_servo_1);
delay(Three_shot);
myservo_1.write(Close_servo_1);
myservo_6.write(Open_servo_6);
delay(Fill_three);
myservo_6.write(Close_servo_6);
count = 0;
}
if (var_1 == 1 && var_2 == 9) {
//One Shot 2, Rest 4
myservo_2.write(Open_servo_2);
delay(One_shot);
myservo_2.write(Close_servo_2);
myservo_4.write(Open_servo_4);
delay(Fill_one);
myservo_4.write(Close_servo_4);
count = 0;
}
if (var_1 == 2 && var_2 == 0) {
//One Shot 2, Rest 5
myservo_2.write(Open_servo_2);
delay(One_shot);
myservo_2.write(Close_servo_2);
myservo_5.write(Open_servo_5);
delay(Fill_one);
myservo_5.write(Close_servo_5);
count = 0;
}
if (var_1 == 2 && var_2 == 1) {
//One Shot 2, Rest 6
myservo_2.write(Open_servo_2);
delay(One_shot);
myservo_2.write(Close_servo_2);
myservo_6.write(Open_servo_6);
delay(Fill_one);
myservo_6.write(Close_servo_6);
count = 0;
}
if (var_1 == 2 && var_2 == 2) {
//Two Shot 2, Rest 4
myservo_2.write(Open_servo_2);
delay(Two_shot);
myservo_2.write(Close_servo_2);
myservo_4.write(Open_servo_4);
delay(Fill_two);
myservo_4.write(Close_servo_4);
count = 0;
}
if (var_1 == 2 && var_2 == 3) {
//Two Shot 2, Rest 5
myservo_2.write(Open_servo_2);
delay(Two_shot);
myservo_2.write(Close_servo_2);
myservo_5.write(Open_servo_5);
delay(Fill_two);
myservo_5.write(Close_servo_5);
count = 0;
}
if (var_1 == 2 && var_2 == 4) {
//Two Shot 2, Rest 6
myservo_2.write(Open_servo_2);
delay(Two_shot);
myservo_2.write(Close_servo_2);
myservo_6.write(Open_servo_6);
delay(Fill_two);
myservo_6.write(Close_servo_6);
count = 0;
}
if (var_1 == 2 && var_2 == 5) {
//Three Shot 2, Rest 4
myservo_2.write(Open_servo_2);
delay(Three_shot);
myservo_2.write(Close_servo_2);
myservo_4.write(Open_servo_4);
delay(Fill_three);
myservo_4.write(Close_servo_4);
count = 0;
}
if (var_1 == 2 && var_2 == 6) {
//Three Shot 2, Rest 5
myservo_2.write(Open_servo_2);
delay(Three_shot);
myservo_2.write(Close_servo_2);
myservo_5.write(Open_servo_5);
delay(Fill_three);
myservo_5.write(Close_servo_5);
count = 0;
}
if (var_1 == 2 && var_2 == 7) {
//Three Shot 2, Rest 6
myservo_2.write(Open_servo_2);
delay(Three_shot);
myservo_2.write(Close_servo_2);
myservo_6.write(Open_servo_6);
delay(Fill_three);
myservo_6.write(Close_servo_6);
count = 0;
}
if (var_1 == 2 && var_2 == 8) {
//One Shot 3, Rest 4
myservo_3.write(Open_servo_3);
delay(One_shot);
myservo_3.write(Close_servo_3);
myservo_4.write(Open_servo_4);
delay(Fill_one);
myservo_4.write(Close_servo_4);
count = 0;
}
if (var_1 == 2 && var_2 == 9) {
//One Shot 3, Rest 5
myservo_3.write(Open_servo_3);
delay(One_shot);
myservo_3.write(Close_servo_3);
myservo_5.write(Open_servo_5);
delay(Fill_one);
myservo_5.write(Close_servo_5);
count = 0;
}
if (var_1 == 3 && var_2 == 0) {
//One Shot 3, Rest 6
myservo_3.write(Open_servo_3);
delay(One_shot);
myservo_3.write(Close_servo_3);
myservo_6.write(Open_servo_6);
delay(Fill_one);
myservo_6.write(Close_servo_6);
count = 0;
}
if (var_1 == 3 && var_2 == 1) {
//Two Shot 3, Rest 4
myservo_3.write(Open_servo_3);
delay(Two_shot);
myservo_3.write(Close_servo_3);
myservo_4.write(Open_servo_4);
delay(Fill_two);
myservo_4.write(Close_servo_4);
count = 0;
}
if (var_1 == 3 && var_2 == 2) {
//Two Shot 3, Rest 5
myservo_3.write(Open_servo_3);
delay(Two_shot);
myservo_3.write(Close_servo_3);
myservo_5.write(Open_servo_5);
delay(Fill_two);
myservo_5.write(Close_servo_5);
count = 0;
}
if (var_1 == 3 && var_2 == 3) {
//Two Shot 3, Rest 6
myservo_3.write(Open_servo_3);
delay(Two_shot);
myservo_3.write(Close_servo_3);
myservo_6.write(Open_servo_6);
delay(Fill_two);
myservo_6.write(Close_servo_6);
count = 0;
}
if (var_1 == 3 && var_2 == 4) {
//Three Shot 3, Rest 4
myservo_3.write(Open_servo_3);
delay(Three_shot);
myservo_3.write(Close_servo_3);
myservo_4.write(Open_servo_4);
delay(Fill_three);
myservo_4.write(Close_servo_4);
count = 0;
}
if (var_1 == 3 && var_2 == 5) {
//Three Shot 3, Rest 5
myservo_3.write(Open_servo_3);
delay(Three_shot);
myservo_3.write(Close_servo_3);
myservo_5.write(Open_servo_5);
delay(Fill_three);
myservo_5.write(Close_servo_5);
count = 0;
}
if (var_1 == 3 && var_2 == 6) {
//Three Shot 3, Rest 6
myservo_3.write(Open_servo_3);
delay(Three_shot);
myservo_3.write(Close_servo_3);
myservo_6.write(Open_servo_6);
delay(Fill_three);
myservo_6.write(Close_servo_6);
count = 0;
}
if (var_1 == 3 && var_2 == 7) {
//Full Cup 4
myservo_4.write(Open_servo_4);
delay(Fill_empty);
myservo_4.write(Close_servo_4);
count = 0;
}
if (var_1 == 3 && var_2 == 8) {
//Full Cup 5
myservo_5.write(Open_servo_5);
delay(Fill_empty);
myservo_5.write(Close_servo_5);
count = 0;
}
if (var_1 == 3 && var_2 == 9) {
//Full Cup 6
myservo_6.write(Open_servo_6);
delay(Fill_empty);
myservo_6.write(Close_servo_6);
count = 0;
}
if (var_1 == 4 && var_2 == 0) {
//Prime 1
myservo_1.write(Open_servo_1);
delay(Prime_time);
myservo_1.write(Close_servo_1);
count = 0;
}
if (var_1 == 4 && var_2 == 1) {
//Prime 2
myservo_2.write(Open_servo_2);
delay(Prime_time);
myservo_2.write(Close_servo_2);
count = 0;
}
if (var_1 == 4 && var_2 == 2) {
//Prime 3
myservo_3.write(Open_servo_3);
delay(Prime_time);
myservo_3.write(Close_servo_3);
count = 0;
}
if (var_1 == 4 && var_2 == 3) {
//Prime 4
myservo_4.write(Open_servo_4);
delay(Prime_time);
myservo_4.write(Close_servo_4);
count = 0;
}
if (var_1 == 4 && var_2 == 4) {
//Prime 5
myservo_5.write(Open_servo_5);
delay(Prime_time);
myservo_5.write(Close_servo_5);
count = 0;
}
if (var_1 == 4 && var_2 == 5) {
//Prime 6
myservo_6.write(Open_servo_6);
delay(Prime_time);
myservo_6.write(Close_servo_6);
count = 0;
}
else
count = 0;
}
}

}