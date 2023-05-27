#latex #obsidian #输入系统 #工作学习流 #方法 #markdown

I use latex for my math notes.
1. the shortcuts of `$ $`  which is the latex block in MD.
2. the shortxcuts of the component of frequent formulas.
3. the shortcuts of proof process.


# Use the Latex Suite Plugin in Obsidian

1. how to typewrite the `$$ $$`, use `dm + <tab>`
	
	in the snippets, it is implemented through
	`{trigger: "dm", replacement: "$$\n$0\n$$", options: "tAw"},`
	
	- `trigger` : The text that triggers this snippet.
		This snippet triggered by "dm"
	- `replacement` : The text to replace the `trigger` with.
	- `options`:
		- `t` : Text mode. Only run this snippet outside math
		- `A` : Auto. Expand this snippet as soon as the trigger is typed. If omitted, the Tab key must be pressed to expand the snippet
		- `w` : Word boundary. Only run this snippet when the trigger is preceded by (and followed by) a word delimiter, such as `.`, `,`, or `-`.  
	
	I need to move the cursor behind the second `$$`, so I change the `replacement ` into `$$\n$0\n$$\1`.
	`Tabstops`:
	- Insert tabstops for the cursor to jump to using `$X`, where X is a number starting from 0.
	- Pressing Tab will move the cursor to the next tabstop.
	- Tabstops with the same number, X, will all be selected at the same time.
	In this way, I can press `<tab>` to move the cursor to the end.
	And I change the `options` into `tw`.  

2. `{trigger: "int", replacement: "\\int $0 \\, d${1:x} $2", options: "mA"}`
	- Tabstops can have placeholders. Use the format `${X:text}`, where `text` is the text that will be selected by the cursor on moving to this tabstop.
	- `m` : Math mode. Only run this snippet inside math
	$$
\int x \, dx
	$$

|Trigger|Replacement|
|-|-|
|sr|^{2}|
|cb|^{3}|
|rd|^{ }|
|\_|\_{ }|
|sq|\sqrt{ }|
|x/y Tab|\frac{x}{y}|
|//|\frac{ }{ }|
|x1|x_{1}|
|xdot|\dot{x}|
|xhat|\hat{x}|
|xbar|\bar{x}|
|xvec|\vec{x}|
|ee|e^{ }|
|dint|`\\int_{${0:0}}^{${1:\\infty}} $2 \\, d${3:x} $4`|
|lim|\lim_{ n \to \infty } |

3. The bracket behind the lim, sum and frac will automatically add \\left and \\right.It makes the brackets nice-looking. 