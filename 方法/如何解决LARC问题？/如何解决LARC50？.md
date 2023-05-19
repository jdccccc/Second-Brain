#LARC #ANPL 
1. In the input_grid Identify the colorful triangles against the black background.Get three vertex for the triangles.
2. In the triangles on the input_grid, find the key vertex.Key vertex do not on the heterochromatic side.
3. Key line is in the direction of the key vertex pointing in the triangles.Key line is between the edge and key vertex.Paint the key line with the color of key Vertex.

## RobotA模板

-   指明矩阵的输入输出的维数，比如6x3
-   积累常用的描述函数模板

```python
import numpy as np
black, blue, red, green, yellow, grey, pink, orange, teal, maroon = range(10)
def main(input_grid: np.ndarray) -> np.ndarray:
	triangles = `In the input_grid Identify the colorful triangles against the black background.Get the triangles.`(input_grid)
	key_vertex = `In the triangles on the input_grid, find the key vertex not on the heterochromatic side.`(triangles, input_grid)
	output_grid = `Key line is in the direction of the key vertex pointing in the triangles.Key line is birthed from the edge and key vertex.Paint the key line with the color of key Vertex.`(triangles, key_vertex, input_grid)
	return output_grid
```

## RobotB模板

You are a skilled Python programmer. Your task is to write Python code to transform the input grid into the output grid.  
In the input grid, you should see a grid with black pixels back ground.  
To make the output grid,
1. In the input_grid Identify the colorful triangle against the black background.Get three vertex for the triangle.
2. In the triangle, find the key_vertex.Key vertex do not on the heterochromatic side of the triangle.
3. Key_line is in the direction of the key_vertex pointing in the triangle.Key_line is between the edge of input_grid and key_vertex.Paint the key_line with the color of key_vertex.
Return your Python code in Markdown format.  
This is the previous section of the code:
```
import numpy as np
black, blue, red, green, yellow, grey, pink, orange, teal, maroon = range(10)
def main(input_grid: np.ndarray) -> np.ndarray:
```
.

There are a group IO for test for you:
```
input_grid = np.array([[0,0,0,0,0,0,0,0,0,0,0],[0,0,0,0,0,0,0,0,0,0,0],[0,0,0,0,0,0,0,0,0,0,0],[0,0,0,0,0,0,0,0,0,0,0],[0,0,0,0,0,0,0,0,0,0,0],[0,0,0,0,0,0,0,0,0,0,0],[0,0,0,0,0,0,0,0,0,0,0],[0,0,0,0,0,0,0,0,0,0,0],[0,0,0,0,0,0,0,0,0,0,0],[0,0,0,0,0,0,0,0,0,0,0],[0,0,0,0,0,0,0,0,0,0,0],[0,0,0,0,0,0,0,0,0,0,0],[0,0,0,4,0,0,0,0,0,0,0],[0,0,4,4,4,0,0,0,0,0,0],[0,4,4,8,4,4,0,0,0,0,0],[0,0,0,0,0,0,0,0,0,0,0]])
output_grid = np.array([[0,0,0,8,0,0,0,0,0,0,0],[0,0,0,8,0,0,0,0,0,0,0],[0,0,0,8,0,0,0,0,0,0,0],[0,0,0,8,0,0,0,0,0,0,0],[0,0,0,8,0,0,0,0,0,0,0],[0,0,0,8,0,0,0,0,0,0,0],[0,0,0,8,0,0,0,0,0,0,0],[0,0,0,8,0,0,0,0,0,0,0],[0,0,0,8,0,0,0,0,0,0,0],[0,0,0,8,0,0,0,0,0,0,0],[0,0,0,8,0,0,0,0,0,0,0],[0,0,0,8,0,0,0,0,0,0,0],[0,0,0,4,0,0,0,0,0,0,0],[0,0,4,4,4,0,0,0,0,0,0],[0,4,4,8,4,4,0,0,0,0,0],[0,0,0,0,0,0,0,0,0,0,0]])
``` 