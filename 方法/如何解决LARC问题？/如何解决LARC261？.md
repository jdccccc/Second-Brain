#LARC #ANPL 

# RobotB
You are a skilled Python programmer. Your task is to write Python code to transform the input grid into the output grid.In the for loop body, you need use input_grid[i]to visit a row of the input_grid.In the input grid, you should see you should see a 3x3 grid with black and grey pixels. To make the output 3x3 grid with green, yellow and red pixels, you should use abstraction and reasoning abilities. Return your Python code in Markdown format.
You can refer to the following method to complete this task.
Each row of input_grid determines each row of output_grid. 
[0,0,5]determains[3,3,3];[0,5,0]determains[4,4,4];[5,0,0]determains[2,2,2].
This is the previous section of the code:
```
import numpy as np
black, blue, red, green, yellow, grey, pink, orange, teal, maroon = range(10)
def main(input_grid: np.ndarray) -> np.ndarray:

```
.
I will give you some IOs for test.
test1:
input1 is `input_grid = np.array([0,0,5],[0,5,0],[5,0,0])`.
output1 is `output_grid = np.array([3,3,3],[4,4,4],[2,2,2])`.
test2:
input2 is `input_grid = np.array([0,0,5],[0,0,5],[0,0,5])`.
output2 is `output_grid = np.array([3,3,3],[3,3,3],[3,3,3])`.
test3:
input3 is `input_grid = np.array([5,0,0],[0,5,0],[5,0,0])`.
output3 is `output_grid = np.array([2,2,2],[4,4,4],[2,2,2])`.
test4:
input4 is `input_grid = np.array([0,5,0],[0,0,5],[0,5,0])`.
output4 is `output_grid = np.array([4,4,4],[3,3,3],[4,4,4])`.

# RobotA
```python
import numpy as np
black, blue, red, green, yellow, grey, pink, orange, teal, maroon = range(10)

def main(input_grid: np.ndarray) -> np.ndarray:
	output_grid = `change each input row to output row :row[0,0,5]changes to row[3,3,3],everything else remain unchanged.`(input_grid)
	output_grid = `change each input row to output row :row[0,5,0]changes to row[4,4,4],everything else remain unchanged.`(output_grid)
	output_grid = `change each input row to output row :row[5,0,0]changes to row[2,2,2],everything else remain unchanged.`(output_grid)
	return output_grid
```