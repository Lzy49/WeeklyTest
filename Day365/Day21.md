# innerText & nodeValue & textContent

## 什么是 DOM

浏览器编译`html`的过程中会将所有标签根据嵌套关系组成一个 DOM 树，这个 DOM 树 的根节点是`html` 标签。

## DOM 类型

DOM 类型有很多种，在节点的`nodeType` 有体现。

- 元素节点 : `Node.ELEMENT_NODE(1)`
- 属性节点 : `Node.ATTRIBUTE_NODE(2) `
- 文本节点 : `Node.TEXT_NODE(3) `
- CDATA 节点 : `Node.CDATA_SECTION_NODE(4)`
- 实体引用名称节点 : `Node.ENTRY_REFERENCE_NODE(5)`
- 实体名称节点 : `Node.ENTITY_NODE(6) `
- 处理指令节点 : `Node.PROCESSING_INSTRUCTION_NODE(7) `
- 注释节点 : `Node.COMMENT_NODE(8) `
- 文档节点 : `Node.DOCUMENT_NODE(9) `
- 文档类型节点 :`Node.DOCUMENT_TYPE_NODE(10) `
- 文档片段节点 :`Node.DOCUMENT_FRAGMENT_NODE(11) `
- DTD 声明节点: `Node.NOTATION_NODE(12)`

## innerText, innerHTML, nodeValue, textContent 的 区别

- `nodeValue` 只能获取到节点本身，的文字，而节点子节点是不能获取的。
- `innerText` 获取子节点，但节点中没有标签。只有文字
- `innerHTML` 获取子节点，包括 HTML
- `textContent` 与 `innerText` 相同获取子节点，且没有标签。区别是 `innerText` 可以获取`display:none` 的文字，而`textContent` 不能
