#盒模型的几个难点总结

###盒模型包括：content、padding、border、margin

一、box-sizing
    
    **我们在CSS里设置的width、height都包括了些什么？**
    box-sizing: content-box|border-box|inherit;

    1.content-box
        设置width = 盒模型content

    2.border-box（常用）
        设置width = 盒content + 盒padding + 盒border
        优点：应对改元素的物理宽度的需求，我们可以直接改写width属性，如果用content-box则要经过一系列计算。
        bootstrap:
            * {box-sizing: border-box}
            hr {box-sizing: content-box} /*文档水平线*/
            input[type="search"] {box-sizing: content-box}

    caniuse：全支持，免浏览器前缀

二、margin

    margin-top和margin-bottom对行内(display:inline)元素无效，除了<img>、<video>和表单元素，如<textarea>、<input>、等等... (详情可搜索：可替换元素)

    1.垂直margin合并
        **块元素的上下外边距会被合并**
        inline、inline-block元素不会发生合并
        左右边距不会发生合并
    
    2.负margin
        **块元素的负margin**

        实际大小 = content + padding + border + 正的margin
        物理大小 = content + padding + border

        1.定宽的块元素
        负的 margin 值不会影响 定宽块元素 的 物理大小。
        如果是负的 margin-top 或 margin-left 值只会引起 块元素 的向上或向左位置移动，如果是负的 margin-bottom 或 margin-right 则会影响 相邻块元素 的显示起始线。

        2.不定宽的块元素
        负的 margin-left、margin-right 能 增大 不定宽元素 的 物理大小。
        bootstrap 的 .row 和 .col- 一定要同时使用，缺一不可。
