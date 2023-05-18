# Multivariate Statistical Data Analysis

## Contents
- [Multivariate Statistical Data Analysis](#multivariate-statistical-data-analysis)
  - [Contents](#contents)
  - [Problem 1](#problem-1)
    - [Solving Problem 1](#solving-problem-1)
      - [a. Income ve education değişkenlerinin histogramlarını çizin. Histogramlar çift modlu mu yoksa tek modlu mu(bimodal or unimodal)? Eğik(skewed) mi, değil mi? Histogramın şeklini yorumlayınız.](#a-income-ve-education-değişkenlerinin-histogramlarını-çizin-histogramlar-çift-modlu-mu-yoksa-tek-modlu-mubimodal-or-unimodal-eğikskewed-mi-değil-mi-histogramın-şeklini-yorumlayınız)
      - [b. Sales değişkeni için ortalama, medyan, varyans ve standart sapma ölçümlerini ve değişkenler arasındaki covaryansı hesaplayınız.](#b-sales-değişkeni-için-ortalama-medyan-varyans-ve-standart-sapma-ölçümlerini-ve-değişkenler-arasındaki-covaryansı-hesaplayınız)
      - [c. Ages değişkeni için 10, 25, 75, 90 niceliklerini hesaplayınız.](#c-ages-değişkeni-için-10-25-75-90-niceliklerini-hesaplayınız)
      - [d. Tüm değişkenleri özetlemek için betimleyici istatistik bilgilerini hesaplayınız.](#d-tüm-değişkenleri-özetlemek-için-betimleyici-istatistik-bilgilerini-hesaplayınız)
  
## Problem 1

Bu problemde kullanılacak olan veri seti, 400 farklı mağazada çocuk oto koltuğu satışlarını içeren simüle edilmiş bir veri setidir. Bu veri seti ışığında aşağıda belirtilen sorular cevaplandırılacaktır.

a.	Income ve education değişkenlerinin histogramlarını çizin. Histogramlar çift modlu mu yoksa tek modlu mu(bimodal or unimodal)? Eğik(skewed) mi, değil mi? Histogramın şeklini yorumlayınız.

b.	Sales değişkeni için ortalama, medyan, varyans ve standart sapma ölçümlerini ve değişkenler arasındaki covaryansı hesaplayınız.

c.	Ages değişkeni için 10, 25, 75, 90 niceliklerini hesaplayınız.

d.	Tüm değişkenleri özetlemek için betimleyici istatistik bilgilerini hesaplayınız.

### Solving Problem 1

#### a. Income ve education değişkenlerinin histogramlarını çizin. Histogramlar çift modlu mu yoksa tek modlu mu(bimodal or unimodal)? Eğik(skewed) mi, değil mi? Histogramın şeklini yorumlayınız.

*Income* : Community income level (in thousands of dollars)
*Education* : Education level at each location

TODO: Histogram grafikleri eklenecek ve istenen sorulara cevap aranacak.

#### b. Sales değişkeni için ortalama, medyan, varyans ve standart sapma ölçümlerini ve değişkenler arasındaki covaryansı hesaplayınız.

```py
def data_metrics(data, column):
    print("Mean: ",data[column].mean())
    print("Median: ",data[column].median())
    print("Variance: ",data[column].var())
    print("Standard Deviation: ",data[column].std())

data_metrics(data,'Sales')
```

```
Mean:  7.496325000000001
Median:  7.49
Variance:  7.975625808897243
Standard Deviation:  2.824115048806837
```

```
data.corr()
```

|  | Sales |	CompPrice |	Income | Advertising | Population | Price |	Age | Education |
|------|---------|--------|------------|--------------|------|-----|-----------|-------------|
|Sales|	1.000000|	0.064079|	0.151951|	0.269507|	0.050471|	-0.444951	|-0.231815	|-0.051955|
|CompPrice|	0.064079|	1.000000	|-0.080653	|-0.024199|	-0.094707|	0.584848	|-0.100239|	0.025197|
|Income|	0.151951|	-0.080653|	1.000000	|0.058995	|-0.007877	|-0.056698	|-0.004670	|-0.056855|
|Advertising	|0.269507|	-0.024199|	0.058995|	1.000000	|0.265652	|0.044537|	-0.004557|	-0.033594|
|Population|	0.050471	|-0.094707|	-0.007877|	0.265652	|1.000000|	-0.012144|	-0.042663|	-0.106378|
|Price	|-0.444951	|0.584848|	-0.056698	|0.044537|	-0.012144|	1.000000	|-0.102177|	0.011747|
|Age|	-0.231815	|-0.100239	|-0.004670	|-0.004557|	-0.042663	|-0.102177|	1.000000|	0.006488|
|Education|	-0.051955	|0.025197	|-0.056855|	-0.033594|	-0.106378	|0.011747|	0.006488|	1.000000|


#### c. Ages değişkeni için 10, 25, 75, 90 niceliklerini hesaplayınız.

TODO: 

#### d. Tüm değişkenleri özetlemek için betimleyici istatistik bilgilerini hesaplayınız.

```python
def check_df(dataframe, head=10):
    '''
    Provides general information about the loaded data.

    Parameters
    ----------
    dataframe: dataframe
    head: int

    Notes
    ----------
    The head value is set to a constant 5.
    '''
    print("##################### Shape #####################")
    print(dataframe.shape)
    print("##################### Types #####################")
    print(dataframe.dtypes)
    print("##################### Head #####################")
    print(dataframe.head(head))
    print("##################### Tail #####################")
    print(dataframe.tail(head))
    print("##################### NA #####################")
    print(dataframe.isnull().sum())
    print("##################### Quantiles #####################")
    print(dataframe.quantile([0, 0.05, 0.50, 0.95, 0.99, 1]).T)
    print("##################### Corr #####################")
    print(dataframe.corr())
    print("##################### Describe #####################")
    print(dataframe.describe())
```

```
##################### Shape #####################
(400, 11)
##################### Types #####################
Sales          float64
CompPrice        int64
Income           int64
Advertising      int64
Population       int64
Price            int64
ShelveLoc       object
Age              int64
Education        int64
Urban           object
US              object
dtype: object
##################### Head #####################
   Sales  CompPrice  Income  Advertising  Population  Price ShelveLoc  Age  \
0   9.50        138      73           11         276    120       Bad   42   
1  11.22        111      48           16         260     83      Good   65   
2  10.06        113      35           10         269     80    Medium   59   
3   7.40        117     100            4         466     97    Medium   55   
4   4.15        141      64            3         340    128       Bad   38   
5  10.81        124     113           13         501     72       Bad   78   
6   6.63        115     105            0          45    108    Medium   71   
7  11.85        136      81           15         425    120      Good   67   
8   6.54        132     110            0         108    124    Medium   76   
9   4.69        132     113            0         131    124    Medium   76   

   Education Urban   US  
0         17   Yes  Yes  
1         10   Yes  Yes  
2         12   Yes  Yes  
3         14   Yes  Yes  
4         13   Yes   No  
5         16    No  Yes  
6         15   Yes   No  
7         10   Yes  Yes  
8         10    No   No  
9         17    No  Yes  
##################### Tail #####################
     Sales  CompPrice  Income  Advertising  Population  Price ShelveLoc  Age  \
390   5.47        108      75            9          61    111    Medium   67   
391   6.10        153      63            0          49    124       Bad   56   
392   4.53        129      42           13         315    130       Bad   34   
393   5.57        109      51           10          26    120    Medium   30   
394   5.35        130      58           19         366    139       Bad   33   
395  12.57        138     108           17         203    128      Good   33   
396   6.14        139      23            3          37    120    Medium   55   
397   7.41        162      26           12         368    159    Medium   40   
398   5.94        100      79            7         284     95       Bad   50   
399   9.71        134      37            0          27    120      Good   49   

     Education Urban   US  
390         12   Yes  Yes  
391         16   Yes   No  
392         13   Yes  Yes  
393         17    No  Yes  
394         16   Yes  Yes  
395         14   Yes  Yes  
396         11    No  Yes  
397         18   Yes  Yes  
398         12   Yes  Yes  
399         16   Yes  Yes  
##################### NA #####################
Sales          0
CompPrice      0
Income         0
Advertising    0
Population     0
Price          0
ShelveLoc      0
Age            0
Education      0
Urban          0
US             0
dtype: int64
##################### Quantiles #####################
             0.00    0.05    0.50      0.95      0.99    1.00
Sales         0.0   3.149    7.49   12.4425   13.9146   16.27
CompPrice    77.0  98.000  125.00  150.0000  159.0200  175.00
Income       21.0  26.000   69.00  115.0000  119.0100  120.00
Advertising   0.0   0.000    5.00   19.0000   23.0100   29.00
Population   10.0  29.000  272.00  493.1500  504.0300  509.00
Price        24.0  77.000  117.00  155.0500  166.0500  191.00
Age          25.0  27.000   54.50   79.0000   80.0000   80.00
Education    10.0  10.000   14.00   18.0000   18.0000   18.00
##################### Corr #####################
                Sales  CompPrice    Income  Advertising  Population     Price  \
Sales        1.000000   0.064079  0.151951     0.269507    0.050471 -0.444951   
CompPrice    0.064079   1.000000 -0.080653    -0.024199   -0.094707  0.584848   
Income       0.151951  -0.080653  1.000000     0.058995   -0.007877 -0.056698   
Advertising  0.269507  -0.024199  0.058995     1.000000    0.265652  0.044537   
Population   0.050471  -0.094707 -0.007877     0.265652    1.000000 -0.012144   
Price       -0.444951   0.584848 -0.056698     0.044537   -0.012144  1.000000   
Age         -0.231815  -0.100239 -0.004670    -0.004557   -0.042663 -0.102177   
Education   -0.051955   0.025197 -0.056855    -0.033594   -0.106378  0.011747   

                  Age  Education  
Sales       -0.231815  -0.051955  
CompPrice   -0.100239   0.025197  
Income      -0.004670  -0.056855  
Advertising -0.004557  -0.033594  
Population  -0.042663  -0.106378  
Price       -0.102177   0.011747  
Age          1.000000   0.006488  
Education    0.006488   1.000000  
##################### Describe #####################
            Sales   CompPrice      Income  Advertising  Population  \
count  400.000000  400.000000  400.000000   400.000000  400.000000   
mean     7.496325  124.975000   68.657500     6.635000  264.840000   
std      2.824115   15.334512   27.986037     6.650364  147.376436   
min      0.000000   77.000000   21.000000     0.000000   10.000000   
25%      5.390000  115.000000   42.750000     0.000000  139.000000   
50%      7.490000  125.000000   69.000000     5.000000  272.000000   
75%      9.320000  135.000000   91.000000    12.000000  398.500000   
max     16.270000  175.000000  120.000000    29.000000  509.000000   

            Price         Age   Education  
count  400.000000  400.000000  400.000000  
mean   115.795000   53.322500   13.900000  
std     23.676664   16.200297    2.620528  
min     24.000000   25.000000   10.000000  
25%    100.000000   39.750000   12.000000  
50%    117.000000   54.500000   14.000000  
75%    131.000000   66.000000   16.000000  
max    191.000000   80.000000   18.000000  
```
