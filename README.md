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
>使用python生成密度图  

5.使用各种小部件  
--  
```  
描述jupyter中的各种Widgets  
```
6.jupyter仪表盘  
--  
```  
如何使用jupyter仪表盘以及布局扩展  
```  
7.共享代码  
--  
```  
如何将你的代码共享给他人  
```  
8.与大数据交互  
--  
```  
介绍jupyter访问大数据的方法  
```  
![image](https://github.com/yftian/jupyter/blob/master/image/P8M4~TUG%605%24%25S2C6S%24T%257XN.png)
