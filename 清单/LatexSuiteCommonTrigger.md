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
|\\begin{} \\end{}|beg|
|\\begin{align}\n$0\n\\end{align}|align|

- CR automatically add `\\`

Customer:
- `   {trigger: "\{", replacement: "\\{ $0 \\} $1", options: "mA"},`
- `   {trigger: "c", replacement: "$0$1", options: "t"},`
- `{trigger: " ", replacement: "\enspace$0", options: "t"},`

