### 运行
1. 在根目录下执行 `sass sass/animation.scss:index.css`
2. 运行根目录下的 `index.html`

### 数据需要以这样的方式排列（每一列的数据放在一个数组中，所有的列组成外层的数组）：
```
    data: [
        ['Row 1 Column 1', 'Row 2 Column 1', 'Row 3 Column 1'], 
        ['Row 1 Column 2', 'Row 2 Column 2', 'Row 3 Column 2'],
        ['Row 1 Column 3', 'Row 2 Column 3', 'Row 3 Column 3'],
        ['Row 1 Column 4', 'Row 2 Column 4', 'Row 3 Column 4']
    ]
```

### 在自己的项目中使用：
1. 你的项目中已经使用了 Vue.js 和 ElementUI
2. 引入本例中的一个文件： `sass/animation.scss`
3. 为需要动画的部分加上相应的类名，最外层的容器加上想要的动画类名如 `animation-scale`，
列的容器加上类名 `column-0`、`column-1`、`column-2`……，行加上类名 `row-0`、`row-1`、`row-2`……
```
    <el-row class="animation-scale">
        <el-col :class="'column-'+ columnIndex" v-for="(column, columnIndex) in data">
            <div :class="'row-'+ index " v-for="(item, index) in column">{{ item }}</div>
        </el-col>
    </el-row>
```

### 动画对应的类的名称：
动画|类的名称
:-|:-
Scale 缩放|animation-scale
Widen 变宽|animation-scale
Fall 下落|animation-widen
Rotate 旋转|animation-rotate
Appear 渐显|animation-appear

> 目前能允许的最大行数和列数均是20，如果需要增加可以修改 `sass/animation.scss` 中 `$maxColumnAmount` 和 `$maxRowAmount` 的值。