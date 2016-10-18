# Visual Diagnostics
@author: Rebecca Bilbro, District Data Labs, Bytecubed

get slides from twitter @rebeccabilbro

Anscombes quartet: illustrates how you can't make assumptions on data based on their stats summaries

## the model selection triple
selecting the right model, the right features, the right parameters
- feature analysis: what's informative?
- model selection: what captures the data behavior?
- hypertuning: optimize the performance of the model

## visual feature analysis
getting started with boxplots: which input features are out of scale?
- maybe you need to normalize 

histograms: looking for a normal distribution  
- otherwise you may need to transform

violin plots: box + hist all together  

sploms: scatterplot matrix, pairwise comparisons  
- check for homoskedactisity

jointplots: more focused than sploms  
- kernel density and pearson coeff

radviz: hunting for separability in classfication  
- plots the features and pull data points based on normalized values

parallel coordinates: line segment represents datapoint vector  

## visual model selection
scikitlearn decision flow is a good starter  

cluster comparison and classifier comparison plots 

models: families, forms, fitted  
- hadley wickham - removing the blindfold  
- families: classification vs bayes, etc
- form: before fit
- fit: paramaters are adjusted 

Comparing models
- classification heatmap
    - use all the models then compare to see who performs the best
- ROC / AUC plots
- model evaluation: compare train and test points
    - prediction error plots
    - residual plots

## visual tuning
validation curves: explore single parameter across values to find optimal point 
- compare train and CV scores  

pairwise hyperparameter tuning: visual grid search  
- heatmap to see where they together result in best performing model

## better workflows
so many libraries! matplotlib, pandas viz, seaborn 

**[Yellowbrick](https://github.com/DistrictDataLabs/yellowbrick)**: machine learning in color
- applying the model selection triple
- plays nicely with scikitlearn API
- gets these features under one library 

additional yellowbrick features  
- class balance report

**testers: bit.ly/ybtesters**
[blog series](http://blog.districtdatalabs.com/visual-diagnostics-for-more-informed-machine-learning-part-1)
[District Data Lab] (http://blog.districtdatalabs.com/)
