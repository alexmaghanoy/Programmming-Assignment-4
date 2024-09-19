# Programmming-Assignment-4
**Submitted by:** Alesandra Joyce P. Maghanoy


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
- Instru = [“Name”, “GEAS”, “Electronics >70”]; where the track is constant as 
Instrumentation and hometown Luzon
- Mindy = [ “Name”, “Track”, “Electronics”, “Average >=55”]; where hometown is 
constant as Mindanao and gender Female

**CODE PROPER:**

      df = pd.read_excel('board2.xlsx')
      df

      Instru = df[(df['Track'] == 'Instrumentation') & 
            (df['Hometown'] == 'Luzon') & 
            (df['Electronics'] > 70)][['Name', 'GEAS', 'Electronics']]`
      Instru

      df['Average']=df[['Math', 'Electronics', 'GEAS', 'Communication']].mean(axis=1)`
      df

      Mindy = df[(df['Gender'] == 'Female') & 
            (df['Hometown'] == 'Mindanao') & 
            (df['Average'] >= 55)][['Name', 'Track', 'Electronics', 'Average']]`
      Mindy

**SAMPLE TEST RUNS:**

## PART 2 - VISUALIZATION OF DATA

**OBJECTIVE:**
- Create visualizations using MatplotLib and Seaborn to show how the different features in the dataset contribute to students' average grades.


**TASK:**

*Generate visualizations that will answer and prove if:*
- The chosen track in college, gender, or hometown contributes to a higher average score.

**NOTES:**
- Use a **vertical bar graph** to compare average grades across different categories (e.g., tracks, gender, hometowns).
- Optionally, include additional visualizations like **boxplots** to show the distribution of data within each category or
**histogram** to see the distribution of data within each category.
  
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


**SAMPLE TEST RUNS:**
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


## VERSION HISTORY
**September 19, 2024** - Initial Upload (on-going) 

- [as of 11:50 PM]
- [as of 4:45 PM] = *uploaded raw jupyter nb code {***w/o*** markdowns yet, will be reuploaded}, building readme file {***w/*** objectives and overview of the problems given; ***w/o*** code proper and sample test runs yet}* 
- [as of 10:03 AM] = *created 'Programming-Assignment-4' repository*

