# Jamun-Calendar

A developer handy Tools.

Calendar is a collection of Beautiful Activities which help others to make there Fully Custom Calendar View with Single and Multi Date Picker Functionality.


### Introduction

* 

### Dual Date Picker

Feature Dual date picker provide fully custom selection between dates, months and year. A very neat and clean view for Your User to Get maximum satisfaction either by UI or UX, And Plus points for developer have with full custom handy tags, for developer maximum satisfaction.

Before Selection | After Selection
---- | ----
![jamun_calendar_dual](https://user-images.githubusercontent.com/38988514/40280633-76b74c0c-5c74-11e8-8843-e4ffbc20b59b.png) | ![jamun_calendar_dual_selection](https://user-images.githubusercontent.com/38988514/40280630-738e61a0-5c74-11e8-8708-9e74c059206e.png)

### Single Date Picker

Feature single Picker is provide you date selection functionality with fully custom tags. Another UI/UX combination for to enhacne app quality and satisfaction.

Selected Date Picker | Custom Date Picker
---- | ----
![jamun_calendar_single](https://user-images.githubusercontent.com/38988514/40280631-746a2762-5c74-11e8-86d0-f3e705db4548.png) | ![jamun_calendar_single_custom_selection](https://user-images.githubusercontent.com/38988514/40280632-75a5872a-5c74-11e8-8db7-6a1a9704de2a.png)
### What's New? (0.0.1)
* Stable **Official Version** for Developers and Live Apps.
* Very Light Weight and Developer app theme Oriented
* Easy Calling Mechanism with **Instant reply** via onActivityResult
* Provide you very flexible wat to Customize the whole Module.
* Need less calls with many customs Tags to reach maximum developer satisfaction.

### Quality Measures? for (0.0.1)

The following apps are using this library without facing any kind of Bugs.

* **[SimplyBlood](https://play.google.com/store/apps/details?id=com.simplyblood)**
* **[ZINI](https://play.google.com/store/apps/details?id=ai.zini)**,

------

## Gradle Configuration

**Add the dependency**

```java
dependencies {
        compile 'tk.jamun:calendar:0.0.1'
}
```

## Maven Config

```xml
<dependency>
  <groupId>tk.jamun</groupId>
  <artifactId>calendar</artifactId>
  <version>0.0.1</version>
  <type>aar</type>
</dependency>
```
------

# How to Implement

Once the project has been added to gradle, You can use these lines of code to configure pickers....

## Calling Code

Three simple steps to Take care of whole Modele : 

### Step 1. Define Intent Object

Simple Object declaration to Define Type of Picker you want, There are two Types : 

A) Single Date Picker
B) Multi or Dual Date Picker

```
**Single Date Picker**
Intent intent = new Intent(getContext(), ActivityCalenderSingle.class);

or

**Multi Date Picker**
Intent intent = new Intent(this, ActivityCalenderDual.class);

```
### Step 2. Start Module By Calling

This method is very common to Android Developer, Very easy calling way to Start an activity help you same for calling this Picker :

```
startActivityForResult(intent, INTENT_CALENDER_SINGLE_PICKER);
```

### Step 3. Get Result from Picker

```
@Override
public void onActivityResult(int requestCode, int resultCode, Intent data) {
super.onActivityResult(requestCode, resultCode, data);
if (requestCode == INTENT_CALENDER_DUAL_PICKER) {
    if (resultCode == RESULT_OK) {
       modelCalenderFrom = data.getParcelableExtra(INTENT_CALENDER_DATA_ONE);
       modelCalenderTo = data.getParcelableExtra(INTENT_CALENDER_DATA_TWO);
       updateDate();
    }
} else if (requestCode == INTENT_CALENDER_SINGLE_PICKER) {
    if (resultCode == RESULT_OK) {
          modelCalender = data.getParcelableExtra(INTENT_CALENDER_DATA);
    }
}
```
Result Provide you ModelCalendar Object, that have all required Object to Full fill any Developer Request. It also have Calendar Object for More satisfaction.

------

## Picker Customize 

Intent Object provide you custom functionality to work Module according to your requirement :

* **Set Title of the Date Picker**

By Defining this tag with String can help you setting Title of the date Picker.

```
intent.putExtra(INTENT_CALENDER_TITLE, "Title of the Picker");
```

* **Set Predefined Date**

To set selected Date in Calendar, Also used if user already selected Date, so this will help you user to Navigate Directly to Selected Once :

```
**Single Date Picker**

intent.putExtra(INTENT_CALENDER_DATE, modelCalender.getDate());
intent.putExtra(INTENT_CALENDER_MONTH, modelCalender.getMonth());//(0 to 11)
intent.putExtra(INTENT_CALENDER_YEAR, modelCalender.getYear());

**Multi Date Picker**
intent.putExtra(INTENT_CALENDER_YEAR_FROM, modelCalenderFrom.getYear());
intent.putExtra(INTENT_CALENDER_MONTH_FROM, modelCalenderFrom.getMonth()); //(0 to 11)
intent.putExtra(INTENT_CALENDER_DATE_FROM, modelCalenderFrom.getDate());
intent.putExtra(INTENT_CALENDER_YEAR_TO, modelCalenderTo.getYear());
intent.putExtra(INTENT_CALENDER_MONTH_TO, modelCalenderTo.getMonth());//(0 to 11)
intent.putExtra(INTENT_CALENDER_DATE_TO, modelCalenderTo.getDate());       
```

* **Set Minimum or Maximum Date Today**

There is a provisioin in this library to start your Picker selection from Today either Today date as Starting date or Ending date :

```
**Minimum Date Today**
intent.putExtra(INTENT_CALENDER_SET_MIN_DATE_TODAY, true);

**Maximum Date Today**
intent.putExtra(INTENT_CALENDER_SET_MAX_DATE_TODAY, true);
```

Warning Note : Don't set them both at once, it may be crash your app;

* **Set Maximum or Minimum Year,Date,Month for selection Upto**

To bound your User Selection, just need to call intent with some Tags and Thats it Boundation Applied:
 
```
**Maximum Year Upto**
intent.putExtra(INTENT_CALENDER_MAX_YEAR, currentYear + 10(upto Value));
intent.putExtra(INTENT_CALENDER_MAX_MONTH, Month(upto Value));//(0 to 11)
intent.putExtra(INTENT_CALENDER_MAX_DATE, date(upto Value));

**Minimum Year Upto**
intent.putExtra(INTENT_CALENDER_MIN_YEAR, currentYear - 10(Above Value));
intent.putExtra(INTENT_CALENDER_MIN_MONTH, Month(Above Value));//(0 to 11)
intent.putExtra(INTENT_CALENDER_MIN_DATE, date(Above Value));

or For setting Both min and max Together
intent.putExtra(INTENT_CALENDER_MAX_YEAR, currentYear + 10(upto Value));
intent.putExtra(INTENT_CALENDER_MAX_MONTH, Month(upto Value));//(0 to 11)
intent.putExtra(INTENT_CALENDER_MAX_DATE, date(upto Value));
intent.putExtra(INTENT_CALENDER_MIN_YEAR, currentYear - 10(upto Value));
intent.putExtra(INTENT_CALENDER_MIN_MONTH, Month(Above Value));//(0 to 11)
intent.putExtra(INTENT_CALENDER_MIN_DATE, date(Above Value));

Also Used as
Either,
intent.putExtra(INTENT_CALENDER_SET_MAX_DATE_TODAY, true);

intent.putExtra(INTENT_CALENDER_MIN_YEAR, currentYear - 10(upto Value));
intent.putExtra(INTENT_CALENDER_MIN_MONTH, Month(Above Value));//(0 to 11)
intent.putExtra(INTENT_CALENDER_MIN_DATE, date(Above Value));

Or,
intent.putExtra(INTENT_CALENDER_SET_MIN_DATE_TODAY, true);

intent.putExtra(INTENT_CALENDER_MAX_YEAR, currentYear + 10(upto Value));
intent.putExtra(INTENT_CALENDER_MAX_MONTH, Month(upto Value));//(0 to 11)
intent.putExtra(INTENT_CALENDER_MAX_DATE, date(upto Value));


```
Warning Note : Don't call with Both INTENT_CALENDER_SET_MAX_DATE_TODAY or with INTENT_CALENDER_SET_MIN_DATE_TODAY together with this, it may be crash your app;

------

### Working Example for Date Of Birth Selection

```
 Intent intentType = new Intent(getContext(), ActivityCalenderSingle.class);
 //used if user already selected Date, so this will help you user to Navigate Directly to Selected Once
 if (modelCalender.getDate() != 0) {
    intentType.putExtra(INTENT_CALENDER_DATE, modelCalender.getDate());
    intentType.putExtra(INTENT_CALENDER_MONTH, modelCalender.getMonth());//(0 to 11)
    intentType.putExtra(INTENT_CALENDER_YEAR, modelCalender.getYear());
 }
 intentType.putExtra(INTENT_CALENDER_TITLE, getString(R.string.string_activity_name_dob));
 intentType.putExtra(INTENT_CALENDER_MAX_YEAR, HelperTime.getInstance().getCurrentYear() - CONSTANT_FOR_DOB_UPTO);
startActivityForResult(intentType, INTENT_CALENDER_SINGLE_PICKER);
```


Single Date Picker | 
---- |
![calender](https://user-images.githubusercontent.com/38988514/40102644-a742f642-5908-11e8-9a28-bc8c8ef7423c.gif)

------

# Dependency (Only)

* Android Appcompact and Support Fragment Library ``v27.1.1``

## Credits

Desgin & Developed by : **[Jatin Sahgal](https://www.linkedin.com/in/jatinsahgal/)**
 (**[Linkedin](https://www.linkedin.com/in/jatinsahgal/)** & **[Website](https://jatin.techcruzers.com)**) 

Content Writer : **[Achal Garg](https://www.linkedin.com/in/techgarg/)**
 (**[Linkedin](https://www.linkedin.com/in/techachal/)** & **[Website](https://achal.techcruzers.com)**) 

Company : **[Techcruzers](https://www.techcruzers.com)**

## More Library under Jamun 

* **[Pickers](https://github.com/Lib-Jamun/Pickers.git)**
Pickers Library provide you a set of Pickers like Country, Language, Share and Intent Chooser.

* **[Country-Pickers](https://github.com/Lib-Jamun/Pickers.git)**
allow you to access Country picking functionality with great UI/UX design, and there are numberous of function which help you to modify picker as per your requirements. Library has been provided with four custom UI initate mode you can decide how the view of picker can be initate. You can also decide weather picker inheriate Single or Multi Selection property. Library consists of updated collection of country name, code and there flags. We are using APIs base structure to avoid increase in the size of apk due to flag Images. This module Maintain the database so that you don't need to call APIs again and again rather than you can choose when to refresh the Database and fetch new real time data.

* **[Language-Pickers](https://github.com/Lib-Jamun/Pickers.git)**
provides you read-made Language picker  which is easy to use and comes with great UI/UX, and there are numberous of function which help you to modify picker as per your requirements. Library has been provided with four custom UI initate mode you can decide how the view of picker can be initate. You can also decide weather picker inheriate Single or Multi Selection property.

* **[Scanner](https://github.com/Lib-Jamun/scanner.git)**
is a collection of Beautiful Activity which help others to make there own Custom QR/Barcode Scanner. 

* **[Volley](https://github.com/Lib-Jamun/Volley.git)**
Library is a set of Custom Classes with UI components for network programming, integration and transaction handling in a better and standard way. This will help developers for making quality use of volley library. 

* **[UI](https://github.com/Lib-Jamun/ui.git)**
library is a set of UI Views, Custom Component and Collection of Helper Classes which help Developer for making quality Product. Such as Camera, Gallery, Number of Pickers, Calendar, Date Pickers, Dialogs and many more Heler UI and Backend Component.

* **[Camera](https://github.com/Lib-Jamun/ui.git)**
library provide you Custom Complete Camera view with full features like Flash, Rotation, Gallery Picker, Focus, Tap to capture, Confirmation window and last but not least croping feature. It also provide you file path in return so that developer can feel a friendly handy way to Deal After. 

* **[Gallery](https://github.com/Lib-Jamun/ui.git)**
have some Beautiful UI Components and Multi files Mode for android Developers to give there app a A Rich look With single and Multi picker Functionality.


## License
    Copyright (c) 2018 Jatin Sahgal

    Licensed under the Apache License, Version 2.0 (the "License");
    you may not use this file except in compliance with the License.
    You may obtain a copy of the License at

    http://www.apache.org/licenses/LICENSE-2.0

    Unless required by applicable law or agreed to in writing, software
    distributed under the License is distributed on an "AS IS" BASIS,
    WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
    See the License for the specific language governing permissions and
    limitations under the License.
  
  
