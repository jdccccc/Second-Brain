#ANPL  #LARC 
# RobotA模板

- 指明矩阵的输入输出的维数，比如6x3
- 积累常用的描述函数模板
```python
import numpy as np
black, blue, red, green, yellow, grey, pink, orange, teal, maroon = range(10)
def main(input_grid: np.ndarray) -> np.ndarray:
	output_grid = `Split each pixel of 3x3 input_grid into 3x3 grid. Make 9x9 output_grid`(input_grid)
	return output_grid
```
# RobotB模板
You are a skilled Python programmer. Your task is to write Python code to transform the input grid into the output grid. 
In the input grid, you should see a 3x3 grid with pixels. 
To make the output 9x9 grid,Split each pixel of 3x3 input_grid into 3x3 grid.
Return your Python code in Markdown format.
This is the previous section of the code:
```
import numpy as np
black, blue, red, green, yellow, grey, pink, orange, teal, maroon = range(10)
def main(input_grid: np.ndarray) -> np.ndarray:
```
.
This is the test IOs:
input1 is `input_grid = np.`.
output1 is `output_grid = np.`.
input2 is `input_grid = np.`.
output2 is `output_grid = np.`.
input3 is `input_grid = np.`.
output3 is `output_grid = np.`.