#LARC #ANPL 
1. find the near red pixels clustering.In a clustering, the distance between each red pixel and the clustering do not exceed two pixels.
2. complete the near red pixels clustering to the rectangle as small as possible.

## RobotA模板

-   指明矩阵的输入输出的维数，比如6x3
-   积累常用的描述函数模板
-   如果需要使用任意维数的概念，也请限定维数的范围，比如不小于20维

```python
import numpy as np
black, blue, red, green, yellow, grey, pink, orange, teal, maroon = range(10)
def main(input_grid: np.ndarray) -> np.ndarray:
	clustering = `find the near red pixels clustering.In a clustering, the distance between each red pixel and the clustering do not exceed two pixels.`(input_grid)
	output_grid = `fill the vacancies of each red pixels clustering to the rectangle with yellow as small as possible.`(clustering, output_grid)
	return output_grid
```

## RobotB模板

You are a skilled Python programmer. Your task is to write Python code to transform the input grid into the output grid.  
In the input grid, you should see a 18x18 grid.  
To make the output 18x18 grid,  
find the near red pixels clustering.In a clustering, the distance between each red pixel and the clustering do not exceed two pixels.
Then fill the vacancies of each red pixels clustering to the rectangle with yellow as small as possible.You need complete all the rectangle in output_grid.
Do not replace the red in the clustering with yellow.
Return your Python code in Markdown format.  
This is the previous section of the code:

```
import numpy as np
black, blue, red, green, yellow, grey, pink, orange, teal, maroon = range(10)
def main(input_grid: np.ndarray) -> np.ndarray:
```
.


Now, please remain all your code and add a step. 
Replace the black pixels in the current output_grid.
Use black or maroon pixels in the same place in the input_grid.