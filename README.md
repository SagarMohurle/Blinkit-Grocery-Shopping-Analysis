## Blinkit Grocery Shopping Insights
This Power BI dashboard explores grocery shopping trends and customer preferences. 
The visualizations and metrics provide valuable insights to support decision-making and improve the overall shopping experience.

**Project Steps Overview**  

1. Understand Requirements: Clearly define the project's objectives and identify key metrics or KPIs to focus on.  
2. Explore and Connect Data: Review the data sources and establish connections to ensure seamless integration.  
3. Clean and Process Data: Prepare the data by cleaning, transforming, and organizing it for accurate analysis.  
4. Create DAX Measures: Develop calculated fields and measures using DAX to drive meaningful insights.  
5. Design Dashboard Layout: Structure the dashboard for clarity and user-friendliness, ensuring easy navigation.  
6. Develop Charts: Build visuals like bar charts, line graphs, and tables to represent data effectively.  
7. Generate Insights: Analyze the visuals to uncover trends, patterns, and actionable insights to inform decisions.  

This dashboard features a variety of visualization charts, including cards, clustered bar charts, pie charts, tables, slicers, funnels, area charts, and more. 
Each chart has been thoughtfully selected to present data effectively and make insights easy to understand.

In these Dashboard , i have make a use of slicer that use the measures it can be created by simple using the following steps 
To create a slicer for the measures defined in your SWITCH statement (such as "Total Sales", "Average Sales", "Average Rating", and "No. Item"),
will need a separate table for the slicer that contains those measure names. Here’s how it  can done:

Step-by-Step Instructions
1. Create the Measure Selector Table
First, need to create a table that lists all the measure names, which will be used in the slicer.
-Go to Modeling in Power BI Desktop.
-Click on New Table.
-Enter the following DAX expression to create the Measure Selector table:
    Measure Selector = DATATABLE(
    "Measure Name", STRING,
    {
        {"Total Sales"},
        {"Average Sales"},
        {"Average Rating"},
        {"No. Item"}
    }
)

This table will contain the names of the measures you want to switch between in the slicer.

2. Create the Selected Measure Measure
You already have the following Selected Measure measure defined:
  Selected Measure = 
SWITCH(
    SELECTEDVALUE('Measure Selector'[Measure Name]),
    "Total Sales", SUM('BlinkIT Grocery Data'[Sales]),
    "Average Sales", AVERAGE('BlinkIT Grocery Data'[Sales]),
    "Average Rating", AVERAGE('BlinkIT Grocery Data'[Rating]),
    "No. Item", COUNT('BlinkIT Grocery Data'[Item Identifier]),
    BLANK()  -- Default to blank if no selection matches
)
This measure will calculate the value based on what the user selects in the slicer.

3. Add the Slicer
    1.Drag the Measure Name field from the Measure Selector table to a slicer visual.
          *Go to the Visualizations pane.
          *Select Slicer.
          *Drag Measure Name from the Measure Selector table into the Field well of the slicer.
    2.Format the Slicer (optional):
           *Can choose between a dropdown or list slicer format depending on how you want the slicer to appear.
   
5. Add the Selected Measure to a Visualization
    1.Add a visual (such as a Card, Table, or Bar Chart) where you want the selected measure to be displayed.
    2.Drag your Selected Measure to the Values field well of the visual.
          *The value will dynamically change based on the selection in the slicer.

 
