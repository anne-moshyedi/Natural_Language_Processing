# NLP- Entity Resolution
This is a project completed by Taylor Kramer and Anne Moshyedi. It focuses on generating a solution to a problem called Entity Resolution that lies within the scope of Natural Language Processing. Entity Resolution deals with disambiguating entities across, or within, datasets, in order to consolidate and strengthen the integrity of the data.

This document provides a brief overview of the project. Further documentation can be found in academic paper that will be available soon.

## Use Case
The specific use case that is explored deals with matching a user entry, in this case a bank or company address, against an extensive dictionary that contains all of the possible exact addresses. 
## Workflow
This approach uses four stages. 

<img width="936" alt="screen shot 2018-08-09 at 12 10 45 pm" src="https://user-images.githubusercontent.com/34118178/43911818-74d6e0c0-9bce-11e8-979e-6478f972b55a.png">

### Step 1: Input
The first is collecting the user input. This input consists of a clean gold copy of all of the addresses that will be queried and the user-entered adress. These user entered addresses can be exact matches, or they may contain ambiguities, missing values, incorrect fields, improper formatting, abbreviations, truncations, and more.
### Step 2: Preliminary Matching
The second step is to send the data through the preliminary lookup stage. This consists of three matching methods-- an index-based search, a dictionary annotator, and a record linkage method. The first method is an index-based search that queries the solr index that is storing the data. The dictionary annotator also makes use of the solr index and utilizes finite state transducers in determining matches. The record linkage method is a python implementation that compares and groups records using a variety of algorithms, such as Jarowinkler and Levenshtein Distance.
### Step 3: Maching Learning Model
If no matches are found in the preliminary lookup stage, the data is sent to the slightly more computationally expensive ML model. This is a semi-supervised ML model that recognizes patterns in training data in order to determine feature importance in discovering matches. This method is unique in that it does not come with a predetermined set of rules, as do the preliminary matching methods, for determining results. The matches that it discovers are dependent on the data on which the model is trained. This model is based on a multitude of methods, which are discussed further in the paper. The most prominent is the Affine Gap Distance, which is used on every different value of the input.
### Step 4: Display the Result
The final step is to provide the user the results from each of the methods. Here, the user has the option to select the correct address, or refine their search if no correct match is found. The user also has the opportunity to evaluate the timing of the operations, compare the results from each method, and evaluate the accuracy of the ML model with performance metrics including precision and recall.

## Comparing the Results
This diagram illustrates some of the differences between each method. It is important to note that the ML model is left blank because of the uniqueness of ML. It does not have a predetermined set of rules for discovering matches. As more data and edge cases are obtained, the matches that are discovered changes, and the accuracy of the model improves.

<img width="887" alt="screen shot 2018-08-09 at 12 23 24 pm" src="https://user-images.githubusercontent.com/34118178/43912331-e87a0eb6-9bcf-11e8-8625-7a69de35d27a.png">
