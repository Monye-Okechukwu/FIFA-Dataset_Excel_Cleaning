# Data Cleaning: Inspecting and Wrangling the FIFA 21 Data Using Microsoft Excel

![image1](https://github.com/Monye-Okechukwu/FIFA-Dataset_Excel_Cleaning/assets/136334167/72e40fa0-5a2d-4ae3-acbf-deac78a7964a)

<sup>Source: *[FIFA-21-Lag.jpeg (1920×1280) (windowsreport.com)](https://cdn.windowsreport.com/wp-content/uploads/2020/10/FIFA-21-Lag.jpeg)*

## Background
I was thrilled to take part in a #datacleaningchallenge in the data-tech community that Promise Chinonso and other data enthusiasts organized in an effort to foster an atmosphere where novice, advanced, and professional data analysts could hone their data cleaning skills. The competition gives Data Analysts a chance to connect with other students and expand their networks. Every participant was also urged to demonstrate their data cleaning abilities using any tool of their choice, including Excel, Power-Query, SQL, Python, R, and Google Sheets.

> The tool used for this challenge was the Microsoft Excel.

![image2](https://github.com/Monye-Okechukwu/FIFA-Dataset_Excel_Cleaning/assets/136334167/4d6857d5-7285-4b53-a187-53c0023fdeee)

Data cleaning, also known as data wrangling, is an important stage in the data analytics process. Prior to the main analysis, data preparation and validation are typically performed for this critical procedure. Although this is commonly used in data cleansing, it is not the only technique. The majority of the effort is devoted to locating and fixing dirty data, which includes incorrect, incomplete, irrelevant, corrupt, or improperly formatted data and replacing, transforming, or removing the dirty or data.

### ***PROJECT OBJECTIVES***
After accessing the data for importing, three objectives should be met after the cleaning process:
-	Data Quality: Ensuring accuracy and consistency of data by addressing incorrect data types, null entries, missing values, special characters, duplicate entries, and errors in spellings and values.
-	Data Integrity: Ensuring the integrity of data by detecting and correcting wrong calculations across rows and columns.
-	Data Relevance: Ensuring data relevance by removing irrelevant data from the dataset.

### ***About the dataset***
The FIFA 21 data was used for this task. It was obtained from Kaggle and can be found [here](https://www.kaggle.com/datasets/yagunnersya/fifa-21-messy-raw-dataset-for-cleaning-exploring). After web scraping sofifa.com, the information was acquired in its unprocessed form. It includes information about football players as well as their performance, which is kept up to current until 2021. It is worth noticing that the FIFA 21 data contains 18979 rows and 77 columns. In order to become acquainted with the data before cleaning, the collection includes a [data glossary](https://haven05-my.sharepoint.com/:p:/g/personal/shalom_haven05_onmicrosoft_com/Ea_1vs8RYLxHvzxE1Z9--GIBlSrxWuM2vKxJdRkOeqhtEA)

### ***DATA EXPLORATION AND CLEANING***
The Raw data was first downloaded as a Zipped file, which was then opened, extracted, and changed to CSV (Comma Separated Values) format before being opened in Microsoft Excel.
I did some quick scrolling in this dataset and let me tell you, it was a real hot mess! But don't you worry, I rolled up my sleeves, put on my cleaning hat and got to work. I had to go through a lot of hoops and loops, but I managed to turn this sloppy data into something beautiful and ready for analysis! And you know what? I'd love to share the whole process with you. Buckle up and get ready to learn how I transformed this dataset from a chaotic mess to a sparkling gem!
I created a copy of the worksheet and renamed it to “Cleaned” so changes made won’t affect the origin data.

- The dataset has no duplicate value.
![image3](https://github.com/Monye-Okechukwu/FIFA-Dataset_Excel_Cleaning/assets/136334167/1befb9fa-d1f2-40b7-9679-56efd0c411d3)

- The ***Name*** and ***LongName*** columns contained some special character. ***PlayerURL*** columns contained weblink of the players’ profile and it has the full names of the players embedded within the URL without special characters.
![image4](https://github.com/Monye-Okechukwu/FIFA-Dataset_Excel_Cleaning/assets/136334167/c9b8e459-379f-4b8a-ba4a-721ef4033f56)

Using text to columns to get the player’s full name then using find and replace to remove the hyphen to space for the column created. PROPER function was used to makes the names in proper case.
![image5](https://github.com/Monye-Okechukwu/FIFA-Dataset_Excel_Cleaning/assets/136334167/32ef56fe-0a40-4305-9f2a-c9de89fc9afd)

- ***PlayerURL*** column has been removed as the full names has been extracted. ***PhotoURL*** column contained link to the images of the players. These columns were removed from the data.
- ***Club*** column had extra spaces or they were unwrapped, I clicked the wrap text in the alignment group to remove the extra spaces.

![image6](https://github.com/Monye-Okechukwu/FIFA-Dataset_Excel_Cleaning/assets/136334167/249ae31e-bdee-4923-8a2e-cfbca54dbb42)

- ***Nationality***, ***Name*** and ***Club*** columns had special characters.

![image7](https://github.com/Monye-Okechukwu/FIFA-Dataset_Excel_Cleaning/assets/136334167/2bd75958-8b51-436b-be4c-e3f75e861ff5)

find and replace was used in correcting them. Correct letters were gotten from the correct ***longName*** column gotten.

![image8](https://github.com/Monye-Okechukwu/FIFA-Dataset_Excel_Cleaning/assets/136334167/dfd38837-43a1-420d-84f4-1e5f4befc666)

- The ***Contract*** column had inconsistent values and the wrong data type. The column has 3 categories of values in the format, *30 Jun, 2021 on Loan*, *Free* and *2004 ~ 2021*. To tackle this issue, I created three new columns. 

Process: The first column agreement to know if the player is on loan, contract or free. I used a conditional statement “=IF(RIGHT(P2,4)="loan","Loan",IF(RIGHT(P2,4)="Free","Free","Contract"))”, where P is the contract column.
To get the ***ContractStart*** column I used a conditional statement “=IF(Q2="Contract",LEFT(P2,4),"")”, where Q is the agreement column.
To get the ***ContractEnd*** column I used a conditional statement “=IF(Q2="Contract",RIGHT(P2,4),"")”

![image9](https://github.com/Monye-Okechukwu/FIFA-Dataset_Excel_Cleaning/assets/136334167/8b6ac5e2-9ecb-4603-82e9-d60eddbd4983)

the ***Contract*** column is no needed again.

- ***Positions*** column was removed because there is another column bearing the ***Best_Position*** of each player. The ***Positions*** column had the details in the ***Best_Position*** column in addition to the extra positions for players that had more than one position.

![image9](https://github.com/Monye-Okechukwu/FIFA-Dataset_Excel_Cleaning/assets/136334167/e21d249e-2ace-41aa-bfb7-e8eaef3d775c)

- ***Height*** column had inconsistencies in the units attached to their values. The entries For the ***Height*** column were in the format, *170cm*, *6’2* (feet & inches). To tackle this issue, I created a new column *Height_cm*

![image10](https://github.com/Monye-Okechukwu/FIFA-Dataset_Excel_Cleaning/assets/136334167/24eca604-7696-42fb-abec-1ecc24ef0f20)

The interconversions were possible using the conditional formula below for *height_cm* column conversion:
I brought out the values in centimetres from the *height* column and named it *cm* using this function: “=IF(RIGHT(A2,2)="cm",LEFT(A2,3),"")”
Then I brought out the values in feet from the *height* column and named it *feet* using this function: “=IF(MID(A2,2,1)="'",LEFT(A2,1),"")”
Then I brought out the values in inches from the *height* column and named it *inches* using this function: =IFERROR(MID(A2,FIND("'",A2)+1,2),"")
Finally I made all the values to be in cm and named it *Height_cm* using this function: =IF(RIGHT(A2,2)="cm",B2,CONVERT(C2,"ft","cm")+CONVERT(D2,"in","cm"))

![image11](https://github.com/Monye-Okechukwu/FIFA-Dataset_Excel_Cleaning/assets/136334167/c9a9a8c1-b80f-4a55-a9ae-f7b879a7fe68)

- *Weight* column had inconsistencies in the units attached to their values. The entries For the *Weight* column were in the format, *79kg*, *172lbs*. To tackle this issue, I created a new column *Weight_kg*

![image12](https://github.com/Monye-Okechukwu/FIFA-Dataset_Excel_Cleaning/assets/136334167/87a359f0-afdb-4e71-bd4b-f4e7a78f9a87)

The interconversions were possible using the conditional formula below for *Weight_kg* column conversion:
Firstly I got the length of the values in the column *weight* using this function: =LEN(H2)
Then I brought out the values in lbs from the *weight* column and named it *lbs* using this function: =IF(RIGHT(H2,3)="lbs",LEFT(H2,3),"")
Then I brought out the values in kg from the *weight* column and named it *kg* using this function: =IF(RIGHT(H2,2)="kg",LEFT(H2,I2-2),"")
Finally, I made all the values to be in *kg* and named it *Weight_kg* using this function: =IF(RIGHT(H2,2)="kg",K2,CONVERT(J2,"lbm","kg"))

![image13](https://github.com/Monye-Okechukwu/FIFA-Dataset_Excel_Cleaning/assets/136334167/c3b48aa1-35a3-42b6-a010-bc8c399de5cc)

- *Joined* column had the start of the agreement and the *loan date end*. I created two new columns to extract the *loan_start* and *loan_end*. For *loan_start* I used this function: =IF(N2="Loan",RIGHT(Q2,4),"")to get loan start year.
For *loan_end* I used this function: =IF(N2="loan",RIGHT(R2,4),"") to get the loan end year.

![image14](https://github.com/Monye-Okechukwu/FIFA-Dataset_Excel_Cleaning/assets/136334167/9c60a6d4-c2e2-4065-91c8-d7c56de02316)

*joined* and *loan date end* were removed after adding this two columns.

- *OVA* and *POT* and *BOV*: The OVA means the Player Overall Rating, POT means Overall Potential and BOV means best overall according to the Data Dictionary. I renamed the columns to *Overall_Rating*, *Potential_Rating* and *Best_Overall_Rating*. They had values in the range of 47-95.  According to the Data Dictionary, it is best they are represented in percentages. To achieve this, these columns were first divided by 100, and then subsequently converted to the percentage data type which multiplied all the values by a factor of 100.

![image15](https://github.com/Monye-Okechukwu/FIFA-Dataset_Excel_Cleaning/assets/136334167/15a6c1a4-e798-4319-9f6d-bb54d61b0d3c)

- *Value*, *Wage* and *Release_clause- columns had data type issues and values with suffixes in front. These columns had suffixes *'M'* for millions, *'K'* for thousands and special character *â‚¬* that should be *€* for euro (currency).

![image16](https://github.com/Monye-Okechukwu/FIFA-Dataset_Excel_Cleaning/assets/136334167/19d4821b-6871-4308-b8a1-d9c0be5a00b1)

Find and replace was used in removing the special character. This functions: “=LEFT(V2,LEN(V2)-1)” removed the suffix for the *Value* column, “=IF(RIGHT(W2,1)="K",LEFT(W2,LEN(W2)-1),W2)” removed suffix for the *Wage* column, it is somewhat different cause some values were without suffix and “=LEFT(X2,LEN(X2)-1)” removed suffix from the *Release clause* column. Removing the suffix made it easy to multiply the values.
“=IF(RIGHT(V2,1)="M",Y2*1000000,IF(RIGHT(V2,1)="K",Y2*1000,0))” This conditional function converted the values to be in millions and thousands for the *value* column.
“=IF(RIGHT(W2,1) = "K",  Z2*1000, Z2)” This conditional function converted the values to be in millions and thousands for the *Wage* column. This formula was used cause all the values here were in “K”
“=IF(RIGHT(X2,1)="M",AA2*1000000,IF(RIGHT(X2,1)="K",AA2*1000,0))” This conditional function converted the values to be in millions and thousands for the *Release Clause* column. I renamed the columns to *Value(£)*, *Wage(£)* and *Release_Clause(£)* respectively and changed the data type to currency.

![image17](https://github.com/Monye-Okechukwu/FIFA-Dataset_Excel_Cleaning/assets/136334167/cf8aedd4-a665-4fc3-9ea6-906a8841059a)

- *W/F*, *SM*, and *IR* columns all contain ratings on a scale of 1-5. The values in these columns had the special character * â˜…* in front.

![image18](https://github.com/Monye-Okechukwu/FIFA-Dataset_Excel_Cleaning/assets/136334167/dd02acb7-148e-4d01-9544-99f18db32157)

The special characters were removed using *Find and replace* with a “” and the columns renamed *WeakFoot_Rating*, *SkillMoves_Rating* and *Injury_Rating* respectively.

![image19](https://github.com/Monye-Okechukwu/FIFA-Dataset_Excel_Cleaning/assets/136334167/6a578ba7-4374-4bdd-bd91-efbae40cdcf9)

- *A/W* and *D/W* columns were renamed to *Attacking_Rate* and *Defensive_Rate*. No issue were found with the columns.
- *Hits* column contained numbers (whole number and decimal number types) with the *K* suffixes. For context, values like 1100 were stored as 1.1K

![image20](https://github.com/Monye-Okechukwu/FIFA-Dataset_Excel_Cleaning/assets/136334167/13f17fee-88c0-4e5d-869f-3a57384310bd)

To get these values in numerical format, I created a column using this function: “=IF(RIGHT(AF2,1)="K",LEFT(AF2,LEN(AF2)-1),AF2)” to remove the suffix *“K”* and leave the others how they are. Then I created another column using this function: “=IF(RIGHT(AF2,1)="K",AG2*1000,AG2)” to multiply the values with suffix “K” by 1000.

![image21](https://github.com/Monye-Okechukwu/FIFA-Dataset_Excel_Cleaning/assets/136334167/6b620086-6a7a-42e6-9ce7-32c356c696ac)

- *Attacking*, *Crossing*, *Finishing*, *Heading_Accuracy*, *Short_Passing*, *Volleys*, *Skill*, *Dribbling*, *Curve*, *FK_Accuracy*, *Long_Passing*, *Ball_Control*, *Movement*, *Acceleration*, *Sprint_Speed*, *Agility*, *Reactions*, *Balance*, *Power*, *Shot_Power*, *Jumping*, *Stamina*,	*Strength*,	*Long_Shots*, *Mentality*, *Aggression*, *Interceptions*, *Positioning*, *Vision*, *Penalties*, *Composure*, *Defending*, *Marking*, *Standing_Tackle*, *Sliding_Tackle*, *Goalkeeping*, *GK_Diving*,	*GK_Handling*, *GK_Kicking*, *GK_Positioning*, *GK_Reflexes*,	*Total_Stats*, *Base_Stats*, *Pace*, *Shooting*, *Passing*, *DRI*, *Defending*, *Physical* were checked and no issues found within the data. The data types were checkmated, and changes were made for some that had wrong data types and column names corrected.

### Conclusion

Although the FIFA 21 data presented some challenges during the cleaning process, the dataset was eventually transformed into a usable format for analysis despite the initial disorganization.

The cleaned dataset can be found in the [Fifa21_cleaned file](https://github.com/Monye-Okechukwu/FIFA-Dataset_Excel_Cleaning/raw/Process/FIFA21/Fifa21_Cleaned.xlsx).

Thanks for your time!
