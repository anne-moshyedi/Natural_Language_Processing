# NLP- Entity Resolution
This is a project completed by Taylor Kramer and Anne Moshyedi. It focuses on generating a solution to a problem called Entity Resolution that lies within the scope of Natural Language Processing. Entity Resolution deals with disambiguating entities across, or within, datasets, in order to consolidate and strengthen the integrity of the data.

This document provides a brief overview of the project. Further documentation can be found in academic paper that will be available soon.

## Use Case
The specific use case that is explored deals with matching a user entry, in this case a bank or company address, against an extensive dictionary that contains all of the possible exact addresses. 
## Workflow
This approach uses four stages. 
### Step 1: Input
The first is collecting the user input. This input consists of a clean gold copy of all of the addresses that will be queried and the user-entered adress. These user entered addresses can be exact matches, or they may contain ambiguities, missing values, incorrect fields, improper formatting, abbreviations, truncations, and more.
### Step 2: Preliminary Matching
The second step is to send the data through the preliminary lookup stage. This consists of three matching methods-- an index-based search, a dictionary annotator, and a record linkage method. The first method is an index-based search that queries the solr index that is storing the data. The dictionary annotator also makes use of the solr index and utilizes finite state transducers in determining matches. The record linkage method is a python implementation that compares and groups records using a variety of algorithms, such as Jarowinkler and Levenshtein Distance.
### Step 3: Maching Learning Model
If no matches are found in the preliminary lookup stage, the data is sent to the slightly more computationally expensive ML model. This is a semi-supervised ML model that recognizes patterns in training data in order to determine feature importance in discovering matches. This method is unique in that it does not come with a predetermined set of rules, as do the preliminary matching methods, for determining results. The matches that it discovers are dependent on the data on which the model is trained.
### Step 4: Display the Result
The final step is to provide the user the results from each of the methods. Here, the user has the option to select the correct address, or refine their search if no correct match is found. The user also has the opportunity to evaluate the timing of the operations, compare the results from each method, and evaluate the accuracy of the ML model with performance metrics including precision and recall.
