#LARC #ANPL 

## RobotA模板

-   指明矩阵的输入输出的维数，比如6x3
-   积累常用的描述函数模板

```python
import numpy as np
black, blue, red, green, yellow, grey, pink, orange, teal, maroon = range(10)
def main(input_grid: np.ndarray) -> np.ndarray:
	non_black_rectangles = `Get rectangles with blue and red pixels from input_grid.The side size doesnot exceed 20 pixels.`(input_grid)
	output_grid = `find the 2d rectangle with the most red pixels.Output 2d grid.`(non_black_rectangles)
	return output_grid
```

## RobotB模板

You are a skilled Python programmer. Your task is to write Python code to transform the input grid into the output grid.  
In the input grid, you should see a 20x20 grid with black, blue and red pixels.  
To make the output grid,  
You should  get rectangles with blue and red pixels from input_grid.The side size of non-black rectangles doesnot exceed 20 pixels.And then find the 2d rectangle with the most red pixels.Output 2d grid.
Return your Python code in Markdown format.  
This is the previous section of the code:

```
import numpy as np
black, blue, red, green, yellow, grey, pink, orange, teal, maroon = range(10)
def main(input_grid: np.ndarray) -> np.ndarray:
```
.