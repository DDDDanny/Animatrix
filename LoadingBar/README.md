## Loading Bar

### CSS实现Material Input效果

<div>
    <p align="center">
        <img src="001.gif" alt="001" style="width:900%;" />
    </p>
</div>

### 实现过程中，需要记忆的点

#### 渐变实现

使用`linear-gradient`属性

```css
/* 默认角度是从上到下，90deg 逆时针旋转后变成从左到右渐变 */
background: linear-gradient(
            90deg,
            var(--gradient-color-1),
            var(--gradient-color-2),
            var(--gradient-color-3),
            var(--gradient-color-4),
            var(--gradient-color-1),
            var(--gradient-color-2),
            var(--gradient-color-3),
            var(--gradient-color-4),
            var(--gradient-color-1)
    );
```

#### 发光效果

这里使用`::before`和`::after`来实现，加上毛玻璃效果。`::before`不需要加

```css
.loading-bar::after {
    ...
    /* 毛玻璃 */
    filter: blur(10px);
   	...
}
```

#### animation动画

```css
/* 
	1. animation-name: 动画名称
	2. duration：动画持续时间
	3. timing-function：时间函数，决定了动画的速度曲线（如：linear匀速）
	4. iteration-count：迭代次数，infinite表示无限次
*/ 
animation: <animation-name> <duration> <timing-function> <iteration-count>; 
```

```css
/* @keyframes 规则用于创建 CSS 动画的关键帧 */
/* 
  关键帧：
  0%：表示动画的起始状态，元素的背景位置设置为 0 0，即背景图像的左上角从容器的左上角开始显示。

  100%：表示动画的结束状态，元素的背景位置设置为 200% 0，即背景图像的左上角被移到容器的右侧。200% 表示背景图像	向右移动两倍容器的宽度。 
*/
@keyframes flow {
    100% {
        background-position: 0 0;
    }

    0% {
        background-position: 200% 0;
    }
}
```

### 特别鸣谢
[草帽Plasticine](https://juejin.cn/user/1324240506200781/posts)
