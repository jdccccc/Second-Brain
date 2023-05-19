#ANPL #LARC 
1. output a black grid.Output size is same as input.
2. find the most color in the input_grid.
3. make a 3d output to store each color 2d pattern in input_grid.
4. complete the patterns to up and down and left and right symmetry.Out put these symmetrical patterns in 3d.
5. Except the_most_color, embed the small patterns into larger pattern in output_grid.
6. In the output_grid, replace the black with the_most_color.
## RobotA模板

-   指明矩阵的输入输出的维数，比如6x3
-   积累常用的描述函数模板

```python
import numpy as np
black, blue, red, green, yellow, grey, pink, orange, teal, maroon = range(10)
def main(input_grid: np.ndarray) -> np.ndarray:
	output_grid = `output a black grid.Output size is same as input.`(input_grid)
	the_most_color = `find the most color in the input_grid.`(input_grid)
	patterns = ` make a 3d 10-color output to store each color 2d pattern in input_grid.`(input_grid)
	symmetrical_patterns = `complete the patterns to up and down and left and right symmetry.Out put these symmetrical patterns in 3d.`(patterns)
	output_grid = `Except the_most_color, embed the small patterns into larger pattern.Output 2d grid.`(output_grid, symmetrical_patterns)
	output_grid = `In the input, replace the black with the_most_color.`(output_grid, the_most_color)
	return output_grid
```

## RobotB模板

You are a skilled Python programmer. Your task is to write Python code to transform the input grid into the output grid.  
In the input grid, you should see a colorful grid with blue and pink pixels.  
To make the output colorful grid,  
1. find the most color in the input_grid.
2. make a 3d temporary grid to store each color 2d pattern in input_grid.
3. complete the 2d patterns in temporary gird to up and down and left and right symmetry.
4. output_grid is size as the largest symmetrical pattern. Fill output_grid with black.
5. Except the_most_color, embed the small  symmetrical patterns into larger symmetrical pattern in output_grid.
6. In the output_grid, replace the black with the_most_color.
Return your Python code in Markdown format.  
This is the previous section of the code:

```
import numpy as np
black, blue, red, green, yellow, grey, pink, orange, teal, maroon = range(10)
def main(input_grid: np.ndarray) -> np.ndarray:
```
.
I will give you a group IO for test.
`input_grid = np.array([[1,1,1,1,1,1,1,1,1,1,1,1,1,4,1,1,1,1,1],[1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1],[1,1,1,1,1,1,1,1,1,1,1,1,1,4,1,1,1,1,1],[1,1,1,1,1,1,1,8,8,8,1,1,1,4,1,1,1,1,1],[1,1,1,1,1,1,1,8,1,8,1,1,1,4,1,1,1,1,1],[1,1,1,1,1,1,1,8,8,8,1,1,1,4,1,1,1,1,1],[1,1,1,1,1,1,1,1,1,1,1,1,1,4,4,4,4,4,1],[1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1],[1,1,1,3,3,1,3,3,1,1,1,1,1,1,1,1,1,1,1],[1,1,1,3,1,1,1,3,1,1,1,1,1,1,1,1,1,1,1],[1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1],[1,1,1,3,1,1,1,3,1,1,1,1,1,1,1,1,1,1,1],[1,1,1,3,3,1,3,3,1,1,1,1,1,1,1,1,1,1,1],[1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1],[1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1],[1,1,1,1,2,2,2,1,1,1,2,2,2,1,6,6,1,1,1],[1,1,1,1,2,1,1,1,1,1,1,1,2,1,6,1,1,1,1],[1,1,1,1,2,1,1,1,1,1,1,1,2,1,1,1,1,1,1],[1,1,1,1,1,1,1,1,1,1,1,1,1,1,6,1,1,1,1]])`

`output_grid = np.array([[4,4,4,4,4,1,4,4,4,4,4],[4,2,2,2,1,1,1,2,2,2,4],[4,2,6,6,1,1,1,6,6,2,4],[4,2,6,3,3,1,3,3,6,2,4],[4,1,1,3,8,8,8,3,1,1,4],[1,1,1,1,8,1,8,1,1,1,1],[4,1,1,3,8,8,8,3,1,1,4],[4,2,6,3,3,1,3,3,6,2,4],[4,2,6,6,1,1,1,6,6,2,4],[4,2,2,2,1,1,1,2,2,2,4],[4,4,4,4,4,1,4,4,4,4,4]])`