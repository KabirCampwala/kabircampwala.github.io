+++
author = "Kabir Campwala"
title = "Password Generator in C"
tags = ["C", "Programming", "Project"]
+++

![Password Generator in C](/c/banner.png)

Having a strong password is a must today. A strong password means better security. It may get exhausting thinking of strong passwords when you have to create an account for something almost everyday. So for your convenience, today we will write a short program which can provide you with random passwords.

### Objectives to accomplish with the password generator are:
1. Greet the user
2. Ask for the length of the password
3. Generate a random password
4. Output that password to the user

![Code Screenshot](/c/1.png)

To start off we are going to use functions from three different libraries so we'll include these into our code.

![Code Screenshot](/c/2.png)

Let us start with the first step of greeting the user. We will do that inside the main function and declare a variable for storing the length of password.

![Code Screenshot](/c/3.png)

Now we'll get the user's input for the length of the password they want.

To generate random passwords we will create a function and name it "password".

![Code Screenshot](/c/4.png)

Let us understand what does that `list` array mean and why do we need it.

To generate the password we need a place from where we can grab random numbers, alphabets and symbols. That is why we created the array list.

A computer cannot generate a random number or a letter. Yes we have the `rand()` function but that function also follows a specific set of rules which will give the same output again and again.

To solve this problem what we can do is use `srand()`.

"S" from `srand()` stands for seeding. A value given for the seed will generate different output based on the value of the seed.

Even after assigning the value of the seed you will find that it still repeats the output. For that we need to think of another way to set a seed value which will change every time we run the program.

Let's think for a while.

What value can automatically change when we run the program each time?

Found the answer?

That's right it's "TIME".

Time will change every time when we run the program. That is why we will use:

![Code Screenshot](/c/5.png)

Now for generating and printing the generated password we will use a `for` loop and use the array `list` we created earlier to get random numbers, letters and symbols from that array.

![Code Screenshot](/c/6.png)

The above code generates a letter or a symbol or an alphabet in every iteration until the password length entered by the user is reached.

That's it! You created a password generator in C.

Now let's see what it looks like after we run the program.

![Code Screenshot](/c/7.png)

Below is the full program with the formatting used above:

```C
#include <stdio.h>
#include <time.h>
#include <stdlib.h>
int password(int password_length) {
char list[] = "1234567890qwertyuiopasdfghjklzxcvbnm!@#$%^&*()_- +=QWERTYUIOPASDFGHJKLZXCVBNM[]{};':\"<>,.?/\|";
printf("\t");
for(int i = 0; i < password_length; i++) {
    printf("*");
}
printf("\n");
printf("\t");
srand(time(NULL));
for(int i = 0; i < password_length; i++) {
    printf("%c", list[rand() % (sizeof list - 1)]);
}
printf("\n");
printf("\t");
for(int i = 0; i < password_length; i++) {
    printf("*");
}
printf("\n");
}
int main() {
int password_length;
printf("\n\t*********************************\n\n");
printf("\tWelcome to the password generator\n\n");
printf("\t*********************************\n");
printf("\n\tEnter length of the password = ");
scanf("%d", &password_length);
printf("\n");
printf("\n");
password(password_length);
return 0;
}
```
