# How To Use the DATA Act prototype broker

Welcome! If you're a U.S. federal employee and want to explore this early prototype of the DATA Act broker, you're in the right place.

## What can be done with the prototype

The hosted version of the prototype is a 'sandbox' where you can run your agency's DATA Act data through an early version of the validation and conversion process.

The pilot team's top priority in creating the prototype broker was understanding how the agency data submission process will work and getting early feedback. The resulting prototype website is a [_minimum viable product_](https://en.wikipedia.org/wiki/Minimum_viable_product "minimum viable product"). This means it's not fully featured, but it provides something concrete for agencies to respond to. We hope you'll give it a try and [let us know what you think](CONTRIBUTING.md "give feedback or ask a question about the DATA Act broker pilot").

Official DATA Act guidance will continue to evolve, so the broker prototype doesn't represent the final version of the agency submission process, and the validations it performs aren't complete. Rather, the validations for this prototype broker only check for basic, simple validations such as field name, field length, data type, and required/optional.

Agencies can use the prototype website for:
* A better understanding of what the submission process is like
* A chance to [provide feedback](CONTRIBUTING.md "give feedback or ask a question about the DATA Act broker pilot") on this process and the experience of using the broker
* A first, high-level validation check of files created for the DATA Act

For a more comprehensive background about the project and submission process we're testing, [watch the pilot's screencast](https://github.com/18F/data-act-pilot/blob/master/assets/screencast/data_act_pilot_screencast_sept_2015.avi?raw=true "download screencast").

## How to use the prototype

The prototype broker website is only open to federal employees. This is a security restriction. If you're not a federal employee, the screencast provides a good overview of the site.

### Prepare your data

If you've made progress on data inventory and mapping, you should be able to create the four data files used in this pilot. You can still go through the process with just one or two records, which can be a useful way to get started and get additional insights into your agency's readiness.

The pilot currently expects DATA Act data in four separate files:

1. [Appropriation (File A)](https://github.com/18F/data-act-pilot/blob/master/app/validator/rules/appropriation_rules.csv "Appropriation Rules")
2. [Object Class Program Activity (File B)](https://github.com/18F/data-act-pilot/blob/master/app/validator/rules/object_class_program_activity_rules.csv "Object Class Program Activity Rules")
3. [Award Financial (File C)](https://github.com/18F/data-act-pilot/blob/master/app/validator/rules/award_financial_rules.csv "Award Financial")
4. [Award (File D)](https://github.com/18F/data-act-pilot/blob/master/app/validator/rules/award_rules.csv "Award Rules")

These files roughly correspond to the _Relationships_ diagram in the _Data Act Elements Guidance_ published by Treasury and [available on MAX](https://community.max.gov/display/Management/B%3A+DATA+Act+Elements+Guidance "Data Act Elements Guidance"). 

To create data files that are compatible with this pilot:

1. Review Treasury's [_DATA Act Elements Guidance_](https://community.max.gov/display/Management/B%3A+DATA+Act+Elements+Guidance "DATA Act Elements Guidance") (version DATA Act Elements Guidance_v0.1.4.1 - 12-31-15).

2. For a better idea of what data the website expects, take a look at [these sample files](../data/dummy "DATA Act broker dummy data") filled out with dummy data.

3. Based on your system inventory and mapping work, create the four files and populate them with data. The order of the columns in each file doesn't matter, but it's important that the column names match those used shown on the templates and dummy data.

### Submit data for validation

This prototype is a 'sandbox.' The website uses anonymized analytics to track overall traffic and usage, but it doesn't track who is logging on, and it won't send or store your data anywhere. When your four files are ready, contact Treasury's DATA Act Program Management Office (DATAPMO@fiscal.treasury.gov) to set up an appointment to test the broker. Because of security restrictions, the sandbox in an in-person sandbox -- meaning that Treasury will provide the environment and when you bring your data, we will help you walk through the process of submitting data. You will be aided by the DATA Act PMO to ensure that you maximize your experience with the sandbox.

Below you can view the steps that you will go through to test your files in the prototype broker.

![broker](images/broker.png "broker")

1. In one or more of the four boxes, click _Choose File_ to upload the data you've created.
1. After you click _Choose File_, use the navigation that appears to find the file on your computer and click _Choose_.

 ![choose file](images/choose-file.png "choose file")

1. After you choose a file, the corresponding box on the main page will let you know you were successful by display the file's name in the box:

 ![files for validation](images/broker-with-files.png "chosen files")

1. Continue choosing the files you want to upload and validate. You don't have to upload all four files, but it's important to make sure that the file you choose for each box matches the title. For example, you can't upload your _Appropriation_ file using the _Award_ box.

1. When you're done selecting the files to validate, click the _Validate Me_ button.

1. Once the validations are complete, the broker will display results on the website.

## Review validation results

In this early stage of the process, we expect that most files will have some type of validation error. We try to return as much information about each type of error as possible, so don't be alarmed if you see a lot of messages on the screen.

Below the upload boxes, you should see a _Results_ section on the website. This displays error messages for each of the four files.

### File was not uploaded

The most basic error message is _File was not uploaded_, and this appears for any of the four files you chose not to upload before running validations. This is just a reminder and not a cause for concern.

![file not uploaded](images/error-file-not-uploaded-small.png "file not uploaded")

### File is of incorrect type

The broker checks the format of each file you upload to make sure:
* It's a .csv.
* The column names are correct (order of columns doesn't matter).

If there's a file format problem, you'll see the _file is of incorrect type_ message.

![invalid format](images/error-invalid-format-small.png "invalid format")

### Some fields are not valid

Once the broker has checked the file format, it runs the file's actual data through a series of [validation rules](VALIDATIONS.md "validation rules").

![some fields are not valid](images/error-fields-not-valid-small.png "some fields are not valid")

Click _View error details_ to see the specific errors. You can also download the error messages to a .csv by clicking _Download CSV_.

![error messages](images/error-messages.png "broker error messages")

The image above is an example of simple validation rules that failed. You'll see a table like this for each row of the uploaded file that contains an error. Here are a few pointers for interpreting these messages:

* Right above the table is some information meant to help track down the data causing the problem:
    * _Row_ is the row number in the uploaded file.
    * Following _Row_ are "key" fields in file. This example is the file that contains obligations and outlays by appropriations account, program activity, and object class. Thus, the error message displays TAS (_i.e._ appropriations account), object class, and program activity to help find the offending data in the source system.
* For each row in the data that didn't pass validations, you'll see one or more _Field names_. This is the name of specific field that didn't pass.
* For each _Field name_, you'll see a _Value_ that displays the data in question and an _Error_ that describes the problem. In this basic example, we're missing some required data and have provided text data for a field that expects integers.

**Reminder:** use the _Download CSV_ link to download error messages to Excel or another spreadsheet application.
