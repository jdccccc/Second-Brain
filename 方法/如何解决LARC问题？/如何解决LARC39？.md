#LARC #ANPL 
1. Find two lines in grid.The lines in the edge of grid.The lines isnt paint with black and green.Output the two_edge_lines.
2. According to the two_lines, split the input_grid to two section.These two section has same size.Two edge line do not in the same section.
3. Paint the green pixels.In each section, paint the green pixels with the color of corresponding edge_line.

## RobotA模板

-   指明矩阵的输入输出的维数，比如6x3
-   积累常用的描述函数模板

```python
import numpy as np
black, blue, red, green, yellow, grey, pink, orange, teal, maroon = range(10)
def main(input_grid: np.ndarray) -> np.ndarray:
	two_edge_lines = `Find two lines in grid.The lines in the edge of grid.The lines isnt paint with black and green.Output the two_edge_lines.`(input_grid)
	split_scale = `According to the two_lines, split the input_grid to two section.These two section has same size.Two edge line do not in the same section.`(two_edge_lines)
	output_grid = `Paint the green pixels.In each section, paint the green pixels with the color of corresponding edge_line.`(two_lines, mid_line, input_grid)
	return output_grid
```

## RobotB模板

You are a skilled Python programmer. Your task is to write Python code to transform the input grid into the output grid.  
In the input grid, you should see a 10x10 grid with blue and pink pixels.  
To make the output 10x10 grid,  
1. Find two lines in grid.The lines in the edge of grid.The lines isnt paint with black and green.Get the two_edge_lines.
2. According to the two_edge_lines, split the input_grid to two section.These two section has same size.Two edge line do not in the same section.
3. Paint the green pixels.In each section, paint the green pixels with the color of corresponding edge_line.
Return your Python code in Markdown format.  
This is the previous section of the code:
```
import numpy as np
black, blue, red, green, yellow, grey, pink, orange, teal, maroon = range(10)
def main(input_grid: np.ndarray) -> np.ndarray:
```
.
There is IO for test:
input is `input_grid = np.array([[5,3,0,0,0,0,0,0,0,4],[5,0,0,0,0,3,0,0,3,4],[5,0,0,0,0,0,0,0,0,4],[5,0,0,3,0,0,0,0,0,4],[5,0,0,0,0,0,3,0,0,4],[5,0,0,3,0,0,0,0,0,4],[5,0,0,0,0,0,0,0,0,4],[5,0,0,0,3,0,0,0,0,4],[5,0,3,0,0,0,3,0,0,4],[5,0,0,0,0,0,0,0,0,4]])`
output is `output_grid = np.array([[5,5,0,0,0,0,0,0,0,4],[5,0,0,0,0,4,0,0,4,4],[5,0,0,0,0,0,0,0,0,4],[5,0,0,5,0,0,0,0,0,4],[5,0,0,0,0,0,4,0,0,4],[5,0,0,5,0,0,0,0,0,4],[5,0,0,0,0,0,0,0,0,4],[5,0,0,0,5,0,0,0,0,4],[5,0,5,0,0,0,4,0,0,4],[5,0,0,0,0,0,0,0,0,4]])`