# Shared Systems Model Provider Matching
## High Level Requirements
In addition to what can be found in the [Design Challenge](https://github.com/cmsuser1/MPSM-BPA/blob/master/DESIGN_CHALLENGE.md), the business owner wishes for you to create a highly available service that accepts the following [Example Input File](https://github.com/cmsuser1/MPSM-BPA/blob/master/Attribute-Matching/provider_matching.csv) and produces files that are to be ingested into the Shared Systems.

The Shared Systems accepts files for each model in which providers are participating in. All models have the same requirement of only individual provider participation. Ensure that valid data will be entered into the Shared System.

Make sure to explain why certain decisions were made while researching, designing, and building this service.
## Input File
The input file contains many different models and providers. **_Please Note that the TIN's in this file are randomized and can be used directly as required by the output file_**

The file was produced by another vendor and thus you cannot control the data it contains. It has the following headers:  

| Field Label  | Field Name | Field Description |  
|---|---|---|
| NPI | National Provider Identifier | This is the provider's ID within the healthcare system.  |
| TIN  | Tax Identification Number  | This is the provider's ID within IRS' system  |
| Model Type  | Model Type  | The name of the model in which the provider is enrolled  |
| Valid Through Date | Valid Through Date | The date in which the model is active through |

## Output Files
The Shared System only accepts files that are in a fixed-width format. 

### File Layout

| Element # | Field Label  | Field Name  | Start Position  | End Position | Data Length | Field Description |
|---|---|---|---|---|---|--|
| 1  | ID  | UNIQUE ID | 1  | 7 | 7 | This is an auto-increment integer identifier.  |
| 2  | PRVDR_NPI  | PROVIDER NPI  | 8  | 17 | 10 | This field is the provider's NPI number  |
| 3  | PRVDR_TIN  | PROVIDER TIN  | 18  | 27  | 10 | This field is the provider's TIN  |
| 4  | DATE_ACT  | DATE ACTIVE  | 28  | 37  | 10 | This is the date in which the provider matching is active. The format is "YYYY-MM-DD" |

## File Naming Requirements
The Shared Systems will only accept files in the following format: **[model name].[mm-dd-yyyy].txt**.

**Model Name:** The name of the model to be loaded into the Shared System. Spaces in the model's name are to be replaced with underscores.  
**MM-DD-YYYY:** The date format. January 5th, 2019 would translated to 01-05-2019.

*Example*  
A model with the name "Medicare Care Choices Model" ran through your service on January 5th, 2019 would result in a file named: Medicare_Care_Choices_Model.01-05-2019.txt

