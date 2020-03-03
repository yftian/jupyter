1.安装和设置  
--
```  
在不同的环境中安装jupyterb  
```  
2.添加Engine  
--  

```  
如何添加Engine到jupyter,以便使用不同的语言进行开发  
```  
>添加R Engine  
```  
conda install r-essentials  #更新 conda update r-essentials  
```  
```  
将R安装为Engine选项，就可以从NEW菜单下拉列表中创建一个新的R笔记笨  
```  
>添加Julia Engine  
```  
第一步，下载并安装对应版本的Julia,  https://julialang.org/downloads  
第二步，启动Julia环境，运行Pkg.add("IJulia")  
```  
>添加JavaScripy Engine  
```  
首先，安装Node.js  
使用npm工具安装 npm install -g ijavascript  
将JavaScripy添加到Jupyter中 ijsinstall  
```  
3.访问和检索数据  
--  
```
访问和检索jupyter中不同格式的文件中的数据  
```  
>访问.csv文件(使用R访问CSV文件)  
```  
heating <- read.csv(file="https://raw.github.com/vincentarelbundock/Rdatasets/master/csv/Ecdat/Heating.csv", header=TRUE, sep=",")  
head(heating)  
``` 
>访问Json文件(使用js访问Json文件)  
```  
//load the JSON dataset
//http://www.carqueryapi.com/api/0.3/?callback=?&cmd=getModels&make=ford
var fords = require('/Users/dtoomey/fords.json');
//display how many Ford models are in our data set
console.log("There are " + fords.Models.length + " Ford models in the data set");
//loop over the set
var index = 1
for(var i=0; i<fords.Models.length; i++) {
    //get this model
    var model = fords.Models[i];
   //pull it's name
    var name = model.model_name;
    //if the model name does not have numerics in it
    if(! name.match(/[0-9]/i)) {
        //display the model name
        console.log("Model " + index + " is a " + name);
        index++;
    }
   //only display the first 5
   if (index>5) break;
}
```  
>访问flat文件(使用Python访问flat文件)  
```  
import pandas as pd

column_names = ["row","id","year","stint","team","g","ab"]
column_widths = [3,9,4,1,3,2,3]
df = pd.read_fwf("c:/Users/Dan/baseball.txt",
 header=None,
 names=column_names,
 widths=column_widths)
df
```  
4.可视化分析  
--  
```  
包括Python、R、Julia  
```
>使用python生成折线图  
```  
import pandas
import matplotlib
%matplotlib inline

baby_name = ['Alice','Charles','Diane','Edward']
number_births = [96, 155, 66, 272]
dataset = list(zip(baby_name,number_births))
df = pandas.DataFrame(data = dataset, columns=['Name', 'Number'])
df['Number'].plot()
```  
![line graph](https://github.com/yftian/jupyter/blob/master/image/graph%20.png)
>使用python生成直方图  
```  
import pylab
import random

random.seed(113)

samples = 1000
dice = []
for i in range(samples):
 total = random.randint(1,6) + random.randint(1,6)
 dice.append(total)

pylab.hist(dice, bins= pylab.arange(1.5,12.6,1.0))
pylab.show()
```  
![histogram ](https://github.com/yftian/jupyter/blob/master/image/histogram%20.png)
>使用python生成3D图  
```  
%matplotlib inline

# import tools we are using
import pandas as pd
import numpy as np
from mpl_toolkits.mplot3d import Axes3D
import matplotlib.pyplot as plt

# read in the car ‘table’ – not a csv, so we need
# to add in the column names
column_names = ['mpg', 'cylinders', 'displacement', 'horsepower', 'weight', 'acceleration', 'year', 'origin', 'name']
df = pd.read_table('http://archive.ics.uci.edu/ml/machine-learning-databases/auto-mpg/auto-mpg.data', sep=r"\s+", index_col=0, header=None, names = column_names)
print(df.head())

#start out plotting (uses a subplot as that can be 3d)
fig = plt.figure()
ax = fig.add_subplot(111, projection='3d')# pull out the 3 columns that we want
xs = []
ys = []
zs = []
for index, row in df.iterrows():
 xs.append(row['weight'])
 ys.append(index) #read_table uses first column as index
 zs.append(row['cylinders'])# based on our dataset the extents of the axes
plt.xlim(min(xs), max(xs))
plt.ylim(min(ys), max(ys))
ax.set_zlim(min(zs), max(zs))

# standard scatter diagram (except it is 3d)
ax.scatter(xs, ys, zs)

ax.set_xlabel('Weight')
ax.set_ylabel('MPG')
ax.set_zlabel('Cylinders')

plt.show()  
```  
![3D](https://github.com/yftian/jupyter/blob/master/image/3d-02.png)  
![3D](https://github.com/yftian/jupyter/blob/master/image/3d-01.png)  
5.使用各种小部件  
--  
```  
什么是小部件（widgets）  
  显示在jupyter笔记本中，用户可以控制与输入控件交互，并能调整笔记本的显示，通过使用小部件，用户可以使用输入设备或者直接调整控件。
```  

```  
描述jupyter中的各种Widgets  
```
6.jupyter仪表盘  
--  
```  
jupyter dashboard  
  Jupyter dashboard是Jupyter的一个扩展，允许笔记本开发人员在特定布局中创建笔记本的视图，而无需使用底层笔记本编码。
  Grid layout（网格布局）  
    屏幕在网格中布局，允许在屏幕内垂直和水平排列元素  
  Report layout（报表布局）  
    接近标准笔记本，元素沿页面垂直布局
```  
7.共享代码  
--  
>使用Jupyter Notebook  
>>Jupyter内置将其公开的web服务器功能，假设服务器是其他用户可以访问的，通过配置JUpyter在该服务器上运行，  
>>为Jupyter安装生成配置文件的命令是：jupyter notebook --generate-config  
>>此命令生成jupyter_notebook_config.py文件，位于主用户目录。  
```
配置如下：  
c.NotebookApp.certfile = u'/path/to/your/cert/cert.pem'
c.NotebookApp.keyfile = u'/ path/to/your/cert/key.key'
c.NotebookApp.ip = '*'
c.NotebookApp.password = u'hashed-password'
c.NotebookApp.open_browser = False
c.NotebookApp.port = 8888
```
>通过web Server(添加到现有的web服务器中)  
```  
配置文件如下：  
c.NotebookApp.tornado_settings = {
 'headers': {
 'Content-Security-Policy': "frame-ancestors 'https://yourwebsite.com' 'self' "
 }
}  
替换yourwebsite.com，完成后即可通过网页访问jupyter.
```  
>通过公开的服务器  
>>目前允许公开分享的服务器GitHub（开源的代码管理系统）  
8.与大数据交互  
--  
>从大文本数据中获取字数
```  
import pyspark

if not 'sc' in globals():
    sc = pyspark.SparkContext()

text_file = sc.textFile("B09656_09_word_count.ipynb")
counts = text_file.flatMap(lambda line: line.split(" ")) \
    .map(lambda word: (word, 1)) \
    .reduceByKey(lambda a, b: a + b)

for x in counts.collect():
    print(x)  
```  
>从大文本数据排序字数  
```  
import pyspark

if not 'sc' in globals():
 sc = pyspark.SparkContext()
 
text_file = sc.textFile("B09656_09_word_count.ipynb")
sorted_counts = text_file.flatMap(lambda line: line.split(" ")) \
 .map(lambda word: (word, 1)) \
 .reduceByKey(lambda a, b: a + b) \
 .sortByKey()

for x in sorted_counts.collect():
 print(x)  
```  
>检查大文本日志文件访问  
```  
import pyspark

if not 'sc' in globals():
    sc = pyspark.SparkContext()

textFile = sc.textFile("access_log")
print(textFile.count(),"access records")

gets = textFile.filter(lambda line: "GET" in line)
print(gets.count(),"GETs")

posts = textFile.filter(lambda line: "POST" in line)
print(posts.count(),"POSTs")

other = textFile.subtract(gets).subtract(posts)
print(other.count(),"Other")
for x in other.collect():
    print(x)  
```  
>用并行运算计算素数  
```  
import pyspark
if not 'sc' in globals():
    sc = pyspark.SparkContext()

#check if a number is prime
def isprime(n):
    # must be positive
    n = abs(int(n))
 
    # 2 or more
    if n < 2:
        return False
 
    # 2 is the only even prime number
    if n == 2:
         return True
    if not n & 1:
        return False
 
    # range starts with 3 and only needs to go up the square root of n
    # for all odd numbers
    for x in range(3, int(n**0.5)+1, 2):
        if n % x == 0:
            return False
    return True  
    nums = sc.parallelize(range(1000000))

# Compute the number of primes in the RDD
print(nums.filter(isprime).count())
```  
