#LARC #ANPL 

## RobotA模板

-   指明矩阵的输入输出的维数，比如6x3
-   积累常用的描述函数模板

```python
import numpy as np
black, blue, red, green, yellow, grey, pink, orange, teal, maroon = range(10)
def main(input_grid: np.ndarray) -> np.ndarray:
	black_rectangles = `find some black rectangles as large as possible.The black area is arrounded by the colored pixels.`(input_grid)
	output_grid = `Fill the black_rectangles with green pixels.The edge of black area remain black.`(input_grid, black_rectangles)
	return output_grid
```

## RobotB模板

You are a skilled Python programmer. Your task is to write Python code to transform the input grid into the output grid.  
In the input grid, you should see a 30x30grid.  
To make the output 30x30 grid,you should fill the black area arrouned by the non-black area.Fill the black area with green pixels.
You can use rectangle to describe the black empty area.
Return your Python code in Markdown format.  
This is the previous section of the code:

```
import numpy as np
black, blue, red, green, yellow, grey, pink, orange, teal, maroon = range(10)
def main(input_grid: np.ndarray) -> np.ndarray:
```

.