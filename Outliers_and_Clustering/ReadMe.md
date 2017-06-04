Outliers Detection and Clustering are related to each other, and in a world without groud truth data, it requires more efforts to find effective and efficient methods.


*********************************************************************************

LEARNING NOTES

* As [my data mining bible reading notes][1] recorded (Chapter 11, high demensional clustering), even it's biclustering (such as <b>MaPle</b>), which searches subsapace in both objects and features, can be time consuming because it enumerates all the subspaces. Here is another implemented example of [HiCS, LOF with description][2], [HiCS code only][3], according to the author, HiCS can solve the subspaces search in an more effective way. I think so, since MaPle is publised in 2008, HiCS is published in 2012. So deserve to try
* People have also implemneted another linear method to detect outliers, [LOF][4], it is densitiy based, and calculates nearest neighbours. Note that, when there is high dimensional features, PCA, LOF can be less effective. This is the so-called The Curse of Dimensionality, when there are more dimensions, proximity-based measures can be time consuming, and outliers, random noise could make the calculation results lose meaning


[1]:https://github.com/hanhanwu/readings/blob/master/ReadingNotes_DMBible.md
[2]:http://shahramabyari.com/2016/01/19/detecting-outliers-in-high-dimensional-data-sets/
[3]:https://github.com/shahramabyari/HiCS/blob/master/hcis.py
[4]:http://shahramabyari.com/2015/12/30/my-first-attempt-with-local-outlier-factorlof-identifying-density-based-local-outliers/