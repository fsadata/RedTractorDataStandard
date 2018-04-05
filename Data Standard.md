# Red Tractor Data Standard
### What Is This Document?
This document describes the data standard for Red Tractor to submitting membership data to the Food Standards Agency. It describes the fields, their data types and order as well as providing specific guidance on acceptable values and which fields use specific reference data values.
This document does not describe the mechanism by which data can be submitted to the Food Standards Agency (the FSA).
### Who Is This Document For?
This document is written for Red Tractor who need to submit membership data to the FSA.
### How This Document Is Structured
- [Red Tractor Data Overview](#red-tractor-data-overview) Contains a brief overview of all the fields in the standard.  
- [Field Definitions](#field-definitions) Complete definitions for each field in the standard, includes constraints and specific data type formatting requirements.  
 1. [FSA Producer ID](#1-fsa-producer-id)
 2. [Site Name](#2-site-name)
 3. [Address](#3-address)
 4. [CPH Number](#4-cph-number)
 5. [Certificate End Date](#5-certificate-end-date)
 6. [Red Tractor Dairy Number](#8-red-tractor-dairy-number)
 7. [Last RT Dairy Inspection Date](#9-last-rt-dairy-inspection-date)
- [Supported File Types](#supported-file-types)
- [Other Requirements](#other-requirements)
- [File Naming Conventions](#file-naming-conventions)

## Red Tractor Data Overview
The following table lists the fields (name and description), their data types, whether they are optional, and whether they use a controlled vocabulary.


Index | Field Name | Description | Data Type | Optional | Controlled Vocabulary | Source
------|------------|-------------|-----------|----------|-----------------------|-------
1|fsa_producer_id|FSA producer unique identifier|Number|No|Yes|FSA
2|site_name|Trading name of milk producer|Text|No|No|FSA
3|address|Address of milk producer|Text|No|No|FSA
4|cph_number|County parish holding number|Text|No|Yes|FSA
5|certificate_end_date|End date of Red Tractor certificate of membership|Date|No|Yes|RT
6|red_tractor_dairy_number|Red Tractor unique identifier|Text|No|Yes|RT
7|last_rt_dairy_inspection_date|Date of last Red Tractor dairy inspection|Date|No|Yes|RT

## Field Definitions

### 1. FSA Producer ID
**Field Name:** ` fsa_producer_id`  
**Data Type:** `Number (controlled vocabulary)  
**Optional:** No  
**Source:** Food Standards Agency  
**Comments:** This is the numeric Food Standards Agency code to identify an establishment registered to produce milk. This must be a unique value.  

### 2. Site Name
**Field Name:** `site_name`  
**Data Type:** Text (50 character limit)  
**Optional:** No  
**Source:** Food Standards Agency  
**Comments:** The trading name of the registered milk producer.  

### 3. Address
**Field Name:** `address`  
**Data Type:** Text (255 character limit)  
**Optional:** No  
**Source:** Food Standards Agency  
**Comments:** The address of the registered milk producer  

### 4. CPH Number 
**Field Name:** `cph_number`  
**Data Type:** Text (14 character limit)  
**Optional:** No  
**Source:** Food Standards Agency  
**Comments:** This is the County Parish Holding number, allocated to any establishment which holds livestock by the Rural Payments Agency. This should follow the nn/nnn/nnnn/nn format.  

### 5. Certificate End Date
**Field Name:** `certificate_end_date`  
**Data Type:** Date (format: `YYYY-MM-DD`)  
**Optional:** No  
**Source:** Red Tractor  
**Comments:** The end date of the producer’s certificate of Red Tractor membership. This should follow the YYYY-MM-DD format as laid out in the International Standard ISO 8601.  

### 6. Red Tractor Dairy Number
**Field Name:** `red_tractor_dairy_number`  
**Data Type:** Text (20 character limit)  
**Optional:** No  
**Source:** Red Tractor  
**Comments:** This is Red Tractor’s unique reference to identify a milk producer who is a current member. It can be any combination of numeric or alphanumeric characters as long as it is unique.    

### 7. Last Red Tractor Dairy Inspection Date
** Field Name:** ` last_rt_dairy_inspection_date`  
**Data Type:** Date (format: `YYYY-MM-DD`)  
**Optional:** No  
**Source:** Red Tractor  
**Comments:** The date of Red Tractor’s last inspection of the milk production establishment. This should follow the YYYY-MM-DD format as laid out in the International Standard ISO 8601.  


## Supported File Types

Currently we are supporting the standard for comma separated values (CSV), Json and XML files.

The [current standard for CSV](https://tools.ietf.org/html/rfc4180) gives a detailed explanation of the common format for CSV files. It's concise and clear and we recommend reading it.

## Other Requirements

### Text Fields

The majority of the fields in the standard are text, which needs to be treated carefully when stored in a CSV file. All text fields must be enclosed within double quotes `"this is the text"`. You should try to avoid using double quotes within a text field as this can cause the field to be misread, but the RFC4180 standard allows it if handled appropriately.

>If double-quotes are used to enclose fields, then a double-quote appearing inside a field must be escaped by preceding it with another double quote. For example: `"aaa","b""bb","ccc"`

### Encoding

Where possible please use `UTF-8` encoding.

## File Naming Conventions

In order to make it easy for us to manage the files longer term, it will be important to name files so that we can tell the time period that each file covers. The format will be RT and the date and time of submission in `YYYYMMDD-HHMMSS` format.

For example, the file submitted the 31st of January 2017 15:20:33 would be named `RT20170131-152033.csv`.
