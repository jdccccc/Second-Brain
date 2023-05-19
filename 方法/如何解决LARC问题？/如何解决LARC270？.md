#LARC #ANPL 
1. 找到所有的3\*3的非黑色正方形
2. 找到包含蓝色最多的正方形色块并输出
ANPL结果：成功
# robotB
You are a skilled Python programmer. Your task is to write Python code to transform the input grid into the output grid. In the input grid, you should see you should see a 9x9 grid with black, blue and teal pixels. To make the output 3x3 grid, you should use abstraction and reasoning abilities, and do as two step below.
1. find all the 3x3 non-black squares.A square is a rectangle of the same width and length , not a pixel.
2. find the 3x3 square in the step 1 containing the most blue. 
Return your Python code in Markdown format.
This is the previous section of the code:
```
import numpy as np
black, blue, red, green, yellow, grey, pink, orange, teal, maroon = range(10)
def main(input_grid: np.ndarray) -> np.ndarray:

```
.
This is the IOs for test:
input1 is `input_grid = np.array([[0,0,1,1,8,0,0,0,0],[0,0,8,8,1,0,8,1,1],[0,0,1,1,8,0,1,1,1],[0,0,0,0,0,0,8,1,8],[8,8,8,0,0,0,0,0,0],[8,8,1,0,8,1,8,0,0],[1,8,8,0,1,8,8,0,0],[0,0,0,0,8,8,1,0,0],[0,0,0,0,0,0,0,0,0]])`.
output1 is `output_grid = np.array([[8,1,1],[1,1,1],[8,1,8]])`.
input2 is `input_grid = np.array([[0,0,0,0,8,8,8,0,0],[8,8,8,0,8,8,8,0,0],[8,8,8,0,1,8,8,0,0],[8,8,8,0,0,0,0,0,0],[0,0,0,0,0,0,8,1,8],[8,1,8,0,0,0,1,1,8],[8,8,1,0,0,0,1,8,1],[1,8,8,0,0,0,0,0,0],[0,0,0,0,0,0,0,0,0]])`.
output2 is `output_grid = np.array([[8,1,8],[1,1,8],[1,8,1]]).
input3 is `input_grid = np.array([[8,8,8,0,0,0,0,0,0],[1,8,8,0,8,1,8,0,0],[8,8,8,0,1,1,8,0,0],[0,0,0,0,8,8,8,0,0],[0,8,8,1,0,0,0,0,0],[0,8,8,8,0,0,8,1,8],[0,8,1,8,0,0,1,8,1],[0,0,0,0,0,0,1,8,1],[0,0,0,0,0,0,0,0,0]])`.
output3 is `output_grid = np.array([[8,1,8],[1,8,1],[1,8,1]])`.
input4 is `input_grid = np.array([[0,8,8,1,0,0,0,0,0],[0,8,1,8,0,8,1,8,0],[0,8,8,8,0,1,8,8,0],[0,0,0,0,0,8,8,1,0],[0,0,8,1,8,0,0,0,0],[0,0,1,1,8,0,0,0,0],[0,0,8,8,1,0,8,8,8],[0,0,0,0,0,0,8,8,8],[0,0,0,0,0,0,1,8,8]])`.
output4 is `output_grid = np.array([[8,1,8],[1,1,8],[8,8,1]])`.

# robotA

```python
import numpy as np
black, blue, red, green, yellow, grey, pink, orange, teal, maroon = range(10)
def main(input_grid: np.ndarray) -> np.ndarray:
	non_black_squares = `find all the 3x3 non-black squares, return 3d array of squares`(input_grid)
	output_grid = `find the 3x3 square containing the most blue.`(non_black_squares)
	return output_grid

```