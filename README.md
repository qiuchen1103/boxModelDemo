#盒模型的几个难点总结

###盒模型包括：content、padding、border、margin

一、box-sizing
    
    **我们在CSS里设置的width、height都包括了些什么？**
    box-sizing: content-box|border-box|inherit;

    1.content-box
        设置width = 盒模型content

    2.border-box（常用）
        设置width = 盒content + 盒padding + 盒border
                  = 元素在文档流中实际占据width
        优点：应对改元素实际占据宽度的需求，我们可以直接改写width属性，如果用content-box则要经过一系列计算。
        bootstrap:
            * {box-sizing: border-box}
            hr {box-sizing: content-box} /*文档水平线*/
            input[type="search"] {box-sizing: content-box}

    caniuse：全支持，免浏览器前缀

二、margin（用padding还是用margin？）

    margin-top和margin-bottom对行内(display:inline)元素无效，除了<img>、<video>和表单元素，如<textarea>、<input>、等等... (详情可搜索：可替换元素)

    1.垂直margin合并
        **块元素的上下外边距会被合并**
        inline、inline-block元素不会发生合并
        左右边距不会发生合并
    
    2.负margin