{{ self.title() }}

## {{ _('Description') }}

Lavender、Carnation、Jasmine、Peony现在在玩一款名叫“赛艇”的游戏。

这个游戏的规则是这样的：

1. 玩家自由组成两队，一个人当赛艇的艇长，另一个人当侦察兵；
2. 每次游戏开始时，双方均拥有由系统生成的某张地图，该地图以01矩阵的形式表示，`1`表示有障碍物，无法通行，`0`表示水域空旷，可以通行；
3. 第一回合，双方的赛艇艇长都要在地图上指定一个出发点，该出发点不能是障碍物，也就是只能为`0`；
4. 在每个回合中，艇长可以指挥自己的赛艇向上/下/左/右四个方向的某一方向的空旷水域移动一个单位的距离，也就是说只能移向四个方向上的某个`0`上（当然，不能移动出地图之外）；在该操作完成之后，**必须向对方说出自己在该回合移动的方向**；
5. 双方的侦察兵负责记录每一回合对方赛艇的移动方向，并负责推断此时对方赛艇可能的位置；如果某方的侦察兵推测出对方赛艇此时的精确位置，那么可以向其发射导弹，该侦察兵所在的一方胜利；

现在，Jasmine记录了一些对方赛艇的路径，她想确定一下此时对方所有可能的位置共有几种。由于她不是很擅长计算，所以这个任务就交给你了。

## {{ _('Input Format') }}

{{ self.input_file() }}

上面会根据具体的评测环境说明输入是文件还是标准输入等。

输入第一行包含一个正整数 $n$，保证 $n \le {{ tools.hn(prob.args['n']) }}$。←这是引用 `conf.json` 中的 `args` 的 `n` 项，然后用“好看”的格式输出。“好看”的格式如 `10^9`，`1,000,000,007`。

`prob.args['n']` 还可以写成 `prob['args']['n']`。引用 `args` 项、 `data` 项、`samples` 项和 `pre` 项现在可以简写成例如 `args['n']` 或 `args.n`。表格中也一样。

`tools` 可以简写成 `tl`，除 `hn` 外，还包括内建函数如 `tl.int`，`math` 中的对象或函数如 `tl.sin`，`datetime` 中的对象或函数如 `tl.time` 类，`num2chinese` 函数（可以把数字转化成中文）。

## {{ _('Output Format') }}

{{ self.output_file() }}

输出一个字符串 `Yes`。注意不要写成 `“Yes”（不包含引号）`。

下面是自动读入样例 `1.in/ans`（存储在 `down` 文件夹内） 然后渲染到题面中；如果只有一组样例，则去掉前两行，样例仍然保存成 `1.in/ans`。其中 `1` 可以是字符串。

{% set vars = {} -%}
{%- do vars.__setitem__('sample_id', 1) -%}
{{ self.sample_text() }}

{{ self.title_sample_description() }}

这是第一组数据的样例说明。

下面是只提示存在第二组样例，但不渲染到题面中。

{% do vars.__setitem__('sample_id', 2) -%}
{{ self.sample_file() }}

## {{ _('Subtasks') }}

不要使用markdown原生的表格，使用下列方式渲染一个表格，其中表格存放在试题目录的 `tables` 子目录下。

{{ tbl('data') }}

{{ tbl('table', width = [1, 6]) }}

表格的例子见 `oi_tools/sample/tables`。原理上用一个二维的 json 表格存储，`null` 表示和上一行合并，不支持横向合并。建议用 python 的格式写，如例子中的 `data.pyinc`，这样可以根据数据生成；跟数据无关的表格则可以像 `table.json` 那样存储。

## {{ _('Scoring') }}

这是评分方法，如果有必要的话。

## {{ _('Hint') }}

这里是一个非常温馨的提示。