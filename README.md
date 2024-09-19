# Programmming-Assignment-4

## OBJECTIVES
- Learn how to filter and manipulate data to specific data frames.
- Understand how to apply condition-based filtering to dataset columns.
- Create proper visualization of data frames using Matlplotlib and Seaborn.


## PROBLEM OVERVIEW

Download the provided ECE Board Exam 2 dataset. 

By using data wrangling and data visualization techniques with storytelling, analyze the data and present different: 
- **Data Frames**
- **Visuals**


## PART 1 - DATA FRAMES

**OBJECTIVE:**
- Create a filtered data frames based on specific conditions and columns using data wrangling techniques.

**TASK:**

*Create the following data frames:*
- `Instru = [“Name”, “GEAS”, “Electronics >70”]; where the track is constant as Instrumentation and hometown Luzon`
- `Mindy = [ “Name”, “Track”, “Electronics”, “Average >=55”]; where hometown is constant as Mindanao and gender Female`

**CODE PROPER:**

      # import data set
      df = pd.read_excel('board2.xlsx')            
      df                                          

      # Filter the data by these conditions, where: the Track must be Instrumentation; the Hometown is Luzon
      # The grade in Electronics must also be greater than 70
      Instru = df[(df['Track'] == 'Instrumentation') &                                                                                  
              (df['Hometown'] == 'Luzon') &                                            
              (df['Electronics'] > 70)][['Name', 'GEAS', 'Electronics']]`
      Instru

      #this will compute the average grade of each student and create another column for the result
      df['Average']=df[['Math', 'Electronics', 'GEAS', 'Communication']].mean(axis=1)`
      df

      # Filter the data by these conditions, where: the Gender must be Female; the Hometown is Mindanao
      # The average grade must also be greater than or equal to 55.
      Mindy = df[(df['Gender'] == 'Female') & 
            (df['Hometown'] == 'Mindanao') & 
            (df['Average'] >= 55)][['Name', 'Track', 'Electronics', 'Average']]`
      Mindy


## PART 2 - VISUALIZATION OF DATA

**OBJECTIVE:**
- Create visualizations using MatplotLib and Seaborn to show how the different features in the dataset contribute to students' average grades.


**TASK:**

*Generate visualizations that will answer and prove if:*
- The chosen track in college, gender, or hometown contributes to a higher average score.

**NOTES:**
- Use a **vertical bar graph** to compare average grades across different categories (e.g., tracks, gender, hometowns).
- Optionally, include additional visualizations like **boxplots** or **histogram** to show the distribution of data within each category.
  
**CODE PROPER:**

- For **Vertical Bar Graph**

`- provides a clear, straightforward way to visualize differences and make comparisons between different sets of data.`

  #### Gender
      plt.figure(figsize=(4,4))                                      #sets the size of the grid
      plt.title("Average Grade Distribution by Gender")              #creates a title for the graph
      sns.barplot(x="Gender", y="Average", data=df)                  #syntax to create a bar graph
      plt.show()                                                     #print

   #### Hometown
      plt.figure(figsize=(4,4))                                      #sets the size of the grid
      plt.title("Average Grade Distribution by Hometown")            #creates a title for the graph
      sns.barplot(x="Hometown", y="Average", data=df)                #syntax to create a bar graph
      plt.show()                                                     #print

   #### Track
      plt.figure(figsize=(4,4))                                      #sets the size of the grid
      plt.title("Average Grade Distribution by Track")               #creates a title for the graph
      sns.barplot(x="Track", y="Average", data=df)                   #syntax to create a bar graph
      plt.show()                                                     #print

### OTHER VISUALS

- For **Boxplot**

`- shows the distribution of grades for each group (track, gender, hometown) and highlights the median, quartiles, and potential outliers.`

   #### Gender
      plt.figure(figsize=(5,3))
      sns.boxplot(x= "Gender", y= "Average", data=df)
      plt.title("Average Grade Distribution by Gender")
      plt.show()

   #### Hometown
      plt.figure(figsize=(5,3))
      sns.boxplot(x= "Hometown", y= "Average", data=df)
      plt.title("Average Grade Distribution by Hometown")
      plt.show()
  
   #### Track
      plt.figure(figsize=(5,3))
      sns.boxplot(x= "Track", y= "Average", data=df)
      plt.title("Average Grade Distribution by Track")
      plt.show()

- For **Histogram**

`- best for visualizing the frequency distribution of a single numeric variable and seeing the overall shape of the grade distribution for each group. `

   #### Create the figure
      plt.figure(figsize=(12,10))
  
   #### Gender
      plt.subplot(2,2,1)
      sns.histplot(df, x = "Average", hue = "Gender", multiple = "stack")
      plt.title("Average Grade Distribution by Gender")
      
   #### Hometown
      plt.subplot(2,2,2)
      sns.histplot(df, x = "Average", hue = "Hometown", multiple = "stack")
      plt.title("Average Grade Distribution by Hometown")
      
   #### Track
      plt.subplot(2,2,3)
      sns.histplot(df, x = "Average", hue = "Track", multiple = "stack")
      plt.title("Average Grade Distribution by Track")

   #### Set the figure and show
      plt.tight_layout()
      plt.show()


## SAMPLE TEST RUN

*Create the following data frames using the same dataset above:*

`Sample = [“Name”, “Track”, “Math”, “Electronics”, “Average > 60"]; where Track is either Microelectronics or Instrumentation, Electronics < Math, and select only the even-numbered rows.`


#### PART 1: DATA FRAME

*Code Proper:*

      #slicing the dataframe in even-numbered rows (for every second row)
      new_df = df.iloc[0:30:2] 

      sample = new_df[((new_df["Track"] == "Microelectronics") | (new_df["Track"] == "Instrumentation"))  
      #track must be either **microelectronics** or **instrumentation**
        
        &((new_df["Electronics"]) < (new_df["Math"]))   
        #their grade in **math** is greater than their grade in **electronics**
        
        &(new_df["Average"] > 60)][["Name", "Track", "Math", "Electronics", "Average"]]   
        #their average grade must be greater than 60; #the specified columns selected and returned to the new data frame
            
      #print the output
      sample

*Expected Output:*

|      | Name  |       Track       | Math | Electronics | Average |
|:----:|:-----:|:-----------------:|:----:|:-----------:|:-------:|
| 2    | S3    | Instrumentation   | 83   |     74      | 72.75   |
| 12   | S13   | Microelectronics  | 88   |     35      | 62.25   |
| 16   | S17   | Microelectronics  | 81   |     79      | 70.50   |
| 18   | S19   | Microelectronics  | 79   |     63      | 73.00   |
| 20   | S21   | Instrumentation   | 83   |     51      | 68.50   |
| 22   | S23   | Instrumentation   | 84   |     70      | 68.75   |
| 26   | S27   | Microelectronics  | 70   |     47      | 60.75   |
| 28   | S29   | Instrumentation   | 73   |     48      | 63.50   |

 
 #### PART 2: VISUALIZATION
 *Create a visualization that shows the correlation between students' grades in Math and Electronics and how their average grade affects them.

 In this problem, we can use **Scatterplot** to visualize these data.

 *Code Proper:*
 
      plt.figure(figsize=(6, 4))
      sns.scatterplot(data=sample, x='Math', y='Electronics', hue='Average', s=80)
      plt.title('Math and Electronics Grades with Average Score Indicators')
      plt.xlabel('Math')
      plt.ylabel('Electronics')
      plt.show()
      
*Expected Output:*

![image](https://github.com/user-attachments/assets/7d6576fa-7690-4fce-bf5b-ec60f46c913f)



## VERSION HISTORY
**September 19, 2024**

- [as of 11:50 PM] = *reuploaded the updated jupyter nb{***w/:*** markdowns and more structured codes}; building readme file {***w/:*** already created sample test runs and code proper}*
- [as of 4:45 PM] = *uploaded raw jupyter nb {***w/o:*** markdowns yet, will be reuploaded}; building readme file {***w/:*** objectives and overview of the problems given; ***w/o:*** code proper and sample test runs yet}* 
- [as of 10:03 AM] = *created 'Programming-Assignment-4' repository ~ {initial upload}*


`Submitted by: Alesandra Joyce P. Maghanoy`

