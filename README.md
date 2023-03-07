# Penguins Classification
This project is about classifying the Penguins into tree type (Chinstrap, Adélie, or Gentoo) based on their body mass (g), flipper length (mm), culmen depth (mm), culmen length (mm), why we do this project because some Penguins looks similar, I use knime as software to build this project, also I used crisp model


### Data
- I use the data from https://www.kaggle.com/datasets/parulpandey/palmer-archipelago-antarctica-penguin-data?select=penguins_size.csv

  penguin data sets. Contains variables:

  - species: penguin species (Chinstrap, Adélie, or Gentoo)
  - culmen_length_mm: culmen length (mm)
  - culmen_depth_mm: culmen depth (mm)
  - flipper_length_mm: flipper length (mm)
  - body_mass_g: body mass (g)
  - island: island name (Dream, Torgersen, or Biscoe) in the Palmer Archipelago (Antarctica)
  - sex: penguin sex

<br>

### Data Understanding

We can try to visualize our dataset to properly understand the dataset we are working with. To achieve this, we can use a few nodes.



  ![Alt text](/img/DataUnderstanding.jpg "Optional title")



  ### Method
  1. Open your workflow in Knime

  2. Add a "File Reader (deprecated)" node to your workflow. You can find this node by typing "File Reader (deprecated)" in the Node Repository search bar.


  ![Alt text](/img/Screenshot%202023-03-01%20212723.jpg "Optional title")
    
 - I use this node to read my data

<br>

  3. Add a "Interactive Table" node to your workflow. You can find this node by typing "Interactive Table" in the Node Repository search bar.
<br>
      ![Alt text](/img/IntractiveTable.jpg "Optional title")
- I use this node the data
 <br>
<br>
  4. Add a "Statistics" node to your workflow. You can find this node by typing "Statistics" in the Node Repository search bar.  
<br>


 ![Alt text](/img/Statistics.jpg "Optional title")


<br>
- I use this node to see if i hava missing Data 

<br>

 ![Alt text](/img/missing%20value.jpg "Optional title")

   <br>
   
   - As you can see in this pic i have missing Data in 
      -  culmen_length_mm 
      
      -  culmen_depth_mm 
      
      -  flipper_length_mm 
 
      -  body_mass_g 
<br>

## Data Preparation

  ![Alt text](/img/DataPreparation.jpg "Optional title")

<br>

  5. Add a "Missing Value" node to your workflow. You can find this node by typing "Missing Value" in the Node Repository search bar.
<br>
 
 <br>

  ![Alt text](/img/Missing%20ValueNode.jpg "Optional title")
 <br>

  - I use this node to fix the missing value

<br>
6. Add a "Colunm Filter" node to your workflow. You can find this node by typing "Colunm Filter" in the Node Repository search bar.

<br>
  
  ![Alt text](/img/column.jpg "Optional title")
 <br>

  - I use this node to choose which column I want

 <br>
  
  ![Alt text](/img/ColumnFilterconfic.PNG "Optional title")

  - put the column you want in the right section


<br>
7. Add a "Patritioning" node to your workflow. You can find this node by typing "Patritioning" in the Node Repository search bar.

<br>
  
  ![Alt text](/img/Partitoning.JPG "Optional title")
 <br>

  - I use this node to split the data into two output 
       - for Learner node 
       - for Predictor

 <br>
  
  ![Alt text](/img/Partitioningconfic.JPG "Optional title")

  - double click on the Partitioning node to open the configuration tab here I choose Relative 20 which means the first output will take 20% of the data and I choose Draw randomly which will take 20% of the data randomly the rest of the data will be on the second output
## Modeling

   ![Alt text](/img/Modeling.jpg "Optional title")

<br>

  <br>

   ![Alt text](/img/firstMachine.JPG "Optional title")
  
  - I connect the first output from Partitioning with Learner and the scond output with Predictor also I connect the blue square of the Learner with the blue square of the predictor 

  - I use Scorer Node to see the result of the machine-learning

<br>

![Alt text](/img/Dublecat4.JPG "Optional title")

  - <span style="color:red">Note</span> I duplicate the last step 4 times because I have 4 Classification Algorithms in Machine Learning .

  -  <span style="color:red">NOTE</span> every machine learning has to own its Learner and Predictor.


  -  <span style="color:red">NOTE</span> to see the result of the machine learning click right on the scorer node and choose the confusion matrix or click on F10 on your keyboard . 

  - It will show you this tab

![Alt text](/img/resultMachine.JPG "Optional title")

## Evaluation

![Alt text](/img/Evaluation.jpg "Optional title")

#### Cleaning up 

We can use the Accuracy statistics to find the accuracy of the models we used. However, the resulting table from the scorer contains unnecessary information, so we will need to filter it.

![Alt text](/img/CleanUp.jpg "Optional title")
We use the Column filter and row filter nodes to get rid of the unneeded columns and rows and then use Column rename node to rename our column.
 
After the filtering, we will be left with this. 

![Alt text](/img/Afterfilterr.jpg "Optional title")

- <span style="color:red">Note</span> I duplicate the last step 4 times because I have 4 Classification Algorithms in Machine Learning .

#### Combining the results and comparing

We can use the Column Appender node to combine our adjusted results and combine it into a singular table which we can use along with another node to compare our results. In this case, I will be using the Tile View and the Table View node.

![Alt text](/img/column%20Appender.jpg "Optional title")

Finally, we can take a look at the views and determine which model would be best suited for us.

![Alt text](/img/TileView.jpg "Optional title")
![Alt text](/img/TableView.jpg "Optional title")

In our case, Naive Bayes seems to have the best accuracy results with 990.% accurate results.

### Conclusion
In this research, I utilized KNIME to assess which machine learning model would be most suited to the given dataset.

### Author
Yaser Abulkhair - 641431023

