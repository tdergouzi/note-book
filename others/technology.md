# Technology

Technology notes.



## Code License



### 许可证类型：

1. GNU通用公共许可证（GNU General Public License，GPL）：这是一种开源许可证，它允许用户自由地使用、修改和分发软件，但要求在任何衍生作品中都必须保持相同的许可证。
2. MIT许可证：这是一种灵活的许可证，它允许用户自由地使用、修改和分发软件，同时不需要保持相同的许可证。
3. BSD许可证：这是一种类似于MIT许可证的许可证，它允许用户自由地使用、修改和分发软件，同时也没有要求保持相同的许可证。
4. Apache许可证：这是一种开源许可证，它允许用户自由地使用、修改和分发软件，同时还有额外的专利授权条款。



### 许可证网站

1. GNU通用公共许可证（GPL）：https://www.gnu.org/licenses/gpl-3.0.en.html

2. MIT许可证：https://opensource.org/licenses/MIT

3. BSD许可证：https://opensource.org/licenses/BSD-3-Clause

4. Apache许可证：http://www.apache.org/licenses/LICENSE-2.0

   

### 如何选择许可证

1. 是否希望代码能够被其他人修改和分发？

如果您希望其他人可以继续改进和开发您的代码，那么应该选择允许修改和分发的开源许可证。常见的开源许可证包括GPL、MIT、BSD、Apache等。

2. 是否有特殊的专利需求？

如果您的项目涉及到专利，那么应该选择一种带有专利授权条款的许可证。Apache许可证就是这样一种带有专利授权条款的许可证。

3. 是否需要强制保留相同的许可证？

如果您希望衍生作品必须保留相同的许可证，那么应该选择类似于GPL的许可证。如果您不需要强制保留相同的许可证，则可以选择类似于MIT或BSD的许可证。

4. 是否需要与其他库或框架进行整合？

如果您的项目需要与其他开源库或框架进行整合，那么应该选择与这些库或框架兼容的许可证。常见的兼容性较好的许可证包括MIT和BSD。



### SPDX

SPDX is an open standard for communicating software bill of material information, including provenance, license, security, and other related information. 



### RLP & SSZ

RLP（Recursive Length Prefix） 和 SSZ（Simple Serialize）都是 Ethereum 中常用的序列化格式。

RLP 是一种将任意数据结构编码为字节数组的序列化格式，采用了递归长度前缀编码。在以太坊协议中，RLP 被广泛用于编码交易、区块头、状态数据、智能合约数据等各种数据对象。

SSZ 是一种基于 RL 编码的二进制格式序列化方案，它通过限制数据结构的类型和字段顺序来降低序列化和反序列化的复杂性。