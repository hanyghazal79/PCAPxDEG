# PCAPxDEG
A Python Clustering Analysis Protocol Of Genes Expression Data Sets
Here, we describe the meaning of the Python statements used to  perform clustering analysis on gene expression data sets. We assume that users have  already installed Python and all the necessary additional packages on their machines. For  more information on setting up a Python environment for machine learning in Windows,  Linux and macOS, the readers could go through the Python user guides related to their installed operating system. 
The first lines of code of any Python script identify the import section, mandatory to include into the script the necessary additional library i.e., the sklearn, numpy, matplolib, seaborn and pandas supplied as additional functions to the programmer. In Listings 3 and 4 the import section starts at line 1 and ends at line 8, in this way all the class and functions of each module can be used by a simple function call, e.g., to show a plot on the screen by using the matplot functions, can be used the following statement plt.show(). It is worth to note that each library different from the built-in must explicitly imported into the script before they can be used. 

The instruction at line 11 of both Listings 3 and 4 defines the variable named data that holds the path to the input data to investigate. To upload the input data, the data variable is passed as argument to the genfromtxt numpy function that will load, transpose and memorize the input data within the variable named gene_exp_val. The other arguments of the genfromtxt are: i) delimiter= that defines symbols used to delimit the  input data e.g., the ',';  ii) usecols= allows to select the range of columns to upload e.g., all the column; iii) skip_header= we pass the index of the headers row, that is not useful for the clustering analysis. At the end of data uploading, calling the numpy transpose functions, the input table will be transposed and stored into the gene_exp_val variable Listings 3 and 4 line 15.

Data scaling is obtained by instantiating a MaxAbsScaler object using the statement at Listings 3 and 4 line 18 called scaler. Next, we invoke on the scaler object the fit_transform(gene_exp_val) and passing the data within the gene_exp_val variable. As a result, the scaled data will be stored into the transformed_data variable Listing 3 and 4 line 20. 
Dimensionality reduction is obtained creating an object of the class PCA calling the constructor. The constructor allows to set up the value of the parameters n_componets = 2, e.g., the number of components to keep and random_state = 78, e.g., using an int value as argument allows to reproduce results across multiple function calls. Next, we call the fit_transform( transformed_data) method feeding it with the transformed data within the transformed_data variable Listing 3 and 4 line 23. 

The pre-processed DEG data are holded within the variable pca_data that will be supplied as input data to both the K-Means object Listing~ref{simpleCode line 26 and the DBSCAN objects Listing~ref{dbscanCode line 26. Now all the information about the K-Means execution are memorized within the variable named kmeans, in particular, we are interested to the labels_ attribute value. Also for DBSCAN the information are stored within the variable named dbscan in particular, we are interested to the labels_ attribute value.

The values of labels_ of both objects, will be used to create and fill the columns of a data frame line 30 of both Listings 3 and 4 to generate the cluster figure through the matplot and seaborn library lines 32 ldots 48. 
The statement at line 32 allows to chose the figure style, whereas line 33 allows to tune the figure size. The statement at line 34 spread on multiple lines just for indentation purpose defines the type of seaborn plot to create, e.g., scatterplot calling the scatterplot function and customizing its parameters as follows. The "X" and "Y" values define the name of the x and y axes in the plot.
The argument s=50 defines the size of scatter markers.
The argument data=dataframe allows to tune the input data structure, whereas hue="clusters" produces points with different colors, and palette="Set2" parameters defines the colors to use when mapping the hue parameters.

The statement at line 42 of both Listings 3 and 4 allows to save the figure as file on the hard disk. The savefig function allows to save the figure in different format by setting the format argument, e.g., format='eps' save on the disk the figure as eps file, at the location defined by the path holded by the fname argument, e.g., './clusters.eps'. The dpi=300 argument defines the resolution in dots per inch. The bbox_extra_artists argument allows to define the extra element to include into the figure list of Artist, optional when the tight bbox is calculated, e.g., the legend lg defined at line 40. The bbox_inches='tight' defines the portion of the figure to save.
The statement at line 47 allows to adjust the padding between and around subplots, and finally the statement at line 48 visualizes on the screen the scatter plot.

Finally, it is worth to note how simple is to perform clustering analysis using different algorithms in Python. The main steps of both data preprocessing and post-processing are the same if using K-Means or DBSCAN method, the only difference is the use of K-Means or DBSCAN at line 26 of both Listings 3 and 4. In this way, it is straightforward to analyze DEG data sets through several different clustering algorithms, allowing researchers to chose the algorithm that provide the best results in terms of predicted clusters, quality of clusters, contributing to detect genes groups affecting the underlying cellular functions to provide new actionable knowledge to provide new treatments as well as to discover new bio-markers.
