---
title: DATA Act business rules
---
As an SBA user, I need to see the business rules being applied to my source data
    
Business rules or validation rules will be applied to ensure that submitted data by the US Small Business Administration meets the DATA Act criteria. Goals of these validation rules will improve cleanliness, accuracy, and meaningfulness of the data set. Agency submissions will be checked against these rules before the data submission is accepted by Treasury. Below is a draft of proposed rules and are subject to change. 
    
**Standard validation**

*Required fields:* 
- Required field validation ensures that users input data in required fields. If required field is empty, an error will be raised. [DATA act schema](https://github.com/18F/intercessor/blob/master/schema/data-act-schema.png) documents the required fields.

*Data types:*
- Data type validation ensures that the data types match with the [DATA Act schema](https://github.com/18F/intercessor/blob/master/schema/data-act-schema.png) . For example, `parentAward` data type required is a string. If a number is entered an error will be raised. 


**Awardee validation:**  

*Award id:*
- Award id validation ensures that `Award id` is an exact number length (if it is not blank). This length can be determined and set. Additionally, award id validation ensures DUNSNumber and SAM number match. If either of those criterias are not met an error will be raised.

*Address:* 

- Address validation ensures that users input data in the Awardee Address fields. If address fields are empty, an error will be raised. 
- State and zip codes validation will ensure that Awardee Zip/Postal Code is valid by looking up the first five characters of the value in a zip code object that contains a record for every valid zip code in the US. If the zip code is not found in the zip code object, an error will be raised. 

*Business type:*

- The Business type two-position numeric code depicts the type of recipient or borrower. Business Type validation ensures that:
    - the numeric code is the exact number length of two. If business type is empty and is not the exact number length, an error will be raised. 
    - the two position numeric code depicts the correct type of recipient or borrow. If buissness type is not accurate in the business type object, an error will be raised. Below are the following business types: 
    - Government codes:
        - 00 = State government
        - 01 = county government
        - 02 = city or township government
        - 04 = special district government
        - 05 = independent school district
        - 06 = State controlled institution of higher education
    - Nonprofit agencies:
        - 11 = Indian tribe
        - 12 = other nonprofit
    - Private:
        - 20 = private higher education
        - 21 = individual
        - 22 = profit organization
        - 23 = small business
        - 25 = all other
    
**Award validation:** 

The following fields will be validated against their respective authoritative sources:

- Object Class
- CFDA Code
- NAICS Code


Questions: 

- How do you keep track of changing addresses? 
- In general, how do we want to track data that changes over time?  
- What are the authoritative sources to validate addresses, NACIS code, CFDA code? 